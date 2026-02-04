# TemplateFox\AccountApi



All URIs are relative to https://api.pdftemplateapi.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getAccount()**](AccountApi.md#getAccount) | **GET** /v1/account | Get account info |
| [**listTransactions()**](AccountApi.md#listTransactions) | **GET** /v1/account/transactions | List transactions |


## `getAccount()`

```php
getAccount(): \TemplateFox\Model\AccountInfoResponse
```

Get account info

Get account information including remaining credits.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** Check credit balance before performing operations.  **No credits consumed:** This is a read-only endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\AccountApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getAccount();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AccountApi->getAccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\TemplateFox\Model\AccountInfoResponse**](../Model/AccountInfoResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listTransactions()`

```php
listTransactions($limit, $offset): \TemplateFox\Model\TransactionsResponse
```

List transactions

List transaction history for the authenticated user.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Pagination:** Use `limit` and `offset` query parameters.  **Transaction types:** - `PDFGEN`: PDF generation (consumes credits) - `REFUND`: Credit refund (on failed generation) - `PURCHASE`: Credit purchase - `BONUS`: Bonus credits  **Credits field:** - Positive value = credits consumed - Negative value = credits added  **No credits consumed:** This is a read-only endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: ApiKeyAuth
$config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKey('x-api-key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = TemplateFox\Configuration::getDefaultConfiguration()->setApiKeyPrefix('x-api-key', 'Bearer');


$apiInstance = new TemplateFox\Api\AccountApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$limit = 300; // int | Number of records to return
$offset = 0; // int | Number of records to skip

try {
    $result = $apiInstance->listTransactions($limit, $offset);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AccountApi->listTransactions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **limit** | **int**| Number of records to return | [optional] [default to 300] |
| **offset** | **int**| Number of records to skip | [optional] [default to 0] |

### Return type

[**\TemplateFox\Model\TransactionsResponse**](../Model/TransactionsResponse.md)

### Authorization

[ApiKeyAuth](../../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
