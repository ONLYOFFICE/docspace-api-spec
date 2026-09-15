# getAuditSettings

Referenced types are defined in the [full reference](../api.md).

> TenantAuditSettingsResponseWrapper getAuditSettings()

`GET /api/2.0/security/audit/settings/lifetime`

Get audit lifetime settings

Returns how long this portal keeps its two security logs: &#x60;loginHistoryLifeTime&#x60; for login events and  &#x60;auditTrailLifeTime&#x60; for audit events, both counted in days, together with &#x60;lastModified&#x60;, the moment the pair  was last saved. The caller needs the portal-settings right of a DocSpace administrator, and in a cloud  installation the login history and audit trail section must be enabled for the portal, otherwise the call is  answered with 402; the audit option of the pricing plan is not required to read the values. Both numbers lie  between 1 and 180 days, and a portal that never changed them reports the default of 180. They define the  window the rest of the audit operations work in: &#x60;GET api/2.0/security/audit/events/last&#x60; looks exactly this  far back, and the reports started by &#x60;POST api/2.0/security/audit/login/report&#x60; and  &#x60;POST api/2.0/security/audit/events/report&#x60; cover exactly this period. The operation is read-only; change the  values with &#x60;POST api/2.0/security/audit/settings/lifetime&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The login history and audit trail lifetimes of the portal, in days | [**TenantAuditSettingsResponseWrapper**](../api.md#model-tenantauditsettingsresponsewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | The login history and audit trail section is not enabled for this portal | - | - |
| **403** | The caller does not have the portal-settings right of a DocSpace administrator | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantAuditSettingsResponseWrapper**](../api.md#model-tenantauditsettingsresponsewrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
