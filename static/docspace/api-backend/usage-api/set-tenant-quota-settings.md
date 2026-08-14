# setTenantQuotaSettings

Referenced types are defined in the [full reference](../api.md).

> TenantQuotaSettingsWrapper setTenantQuotaSettings(TenantQuotaSettingsRequestsDto)

`PUT /api/2.0/settings/tenantquotasettings`

Save the tenant quota settings

Saves the tenant quota settings specified in the request to the current portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **TenantQuotaSettingsRequestsDto** | body | [**TenantQuotaSettingsRequestsDto**](../api.md#model-tenantquotasettingsrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Tenant quota settings | [**TenantQuotaSettingsWrapper**](../api.md#model-tenantquotasettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | Your pricing plan does not support this option | - | - |
| **405** | Not available | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantQuotaSettingsWrapper**](../api.md#model-tenantquotasettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## SettingsRebrandingApi
