# # RecipientInput

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** | ФИО или название получателя. При resolve_address_by_inn&#x3D;true ПЕРЕЗАПИСЫВАЕТСЯ наименованием из ЕГРЮЛ. |
**address** | **string** | Адрес получателя (строкой; нормализуется на нашей стороне). Можно опустить при resolve_address_by_inn&#x3D;true. | [optional]
**party_type** | [**\Doslano\Model\PartyType**](PartyType.md) |  | [optional]
**inn** | **string** |  | [optional]
**resolve_address_by_inn** | **bool** | Авто-резолв адреса по ИНН из ЕГРЮЛ. Работает только для party_type&#x3D;organization с заданным inn: адрес и наименование берутся из реестра (DaData findById/party, головная организация), address можно не передавать. Если резолв не удался и address не передан — 422 recipient_address_unresolved; флаг без inn или не для organization — 422 recipient_resolve_requires_inn. Если передан и address — он fallback при неудаче резолва. | [optional] [default to false]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
