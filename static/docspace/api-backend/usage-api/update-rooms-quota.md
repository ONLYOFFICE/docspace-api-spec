# updateRoomsQuota

Referenced types are defined in the [full reference](../files.md).

> FolderIntegerArrayWrapper updateRoomsQuota(UpdateRoomsQuotaRequestDtoInteger)

`PUT /api/2.0/files/rooms/roomquota`

Change the room quota limit

Changes the quota limit for the rooms with the IDs specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **UpdateRoomsQuotaRequestDtoInteger** | body | [**UpdateRoomsQuotaRequestDtoInteger**](../files.md#model-updateroomsquotarequestdtointeger) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of rooms with the detailed information | [**FolderIntegerArrayWrapper**](../files.md#model-folderintegerarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderIntegerArrayWrapper**](../files.md#model-folderintegerarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## FilesSettingsApi
