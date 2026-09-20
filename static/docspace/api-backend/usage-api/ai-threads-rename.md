# aiThreadsRename

Referenced types are defined in the [full reference](../aichat.md).

> AiSuccessResponse aiThreadsRename(aiThreadsRename\_request)

`PUT /api/2.0/ai/threads/rename`

Rename a chat thread

Replaces a thread&#39;s title with the one supplied and bumps its last-edit date. Both &#x60;threadId&#x60; and a title with at least one non-whitespace character are required - a blank title is rejected rather than silently stored, so a thread cannot end up nameless. The answer only confirms the write. To have the model produce a title instead of supplying one, use &#x60;POST api/2.0/ai/threads/regenerate-title&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsRename\_request** | body | [**aiThreadsRename_request**](../aichat.md#model-aithreadsrename-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the new title was stored. | [**AiSuccessResponse**](../aichat.md#model-aisuccessresponse) | - |
| **400** | &#x60;threadId&#x60; or the new title is missing. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../aichat.md#model-aisuccessresponse)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
