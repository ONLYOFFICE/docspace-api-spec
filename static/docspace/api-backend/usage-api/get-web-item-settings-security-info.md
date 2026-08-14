# getWebItemSettingsSecurityInfo

Referenced types are defined in the [full reference](../api.md).

> SecurityArrayWrapper getWebItemSettingsSecurityInfo(ids)

`GET /api/2.0/settings/security`

Get the security settings

Returns the security settings for the modules specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **ids** | query | **List** | The list of module identifiers for which to retrieve the security settings. | [optional] [example: ["item1","item2"]] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Security settings | [**SecurityArrayWrapper**](../api.md#model-securityarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**SecurityArrayWrapper**](../api.md#model-securityarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
