# deleteBatchItems

Referenced types are defined in the [full reference](../files.md).

> FileOperationArrayWrapper deleteBatchItems(DeleteBatchRequestDto)

`PUT /api/2.0/files/fileops/delete`

Delete files and folders

Queues a background job that deletes the requested files and folders, and answers with the caller&#39;s delete  operations, including the one just started. Poll &#x60;GET api/2.0/files/fileops&#x60; until the operation reports  &#x60;finished&#x60;, and read its &#x60;error&#x60;: a failure on a single item is reported there rather than as a status code.  With &#x60;immediately&#x3D;false&#x60; the items are moved to the caller&#39;s Trash and can be restored from it, while  &#x60;immediately&#x3D;true&#x60; removes them at once and for good; deleting a folder takes everything inside it either way.  The call is destructive and it is not a no-op on repetition — a second call with the same ids deletes whatever  has been restored in the meantime. Access is checked before the job is queued: deleting from a room requires  room manager or content-creator rights, editing or read rights are refused with 403, and an id that resolves  to nothing is answered as missing. An empty selection queues nothing and answers with the operations that are  already there. To clear the Trash itself use &#x60;PUT api/2.0/files/fileops/emptytrash&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **DeleteBatchRequestDto** | body | [**DeleteBatchRequestDto**](../files.md#model-deletebatchrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The delete operations of the caller, the one just queued included | [**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller does not have the rights to delete one of the listed items | - | - |
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
