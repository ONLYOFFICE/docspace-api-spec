# getServiceLimit

> ServiceLimitWrapper getServiceLimit(id)

`GET /api/2.0/portal/payment/servicelimit/{id}`

Get a service limit

Returns one spending limit on the AI services of the portal by its ID - the limit of the portal as a whole, the  one for every user, or a personal one. Only a DocSpace administrator may read it, an installation without a  billing service answers 403, and the call is read-only. The limit comes back with its scope, thresholds, their  currency and unit, the period and whether it is in force, but without its spending: that comes with  `GET api/2.0/portal/payment/servicelimit/total` for the portal and with  `GET api/2.0/portal/payment/servicelimit/participants` for each user. A portal with no billing customer, and an  ID that does not exist, belongs to another portal or is not a limit on the AI services, answer 404.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The ID of the service limit, as returned in `id` by the operation that created it or by the reads of limits. | [required] [example: `42`] [min: 1] [max: 2147483647] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The service limit with its scope, thresholds, period and state | [**ServiceLimitWrapper**](../../models/service-limit-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The ID is zero or negative | - | - |
| **403** | The caller is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer, or the portal has no limit on the AI services with this ID | - | - |
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
