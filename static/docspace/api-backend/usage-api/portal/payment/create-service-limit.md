# createServiceLimit

> ServiceLimitWrapper createServiceLimit(CreateServiceLimitRequestDto)

`POST /api/2.0/portal/payment/servicelimit`

Create a service limit

Creates a spending limit on the AI services - AI tools and AI search together - with `scope` saying whom it  applies to: `Total` for the portal as a whole, `Global` for every user separately, `Custom` for the user in  `userId`, which only this scope takes. A personal limit applies to its user instead of the one for every user,  and the limit of the portal is checked on top of both. The portal needs a billing customer, and the caller needs  the permission to edit the portal settings as well as DocSpace administrator rights. At least one of  `amountValue` and `quantityValue` must be given; with both, the services stop as soon as either is reached. The  call is mutating and written to the portal audit trail. It is not idempotent: a second limit of the same scope,  or for the same user, is refused with 409 - change the existing one with  `PUT api/2.0/portal/payment/servicelimit` instead. The scope, the user and the period cannot be changed later.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CreateServiceLimitRequestDto** | body | [**CreateServiceLimitRequestDto**](../../models/create-service-limit-request-dto.md) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The service limit as it was created | [**ServiceLimitWrapper**](../../models/service-limit-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Neither `amountValue` nor `quantityValue` is given, `userId` is missing for the scope `Custom` or given for another scope, a value is outside its range, or the accounting service rejects a threshold, such as a quantity for services with different units | - | - |
| **403** | The caller may not edit the portal settings or is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer, or the user does not exist | - | - |
| **409** | A limit of this scope, or for this user, exists already | - | - |
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
