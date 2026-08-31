# StripyHorse.Api.SimulatorApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ClearJobs**](SimulatorApi.md#clearjobs) | **DELETE** /v1/printers/{printerId}/jobs | Delete all captured jobs |
| [**CreatePrinter**](SimulatorApi.md#createprinter) | **POST** /v1/printers | Create a virtual printer |
| [**DeleteJob**](SimulatorApi.md#deletejob) | **DELETE** /v1/printers/{printerId}/jobs/{jobId} | Delete one captured job |
| [**DeletePrinter**](SimulatorApi.md#deleteprinter) | **DELETE** /v1/printers/{printerId} | Delete a printer and its captured jobs |
| [**GetJob**](SimulatorApi.md#getjob) | **GET** /v1/printers/{printerId}/jobs/{jobId} | Get one job including its raw ZPL |
| [**GetJobLabel**](SimulatorApi.md#getjoblabel) | **GET** /v1/printers/{printerId}/jobs/{jobId}/labels/{index}.png | Get one rendered label as a PNG |
| [**GetPrinter**](SimulatorApi.md#getprinter) | **GET** /v1/printers/{printerId} | Get a printer with live state |
| [**ListJobs**](SimulatorApi.md#listjobs) | **GET** /v1/printers/{printerId}/jobs | List captured jobs, newest first |
| [**ListPrinters**](SimulatorApi.md#listprinters) | **GET** /v1/printers | List your printers |
| [**LoadPrinterMedia**](SimulatorApi.md#loadprintermedia) | **POST** /v1/printers/{printerId}/media | Fit a fresh roll and ribbon |
| [**ResetPrinter**](SimulatorApi.md#resetprinter) | **POST** /v1/printers/{printerId}/reset | Clear all faults and flush held jobs |
| [**SetPrinterFaults**](SimulatorApi.md#setprinterfaults) | **POST** /v1/printers/{printerId}/faults | Inject or clear fault conditions |
| [**UpdatePrinter**](SimulatorApi.md#updateprinter) | **PATCH** /v1/printers/{printerId} | Rename a printer or set its webhook URL |

<a id="clearjobs"></a>
# **ClearJobs**
> void ClearJobs (string printerId)

Delete all captured jobs

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ClearJobsExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 

            try
            {
                // Delete all captured jobs
                apiInstance.ClearJobs(printerId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.ClearJobs: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ClearJobsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete all captured jobs
    apiInstance.ClearJobsWithHttpInfo(printerId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.ClearJobsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | No Content |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createprinter"></a>
# **CreatePrinter**
> PrinterBody CreatePrinter (CreatePrinterInputBody createPrinterInputBody)

Create a virtual printer

Free tier: one ephemeral printer, expiring after 4h with no jobs. Paid tiers: persistent printers. The ingest URL and webhook secret are only returned here.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class CreatePrinterExample
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

            var apiInstance = new SimulatorApi(config);
            var createPrinterInputBody = new CreatePrinterInputBody(); // CreatePrinterInputBody | 

            try
            {
                // Create a virtual printer
                PrinterBody result = apiInstance.CreatePrinter(createPrinterInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.CreatePrinter: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreatePrinterWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a virtual printer
    ApiResponse<PrinterBody> response = apiInstance.CreatePrinterWithHttpInfo(createPrinterInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.CreatePrinterWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createPrinterInputBody** | [**CreatePrinterInputBody**](CreatePrinterInputBody.md) |  |  |

### Return type

[**PrinterBody**](PrinterBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletejob"></a>
# **DeleteJob**
> void DeleteJob (string printerId, long jobId)

Delete one captured job

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class DeleteJobExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var jobId = 789L;  // long | 

            try
            {
                // Delete one captured job
                apiInstance.DeleteJob(printerId, jobId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.DeleteJob: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteJobWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete one captured job
    apiInstance.DeleteJobWithHttpInfo(printerId, jobId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.DeleteJobWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **jobId** | **long** |  |  |

### Return type

void (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | No Content |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteprinter"></a>
# **DeletePrinter**
> void DeletePrinter (string printerId)

Delete a printer and its captured jobs

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class DeletePrinterExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 

            try
            {
                // Delete a printer and its captured jobs
                apiInstance.DeletePrinter(printerId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.DeletePrinter: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeletePrinterWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a printer and its captured jobs
    apiInstance.DeletePrinterWithHttpInfo(printerId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.DeletePrinterWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | No Content |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getjob"></a>
# **GetJob**
> JobOutputBody GetJob (string printerId, long jobId)

Get one job including its raw ZPL

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class GetJobExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var jobId = 789L;  // long | 

            try
            {
                // Get one job including its raw ZPL
                JobOutputBody result = apiInstance.GetJob(printerId, jobId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.GetJob: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetJobWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get one job including its raw ZPL
    ApiResponse<JobOutputBody> response = apiInstance.GetJobWithHttpInfo(printerId, jobId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.GetJobWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **jobId** | **long** |  |  |

### Return type

[**JobOutputBody**](JobOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getjoblabel"></a>
# **GetJobLabel**
> string GetJobLabel (string printerId, long jobId, long index)

Get one rendered label as a PNG

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class GetJobLabelExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var jobId = 789L;  // long | 
            var index = 789L;  // long | 

            try
            {
                // Get one rendered label as a PNG
                string result = apiInstance.GetJobLabel(printerId, jobId, index);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.GetJobLabel: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetJobLabelWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get one rendered label as a PNG
    ApiResponse<string> response = apiInstance.GetJobLabelWithHttpInfo(printerId, jobId, index);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.GetJobLabelWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **jobId** | **long** |  |  |
| **index** | **long** |  |  |

### Return type

**string**

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  * Content-Type -  <br>  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprinter"></a>
# **GetPrinter**
> PrinterBody GetPrinter (string printerId)

Get a printer with live state

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class GetPrinterExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 

            try
            {
                // Get a printer with live state
                PrinterBody result = apiInstance.GetPrinter(printerId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.GetPrinter: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPrinterWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a printer with live state
    ApiResponse<PrinterBody> response = apiInstance.GetPrinterWithHttpInfo(printerId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.GetPrinterWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |

### Return type

[**PrinterBody**](PrinterBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listjobs"></a>
# **ListJobs**
> ListJobsOutputBody ListJobs (string printerId, long? limit = null, long? before = null)

List captured jobs, newest first

For CI assertions and inbox views. Cursor-paged via before.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ListJobsExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var limit = 50L;  // long? |  (optional)  (default to 50)
            var before = 789L;  // long? | Return jobs with id lower than this cursor (optional) 

            try
            {
                // List captured jobs, newest first
                ListJobsOutputBody result = apiInstance.ListJobs(printerId, limit, before);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.ListJobs: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListJobsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List captured jobs, newest first
    ApiResponse<ListJobsOutputBody> response = apiInstance.ListJobsWithHttpInfo(printerId, limit, before);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.ListJobsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **limit** | **long?** |  | [optional] [default to 50] |
| **before** | **long?** | Return jobs with id lower than this cursor | [optional]  |

### Return type

[**ListJobsOutputBody**](ListJobsOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listprinters"></a>
# **ListPrinters**
> ListPrintersOutputBody ListPrinters ()

List your printers

Every printer on your account, whichever of its keys created them.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ListPrintersExample
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

            var apiInstance = new SimulatorApi(config);

            try
            {
                // List your printers
                ListPrintersOutputBody result = apiInstance.ListPrinters();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.ListPrinters: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListPrintersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List your printers
    ApiResponse<ListPrintersOutputBody> response = apiInstance.ListPrintersWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.ListPrintersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ListPrintersOutputBody**](ListPrintersOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="loadprintermedia"></a>
# **LoadPrinterMedia**
> StateOutputBody LoadPrinterMedia (string printerId, MediaInputBody mediaInputBody)

Fit a fresh roll and ribbon

A loaded roll runs down as labels print and raises paper out when it is spent, which holds everything sent after it. Zero is an endless roll, which is the default and never runs out.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class LoadPrinterMediaExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var mediaInputBody = new MediaInputBody(); // MediaInputBody | 

            try
            {
                // Fit a fresh roll and ribbon
                StateOutputBody result = apiInstance.LoadPrinterMedia(printerId, mediaInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.LoadPrinterMedia: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the LoadPrinterMediaWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Fit a fresh roll and ribbon
    ApiResponse<StateOutputBody> response = apiInstance.LoadPrinterMediaWithHttpInfo(printerId, mediaInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.LoadPrinterMediaWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **mediaInputBody** | [**MediaInputBody**](MediaInputBody.md) |  |  |

### Return type

[**StateOutputBody**](StateOutputBody.md)

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

<a id="resetprinter"></a>
# **ResetPrinter**
> StateOutputBody ResetPrinter (string printerId)

Clear all faults and flush held jobs

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class ResetPrinterExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 

            try
            {
                // Clear all faults and flush held jobs
                StateOutputBody result = apiInstance.ResetPrinter(printerId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.ResetPrinter: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ResetPrinterWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Clear all faults and flush held jobs
    ApiResponse<StateOutputBody> response = apiInstance.ResetPrinterWithHttpInfo(printerId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.ResetPrinterWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |

### Return type

[**StateOutputBody**](StateOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="setprinterfaults"></a>
# **SetPrinterFaults**
> StateOutputBody SetPrinterFaults (string printerId, Faults faults)

Inject or clear fault conditions

Blocking faults hold incoming jobs in the receive buffer; clearing them flushes the queue in order.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class SetPrinterFaultsExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var faults = new Faults(); // Faults | 

            try
            {
                // Inject or clear fault conditions
                StateOutputBody result = apiInstance.SetPrinterFaults(printerId, faults);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.SetPrinterFaults: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SetPrinterFaultsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Inject or clear fault conditions
    ApiResponse<StateOutputBody> response = apiInstance.SetPrinterFaultsWithHttpInfo(printerId, faults);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.SetPrinterFaultsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **faults** | [**Faults**](Faults.md) |  |  |

### Return type

[**StateOutputBody**](StateOutputBody.md)

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

<a id="updateprinter"></a>
# **UpdatePrinter**
> PrinterBody UpdatePrinter (string printerId, UpdatePrinterInputBody updatePrinterInputBody)

Rename a printer or set its webhook URL

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using StripyHorse.Api;
using StripyHorse.Client;
using StripyHorse.Model;

namespace Example
{
    public class UpdatePrinterExample
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

            var apiInstance = new SimulatorApi(config);
            var printerId = "printerId_example";  // string | 
            var updatePrinterInputBody = new UpdatePrinterInputBody(); // UpdatePrinterInputBody | 

            try
            {
                // Rename a printer or set its webhook URL
                PrinterBody result = apiInstance.UpdatePrinter(printerId, updatePrinterInputBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling SimulatorApi.UpdatePrinter: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdatePrinterWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Rename a printer or set its webhook URL
    ApiResponse<PrinterBody> response = apiInstance.UpdatePrinterWithHttpInfo(printerId, updatePrinterInputBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling SimulatorApi.UpdatePrinterWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **printerId** | **string** |  |  |
| **updatePrinterInputBody** | [**UpdatePrinterInputBody**](UpdatePrinterInputBody.md) |  |  |

### Return type

[**PrinterBody**](PrinterBody.md)

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

