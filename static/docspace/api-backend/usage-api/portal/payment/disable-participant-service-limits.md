# disableParticipantServiceLimits

> Int32Wrapper disableParticipantServiceLimits()

`PUT /api/2.0/portal/payment/servicelimit/participants/disable`

Disable the user service limits

Switches off every personal spending limit on the AI services in one call, so each user falls back to the limit  for every user, if one is set. The limit of the portal as a whole and the one for every user stay as they are.  The portal needs a billing customer, and the caller needs the permission to edit the portal settings as well as  DocSpace administrator rights. The switched-off limits stop restricting their users at once and are kept, so  each can be switched back on with `PUT api/2.0/portal/payment/servicelimit`. The call is mutating and  idempotent - repeating it switches off nothing more - and it is written to the portal audit trail. The answer is  the number of personal limits that were switched off, zero when none was in force. To switch off the limit of a  single user, use `PUT api/2.0/portal/payment/servicelimit` with `enabled` set to false.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The number of personal limits that were switched off | [**Int32Wrapper**](../../models/int-32-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller may not edit the portal settings or is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer | - | - |
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

- **Content-Type**: Not defined
- **Accept**: application/json
