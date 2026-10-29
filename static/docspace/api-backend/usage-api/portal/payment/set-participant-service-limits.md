# setParticipantServiceLimits

> Int32Wrapper setParticipantServiceLimits(SetParticipantServiceLimitsRequestDto)

`PUT /api/2.0/portal/payment/servicelimit/participants`

Set the user service limits

Sets the same personal spending limit on the AI services for each of the listed portal users in one call,  replacing the personal limit any of them already has and switching it on, so it is how a ceiling is rolled out  to a group of users. The portal needs a billing customer, and the caller needs the permission to edit the portal  settings as well as DocSpace administrator rights. At least one of `amountValue` and `quantityValue` must be  given, every user in `userIds` must exist on the portal, and a user listed twice is limited once. One call takes  at most 1000 users; split a larger group into several calls. Unlike  `PUT api/2.0/portal/payment/servicelimit`, this sets the whole limit: a threshold left out is removed, and the  period may change, though a lifetime limit set to lifetime again keeps counting from where it was. Each personal  limit applies instead of the one for every user, and the limit of the portal is checked on top. The call is mutating and idempotent, and it is written to the portal audit trail. The answer is  the number of personal limits that were set; the result is listed by  `GET api/2.0/portal/payment/servicelimit/participants`.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **SetParticipantServiceLimitsRequestDto** | body | [**SetParticipantServiceLimitsRequestDto**](../../models/set-participant-service-limits-request-dto.md) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The number of personal limits that were set | [**Int32Wrapper**](../../models/int-32-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | `userIds` is empty or lists more than 1000 users, neither `amountValue` nor `quantityValue` is given, a value is outside its range, or the accounting service rejects a threshold, such as a quantity for services with different units | - | - |
| **403** | The caller may not edit the portal settings or is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer, or one of the users does not exist | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**Int32Wrapper**](../../models/int-32-wrapper.md)

## Authorization

[Basic](../portal.md#basic), [OAuth2](../portal.md#oauth2) (scopes: read, write), [ApiKeyBearer](../portal.md#apikeybearer), [asc_auth_key](../portal.md#asc_auth_key), [Bearer](../portal.md#bearer), [OpenId](../portal.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
