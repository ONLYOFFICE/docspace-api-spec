# getSubscriptionBalanceInfo

Referenced types are defined in the [full reference](../api.md).

> SubscriptionBalanceInfoWrapper getSubscriptionBalanceInfo()

`GET /api/2.0/portal/payment/subscription/balance`

Get the subscription balance information

Returns the information about the current subscription and its unused (prorated) balance.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The subscription balance information | [**SubscriptionBalanceInfoWrapper**](../api.md#model-subscriptionbalanceinfowrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Invalid request parameters | - | - |
| **402** | Tariff is not paid | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | Customer or subscription could not be found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**SubscriptionBalanceInfoWrapper**](../api.md#model-subscriptionbalanceinfowrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
