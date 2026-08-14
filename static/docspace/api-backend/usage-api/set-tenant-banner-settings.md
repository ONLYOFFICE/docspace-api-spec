# setTenantBannerSettings

Referenced types are defined in the [full reference](../api.md).

> TenantBannerSettingsWrapper setTenantBannerSettings(TenantBannerSettingsDto)

`POST /api/2.0/settings/banner`

Set the banners visibility

Sets the visibility settings of the promotional banners in the portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **TenantBannerSettingsDto** | body | [**TenantBannerSettingsDto**](../api.md#model-tenantbannersettingsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Promotional banners visibility settings | [**TenantBannerSettingsWrapper**](../api.md#model-tenantbannersettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantBannerSettingsWrapper**](../api.md#model-tenantbannersettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## SecurityCSPApi
