# setAuditSettings

Referenced types are defined in the [full reference](../api.md).

> TenantAuditSettingsWrapper setAuditSettings(TenantAuditSettingsWrapper)

`POST /api/2.0/security/audit/settings/lifetime`

Set the audit trail settings

Sets the audit trail settings for the current portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **TenantAuditSettingsWrapper** | body | [**TenantAuditSettingsWrapper**](../api.md#model-tenantauditsettingswrapper) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Audit trail settings | [**TenantAuditSettingsWrapper**](../api.md#model-tenantauditsettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Exception in LoginHistoryLifeTime or AuditTrailLifeTime | - | - |
| **402** | Your pricing plan does not support this option | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantAuditSettingsWrapper**](../api.md#model-tenantauditsettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
