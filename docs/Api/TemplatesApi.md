# TemplateFox\TemplatesApi



All URIs are relative to https://api.pdftemplateapi.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getTemplateFields()**](TemplatesApi.md#getTemplateFields) | **GET** /v1/templates/{template_id}/fields | Get template fields |
| [**listTemplates()**](TemplatesApi.md#listTemplates) | **GET** /v1/templates | List templates |


## `getTemplateFields()`

```php
getTemplateFields($template_id): \TemplateFox\Model\TemplateField[]
```

Get template fields

Get the dynamic fields for a template.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** This endpoint is designed for Zapier Dynamic Fields integration. It returns an array of field definitions that Zapier uses to dynamically generate input forms.  **Response format:** Array of objects compatible with Zapier InputFieldsSchema. Each field has: `key`, `label`, `type`, `required`, and optional `helpText`.  **Field types:** - `string`: Text input (also used for JSON arrays/objects) - `integer`: Integer number - `number`: Decimal number - `boolean`: True/False checkbox  **Arrays and objects:** Complex types are returned as `string` type with a `helpText` showing the expected JSON format.  **No credits consumed:** This is a read-only endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string

try {
    $result = $apiInstance->getTemplateFields($template_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->getTemplateFields: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**|  | |

### Return type

[**\TemplateFox\Model\TemplateField[]**](../Model/TemplateField.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listTemplates()`

```php
listTemplates(): \TemplateFox\Model\TemplatesListResponse
```

List templates

List all templates for the authenticated user.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** This endpoint is designed for no-code tools (Zapier, Make, n8n) to populate template selection dropdowns.  **No credits consumed:** This is a read-only endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listTemplates();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->listTemplates: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\TemplateFox\Model\TemplatesListResponse**](../Model/TemplatesListResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
