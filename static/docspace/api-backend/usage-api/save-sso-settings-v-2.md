# saveSsoSettingsV2

Referenced types are defined in the [full reference](../api.md).

> SsoSettingsV2Wrapper saveSsoSettingsV2(SsoSettingsRequestsDto)

`POST /api/2.0/settings/ssov2`

Save the SSO settings

Saves the SSO settings for the current portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **SsoSettingsRequestsDto** | body | [**SsoSettingsRequestsDto**](../api.md#model-ssosettingsrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | SSO settings | [**SsoSettingsV2Wrapper**](../api.md#model-ssosettingsv2wrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Settings could not be null | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**SsoSettingsV2Wrapper**](../api.md#model-ssosettingsv2wrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## SettingsSecurityApi
