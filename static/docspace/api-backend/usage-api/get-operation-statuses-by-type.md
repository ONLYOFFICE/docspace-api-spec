# getOperationStatusesByType

Referenced types are defined in the [full reference](../files.md).

> FileOperationArrayWrapper getOperationStatusesByType(operationType, id)

`GET /api/2.0/files/fileops/{operationType}`

Get file operation statuses

Retrieves the statuses of operations filtered by the specified operation type.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **operationType** | path | **FileOperationType** | Specifies the type of file operation to be retrieved. | [required] [example: 0] [enum: 0, 1, 2, 3, 4, 5, 6, 7] |
| **id** | query | **String** | The ID of the file operation. | [optional] [example: operation-123-abc] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of file operations | [**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileOperationArrayWrapper**](../files.md#model-fileoperationarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
