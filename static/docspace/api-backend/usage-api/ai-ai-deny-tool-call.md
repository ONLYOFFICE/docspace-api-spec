# aiAiDenyToolCall

Referenced types are defined in the [full reference](../aichat.md).

> AiChatEvent aiAiDenyToolCall(AiAiToolCallData)

`POST /api/2.0/ai/ai/deny-tool-call`

Deny tool call

Refuses the tool call a chat round is paused on and resumes it immediately, streaming the continuation as newline-delimited &#x60;ChatEvent&#x60; objects. The literal &#x60;User deny tool call&#x60; is persisted in place of the tool result, so the model sees an explicit refusal rather than a missing answer and may reply without the tool or ask for something else. Nothing is executed and no result is accepted from the caller. Use &#x60;POST api/2.0/ai/ai/approve-tool-call&#x60; to supply a result instead.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiToolCallData** | body | [**AiAiToolCallData**](../aichat.md#model-aiaitoolcalldata) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](../aichat.md#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiChatEvent**](../aichat.md#model-aichatevent)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json
