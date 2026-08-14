# testExternalDatabaseConnection

Referenced types are defined in the [full reference](../api.md).

> ConnectionTestResultWrapper testExternalDatabaseConnection(ExternalDatabaseSettings)

`POST /api/2.0/settings/authservice/externaldb/test`

Test external database connection

Tests an external database connection with the provided settings without saving them.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **ExternalDatabaseSettings** | body | [**ExternalDatabaseSettings**](../api.md#model-externaldatabasesettings) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Connection test result with Success flag and optional Error message | [**ConnectionTestResultWrapper**](../api.md#model-connectiontestresultwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ConnectionTestResultWrapper**](../api.md#model-connectiontestresultwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## SettingsBannersVisibilityApi
