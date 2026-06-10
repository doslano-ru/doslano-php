# # CreateLetterRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**sender** | [**\Doslano\Model\SenderInput**](SenderInput.md) | Отправитель. Если не указан — берётся отправитель по умолчанию из профиля аккаунта. | [optional]
**recipients** | [**\Doslano\Model\RecipientInput[]**](RecipientInput.md) |  |
**content** | [**\Doslano\Model\LetterContent**](LetterContent.md) |  |
**letter_class** | [**\Doslano\Model\LetterClass**](LetterClass.md) |  | [optional]
**promo_code** | **string** | Промокод (опционально). | [optional]
**on_promo_invalid** | **string** | Что делать, если промокод не применился: &#x60;ignore&#x60; — отправить без скидки и вернуть пометку в &#x60;pricing.promo&#x60;; &#x60;reject&#x60; — отклонить (422). | [optional] [default to 'ignore']
**on_insufficient_funds** | **string** | Что делать при нехватке средств: &#x60;reject&#x60; — отклонить (402), письмо не создаётся; &#x60;hold&#x60; — создать письмо в статусе &#x60;awaiting_payment&#x60;, оно оплатится автоматически при пополнении баланса. | [optional] [default to 'reject']
**callback_url** | **string** | HTTPS-URL для колбеков по этому письму. Если не указан — используйте поллинг. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
