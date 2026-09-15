# getEditHistory

Referenced types are defined in the [full reference](../files.md).

> EditHistoryArrayWrapper getEditHistory(fileId)

`GET /api/2.0/files/file/{fileId}/edit/history`

Get version history

Returns the editing revisions of a file, oldest first, as the document service understands them: each entry  carries the version and the revision group it belongs to, the account that saved it, when it was saved, the  comment left on it, the document key of that revision and, where the portal stored them, the changes it  introduced. Only the revisions a person saved are listed - the autosaves an editing session writes in between  are left out, which is what separates this list from the plain version list of  &#x60;GET api/2.0/files/file/{fileId}/history&#x60;. The caller needs the right to read the history of the file, which  editing access and above grant: commenting access, read-only access, a guest, a member without access to the  room and an anonymous caller are all refused, and so is a file kept in a connected third-party storage, which  keeps no history in the portal. The operation is read-only. Take one entry to  &#x60;GET api/2.0/files/file/{fileId}/edit/diff&#x60; to show its changes, or to  &#x60;POST api/2.0/files/file/{fileId}/restoreversion&#x60; to bring it back.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file the operation addresses. Take the identifier from a listing such as &#x60;GET api/2.0/files/{folderId}&#x60;: a  file stored on the portal is numbered, while a file in a connected third-party account is named by an opaque  string. | [required] [example: 10] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The editing revisions of the file, oldest first | [**EditHistoryArrayWrapper**](../files.md#model-edithistoryarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EditHistoryArrayWrapper**](../files.md#model-edithistoryarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
