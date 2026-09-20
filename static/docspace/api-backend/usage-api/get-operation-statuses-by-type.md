# getOperationStatusesByType

Referenced types are defined in the [full reference](../files.md).

> FileOperationArrayWrapper getOperationStatusesByType(operationType, id)

`GET /api/2.0/files/fileops/{operationType}`

Get file operations by type

Returns the background file operations of the caller that are of one kind, named by the number in the route:  &#x60;1&#x60; for a copy, &#x60;2&#x60; for a deletion, &#x60;3&#x60; for a download, &#x60;4&#x60; for a mark-as-read and &#x60;7&#x60; for a duplication. The  answer carries the same records as &#x60;GET api/2.0/files/fileops&#x60;, with the same rule that a finished operation  is reported once and then dropped, and &#x60;id&#x60; narrows it further to a single operation. Moves, kind &#x60;0&#x60;, cannot  be read through this route: the address &#x60;api/2.0/files/fileops/move&#x60; belongs to another operation, so read  moves from &#x60;GET api/2.0/files/fileops&#x60; and pick the records whose &#x60;operation&#x60; is &#x60;0&#x60;. A kind that has no queue  of its own — &#x60;5&#x60; for an import, &#x60;6&#x60; for a conversion — is accepted and answers with an empty array, while a  number outside the operation type is rejected as an invalid request. The call changes nothing and never shows  another account&#39;s operations.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **operationType** | path | **FileOperationType** | The kind of operation the answer is limited to. Only the kinds that have a queue of their own ever carry  records — a copy, a deletion, a download, a mark-as-read and a duplication — and moves cannot be read through  this route at all, because its address belongs to another operation. | [required] [example: 2] [enum: 0, 1, 2, 3, 4, 5, 6, 7] |
| **id** | query | **String** | The operation to report on, as returned in &#x60;id&#x60; when it was started; without it every operation of the caller  is reported. An id that is not among the caller&#39;s operations gives an empty answer rather than an error. | [optional] [example: b2f3e9a4-7c15-4d8e-9f60-3a1c5e7d0b42] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The operations of the caller that are of the requested kind | [**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper)

## Authorization

[cookieAuth](../files.md#cookieauth), [bearerAuth](../files.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
