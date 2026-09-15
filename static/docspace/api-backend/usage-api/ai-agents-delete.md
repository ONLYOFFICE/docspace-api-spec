# aiAgentsDelete

Referenced types are defined in the [full reference](../newai.md).

> AiFileOperationWrapper aiAgentsDelete(id, aiAgentsDelete\_request)

`DELETE /api/2.0/ai/agents/{id}`

Delete an agent

Deletes an AI agent room. The ID has to be the room&#39;s integer identifier, and the body is forwarded to the DocSpace AI service unchanged, so it accepts the same options as deleting an ordinary room - &#x60;deleteAfter&#x60; among them. Deletion is asynchronous there: the answer is a file-operation payload to poll, not a completed result. The agent&#39;s model binding is deliberately left behind, because the upstream assignment API has no per-entry delete, so an orphaned assignment row survives the room.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] [example: 1234] |
| **aiAgentsDelete\_request** | body | [**aiAgentsDelete_request**](../newai.md#model-aiagentsdelete-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The queued file operation. Deletion runs asynchronously, so poll DocSpace for its outcome. | [**AiFileOperationWrapper**](../newai.md#model-aifileoperationwrapper) | - |
| **400** | The agent ID is not a positive integer. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFileOperationWrapper**](../newai.md#model-aifileoperationwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
