# aiThreadsAppendUserMessage

Referenced types are defined in the [full reference](../newai.md).

> aiThreadsAppendUserMessage_200_response aiThreadsAppendUserMessage(aiThreadsAppendUserMessage\_request)

`POST /api/2.0/ai/threads/append-user-message`

Append user message

Stores a user message in a thread and bumps its last-edit date so the thread resurfaces at the top of the list. The per-kind attachment cap of the composer is enforced here as well, so a direct API call cannot exceed what the UI allows. Passing &#x60;profileId&#x60; rebinds the thread to another model, which is how a mid-conversation model switch is recorded. The answer carries the new message&#39;s ID; the message is stored as sent and no reply is generated - run a round with &#x60;POST api/2.0/ai/ai/send-with-stream&#x60; for that.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsAppendUserMessage\_request** | body | [**aiThreadsAppendUserMessage_request**](../newai.md#model-aithreadsappendusermessage-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The stored message, with the ID storage assigned to it. | [**aiThreadsAppendUserMessage_200_response**](../newai.md#model-aithreadsappendusermessage-200-response) | - |
| **400** | The message is longer than the limit allows. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiThreadsAppendUserMessage_200_response**](../newai.md#model-aithreadsappendusermessage-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
