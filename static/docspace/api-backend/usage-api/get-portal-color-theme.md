# getPortalColorTheme

Referenced types are defined in the [full reference](../api.md).

> CustomColorThemesSettingsWrapper getPortalColorTheme()

`GET /api/2.0/settings/colortheme`

Get a color theme

Returns the portal color theme.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Settings of the portal themes | [**CustomColorThemesSettingsWrapper**](../api.md#model-customcolorthemessettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CustomColorThemesSettingsWrapper**](../api.md#model-customcolorthemessettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
