# getFolderInfo

Referenced types are defined in the [full reference](../files.md).

> FolderWrapper getFolderInfo(folderId)

`GET /api/2.0/files/folder/{folderId}`

Get folder information

Returns one folder as an object - its title, its parent, the moments it was created and last changed, the  access the caller has to it, the number of items that are new for them, and the room settings when the folder  is a room - without listing anything inside it. Use it to resolve a folder identifier into something  displayable, and &#x60;GET api/2.0/files/{folderId}&#x60; when the contents are what is wanted; unlike that operation,  this one leaves the new-item marks of the folder alone. Any member who can read the folder may call it, and an  anonymous caller only through an external link that grants access, everybody else being refused; a folder that  does not exist is answered as not found. The call is read-only. The chain of parents above the folder is not  part of the answer and is read with &#x60;GET api/2.0/files/folder/{folderId}/path&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **Integer** (int32) | The folder the operation acts on. Take the identifier from a listing such as &#x60;GET api/2.0/files/@root&#x60; or  &#x60;GET api/2.0/files/{folderId}&#x60;: a folder stored in the portal is numbered, while a folder in a connected  third-party account is named by an opaque string. | [required] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The folder | [**FolderWrapper**](../files.md#model-folderwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderWrapper**](../files.md#model-folderwrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | path | **String** | The folder the operation acts on. Take the identifier from a listing such as &#x60;GET api/2.0/files/@root&#x60; or  &#x60;GET api/2.0/files/{folderId}&#x60;: a folder stored in the portal is numbered, while a folder in a connected  third-party account is named by an opaque string. | [required] [example: 1] |

Return type: [**ThirdPartyFolderWrapper**](../files.md#model-thirdpartyfolderwrapper)

## Authorization

[cookieAuth](../files.md#cookieauth), [bearerAuth](../files.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
