# getFileInfo

Referenced types are defined in the [full reference](../files.md).

> FileWrapper getFileInfo(fileId, version)

`GET /api/2.0/files/file/{fileId}`

Get file information

Returns one file as the portal stores it, together with the state it has for the caller: the title, the folder  it lies in, the size, the current version and revision group, the addresses for viewing and editing it, the  actions the caller is allowed to perform on it, the sharing rights it was reached through, and the thumbnail  state. &#x60;version&#x60; picks an older version instead of the current one; the default of -1 means the current  version. When the file belongs to another person&#39;s own section and the caller cannot read the folder holding  it, the answer reports the Shared with me section as its folder, so that a client can show it in a place the  caller can actually open. The caller needs read access to the file, which any member of the room it lies in  has; a caller without access to the room is refused and an anonymous caller without an external share link is  rejected. The operation is read-only. For every version at once use &#x60;GET api/2.0/files/file/{fileId}/history&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file to read. | [required] [example: 1] |
| **version** | query | **Integer** (int32) | The version to read, as reported by &#x60;GET api/2.0/files/file/{fileId}/history&#x60;; -1, the default, reads the  current version. | [optional] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The file as it is stored, with the state it has for the caller | [**FileWrapper**](../files.md#model-filewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileWrapper**](../files.md#model-filewrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **String** | The file to read. | [required] [example: 1] |

Return type: [**ThirdPartyFileWrapper**](../files.md#model-thirdpartyfilewrapper)

## Authorization

[cookieAuth](../files.md#cookieauth), [bearerAuth](../files.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
