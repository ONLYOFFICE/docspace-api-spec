# aiAiSendWithStream

Referenced types are defined in the [full reference](../aichat.md).

> AiChatEvent aiAiSendWithStream(AiAiSendStreamBody)

`POST /api/2.0/ai/ai/send-with-stream`

Send with stream

Runs one chat round and streams it back as newline-delimited &#x60;ChatEvent&#x60; objects. Omitting &#x60;threadId&#x60; opens a new thread, which requires that &#x60;entityId&#x60; names a room the caller can open and that a profile resolves for it; the user message and the reply are persisted either way, and a new thread also gets a generated title. The model is settled in a fixed order - an agent&#39;s assignment in scope overrides everything, then the explicit &#x60;profileId&#x60;, then the one stored on the thread, then the &#x60;Chat&#x60; assignment - and the effective profile is checked before the stream opens, so an unknown one fails with 400 rather than as an error buried in a 200. A tool call pauses the round and ends the stream; resume it with &#x60;POST api/2.0/ai/ai/approve-tool-call&#x60; or &#x60;POST api/2.0/ai/ai/deny-tool-call&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiSendStreamBody** | body | [**AiAiSendStreamBody**](../aichat.md#model-aiaisendstreambody) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](../aichat.md#model-aichatevent) | - |
| **400** | The prompt is empty, more attachments were sent than the limit allows, or no AI profile could be resolved for the requested action. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **402** | The portal has no paid AI quota left, so the profile bound to this action cannot be dispatched. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The &#x60;entityId&#x60; names a room the caller cannot open, or no live profile is bound to it. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiChatEvent**](../aichat.md#model-aichatevent)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json
