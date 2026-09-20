# getFileVersionInfo

Referenced types are defined in the [full reference](../files.md).

> FileArrayWrapper getFileVersionInfo(fileId)

`GET /api/2.0/files/file/{fileId}/history`

Get file versions

Returns every stored version of a file, newest first, each of them shaped like the file itself - the version  and the revision group it belongs to, the size, the comment saved with it, the addresses for viewing it, and  the thumbnail and lock state. Unlike the editing revisions of &#x60;GET api/2.0/files/file/{fileId}/edit/history&#x60;,  this list also holds the autosave revisions an editing session writes, so it is the fuller of the two, and it  is the shape a client already knows how to render. The caller needs the right to read the history of the file,  which is a stricter rule than reading the file: in a room only its managers and content creators may read the  history, and in a personal section editing access is enough, so a member with read access to somebody else&#39;s  file, and even a DocSpace admin in that position, are refused, as is an anonymous caller. The operation is  read-only. To restore one of the versions use &#x60;POST api/2.0/files/file/{fileId}/restoreversion&#x60;, and to close  or reopen a revision group &#x60;PUT api/2.0/files/file/{fileId}/history&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file the operation addresses. Take the identifier from a listing such as &#x60;GET api/2.0/files/{folderId}&#x60;: a  file stored on the portal is numbered, while a file in a connected third-party account is named by an opaque  string. | [required] [example: 10] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Every stored version of the file, newest first | [**FileArrayWrapper**](../files.md#model-filearraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileArrayWrapper**](../files.md#model-filearraywrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **String** | The file the operation addresses. Take the identifier from a listing such as &#x60;GET api/2.0/files/{folderId}&#x60;: a  file stored on the portal is numbered, while a file in a connected third-party account is named by an opaque  string. | [required] [example: 10] |

Return type: [**ThirdPartyFileArrayWrapper**](../files.md#model-thirdpartyfilearraywrapper)

## Authorization

[cookieAuth](../files.md#cookieauth), [bearerAuth](../files.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
