# StripyHorse.Model.Element

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Align** | **string** | Alignment when wrapping | [optional] 
**CornerRadius** | **long** | Box corner rounding 0-8 | [optional] 
**Data** | **string** | Barcode payload; {{name}} interpolates | [optional] 
**Diameter** | **long** | Circle diameter in dots | [optional] 
**ErrorCorrection** | **string** | QR error correction (default M) | [optional] 
**Font** | **string** | Printer font: 0 (scalable, default) or A-Z | [optional] 
**FontHeight** | **long** | Character height in dots (text) | [optional] 
**FontWidth** | **long** | Character width in dots; 0 follows fontHeight | [optional] 
**Height** | **long** | Bar height in dots (1D) / box height in dots (box) | [optional] 
**Length** | **long** | Line length in dots | [optional] 
**Lines** | **long** | Max lines when wrapping (default 1) | [optional] 
**Magnification** | **long** | QR module magnification (default 3) | [optional] 
**MaxWidth** | **long** | Wrap text into a block this many dots wide | [optional] 
**ModuleSize** | **long** | DataMatrix module size in dots (default 4) | [optional] 
**ModuleWidth** | **long** | Narrow element width in dots (1D; default 3) | [optional] 
**Orientation** | **string** | Line direction | [optional] 
**Png** | **string** | PNG/GIF/JPEG, base64-encoded | [optional] 
**PrintText** | **bool** | Print the human-readable line under 1D barcodes (default true) | [optional] 
**Rotation** | **long** |  | [optional] 
**Text** | **string** | Text content; {{name}} interpolates from variables | [optional] 
**Thickness** | **long** | Stroke thickness in dots (default 1) | [optional] 
**Threshold** | **long** | Bitonal threshold (default 128) | [optional] 
**Type** | **string** | What to place | 
**Width** | **long** | Box/image width in dots | [optional] 
**X** | **long** | Left edge in dots | [optional] 
**Y** | **long** | Top edge in dots | [optional] 
**Zpl** | **string** | Verbatim ZPL commands (raw only) - the escape hatch | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

