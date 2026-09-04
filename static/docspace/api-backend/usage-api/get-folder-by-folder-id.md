# getFolderByFolderId

Referenced types are defined in the [full reference](../files.md).

> FolderContentIntegerWrapper getFolderByFolderId(folderId, userIdOrGroupId, sharedBy, filterType, roomId, folderType, excludeSubject, applyFilterOption, withSubFolders, extension, searchArea, formsItemKey, formsItemType, count, startIndex, sortBy, sortOrder, filterValue, Location)

`GET /api/2.0/files/{folderId}`

Get a folder by ID

Returns the detailed list of files and folders located in the folder with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder ID. | [required] [example: 1] |
| **userIdOrGroupId** | query | **UUID** (uuid) | The user or group ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **sharedBy** | query | **UUID** (uuid) | The identifier of the user who shared the folder or file. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **filterType** | query | **FilterType** | The filter type. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 17, 20, 22, 23, 24, 25, 26] |
| **roomId** | query | **Integer** (int32) | The room ID. | [optional] [example: 1] |
| **folderType** | query | **List** | The parent folder types used to filter the folder contents by folder type. | [optional] [example: [2]] [enum: 0, 1, 2, 3, 5, 6, 8, 10, 11, 12, 13, 14, 15, 16, 19, 20, 21, 22, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36] |
| **excludeSubject** | query | **Boolean** | Specifies whether to exclude search by user or group ID. | [optional] [example: false] |
| **applyFilterOption** | query | **ApplyFilterOption** | Specifies whether to return only files, only folders, or all elements from the specified folder. | [optional] [example: 1] [enum: 0, 1, 2] |
| **withSubFolders** | query | **Boolean** | Specifies whether to include files from subfolders in the results. | [optional] [example: true] |
| **extension** | query | **String** | Specifies whether to search for the specific file extension. | [optional] [example: .docx] |
| **searchArea** | query | **SearchArea** | The search area. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9] |
| **formsItemKey** | query | **String** | The forms item key. | [optional] [example: doc_key_123] |
| **formsItemType** | query | **String** | The forms item type. | [optional] [example: text] |
| **count** | query | **Integer** (int32) | The maximum number of items to retrieve in the request. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The zero-based index of the first item to retrieve in a paginated request. | [optional] [example: 0] |
| **sortBy** | query | **String** | The property used for sorting the folder request results. | [optional] [example: DateAndTime] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 1] [enum: 0, 1] |
| **filterValue** | query | **String** | The text value used as a filter parameter for folder content queries. | [optional] [example: My Document] |
| **Location** | query | **Location** | The location context of the request, specifying the area  where the operation is performed, such as a room, documents, or a link. | [optional] [example: 1] [enum: 1, 2, 3] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Folder contents | [**FolderContentIntegerWrapper**](../files.md#model-foldercontentintegerwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to view the folder content | - | - |
| **404** | The required folder was not found | - | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderContentIntegerWrapper**](../files.md#model-foldercontentintegerwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
