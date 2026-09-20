# getFavoritesFolder

Referenced types are defined in the [full reference](../files.md).

> FolderContentWrapper getFavoritesFolder(userIdOrGroupId, filterType, count, startIndex, sortBy, sortOrder, filterValue)

`GET /api/2.0/files/@favorites`

Get the Favorites section

Returns the caller&#39;s own Favorites section: the files and folders this account has marked as favorite,  together with the section folder itself. Favorites are per-account, so the entries another member marked are  not listed here, and a guest sees only their own, usually empty, list. Mark a single file with  &#x60;GET api/2.0/files/favorites/{fileId}&#x60;, or add and remove batches of files and folders with  &#x60;POST api/2.0/files/favorites&#x60; and &#x60;DELETE api/2.0/files/favorites&#x60;. Nothing in the section is modified,  though passing &#x60;sortBy&#x60; saves the requested order as the default order for this account. Entries the caller  can no longer read, and entries that have been moved to the Trash section, drop out of the listing even  though their favorite mark stays, so the section can shrink without an explicit unmark. &#x60;folders&#x60; and &#x60;files&#x60;  hold one page of the section, &#x60;total&#x60; counts the entries matching the request before &#x60;count&#x60; and &#x60;startIndex&#x60;  are applied, and &#x60;current&#x60; describes the section folder itself.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userIdOrGroupId** | query | **UUID** (uuid) | Restricts the listing to the entries authored by this portal member, or by the members of this group; the same  parameter accepts either kind of identifier. Omit it to list everything the caller can read. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **filterType** | query | **FilterType** | Narrows the listing to a single kind of entry, such as documents, images or one type of room. Omit it to list  every kind the section holds. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 17, 20, 22, 23, 24, 25, 26] |
| **count** | query | **Integer** (int32) | The size of one page of section content. Pair it with &#x60;startIndex&#x60; to walk the listing, and compare the two  with &#x60;total&#x60; in the response to see when the last page has been read. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The number of matching entries to skip before the returned page begins; add &#x60;count&#x60; to it to ask for the next  page. | [optional] [example: 0] |
| **sortBy** | query | **String** | The name of the field the entries are ordered by, matched case-insensitively against the file sort fields:  &#x60;DateAndTime&#x60;, &#x60;AZ&#x60;, &#x60;Size&#x60;, &#x60;Author&#x60;, &#x60;Type&#x60;, &#x60;New&#x60;, &#x60;DateAndTimeCreation&#x60;, &#x60;RoomType&#x60;, &#x60;Tags&#x60;, &#x60;Room&#x60;,  &#x60;CustomOrder&#x60;, &#x60;LastOpened&#x60; and &#x60;UsedSpace&#x60;. A recognized value is also saved as the default order of the  account and reused by later listings that omit the parameter, while a value matching none of the fields leaves  that saved order in place. | [optional] [example: DateAndTime] |
| **sortOrder** | query | **SortOrder** | The direction in which the &#x60;sortBy&#x60; field is ordered. It is saved together with &#x60;sortBy&#x60; as the default order  of the account. | [optional] [example: 1] [enum: 0, 1] |
| **filterValue** | query | **String** | The search string the section is filtered by: it is matched as a substring of entry titles and, for files,  against the indexed document content as well. Omit it to list the section unfiltered. | [optional] [example: My Document] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The Favorites section with one page of the entries the caller marked as favorite | [**FolderContentWrapper**](../files.md#model-foldercontentwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not allowed to read the Favorites section | - | - |
| **404** | The Favorites section could not be resolved for this account | - | - |
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
