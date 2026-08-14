# getTenant

Referenced types are defined in the [full reference](../api.md).

> DocsCloudTenantWrapper getTenant(refresh)

`GET /api/2.0/settings/docscloud/tenant`

Get the DocsCloud tenant

Returns the DocsCloud tenant of the current portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** |  | [optional] [default to false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | DocsCloud tenant | [**DocsCloudTenantWrapper**](../api.md#model-docscloudtenantwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocsCloudTenantWrapper**](../api.md#model-docscloudtenantwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
