# checkConfirm

Referenced types are defined in the [full reference](../api.md).

> ConfirmWrapper checkConfirm(EmailValidationKeyModel)

`POST /api/2.0/authentication/confirm`

Check a confirmation link

Checks the key of a confirmation link that the portal sent by email and reports whether the action behind that  link can still be carried out - an employee invitation, phone activation, a password change, portal removal  and so on. Take &#x60;key&#x60; and &#x60;type&#x60; from the query string of the link; when &#x60;key&#x60; is left empty, the key saved in  the confirmation cookie of the same &#x60;type&#x60; is used instead. Open to unauthenticated callers and read-only: it  neither accepts the invitation nor signs anyone in. &#x60;result&#x60; is &#x60;Ok&#x60; when the link may be used, &#x60;Invalid&#x60; when  the key does not match the type or the email, &#x60;Expired&#x60; when it is too old, and &#x60;TariffLimit&#x60;, &#x60;UserExisted&#x60;,  &#x60;UserExcluded&#x60; or &#x60;QuotaFailed&#x60; when the key is sound but the invitation behind it cannot be accepted. Only  &#x60;Ok&#x60; should be followed by the operation that performs the action - &#x60;POST api/2.0/people&#x60; with  &#x60;fromInviteLink&#x60; for an invitation, &#x60;POST api/2.0/authentication&#x60; with &#x60;confirmData&#x60; for a sign-in link - and  for an invitation to a room the answer also carries the identifier and the title of that room.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **EmailValidationKeyModel** | body | [**EmailValidationKeyModel**](../api.md#model-emailvalidationkeymodel) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the confirmation link may be used, with the room and the email it was issued for when it is an invitation | [**ConfirmWrapper**](../api.md#model-confirmwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The portal&#39;s IP restrictions do not allow this address to check an invitation link | - | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ConfirmWrapper**](../api.md#model-confirmwrapper)

## Authorization

[cookieAuth](../api.md#cookieauth), [bearerAuth](../api.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
