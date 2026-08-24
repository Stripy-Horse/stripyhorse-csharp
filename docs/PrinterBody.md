# StripyHorse.Model.PrinterBody

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**CreatedAt** | **DateTime** |  | 
**Dpmm** | **long** |  | 
**ExpiresAt** | **DateTime** |  | [optional] 
**HeightMm** | **double** |  | 
**Id** | **string** |  | 
**IngestUrl** | **string** | HTTPS print capability URL. Only returned on creation. | [optional] 
**Mode** | **string** |  | 
**Name** | **string** |  | 
**State** | [**StatusSnapshot**](StatusSnapshot.md) |  | [optional] 
**Tcp** | [**PrinterBodyTCPStruct**](PrinterBodyTCPStruct.md) |  | 
**WebhookSecret** | **string** | HMAC-SHA256 key for X-Stripy-Horse-Signature. Only returned on creation. | [optional] 
**WebhookUrl** | **string** |  | [optional] 
**WidthMm** | **double** |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

