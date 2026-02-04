# # S3ConfigRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**endpoint_url** | **string** | S3-compatible endpoint URL. Must start with https:// |
**access_key_id** | **string** | Access key ID for S3 authentication |
**secret_access_key** | **string** |  | [optional]
**bucket_name** | **string** | S3 bucket name. Must follow S3 naming conventions (lowercase, no underscores) |
**default_prefix** | **string** | Default path prefix for uploaded files. Can include slashes for folder structure | [optional] [default to '']

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
