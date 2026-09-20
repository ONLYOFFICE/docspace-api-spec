# getRecentFolder

Referenced types are defined in the [full reference](../files.md).

> FolderContentWrapper getRecentFolder(userIdOrGroupId, filterType, excludeSubject, applyFilterOption, searchArea, extension, count, startIndex, sortBy, sortOrder, filterValue)

`GET /api/2.0/files/recent`

Get the Recent section

Returns the Recent section: the files the calling account has opened lately. The section holds files only,  so &#x60;folders&#x60; comes back empty, and it is personal, so another member&#39;s history is not visible here. A file is  added when it is opened and can also be added explicitly with &#x60;POST api/2.0/files/file/{fileId}/recent&#x60;;  &#x60;DELETE api/2.0/files/recent&#x60; clears the whole history, and &#x60;PUT api/2.0/files/displayrecent&#x60; switches the  section on and off for the account, which also decides whether &#x60;GET api/2.0/files/@root&#x60; includes it. Nothing  in the section is modified, though passing &#x60;sortBy&#x60; saves the requested order as the default order for this  account. The listing is ordered by the moment the caller last opened each file, newest first, and &#x60;sortBy&#x60; and  &#x60;sortOrder&#x60; do not change that order. &#x60;files&#x60; holds one page, &#x60;total&#x60; counts the files matching the request  before &#x60;count&#x60; and &#x60;startIndex&#x60; are applied, and &#x60;current&#x60; describes the section folder itself.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userIdOrGroupId** | query | **UUID** (uuid) | Restricts the listing to the files authored by this portal member, or by the members of this group; the same  parameter accepts either kind of identifier. Omit it to list the whole history. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **filterType** | query | **FilterType** | Narrows the listing to a single kind of file, such as documents, spreadsheets or images. Omit it to list every  kind the history holds. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 17, 20, 22, 23, 24, 25, 26] |
| **excludeSubject** | query | **Boolean** | Inverts &#x60;userIdOrGroupId&#x60;: with &#x60;true&#x60; the files of that member or group are the ones left out of the listing  instead of the only ones kept. | [optional] [example: false] |
| **applyFilterOption** | query | **ApplyFilterOption** | Chooses which half of a listing &#x60;filterType&#x60; and &#x60;filterValue&#x60; are applied to. The Recent section holds  files only, so the value does not change what comes back. | [optional] [example: 1] [enum: 0, 1, 2] |
| **searchArea** | query | **SearchArea** | The area a listing is taken from. The Recent section is assembled from the caller&#39;s own open history rather  than from an area, so the value does not change which files are returned. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9] |
| **extension** | query | **List** | The file extensions the listing is limited to, matched against the end of the file name. The leading dot is  optional, and the parameter is repeated once per extension. | [optional] [example: .docx] |
| **count** | query | **Integer** (int32) | The size of one page of section content. Pair it with &#x60;startIndex&#x60; to walk the listing, and compare the two  with &#x60;total&#x60; in the response to see when the last page has been read. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The number of matching entries to skip before the returned page begins; add &#x60;count&#x60; to it to ask for the next  page. | [optional] [example: 0] |
| **sortBy** | query | **String** | The name of the field the entries are ordered by, matched case-insensitively against the file sort fields:  &#x60;DateAndTime&#x60;, &#x60;AZ&#x60;, &#x60;Size&#x60;, &#x60;Author&#x60;, &#x60;Type&#x60;, &#x60;New&#x60;, &#x60;DateAndTimeCreation&#x60;, &#x60;RoomType&#x60;, &#x60;Tags&#x60;, &#x60;Room&#x60;,  &#x60;CustomOrder&#x60;, &#x60;LastOpened&#x60; and &#x60;UsedSpace&#x60;. A recognized value is also saved as the default order of the  account and reused by later listings that omit the parameter, while a value matching none of the fields leaves  that saved order in place. The Recent section keeps its own newest-first order, so the value does not  reorder this listing. | [optional] [example: DateAndTime] |
| **sortOrder** | query | **SortOrder** | The direction in which the &#x60;sortBy&#x60; field is ordered. It is saved together with &#x60;sortBy&#x60; as the default order  of the account. The Recent section keeps its own newest-first order, so the value does not reorder this  listing. | [optional] [example: 1] [enum: 0, 1] |
| **filterValue** | query | **String** | The search string the history is filtered by: it is matched as a substring of file titles and against the  indexed document content as well. Omit it to list the whole history. | [optional] [example: My Document] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The Recent section with one page of the files the caller opened lately | [**FolderContentWrapper**](../files.md#model-foldercontentwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not allowed to read the Recent section | - | - |
| **404** | The Recent section could not be resolved for this account | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderContentWrapper**](../files.md#model-foldercontentwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
