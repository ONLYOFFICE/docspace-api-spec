# saveDefaultFolder

Referenced types are defined in the [full reference](../api.md).

> StudioDefaultPageSettingsWrapper saveDefaultFolder(DefaultProductRequestDto)

`PUT /api/2.0/settings/defaultfolder`

Set the default folder

Sets the default folder.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **DefaultProductRequestDto** | body | [**DefaultProductRequestDto**](../api.md#model-defaultproductrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Message about saving settings successfully | [**StudioDefaultPageSettingsWrapper**](../api.md#model-studiodefaultpagesettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StudioDefaultPageSettingsWrapper**](../api.md#model-studiodefaultpagesettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
