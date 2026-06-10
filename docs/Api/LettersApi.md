# Doslano\LettersApi

All URIs are relative to https://integration.doslano.ru, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createLetter()**](LettersApi.md#createLetter) | **POST** /v1/letters | Отправить письмо |
| [**getLetter()**](LettersApi.md#getLetter) | **GET** /v1/letters/{id} | Статус письма |
| [**getRecipientTracking()**](LettersApi.md#getRecipientTracking) | **GET** /v1/letters/{id}/recipients/{recipient_id}/tracking | Трек-события получателя |
| [**listLetters()**](LettersApi.md#listLetters) | **GET** /v1/letters | Список писем |


## `createLetter()`

```php
createLetter($create_letter_request, $idempotency_key): \Doslano\Model\Letter
```

Отправить письмо

Создаёт и (по умолчанию) сразу оплачивает с баланса одно заказное письмо одним запросом. Опись формируется автоматически на нашей стороне.  Требуется scope `letters:write`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (API key) authorization: apiKey
$config = Doslano\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Doslano\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_letter_request = new \Doslano\Model\CreateLetterRequest(); // \Doslano\Model\CreateLetterRequest
$idempotency_key = 'idempotency_key_example'; // string | Ключ идемпотентности. Повтор с тем же ключом в течение TTL вернёт исходный результат, не создавая письмо повторно.

try {
    $result = $apiInstance->createLetter($create_letter_request, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->createLetter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_letter_request** | [**\Doslano\Model\CreateLetterRequest**](../Model/CreateLetterRequest.md)|  | |
| **idempotency_key** | **string**| Ключ идемпотентности. Повтор с тем же ключом в течение TTL вернёт исходный результат, не создавая письмо повторно. | [optional] |

### Return type

[**\Doslano\Model\Letter**](../Model/Letter.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getLetter()`

```php
getLetter($id): \Doslano\Model\Letter
```

Статус письма

Полное состояние письма с разбивкой по получателям и трек-номерами. Требуется scope `letters:read`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (API key) authorization: apiKey
$config = Doslano\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Doslano\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | Идентификатор письма.

try {
    $result = $apiInstance->getLetter($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->getLetter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| Идентификатор письма. | |

### Return type

[**\Doslano\Model\Letter**](../Model/Letter.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getRecipientTracking()`

```php
getRecipientTracking($id, $recipient_id): \Doslano\Model\TrackingInfo
```

Трек-события получателя

События трекинга Почты России по конкретному получателю (если трек-номер присвоен). Требуется scope `letters:read`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (API key) authorization: apiKey
$config = Doslano\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Doslano\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | Идентификатор письма.
$recipient_id = 'recipient_id_example'; // string

try {
    $result = $apiInstance->getRecipientTracking($id, $recipient_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->getRecipientTracking: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| Идентификатор письма. | |
| **recipient_id** | **string**|  | |

### Return type

[**\Doslano\Model\TrackingInfo**](../Model/TrackingInfo.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listLetters()`

```php
listLetters($limit, $offset, $status, $created_from, $created_to): \Doslano\Model\ListLetters200Response
```

Список писем

Письма аккаунта (все каналы — и API, и личный кабинет; канал указан в поле `channel`). Требуется scope `letters:read`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (API key) authorization: apiKey
$config = Doslano\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Doslano\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$limit = 20; // int
$offset = 0; // int
$status = new \Doslano\Model\\Doslano\Model\LetterStatus(); // \Doslano\Model\LetterStatus
$created_from = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$created_to = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime

try {
    $result = $apiInstance->listLetters($limit, $offset, $status, $created_from, $created_to);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->listLetters: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **limit** | **int**|  | [optional] [default to 20] |
| **offset** | **int**|  | [optional] [default to 0] |
| **status** | [**\Doslano\Model\LetterStatus**](../Model/.md)|  | [optional] |
| **created_from** | **\DateTime**|  | [optional] |
| **created_to** | **\DateTime**|  | [optional] |

### Return type

[**\Doslano\Model\ListLetters200Response**](../Model/ListLetters200Response.md)

### Authorization

[apiKey](../../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
