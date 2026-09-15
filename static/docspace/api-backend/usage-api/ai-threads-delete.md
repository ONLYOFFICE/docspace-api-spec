# aiThreadsDelete

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiThreadsDelete(body)

`DELETE /api/2.0/ai/threads/delete`

Delete a chat thread

Deletes a thread together with every message in it. The thread has to exist: unlike the other operations that take a &#x60;threadId&#x60;, this one checks first and answers 404 for an unknown or already-deleted thread rather than reporting success. The deletion is permanent and the messages cannot be recovered. To empty a thread but keep it, use &#x60;DELETE api/2.0/ai/threads/clear-messages&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** | The ID of the thread to delete, as a bare JSON string. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the thread and its messages are gone. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **400** | &#x60;threadId&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **404** | No thread has this ID. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
