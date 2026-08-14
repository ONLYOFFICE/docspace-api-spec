# checkFillFormDraft

Referenced types are defined in the [full reference](../files.md).

> StringWrapper checkFillFormDraft(fileId, CheckFillFormDraft)

`POST /api/2.0/files/masterform/{fileId}/checkfillformdraft`

Check the form draft filling

Checks if the current file is a form draft which can be filled out.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file ID of the form draft. | [required] [example: 1] |
| **CheckFillFormDraft** | body | [**CheckFillFormDraft**](../files.md#model-checkfillformdraft) | The parameters for checking the form draft filling. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Link to the form | [**StringWrapper**](../files.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | You don&#39;t have enough permission to view the file | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../files.md#model-stringwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
