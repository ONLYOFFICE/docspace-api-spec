# getCustomerMonthlyUsage

Referenced types are defined in the [full reference](../api.md).

> CustomerMonthlyUsageArrayWrapper getCustomerMonthlyUsage(startDate, endDate)

`GET /api/2.0/portal/payment/customer/usage/monthly`

Get the customer monthly usage

Returns the customer spending aggregated per calendar month from the accounting service.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **startDate** | query | **Date** (date-time) | Start of the period (inclusive). | [optional] [example: 2025-01-01T00:00:00Z] |
| **endDate** | query | **Date** (date-time) | End of the period (inclusive). | [optional] [example: 2025-12-31T23:59:59Z] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The customer monthly usage | [**CustomerMonthlyUsageArrayWrapper**](../api.md#model-customermonthlyusagearraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CustomerMonthlyUsageArrayWrapper**](../api.md#model-customermonthlyusagearraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
