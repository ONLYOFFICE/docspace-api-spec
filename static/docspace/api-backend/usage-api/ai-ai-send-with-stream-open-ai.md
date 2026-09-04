# aiAiSendWithStreamOpenAI

Referenced types are defined in the [full reference](../newai.md).

> AiOpenAIStreamChunk aiAiSendWithStreamOpenAI(AiAiSendStreamBody)

`POST /api/2.0/ai/ai/send-with-stream-openai`

Send with stream open ai

The same chat round as &#x60;send-with-stream&#x60;, re-encoded as an OpenAI Chat Completions stream of &#x60;chat.completion.chunk&#x60; objects. Storage, title generation and tool-call pauses are identical - only the wire shape differs; a tool call ends the stream with &#x60;finish_reason: tool_calls&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiSendStreamBody** | body | [**AiAiSendStreamBody**](../newai.md#model-aiaisendstreambody) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Server-sent events stream of OpenAI &#x60;chat.completion.chunk&#x60; objects, terminated by a &#x60;[DONE]&#x60; sentinel. | [**AiOpenAIStreamChunk**](../newai.md#model-aiopenaistreamchunk) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiOpenAIStreamChunk**](../newai.md#model-aiopenaistreamchunk)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: text/event-stream, application/json

## AIAgentsApi
