# StripyHorse.Api.ConvertApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ConvertBatch**](ConvertApi.md#convertbatch) | **POST** /v1/convert/batch | Convert many documents in one request, results streamed |
| [**ConvertDocument**](ConvertApi.md#convertdocument) | **POST** /v1/convert | Convert a PDF or image to ZPL |
| [**ConvertHtml**](ConvertApi.md#converthtml) | **POST** /v1/convert/html | Convert an HTML label design to ZPL |
| [**ConvertZplToHtml**](ConvertApi.md#convertzpltohtml) | **POST** /v1/convert/zpl-html | Decompile ZPL into editable HTML |
| [**RasterizeUnicode**](ConvertApi.md#rasterizeunicode) | **POST** /v1/unicode | Make Unicode ZPL printable on any Zebra |
| [**VoidZpl**](ConvertApi.md#voidzpl) | **POST** /v1/void | Stamp ZPL as void / do-not-ship |

<a id="convertbatch"></a>
# **ConvertBatch**
> void ConvertBatch (List<System.IO.Stream> files, bool? barcodeAware = null, string? compression = null, long? dpmm = null, double? heightMm = null, string? preset = null, long? rotation = null, string? scale = null, long? threshold = null, double? widthMm = null)

Convert many documents in one request, results streamed

Upload up to 20 PDFs/images as repeated `files` fields. The response is application/x-ndjson: one JSON object per converted page, streamed as each page finishes — `{\"file\":…,\"page\":…,\"pageCount\":…,\"zpl\":…}` on success, `{\"file\":…,\"error\":…}` per failed file (remaining files still convert).

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ConvertBatchExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.stripyhorse.io";
            // Configure API key authorization: headerKey
            config.AddApiKey("X-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Api-Key", "Bearer");
            // Configure Bearer token for authorization: bearerKey
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ConvertApi(config);
            var files = new List<System.IO.Stream>(); // List<System.IO.Stream> | 
            var barcodeAware = true;  // bool? |  (optional) 
            var compression = "compression_example";  // string? |  (optional) 
            var dpmm = 789L;  // long? |  (optional) 
            var heightMm = 1.2D;  // double? |  (optional) 
            var preset = "preset_example";  // string? |  (optional) 
            var rotation = 789L;  // long? |  (optional) 
            var scale = "scale_example";  // string? |  (optional) 
            var threshold = 789L;  // long? |  (optional) 
            var widthMm = 1.2D;  // double? |  (optional) 

            try
            {
                // Convert many documents in one request, results streamed
                apiInstance.ConvertBatch(files, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ConvertApi.ConvertBatch: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ConvertBatchWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Convert many documents in one request, results streamed
    apiInstance.ConvertBatchWithHttpInfo(files, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ConvertApi.ConvertBatchWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **files** | **List&lt;System.IO.Stream&gt;** |  |  |
| **barcodeAware** | **bool?** |  | [optional]  |
| **compression** | **string?** |  | [optional]  |
| **dpmm** | **long?** |  | [optional]  |
| **heightMm** | **double?** |  | [optional]  |
| **preset** | **string?** |  | [optional]  |
| **rotation** | **long?** |  | [optional]  |
| **scale** | **string?** |  | [optional]  |
| **threshold** | **long?** |  | [optional]  |
| **widthMm** | **double?** |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="convertdocument"></a>
# **ConvertDocument**
> ConvertOutputBody ConvertDocument (System.IO.Stream file, bool? barcodeAware = null, string? compression = null, long? dpmm = null, double? heightMm = null, string? preset = null, long? rotation = null, string? scale = null, long? threshold = null, double? widthMm = null)

Convert a PDF or image to ZPL

Each page becomes its own ^GFA command (Zebra ACS run-length compression). PDFs up to 16 pages.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ConvertDocumentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.stripyhorse.io";
            // Configure API key authorization: headerKey
            config.AddApiKey("X-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Api-Key", "Bearer");
            // Configure Bearer token for authorization: bearerKey
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ConvertApi(config);
            var file = new System.IO.MemoryStream(System.IO.File.ReadAllBytes("/path/to/file.txt"));  // System.IO.Stream | PDF, PNG, GIF or JPEG
            var barcodeAware = true;  // bool? | EXPERIMENTAL: re-emit decodable barcodes as native ^BC/^BQ fields, verified by a decode round trip with automatic fallback to plain rasterization (optional) 
            var compression = "compression_example";  // string? | acs (default) or z64 (zlib+base64, smaller payloads) (optional) 
            var dpmm = 789L;  // long? |  (optional) 
            var heightMm = 1.2D;  // double? |  (optional) 
            var preset = "preset_example";  // string? |  (optional) 
            var rotation = 789L;  // long? |  (optional) 
            var scale = "scale_example";  // string? | cover (fit), fill (stretch) or none (optional) 
            var threshold = 789L;  // long? |  (optional) 
            var widthMm = 1.2D;  // double? |  (optional) 

            try
            {
                // Convert a PDF or image to ZPL
                ConvertOutputBody result = apiInstance.ConvertDocument(file, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ConvertApi.ConvertDocument: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ConvertDocumentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Convert a PDF or image to ZPL
    ApiResponse<ConvertOutputBody> response = apiInstance.ConvertDocumentWithHttpInfo(file, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ConvertApi.ConvertDocumentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **file** | **System.IO.Stream****System.IO.Stream** | PDF, PNG, GIF or JPEG |  |
| **barcodeAware** | **bool?** | EXPERIMENTAL: re-emit decodable barcodes as native ^BC/^BQ fields, verified by a decode round trip with automatic fallback to plain rasterization | [optional]  |
| **compression** | **string?** | acs (default) or z64 (zlib+base64, smaller payloads) | [optional]  |
| **dpmm** | **long?** |  | [optional]  |
| **heightMm** | **double?** |  | [optional]  |
| **preset** | **string?** |  | [optional]  |
| **rotation** | **long?** |  | [optional]  |
| **scale** | **string?** | cover (fit), fill (stretch) or none | [optional]  |
| **threshold** | **long?** |  | [optional]  |
| **widthMm** | **double?** |  | [optional]  |

### Return type

[**ConvertOutputBody**](ConvertOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="converthtml"></a>
# **ConvertHtml**
> HtmlOutputBody ConvertHtml (HtmlInputBody htmlInputBody)

Convert an HTML label design to ZPL

Renders the HTML at exact print resolution (headless Chrome, network access blocked) and rasterizes it — except `<zpl-barcode type=\"code128|qr\" data=\"…\">` elements, which are measured from the layout and emitted as native ^BC/^BQ fields at their exact boxes. Size and position them with CSS (`left/top/width/height`); optional `module` (^BY dots) and `mag` (QR magnification) attributes pin exact bar geometry instead of fitting it to the box. Unsupported types or unencodable data fail loudly.  **PHP** (`composer require stripyhorse/stripyhorse-php`): ```php $out = $convert->convertHtml(new StripyHorse\\Model\\HtmlInputBody([     'html' => '<div style=\"position:absolute;left:40px;top:40px;font-size:50px\">Hello</div>',     'preset' => '4x6', ])); echo $out->getZpl(); ```

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ConvertHtmlExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.stripyhorse.io";
            // Configure API key authorization: headerKey
            config.AddApiKey("X-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Api-Key", "Bearer");
            // Configure Bearer token for authorization: bearerKey
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ConvertApi(config);
            var htmlInputBody = new HtmlInputBody(); // HtmlInputBody | 

            try
            {
                // Convert an HTML label design to ZPL
                HtmlOutputBody result = apiInstance.ConvertHtml(htmlInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ConvertApi.ConvertHtml: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ConvertHtmlWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Convert an HTML label design to ZPL
    ApiResponse<HtmlOutputBody> response = apiInstance.ConvertHtmlWithHttpInfo(htmlInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ConvertApi.ConvertHtmlWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **htmlInputBody** | [**HtmlInputBody**](HtmlInputBody.md) |  |  |

### Return type

[**HtmlOutputBody**](HtmlOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="convertzpltohtml"></a>
# **ConvertZplToHtml**
> ZplHTMLOutputBody ConvertZplToHtml (ZplHTMLInputBody zplHTMLInputBody)

Decompile ZPL into editable HTML

The migration path for legacy ZPL templates: text, boxes and Code128/QR barcodes become editable HTML in the dialect convertHtml accepts; unsupported elements (raster graphics, exotic barcodes) are embedded as positioned images so the layout survives. Round-tripping through convertHtml preserves scannable barcodes.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ConvertZplToHtmlExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.stripyhorse.io";
            // Configure API key authorization: headerKey
            config.AddApiKey("X-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Api-Key", "Bearer");
            // Configure Bearer token for authorization: bearerKey
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ConvertApi(config);
            var zplHTMLInputBody = new ZplHTMLInputBody(); // ZplHTMLInputBody | 

            try
            {
                // Decompile ZPL into editable HTML
                ZplHTMLOutputBody result = apiInstance.ConvertZplToHtml(zplHTMLInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ConvertApi.ConvertZplToHtml: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ConvertZplToHtmlWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Decompile ZPL into editable HTML
    ApiResponse<ZplHTMLOutputBody> response = apiInstance.ConvertZplToHtmlWithHttpInfo(zplHTMLInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ConvertApi.ConvertZplToHtmlWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **zplHTMLInputBody** | [**ZplHTMLInputBody**](ZplHTMLInputBody.md) |  |  |

### Return type

[**ZplHTMLOutputBody**](ZplHTMLOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="rasterizeunicode"></a>
# **RasterizeUnicode**
> UnicodeOutputBody RasterizeUnicode (UnicodeInputBody unicodeInputBody)

Make Unicode ZPL printable on any Zebra

Text fields containing characters the printer's fonts can't render — Arabic (contextual joining, RTL), Cyrillic, and everything else beyond ASCII — are shaped properly and re-emitted as ^GFA bitmaps at the field's exact position and size. Every other byte (barcodes, ASCII text, graphics) passes through untouched. Fields that can't be converted safely (rotated, ^FH-escaped) are left unchanged and reported in `skipped`.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class RasterizeUnicodeExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.stripyhorse.io";
            // Configure API key authorization: headerKey
            config.AddApiKey("X-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Api-Key", "Bearer");
            // Configure Bearer token for authorization: bearerKey
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ConvertApi(config);
            var unicodeInputBody = new UnicodeInputBody(); // UnicodeInputBody | 

            try
            {
                // Make Unicode ZPL printable on any Zebra
                UnicodeOutputBody result = apiInstance.RasterizeUnicode(unicodeInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ConvertApi.RasterizeUnicode: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RasterizeUnicodeWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Make Unicode ZPL printable on any Zebra
    ApiResponse<UnicodeOutputBody> response = apiInstance.RasterizeUnicodeWithHttpInfo(unicodeInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ConvertApi.RasterizeUnicodeWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **unicodeInputBody** | [**UnicodeInputBody**](UnicodeInputBody.md) |  |  |

### Return type

[**UnicodeOutputBody**](UnicodeOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="voidzpl"></a>
# **VoidZpl**
> VoidOutputBody VoidZpl (VoidInputBody voidInputBody)

Stamp ZPL as void / do-not-ship

Overlays a large diagonal VOID - DO NOT MAIL warning (and an optional attribution stamp) across every label in the stream, so printed dev and test labels can never be mistaken for shippable ones. Original fields are untouched; stamps draw on top.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class VoidZplExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.stripyhorse.io";
            // Configure API key authorization: headerKey
            config.AddApiKey("X-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Api-Key", "Bearer");
            // Configure Bearer token for authorization: bearerKey
            config.AccessToken = "YOUR_BEARER_TOKEN";

            var apiInstance = new ConvertApi(config);
            var voidInputBody = new VoidInputBody(); // VoidInputBody | 

            try
            {
                // Stamp ZPL as void / do-not-ship
                VoidOutputBody result = apiInstance.VoidZpl(voidInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ConvertApi.VoidZpl: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the VoidZplWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Stamp ZPL as void / do-not-ship
    ApiResponse<VoidOutputBody> response = apiInstance.VoidZplWithHttpInfo(voidInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ConvertApi.VoidZplWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **voidInputBody** | [**VoidInputBody**](VoidInputBody.md) |  |  |

### Return type

[**VoidOutputBody**](VoidOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

