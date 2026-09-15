# moveBatchItems

Referenced types are defined in the [full reference](../files.md).

> FileOperationArrayWrapper moveBatchItems(BatchRequestDto)

`PUT /api/2.0/files/fileops/move`

Move files and folders

Queues a background job that moves the requested files and folders into &#x60;destFolderId&#x60;, removing them from  where they were, and answers with the caller&#39;s move and copy operations, including the one just started. Poll  &#x60;GET api/2.0/files/fileops&#x60; until the operation reports &#x60;finished&#x60;. Before starting,  &#x60;GET api/2.0/files/fileops/move&#x60; reports which items already have a same-named entry at the destination and  &#x60;conflictResolveType&#x60; decides what happens to them, while &#x60;GET api/2.0/files/fileops/checkdestfolder&#x60; reports  whether the destination accepts the files at all. The caller needs create access to the destination and the  right to take the items out of their source, which is why room members with editing or review rights are  refused with 403, and why content-creator rights inside a room allow copying an item out of it but not moving  it. A room cannot be moved this way — use &#x60;PUT api/2.0/files/rooms/{id}/archive&#x60; instead. To keep the  originals use &#x60;PUT api/2.0/files/fileops/copy&#x60;. An empty selection queues nothing.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BatchRequestDto** | body | [**BatchRequestDto**](../files.md#model-batchrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The move and copy operations of the caller, the one just queued included | [**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller cannot create items in the destination folder, or cannot take one of the items out of its source | - | - |
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
