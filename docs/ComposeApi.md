# StripyHorse.Api.ComposeApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ComposeLabel**](ComposeApi.md#composelabel) | **POST** /v1/labels/compose | Compose ZPL from typed JSON elements |

<a id="composelabel"></a>
# **ComposeLabel**
> ComposeOutputBody ComposeLabel (ComposeInputBody composeInputBody)

Compose ZPL from typed JSON elements

Labels as JSON: place text, barcodes (code128/39, QR, DataMatrix), boxes, lines, circles, images and raw ZPL passthrough on a label and get back ZPL - optionally with rendered previews. {{name}} in text/data interpolates from the variables map; an unresolved variable is an error, never a blank on a real shipment. Positions are printer dots.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ComposeLabelExample
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

            var apiInstance = new ComposeApi(config);
            var composeInputBody = new ComposeInputBody(); // ComposeInputBody | 

            try
            {
                // Compose ZPL from typed JSON elements
                ComposeOutputBody result = apiInstance.ComposeLabel(composeInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ComposeApi.ComposeLabel: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ComposeLabelWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Compose ZPL from typed JSON elements
    ApiResponse<ComposeOutputBody> response = apiInstance.ComposeLabelWithHttpInfo(composeInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ComposeApi.ComposeLabelWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **composeInputBody** | [**ComposeInputBody**](ComposeInputBody.md) |  |  |

### Return type

[**ComposeOutputBody**](ComposeOutputBody.md)

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

