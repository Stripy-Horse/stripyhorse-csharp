# StripyHorse.Model.CreatePrinterInputBody

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AccessMode** | **string** | Who may print to the TCP port; default open. Use token from CI, where the source address is different every run. | [optional] 
**Anonymize** | **bool** | Mask PII and strip graphics from every captured frame | [optional] 
**Dpmm** | **long** | Print density in dots/mm (152/203/300/600 dpi); default 8 | [optional] 
**HeightMm** | **double** |  | [optional] 
**Mode** | **string** |  | [optional] 
**Name** | **string** |  | 
**Preset** | **string** | Named label size in inches; alternative to widthMm/heightMm | [optional] 
**SharedPort** | **bool** | Put this printer on the shared router port instead of spending one of the plan&#39;s dedicated ports. It is then reached by naming it in the stream, a ZPL comment carrying the ingest token, which suits CI. | [optional] 
**WebhookUrl** | **string** |  | [optional] 
**WidthMm** | **double** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

