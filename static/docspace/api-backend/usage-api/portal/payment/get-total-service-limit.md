# getTotalServiceLimit

> ServiceLimitWrapper getTotalServiceLimit()

`GET /api/2.0/portal/payment/servicelimit/total`

Get the portal service limit

Returns the spending limit on the AI services for the portal as a whole - the ceiling the spending of every user  counts towards - together with what was spent against it in the current period and what is left. Only a  DocSpace administrator may read it, an installation without a billing service answers 403, and the call is  read-only. The limit is checked in addition to the limits  of the users, so a user can be stopped by it before reaching their own. The spending includes the expected cost  of AI operations still in progress. When no such limit has been set, or it was deleted, the answer is 200 with a  null `response`; create the limit with `POST api/2.0/portal/payment/servicelimit` and the scope `Total`. A  switched-off limit is still returned, with `enabled` false. A portal with no billing customer answers 404.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The limit of the portal as a whole with its spending, or null when no such limit is set | [**ServiceLimitWrapper**](../../models/service-limit-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
