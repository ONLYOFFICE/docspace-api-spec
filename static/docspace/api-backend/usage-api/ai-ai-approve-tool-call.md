# aiAiApproveToolCall

Referenced types are defined in the [full reference](../newai.md).

> AiChatEvent aiAiApproveToolCall(aiAiApproveToolCall\_request)

`POST /api/2.0/ai/ai/approve-tool-call`

Approve tool call

Resumes a chat round that a tool call has paused, and streams the continuation as newline-delimited &#x60;ChatEvent&#x60; objects. The result supplied in the request is persisted onto the assistant message that issued the call, so the tool is not executed here - the caller runs it and reports the outcome. The round continues against the augmented history and may pause again on a further tool call. Call &#x60;POST api/2.0/ai/ai/deny-tool-call&#x60; instead to refuse the call and let the model answer without it.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiApproveToolCall\_request** | body | [**aiAiApproveToolCall_request**](../newai.md#model-aiaiapprovetoolcall-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](../newai.md#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiChatEvent**](../newai.md#model-aichatevent)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json
