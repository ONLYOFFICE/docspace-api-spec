# toggleFileFavorite

Referenced types are defined in the [full reference](../files.md).

> BooleanWrapper toggleFileFavorite(fileId, favorite)

`GET /api/2.0/files/favorites/{fileId}`

Set the file favorite status

Sets or clears the favorite mark of one file for the calling account: &#x60;true&#x60; adds the file to the favorites,  &#x60;false&#x60; takes it out again. The call changes stored state even though it is a GET, so it is not one to issue  speculatively; repeating it with the same value changes nothing further. The mark is personal, no other member  sees it, and the file stays where it is stored. Read access is enough, so a room member with view-only rights  and a guest may call it. The answer only echoes the value that was asked for: an identifier that resolves to  nothing and a file the caller cannot read are skipped without a word, an encrypted file of a private room is  never marked, and the requested value still comes back, so read the outcome from  &#x60;GET api/2.0/files/@favorites&#x60; instead. A file moved to the Trash keeps its mark and is left out of that  listing until it is restored. To mark several entries at once, or to mark folders, use  &#x60;POST api/2.0/files/favorites&#x60; and &#x60;DELETE api/2.0/files/favorites&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file the operation addresses. Take the identifier from a listing such as &#x60;GET api/2.0/files/{folderId}&#x60;: a  file stored on the portal is numbered, while a file in a connected third-party account is named by an opaque  string. | [required] [example: 10] |
| **favorite** | query | **Boolean** | Which state to put the mark in: &#x60;true&#x60; adds the file to the favorites of the calling account, &#x60;false&#x60; removes  it from them. Leaving the field out of the request removes the mark rather than setting it. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Echo of the requested state, which does not prove that the mark was changed | [**BooleanWrapper**](../files.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | Changing the favorite mark is refused for the caller | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../files.md#model-booleanwrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **String** | The file the operation addresses. Take the identifier from a listing such as &#x60;GET api/2.0/files/{folderId}&#x60;: a  file stored on the portal is numbered, while a file in a connected third-party account is named by an opaque  string. | [required] [example: 10] |


## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
