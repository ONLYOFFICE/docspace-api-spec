# getRoomsFolder

Referenced types are defined in the [full reference](../files.md).

> FolderContentIntegerWrapper getRoomsFolder(type, subjectId, subjectOwnerId, searchArea, withoutTags, tags, excludeSubject, provider, quotaFilter, storageFilter, privacyFilter, count, startIndex, sortBy, sortOrder, filterValue, groupId)

`GET /api/2.0/files/rooms`

Get rooms

Returns the contents of the Rooms section by the parameters specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **type** | query | [**List**](../files.md#model-roomtype) | The filter by room type. | [optional] [example: 1] |
| **subjectId** | query | **UUID** (uuid) | The filter by user ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **subjectOwnerId** | query | **UUID** (uuid) | The filter by room owner ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **searchArea** | query | **SearchArea** | The room search area (Active, Archive, Any, Recent by links). | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9] |
| **withoutTags** | query | **Boolean** | Specifies whether to search by tags or not. | [optional] [example: false] |
| **tags** | query | **String** | The tags in the serialized format. | [optional] [example: tag1] |
| **excludeSubject** | query | **Boolean** | Specifies whether to exclude search by user or group ID. | [optional] [example: false] |
| **provider** | query | **ProviderFilter** | The filter by provider name (None, Box, DropBox, GoogleDrive, kDrive, OneDrive, SharePoint, WebDav, Yandex, Storage). | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9] |
| **quotaFilter** | query | **QuotaFilter** | The filter by quota (All - 0, Default - 1, Custom - 2). | [optional] [example: 1] [enum: 0, 1, 2] |
| **storageFilter** | query | **StorageFilter** | The filter by storage (None - 0, Internal - 1, ThirdParty - 2). | [optional] [example: 1] [enum: 0, 1, 2] |
| **privacyFilter** | query | **RoomPrivacyFilter** | The filter by room privacy (None - 0, Private - 1, NotPrivate - 2). When omitted, all rooms are returned. | [optional] [example: 1] [enum: 0, 1, 2] |
| **count** | query | **Integer** (int32) | Specifies the maximum number of items to retrieve. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The index from which to start retrieving the room content. | [optional] [example: 0] |
| **sortBy** | query | **String** | Specifies the field by which the room content should be sorted. | [optional] [example: DateAndTime] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 1] [enum: 0, 1] |
| **filterValue** | query | **String** | The text filter value used to refine search or query operations. | [optional] [example: My Document] |
| **groupId** | query | **Integer** (int32) | The group ID | [optional] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Returns the contents of the Rooms section | [**FolderContentIntegerWrapper**](../files.md#model-foldercontentintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to view the room content | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderContentIntegerWrapper**](../files.md#model-foldercontentintegerwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
