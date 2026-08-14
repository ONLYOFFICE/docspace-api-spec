# getCheckoutSetupUrl

Referenced types are defined in the [full reference](../api.md).

> StringWrapper getCheckoutSetupUrl(BackUrl, SuccessUrl)

`GET /api/2.0/portal/payment/checkoutsetupurl`

Get the checkout setup page URL

Returns the URL to the checkout setup page.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BackUrl** | query | **URI** (uri) | The URL where the user will be redirected after setup cancellation. | [required] [example: https://example.com/payment/back] [minLength: 0] [maxLength: 255] |
| **SuccessUrl** | query | **URI** (uri) | The URL where the user will be redirected after successful payment. | [required] [example: https://example.com/payment/success] [minLength: 0] [maxLength: 255] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The URL to the checkout setup page | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
