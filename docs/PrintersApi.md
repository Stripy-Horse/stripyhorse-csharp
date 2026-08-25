# StripyHorse.Api.PrintersApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ParseHostStatus**](PrintersApi.md#parsehoststatus) | **POST** /v1/host-status/parse | Decode a Zebra ~HS host status response |

<a id="parsehoststatus"></a>
# **ParseHostStatus**
> HostStatusOutputBody ParseHostStatus (HostStatusInputBody hostStatusInputBody)

Decode a Zebra ~HS host status response

Parses the three-line ~HS answer a Zebra printer (or our virtual printer) returns on port 9100 into typed fields - paper out, pause, buffer contents, head temperature - so you never write a positional comma parser. Accepts raw bytes, cat -v style ^B/^C markers, or hand-cleaned lines. Does not count against your monthly quota.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ParseHostStatusExample
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

            var apiInstance = new PrintersApi(config);
            var hostStatusInputBody = new HostStatusInputBody(); // HostStatusInputBody | 

            try
            {
                // Decode a Zebra ~HS host status response
                HostStatusOutputBody result = apiInstance.ParseHostStatus(hostStatusInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PrintersApi.ParseHostStatus: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ParseHostStatusWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Decode a Zebra ~HS host status response
    ApiResponse<HostStatusOutputBody> response = apiInstance.ParseHostStatusWithHttpInfo(hostStatusInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PrintersApi.ParseHostStatusWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **hostStatusInputBody** | [**HostStatusInputBody**](HostStatusInputBody.md) |  |  |

### Return type

[**HostStatusOutputBody**](HostStatusOutputBody.md)

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

