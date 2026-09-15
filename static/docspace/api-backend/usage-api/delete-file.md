# deleteFile

Referenced types are defined in the [full reference](../files.md).

> FileOperationArrayWrapper deleteFile(fileId, Delete, ReturnSingleOperation)

`DELETE /api/2.0/files/file/{fileId}`

Delete a file

Queues the deletion of one file and answers with the caller&#39;s file operations, the one just created among  them. The file is not gone when the response arrives: poll &#x60;GET api/2.0/files/fileops&#x60; until the operation  reports &#x60;finished&#x60;, and read its &#x60;error&#x60; to learn whether the deletion succeeded. By default the file is moved  to Trash, from where it can be restored; &#x60;immediately&#x3D;true&#x60; deletes it for good instead, and inside a room,  where there is no Trash, deletion is always final. &#x60;deleteAfter&#x3D;true&#x60; postpones the deletion until the editing  session on the file has ended, so a file somebody is working on is not pulled away.  &#x60;returnSingleOperation&#x3D;true&#x60; narrows the answer to this deletion instead of listing every active operation of  the caller. The caller needs the right to delete the file, which the room admin, a DocSpace admin acting as  room manager and a content creator acting on their own file have; editing access alone, read access, a guest  and a member without access to the room are all refused. The call is destructive. To delete several items at  once use &#x60;PUT api/2.0/files/fileops/delete&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file to delete. | [required] [example: 1] |
| **Delete** | body | [**Delete**](../files.md#model-delete) | When and how the file is deleted. | [required] |
| **ReturnSingleOperation** | query | **Boolean** | Which operations the answer carries: &#x60;true&#x60; returns the operation this call started and nothing else, &#x60;false&#x60;  returns every operation of the same kind that the caller has running or unread. When nothing was queued, which  happens for an empty selection, &#x60;true&#x60; falls back to the full list. | [optional] [example: false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The file operations of the caller, including the deletion just queued | [**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
