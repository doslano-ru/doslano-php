# # Recipient

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**name** | **string** |  |
**address** | **string** |  | [optional]
**status** | [**\Doslano\Model\RecipientStatus**](RecipientStatus.md) |  |
**shipment_number** | **string** | Наш трек-номер (РПО), присваивается сразу при создании. | [optional]
**tracking_number** | **string** | Трек-номер Почты России (ШПИ). Появляется после регистрации отправления. | [optional]
**price_minor** | **int** | Стоимость отправления этому получателю, в копейках. | [optional]
**error** | **string** | Причина ошибки (для &#x60;failed&#x60;). | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
