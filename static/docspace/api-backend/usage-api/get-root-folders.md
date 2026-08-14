# getRootFolders

Referenced types are defined in the [full reference](../files.md).

> FolderContentIntegerArrayWrapper getRootFolders(userIdOrGroupId, filterType, withoutTrash, count, startIndex, sortBy, sortOrder, filterValue)

`GET /api/2.0/files/@root`

Get filtered sections

Returns all the sections matching the parameters specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userIdOrGroupId** | query | **UUID** (uuid) | The user or group ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **filterType** | query | **FilterType** | The filter type. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 17, 20, 22, 23, 24, 25, 26] |
| **withoutTrash** | query | **Boolean** | Specifies whether to return the Trash section or not. | [optional] [example: false] |
| **count** | query | **Integer** (int32) | The maximum number of items to retrieve in the response. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting position of the items to be retrieved. | [optional] [example: 0] |
| **sortBy** | query | **String** | Specifies the field by which the folder content should be sorted. | [optional] [example: DateAndTime] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 1] [enum: 0, 1] |
| **filterValue** | query | **String** | The text used as a filter for searching or retrieving folder contents. | [optional] [example: My Document] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of section contents with the following parameters | [**FolderContentIntegerArrayWrapper**](../files.md#model-foldercontentintegerarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to view the folder content | - | - |
| **404** | The required folder was not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderContentIntegerArrayWrapper**](../files.md#model-foldercontentintegerarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
