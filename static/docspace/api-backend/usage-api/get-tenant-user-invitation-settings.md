# getTenantUserInvitationSettings

Referenced types are defined in the [full reference](../api.md).

> TenantUserInvitationSettingsWrapper getTenantUserInvitationSettings()

`GET /api/2.0/settings/invitationsettings`

Get the user invitation settings

Returns the portal user invitation settings.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | portal user invitation settings | [**TenantUserInvitationSettingsWrapper**](../api.md#model-tenantuserinvitationsettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantUserInvitationSettingsWrapper**](../api.md#model-tenantuserinvitationsettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
