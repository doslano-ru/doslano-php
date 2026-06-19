# Doslano\DefaultApi

All URIs are relative to https://integration.doslano.ru, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**onLetterStatusChanged()**](DefaultApi.md#onLetterStatusChanged) | **POST** /letterStatusChanged | Колбек на финальный статус |


## `onLetterStatusChanged()`

```php
onLetterStatusChanged($webhook_event)
```

Колбек на финальный статус

Если при отправке письма указан `callback_url`, мы шлём на него POST при достижении финального статуса — по каждому получателю (`recipient.sent` / `recipient.failed`) и агрегатно по письму (`letter.sent` / `letter.partial_failure` / `letter.failed` / `letter.cancelled`).  Отдельный случай `letter.cancelled` — когда адрес/ФИО не прошли проверку Почты России **уже после** ответа `201` (поздний preflight: проверка не успела завершиться в окне синхронного ответа). Письмо отменяется автоматически, в `data.error` — перечень полей с ошибками; исправьте данные и создайте письмо заново. Если же ошибка адреса выявлена **сразу** при создании — вы получаете её синхронно (HTTP 422 `address_validation_failed`), и колбек по такому письму НЕ шлётся. То есть на одно письмо приходит ровно один сигнал об адресной ошибке: либо синхронный 422, либо асинхронный `letter.cancelled`.  **Подпись.** Заголовок `X-Doslano-Signature: t=<unix>,v1=<hex>` — где `v1 = HMAC_SHA256(secret, \"<t>.\" + raw_body)`, `secret` — секрет аккаунта из ЛК (раздел «API»). Проверьте подпись и свежесть `t` (±5 мин).  **Доставка.** At-least-once: ждём ответ `2xx`; иначе ретраим по нарастающему графику (несколько попыток в течение ~24 ч), затем помечаем как недоставленный (видно в ЛК, можно переотправить). Дедуп — по `id` события. Порядок не гарантируется — сверяйтесь со `status` в теле.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new Doslano\Api\DefaultApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$webhook_event = new \Doslano\Model\WebhookEvent(); // \Doslano\Model\WebhookEvent

try {
    $apiInstance->onLetterStatusChanged($webhook_event);
} catch (Exception $e) {
    echo 'Exception when calling DefaultApi->onLetterStatusChanged: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **webhook_event** | [**\Doslano\Model\WebhookEvent**](../Model/WebhookEvent.md)|  | |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
