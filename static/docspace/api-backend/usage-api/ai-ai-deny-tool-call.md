# aiAiDenyToolCall

Referenced types are defined in the [full reference](../newai.md).

> AiChatEvent aiAiDenyToolCall(AiAiToolCallData)

`POST /api/2.0/ai/ai/deny-tool-call`

Deny tool call

Denies the pending tool call and resumes the chat immediately, with &#x60;User deny tool call&#x60; standing in for the tool result.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiAiToolCallData** | body | [**AiAiToolCallData**](../newai.md#model-aiaitoolcalldata) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Newline-delimited stream of chat events — one JSON &#x60;ChatEvent&#x60; object per line. | [**AiChatEvent**](../newai.md#model-aichatevent) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiChatEvent**](../newai.md#model-aichatevent)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/x-ndjson, application/json
