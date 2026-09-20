# getTrashFolder

Referenced types are defined in the [full reference](../files.md).

> FolderContentWrapper getTrashFolder(userIdOrGroupId, filterType, applyFilterOption, count, startIndex, sortBy, sortOrder, filterValue)

`GET /api/2.0/files/@trash`

Get the Trash section

Returns the caller&#39;s Trash section: the files and folders this account has deleted, kept there until they  are restored or discarded. Each member has a Trash of their own and sees only what they deleted themselves.  Restore an entry by moving it back with &#x60;PUT api/2.0/files/fileops/move&#x60;, or discard the whole section with  &#x60;PUT api/2.0/files/fileops/emptytrash&#x60;; both start a background operation that is polled through  &#x60;GET api/2.0/files/fileops&#x60;. This call itself modifies nothing, though passing &#x60;sortBy&#x60; saves the requested  order as the default order for this account. Only the top level of the section is listed, so the contents of a  deleted folder are not expanded into it, and &#x60;filterValue&#x60; is matched against titles alone here rather than  against document content. &#x60;folders&#x60; and &#x60;files&#x60; hold one page of the result, &#x60;total&#x60; counts everything that  matches before &#x60;count&#x60; and &#x60;startIndex&#x60; are applied, and &#x60;current&#x60; describes the section folder. An account  that is given no Trash of its own, an outsider for instance, receives 404.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userIdOrGroupId** | query | **UUID** (uuid) | Restricts the listing to the entries authored by this portal member, or by the members of this group; the same  parameter accepts either kind of identifier. Omit it to list everything the caller can read. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **filterType** | query | **FilterType** | Narrows the listing to a single kind of entry, such as documents, images or one type of room. Omit it to list  every kind the section holds. | [optional] [example: 1] [enum: 0, 1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 17, 20, 22, 23, 24, 25, 26] |
| **applyFilterOption** | query | **ApplyFilterOption** | Chooses which half of the listing &#x60;filterType&#x60; and &#x60;filterValue&#x60; are applied to: with &#x60;Files&#x60; the folders come  back unfiltered, with &#x60;Folders&#x60; the files do, and with &#x60;All&#x60; both halves are filtered. | [optional] [example: 1] [enum: 0, 1, 2] |
| **count** | query | **Integer** (int32) | The size of one page of section content. Pair it with &#x60;startIndex&#x60; to walk the listing, and compare the two  with &#x60;total&#x60; in the response to see when the last page has been read. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The number of matching entries to skip before the returned page begins; add &#x60;count&#x60; to it to ask for the next  page. | [optional] [example: 0] |
| **sortBy** | query | **String** | The name of the field the entries are ordered by, matched case-insensitively against the file sort fields:  &#x60;DateAndTime&#x60;, &#x60;AZ&#x60;, &#x60;Size&#x60;, &#x60;Author&#x60;, &#x60;Type&#x60;, &#x60;New&#x60;, &#x60;DateAndTimeCreation&#x60;, &#x60;RoomType&#x60;, &#x60;Tags&#x60;, &#x60;Room&#x60;,  &#x60;CustomOrder&#x60;, &#x60;LastOpened&#x60; and &#x60;UsedSpace&#x60;. A recognized value is also saved as the default order of the  account and reused by later listings that omit the parameter, while a value matching none of the fields leaves  that saved order in place. | [optional] [example: DateAndTime] |
| **sortOrder** | query | **SortOrder** | The direction in which the &#x60;sortBy&#x60; field is ordered. It is saved together with &#x60;sortBy&#x60; as the default order  of the account. | [optional] [example: 1] [enum: 0, 1] |
| **filterValue** | query | **String** | The search string the section is filtered by, matched as a substring of entry titles. Omit it to list the  section unfiltered. | [optional] [example: My Document] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The Trash section with one page of the entries the caller deleted | [**FolderContentWrapper**](../files.md#model-foldercontentwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not allowed to read the Trash section | - | - |
| **404** | This account has no Trash section | - | - |
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
