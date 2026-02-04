# TemplateFox\IntegrationsApi



All URIs are relative to https://api.pdftemplateapi.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**deleteS3Config()**](IntegrationsApi.md#deleteS3Config) | **DELETE** /v1/integrations/s3 | Delete S3 configuration |
| [**getS3Config()**](IntegrationsApi.md#getS3Config) | **GET** /v1/integrations/s3 | Get S3 configuration |
| [**saveS3Config()**](IntegrationsApi.md#saveS3Config) | **POST** /v1/integrations/s3 | Save S3 configuration |
| [**testS3Connection()**](IntegrationsApi.md#testS3Connection) | **POST** /v1/integrations/s3/test | Test S3 connection |


## `deleteS3Config()`

```php
deleteS3Config(): \TemplateFox\Model\S3SuccessResponse
```

Delete S3 configuration

Delete S3 storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Remove your S3 integration. Generated PDFs will use the default CDN storage after deletion.  **Warning:** This action is irreversible. You'll need to reconfigure S3 to use it again.  **No credits consumed:** This is a configuration endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->deleteS3Config();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->deleteS3Config: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\TemplateFox\Model\S3SuccessResponse**](../Model/S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getS3Config()`

```php
getS3Config(): \TemplateFox\Model\S3ConfigResponse
```

Get S3 configuration

Get current S3 storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Retrieve your S3 integration settings. Secret access key is masked for security.  **Returns 404** if S3 is not configured.  **No credits consumed:** This is a read-only endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getS3Config();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->getS3Config: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\TemplateFox\Model\S3ConfigResponse**](../Model/S3ConfigResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `saveS3Config()`

```php
saveS3Config($s3_config_request): \TemplateFox\Model\S3SuccessResponse
```

Save S3 configuration

Save or update S3-compatible storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Configure your S3-compatible storage to receive generated PDFs directly in your own bucket instead of the default CDN.  **Supported providers:** - Amazon S3 - DigitalOcean Spaces - Cloudflare R2 - MinIO - Any S3-compatible storage  **Secret key behavior:** - For new configuration: `secret_access_key` is required - For updates: Omit `secret_access_key` to keep existing value  **No credits consumed:** This is a configuration endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$s3_config_request = new \TemplateFox\Model\S3ConfigRequest(); // \TemplateFox\Model\S3ConfigRequest

try {
    $result = $apiInstance->saveS3Config($s3_config_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->saveS3Config: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **s3_config_request** | [**\TemplateFox\Model\S3ConfigRequest**](../Model/S3ConfigRequest.md)|  | |

### Return type

[**\TemplateFox\Model\S3SuccessResponse**](../Model/S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `testS3Connection()`

```php
testS3Connection(): \TemplateFox\Model\S3TestResponse
```

Test S3 connection

Test S3 connection with stored credentials.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Verify your S3 configuration is working correctly. The test will: 1. Connect to the endpoint 2. Verify bucket access 3. Check write permissions by uploading a small test file  **Prerequisite:** S3 must be configured first using `POST /v1/integrations/s3`  **No credits consumed:** This is a diagnostic endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\IntegrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->testS3Connection();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IntegrationsApi->testS3Connection: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\TemplateFox\Model\S3TestResponse**](../Model/S3TestResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
