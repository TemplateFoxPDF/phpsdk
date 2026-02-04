# TemplateFox PHP SDK

Official PHP SDK for [TemplateFox](https://pdftemplateapi.com) - Generate PDFs from HTML templates via API.

[![Packagist Version](https://img.shields.io/packagist/v/templatefox/sdk.svg)](https://packagist.org/packages/templatefox/sdk)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Installation

```bash
composer require templatefox/sdk
```

## Requirements

- PHP 7.4 or later
- ext-curl
- ext-json
- ext-mbstring

## Quick Start

```php
<?php

require_once __DIR__ . '/vendor/autoload.php';

use TemplateFox\Api\PDFApi;
use TemplateFox\Configuration;
use TemplateFox\Model\CreatePdfRequest;

// Initialize the client
$config = Configuration::getDefaultConfiguration()
    ->setApiKey('x-api-key', 'your-api-key');

$api = new PDFApi(null, $config);

// Generate a PDF
$request = new CreatePdfRequest([
    'template_id' => 'YOUR_TEMPLATE_ID',
    'data' => [
        'name' => 'John Doe',
        'invoice_number' => 'INV-001',
        'total_amount' => 150.00,
    ],
]);

try {
    $response = $api->createPdf($request);
    echo "PDF URL: " . $response->getUrl() . "\n";
    echo "Credits remaining: " . $response->getCreditsRemaining() . "\n";
} catch (Exception $e) {
    echo "Error: " . $e->getMessage() . "\n";
}
```

## Features

- **Template-based PDF generation** - Create templates with dynamic variables, generate PDFs with your data
- **Multiple export options** - Get a signed URL (default) or raw binary PDF
- **S3 integration** - Upload generated PDFs directly to your own S3-compatible storage
- **PSR-18 compatible** - Works with any PSR-18 HTTP client

## API Methods

### PDF Generation

```php
$request = new CreatePdfRequest([
    'template_id' => 'TEMPLATE_ID',
    'data' => ['name' => 'John Doe'],
    'export_type' => 'url',      // 'url' or 'binary'
    'expiration' => 86400,       // URL expiration in seconds
    'filename' => 'invoice-001', // Custom filename
]);

$response = $api->createPdf($request);
```

### Templates

```php
use TemplateFox\Api\TemplatesApi;

$templatesApi = new TemplatesApi(null, $config);

// List all templates
$templates = $templatesApi->listTemplates();
foreach ($templates->getTemplates() as $template) {
    echo $template->getId() . ": " . $template->getName() . "\n";
}

// Get template fields
$fields = $templatesApi->getTemplateFields('TEMPLATE_ID');
foreach ($fields as $field) {
    echo $field->getKey() . ": " . $field->getType() . "\n";
}
```

### Account

```php
use TemplateFox\Api\AccountApi;

$accountApi = new AccountApi(null, $config);

// Get account info
$account = $accountApi->getAccount();
echo "Credits: " . $account->getCredits() . "\n";
echo "Email: " . $account->getEmail() . "\n";

// List transactions
$transactions = $accountApi->listTransactions(100, 0);
foreach ($transactions->getTransactions() as $tx) {
    echo $tx->getTransactionType() . ": " . $tx->getCredits() . " credits\n";
}
```

### S3 Integration

```php
use TemplateFox\Api\IntegrationsApi;
use TemplateFox\Model\S3ConfigRequest;

$integrationsApi = new IntegrationsApi(null, $config);

// Save S3 configuration
$s3Config = new S3ConfigRequest([
    'endpoint_url' => 'https://s3.amazonaws.com',
    'access_key_id' => 'AKIAIOSFODNN7EXAMPLE',
    'secret_access_key' => 'your-secret-key',
    'bucket_name' => 'my-pdf-bucket',
    'default_prefix' => 'generated/pdfs/',
]);

$integrationsApi->saveS3Config($s3Config);

// Test connection
$test = $integrationsApi->testS3Connection();
echo "Connection: " . ($test->getSuccess() ? "OK" : "Failed") . "\n";
```

## Configuration

```php
$config = Configuration::getDefaultConfiguration()
    ->setHost('https://api.pdftemplateapi.com')  // Default API URL
    ->setApiKey('x-api-key', getenv('TEMPLATEFOX_API_KEY'));
```

## Error Handling

```php
use TemplateFox\ApiException;

try {
    $response = $api->createPdf($request);
} catch (ApiException $e) {
    switch ($e->getCode()) {
        case 402:
            echo "Insufficient credits\n";
            break;
        case 403:
            echo "Access denied - check your API key\n";
            break;
        case 404:
            echo "Template not found\n";
            break;
        default:
            echo "Error: " . $e->getMessage() . "\n";
    }
}
```

## Laravel Integration

```php
// config/services.php
'templatefox' => [
    'api_key' => env('TEMPLATEFOX_API_KEY'),
],

// AppServiceProvider.php
use TemplateFox\Api\PDFApi;
use TemplateFox\Configuration;

public function register()
{
    $this->app->singleton(PDFApi::class, function ($app) {
        $config = Configuration::getDefaultConfiguration()
            ->setApiKey('x-api-key', config('services.templatefox.api_key'));
        return new PDFApi(null, $config);
    });
}
```

## Documentation

- [API Documentation](https://pdftemplateapi.com/docs)
- [Swagger UI](https://api.pdftemplateapi.com/docs)
- [Dashboard](https://pdftemplateapi.com/dashboard)

## Support

- Email: support@pdftemplateapi.com
- Issues: [GitHub Issues](https://github.com/TemplateFoxPDF/phpsdk/issues)

## License

MIT License - see [LICENSE](LICENSE) for details.
