# getTenantWalletServiceSettings

Referenced types are defined in the [full reference](../api.md).

> TenantWalletServiceSettingsWrapper getTenantWalletServiceSettings()

`GET /api/2.0/portal/payment/servicessettings`

Gets the wallet service settings for the tenant.

Retrieves configuration settings related to the wallet service associated with the current tenant.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The wallet service settings for the tenant | [**TenantWalletServiceSettingsWrapper**](../api.md#model-tenantwalletservicesettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantWalletServiceSettingsWrapper**](../api.md#model-tenantwalletservicesettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
