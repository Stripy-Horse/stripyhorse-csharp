# StripyHorse.Model.Barcode

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**BlurMarginDots** | **long** | Largest blur radius the symbol survives; 0 &#x3D; no margin | 
**Checks** | [**List&lt;Check&gt;**](Check.md) |  | 
**CrossDpi** | [**List&lt;DPIVerdict&gt;**](DPIVerdict.md) | X-dimension at other print densities, same dot counts | [optional] 
**Format** | **string** | CODE_128, CODE_39, ITF, QR_CODE, DATA_MATRIX | 
**ModuleDots** | **double** | Measured narrow-element width in printer dots (1D only) | [optional] 
**QuietLeftModules** | **double** |  | [optional] 
**QuietRightModules** | **double** |  | [optional] 
**Value** | **string** |  | 
**XDimensionMm** | **double** | Physical narrow-element width at the analyzed density | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

