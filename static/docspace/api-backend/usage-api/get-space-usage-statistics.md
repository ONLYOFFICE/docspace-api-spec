# getSpaceUsageStatistics

Referenced types are defined in the [full reference](../api.md).

> UsageSpaceStatItemArrayWrapper getSpaceUsageStatistics(id)

`GET /api/2.0/settings/statistics/spaceusage/{id}`

Get the space usage statistics

Returns the space usage statistics for the module with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **UUID** (uuid) | The ID extracted from the route parameters. | [required] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Module space usage statistics | [**UsageSpaceStatItemArrayWrapper**](../api.md#model-usagespacestatitemarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**UsageSpaceStatItemArrayWrapper**](../api.md#model-usagespacestatitemarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## SettingsStorageApi
