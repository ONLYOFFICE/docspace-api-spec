# aiAiRegenerateStream

Referenced types are defined in the [full reference](../aichat.md).

> AiChatEvent aiAiRegenerateStream(aiAiRegenerateStream\_request)

`POST /api/2.0/ai/ai/regenerate-stream`

Regenerate stream

Re-rolls the last assistant reply of an existing thread: every message after the last user message - the previous reply and any tool-call hops - is dropped, and a fresh reply is streamed as newline-delimited &#x60;ChatEvent&#x60; objects against the unchanged prompt. The thread has to exist already, &#x60;threadId&#x60; is required, and no title is generated. The dropped messages are gone for good, so this is a destructive operation on the thread&#39;s tail rather than a retry that keeps both answers. Unlike &#x60;send-with-stream&#x60; the profile is not verified before the stream opens, so an unusable model surfaces as an error frame inside the 200 rather than as a 4xx.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiRegenerateStream\_request** | body | [**aiAiRegenerateStream_request**](../aichat.md#model-aiairegeneratestream-request-body) |  | [required] |

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
