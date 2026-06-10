# # Letter

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**channel** | **string** | Канал создания письма — &#x60;api&#x60; (этот API) или &#x60;web&#x60; (личный кабинет). |
**status** | [**\Doslano\Model\LetterStatus**](LetterStatus.md) |  |
**created_at** | **\DateTime** |  |
**sender** | [**\Doslano\Model\Party**](Party.md) |  | [optional]
**recipients** | [**\Doslano\Model\Recipient[]**](Recipient.md) |  |
**pricing** | [**\Doslano\Model\Pricing**](Pricing.md) |  |
**payment** | [**\Doslano\Model\PaymentResult**](PaymentResult.md) |  | [optional]
**callback_url** | **string** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
