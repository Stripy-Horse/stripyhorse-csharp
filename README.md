# Stripy Horse C# SDK

Official .NET client for the [Stripy Horse](https://stripyhorse.io) API - Zebra/ZPL
developer tools: render ZPL to PNG, convert PDFs/images/HTML to print-ready ZPL,
and drive hosted virtual Zebra printers from your tests.

Generated from the live [OpenAPI spec](https://stripyhorse.io/openapi.yaml), which is
itself emitted from the server's handler code, so the SDK can never drift from the API.

Targets .NET 8.

## Install

```bash
dotnet add package StripyHorse
```

## Setup

```csharp
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

var config = new Configuration { AccessToken = "sh_live_YOUR_KEY" };
```

## Render ZPL to PNG

```csharp
var render = new RenderApi(config);
var outp = render.RenderZpl(new RenderInputBody(
    zpl: "^XA^FO50,50^A0N,45,45^FDHello^FS^XZ",
    preset: RenderInputBody.PresetEnum._4x6));
File.WriteAllBytes("label.png", Convert.FromBase64String(outp.Labels[0].Png));
```

## Convert a PDF (or PNG/GIF/JPEG) to ZPL

```csharp
var convert = new ConvertApi(config);
using var pdf = File.OpenRead("shipping-label.pdf");
var result = convert.ConvertDocument(pdf, preset: "4x6");  // multipart params stay strings
foreach (var page in result.Pages)
    SendToPrinter(page.Zpl);
```

## Design a label in HTML, get ZPL

```csharp
var outp = convert.ConvertHtml(new HtmlInputBody(
    html: """<div style="position:absolute;left:40px;top:40px;font-size:50px">Hello</div>""",
    preset: HtmlInputBody.PresetEnum._4x6));
Console.WriteLine(outp.Zpl);
```

## Test label printing in CI with a virtual printer

```csharp
var sim = new SimulatorApi(config);

var printer = sim.CreatePrinter(new CreatePrinterInputBody(
    name: "ci-run-42", preset: CreatePrinterInputBody.PresetEnum._4x6));

// Point the system under test at the printer, exactly like hardware:
var addr = $"{printer.Tcp.Host}:{printer.Tcp.Port}";

// ... run your fulfillment code against addr ...

// Then assert on what it printed:
var jobs = sim.ListJobs(printer.Id);
Debug.Assert(jobs.Jobs.Count == 1);

// Reproduce a paper-out jam and watch jobs hold in the buffer:
sim.SetPrinterFaults(printer.Id, new Faults(paperOut: true));
```

Every method also has an `...Async` variant taking a `CancellationToken`.

## Errors

API errors throw `StripyHorse.Client.ApiException`; `ErrorContent` carries the
JSON error envelope. HTTP 429 includes a `Retry-After` header.

## Regenerating

Every file here is generated from the [OpenAPI spec](https://stripyhorse.io/openapi.yaml),
which is emitted from the server's own handler code. Hand edits are overwritten by the
next spec change, so report a problem with the SDK as a problem with the API:
[stripyhorse.io/contact](https://stripyhorse.io/contact).
