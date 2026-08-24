# StripyHorse.Api.RenderApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**RenderZpl**](RenderApi.md#renderzpl) | **POST** /v1/render | Render ZPL to PNG images |
| [**RenderZplPng**](RenderApi.md#renderzplpng) | **POST** /v1/render.png | Render ZPL and return the first label as a raw PNG |

<a id="renderzpl"></a>
# **RenderZpl**
> RenderOutputBody RenderZpl (RenderInputBody renderInputBody)

Render ZPL to PNG images

Renders every label in the ZPL stream. For a raw PNG of a single label use renderZplPng.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class RenderZplExample
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

            var apiInstance = new RenderApi(config);
            var renderInputBody = new RenderInputBody(); // RenderInputBody | 

            try
            {
                // Render ZPL to PNG images
                RenderOutputBody result = apiInstance.RenderZpl(renderInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RenderApi.RenderZpl: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RenderZplWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Render ZPL to PNG images
    ApiResponse<RenderOutputBody> response = apiInstance.RenderZplWithHttpInfo(renderInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RenderApi.RenderZplWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **renderInputBody** | [**RenderInputBody**](RenderInputBody.md) |  |  |

### Return type

[**RenderOutputBody**](RenderOutputBody.md)

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

<a id="renderzplpng"></a>
# **RenderZplPng**
> string RenderZplPng (RenderInputBody renderInputBody)

Render ZPL and return the first label as a raw PNG

curl-friendly variant: the X-Label-Count response header carries the total label count.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class RenderZplPngExample
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

            var apiInstance = new RenderApi(config);
            var renderInputBody = new RenderInputBody(); // RenderInputBody | 

            try
            {
                // Render ZPL and return the first label as a raw PNG
                string result = apiInstance.RenderZplPng(renderInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RenderApi.RenderZplPng: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RenderZplPngWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Render ZPL and return the first label as a raw PNG
    ApiResponse<string> response = apiInstance.RenderZplPngWithHttpInfo(renderInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RenderApi.RenderZplPngWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **renderInputBody** | [**RenderInputBody**](RenderInputBody.md) |  |  |

### Return type

**string**

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  * Content-Type -  <br>  * X-Label-Count -  <br>  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

