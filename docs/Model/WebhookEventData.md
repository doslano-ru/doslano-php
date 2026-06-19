# # WebhookEventData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**letter_id** | **string** |  |
**recipient_id** | **string** |  | [optional]
**status** | **string** |  |
**shipment_number** | **string** |  | [optional]
**tracking_number** | **string** |  | [optional]
**error** | **string** |  | [optional]
**amount_minor** | **int** | Фактически списанная стоимость отправления ЭТОМУ получателю, в копейках (доля дисконтированного тотала письма с учётом промокода). Присутствует только в &#x60;recipient.sent&#x60; — отправление реально ушло и оплачено. В &#x60;recipient.failed&#x60; отсутствует: при провале сумма возвращается на баланс. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
