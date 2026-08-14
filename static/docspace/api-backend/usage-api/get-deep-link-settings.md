# getDeepLinkSettings

Referenced types are defined in the [full reference](../api.md).

> TenantDeepLinkSettingsWrapper getDeepLinkSettings()

`GET /api/2.0/settings/deeplink`

Get the deep link settings

Returns the deep link settings.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**TenantDeepLinkSettingsWrapper**](../api.md#model-tenantdeeplinksettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantDeepLinkSettingsWrapper**](../api.md#model-tenantdeeplinksettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
