# setSettings

Referenced types are defined in the [full reference](../api.md).

> AppWrapper setSettings(id, SetAppSettingsBody)

`PUT /api/2.0/apps/{id}/settings`

Save app settings

Saves an arbitrary JSON settings document for the specified application for the current tenant.  Requires portal administrator permissions.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The application identifier. | [required] [example: ai-room] |
| **SetAppSettingsBody** | body | [**SetAppSettingsBody**](../api.md#model-setappsettingsbody) | New settings document. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Updated application info | [**AppWrapper**](../api.md#model-appwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Settings is not valid JSON | - | - |
| **403** | You don&#39;t have enough permission to manage apps | - | - |
| **404** | Application not found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**AppWrapper**](../api.md#model-appwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AuthenticationApi
