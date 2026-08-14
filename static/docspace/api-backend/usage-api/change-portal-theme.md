# changePortalTheme

Referenced types are defined in the [full reference](../people.md).

> DarkThemeSettingsWrapper changePortalTheme(DarkThemeSettingsRequestDto)

`PUT /api/2.0/people/theme`

Change the portal theme

Changes the current portal theme.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **DarkThemeSettingsRequestDto** | body | [**DarkThemeSettingsRequestDto**](../people.md#model-darkthemesettingsrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Theme | [**DarkThemeSettingsWrapper**](../people.md#model-darkthemesettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DarkThemeSettingsWrapper**](../people.md#model-darkthemesettingswrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
