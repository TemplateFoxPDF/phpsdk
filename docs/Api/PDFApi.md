# TemplateFox\PDFApi



All URIs are relative to https://api.pdftemplateapi.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createPdf()**](PDFApi.md#createPdf) | **POST** /v1/pdf/create | Generate PDF from template |


## `createPdf()`

```php
createPdf($create_pdf_request): \TemplateFox\Model\CreatePdfResponse
```

Generate PDF from template

Generate a PDF from a saved template with dynamic data.  **Authentication:** API Key required (`x-api-key` header)  ## Request Body  | Field | Type | Required | Description | |-------|------|----------|-------------| | `template_id` | string | ✅ Yes | Template short ID (12 characters) | | `data` | object | ✅ Yes | Key-value data to render in template | | `export_type` | string | No | `url` (default) or `binary` | | `expiration` | integer | No | URL expiration in seconds (60-604800, default: 86400) |  ## Export Types - `url` (default): PDF is uploaded to CDN, returns JSON with URL - `binary`: Returns raw PDF bytes directly  **Credits:** 1 credit deducted per successful generation.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\PDFApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_pdf_request = new \TemplateFox\Model\CreatePdfRequest(); // \TemplateFox\Model\CreatePdfRequest

try {
    $result = $apiInstance->createPdf($create_pdf_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PDFApi->createPdf: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_pdf_request** | [**\TemplateFox\Model\CreatePdfRequest**](../Model/CreatePdfRequest.md)|  | |

### Return type

[**\TemplateFox\Model\CreatePdfResponse**](../Model/CreatePdfResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/pdf`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
