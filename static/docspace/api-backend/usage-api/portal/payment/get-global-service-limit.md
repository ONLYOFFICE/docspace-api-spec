# getGlobalServiceLimit

> ServiceLimitWrapper getGlobalServiceLimit()

`GET /api/2.0/portal/payment/servicelimit/global`

Get the global service limit

Returns the spending limit on the AI services for every user - the same ceiling applied to each user separately,  for any user without a personal limit in force. Only a DocSpace administrator may read it, an installation  without a billing service answers 403, and the call is read-only. It comes without spending, since that is  counted per user: read it for each user from `GET api/2.0/portal/payment/servicelimit/participants`; `periodEnd`  still says when the current period ends for everyone. When no  such limit has been set, or it was deleted, the answer is 200 with a null `response`; create the limit with  `POST api/2.0/portal/payment/servicelimit` and the scope `Global`. A switched-off limit is still returned, with  `enabled` false. A portal with no billing customer answers 404.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The limit for every user, or null when no such limit is set | [**ServiceLimitWrapper**](../../models/service-limit-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ServiceLimitWrapper**](../../models/service-limit-wrapper.md)

## Authorization

[Basic](../portal.md#basic), [OAuth2](../portal.md#oauth2) (scopes: read, write), [ApiKeyBearer](../portal.md#apikeybearer), [asc_auth_key](../portal.md#asc_auth_key), [Bearer](../portal.md#bearer), [OpenId](../portal.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
