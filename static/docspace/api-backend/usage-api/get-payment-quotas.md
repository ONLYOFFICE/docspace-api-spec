# getPaymentQuotas

Referenced types are defined in the [full reference](../api.md).

> QuotaArrayWrapper getPaymentQuotas(wallet, additional)

`GET /api/2.0/portal/payment/quotas`

Get quotas

Returns the available portal quotas.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **wallet** | query | **Boolean** | Specifies whether to return the wallet quotas only. | [optional] [example: true] |
| **additional** | query | **Boolean** | Specifies whether to return additional quotas only. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of available portal quotas | [**QuotaArrayWrapper**](../api.md#model-quotaarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**QuotaArrayWrapper**](../api.md#model-quotaarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
