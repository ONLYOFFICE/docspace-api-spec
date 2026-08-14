# updateCdnStorage

Referenced types are defined in the [full reference](../api.md).

> CdnStorageSettingsWrapper updateCdnStorage(StorageRequestsDto)

`PUT /api/2.0/settings/storage/cdn`

Update the CDN storage

Updates the CDN storage with the parameters specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **StorageRequestsDto** | body | [**StorageRequestsDto**](../api.md#model-storagerequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Updated CDN storage | [**CdnStorageSettingsWrapper**](../api.md#model-cdnstoragesettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Module | - | - |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CdnStorageSettingsWrapper**](../api.md#model-cdnstoragesettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
