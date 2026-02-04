# # CreatePdfRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**template_id** | **string** | **Required.** Template short ID (12 characters) |
**data** | **array<string,mixed>** | **Required.** Key-value data to render in the template. Keys must match template variables. |
**export_type** | [**\TemplateFox\Model\ExportType**](ExportType.md) | Export format: &#x60;url&#x60; uploads to CDN and returns URL, &#x60;binary&#x60; returns raw PDF bytes | [optional]
**expiration** | **int** | URL expiration in seconds. Min: 60 (1 min), Max: 604800 (7 days). Only applies to &#x60;url&#x60; export type. | [optional] [default to 86400]
**filename** | **string** |  | [optional]
**store_s3** | **bool** | Upload to your configured S3 bucket instead of CDN | [optional] [default to false]
**s3_filepath** | **string** |  | [optional]
**s3_bucket** | **string** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
