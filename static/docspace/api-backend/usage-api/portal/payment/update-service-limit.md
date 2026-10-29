# updateServiceLimit

> ServiceLimitWrapper updateServiceLimit(UpdateServiceLimitRequestDto)

`PUT /api/2.0/portal/payment/servicelimit`

Update a service limit

Changes the thresholds of an existing spending limit on the AI services, or switches it off and back on with  `enabled`. The portal needs a billing customer, and the caller needs the permission to edit the portal settings  as well as DocSpace administrator rights. Only the given fields change: an omitted threshold keeps its value, so  a threshold once set cannot be removed here - delete the limit with  `DELETE api/2.0/portal/payment/servicelimit/{id}` and create it anew with  `POST api/2.0/portal/payment/servicelimit`, which is also the way to change its scope, user or period. A  switched-off limit stops restricting the AI services at once. The call is mutating and idempotent, it is written  to the portal audit trail, and a new threshold applies from the very next operation; lowering it below what was  already spent blocks the AI services until the period ends. An ID that does not exist, belongs to another portal  or is not a limit on the AI services answers 404.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **UpdateServiceLimitRequestDto** | body | [**UpdateServiceLimitRequestDto**](../../models/update-service-limit-request-dto.md) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The service limit as it was stored | [**ServiceLimitWrapper**](../../models/service-limit-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The ID is zero or negative, a value is outside its range, or the accounting service rejects a threshold, such as a quantity for services with different units | - | - |
| **403** | The caller may not edit the portal settings or is not a DocSpace administrator, or the portal has no billing service configured | - | - |
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

- **Content-Type**: application/json
- **Accept**: application/json
