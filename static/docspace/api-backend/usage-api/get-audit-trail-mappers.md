# getAuditTrailMappers

Referenced types are defined in the [full reference](../api.md).

> ObjectWrapper getAuditTrailMappers(productType, moduleType)

`GET /api/2.0/security/audit/mappers`

Get audit trail mappers

Returns the mappers for the audit trail types.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **productType** | query | **ProductType** | The type of product related to the audit trail. | [optional] [example: Documents] [enum: 2, 3, 7, 8] |
| **moduleType** | query | **LocationType** | The location associated with the audit trail. | [optional] [example: Files] [enum: 0, 1, 2, 3, 27, 29, 30, 31] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Audit trail mappers | [**ObjectWrapper**](../api.md#model-objectwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ObjectWrapper**](../api.md#model-objectwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
