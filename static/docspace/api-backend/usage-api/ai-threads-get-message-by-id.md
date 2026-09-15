# aiThreadsGetMessageById

Referenced types are defined in the [full reference](../newai.md).

> AiThreadMessageLike aiThreadsGetMessageById(messageId)

`GET /api/2.0/ai/threads/get-message-by-id`

Get one chat message

Returns one message by its ID, wherever it sits, without needing the thread it belongs to. &#x60;messageId&#x60; is required. Unlike &#x60;GET api/2.0/ai/threads/get-by-id&#x60; an unknown ID is not reported as 404: the answer is an empty body with status 200, so a client has to treat a missing payload as no such message. Message IDs come from the thread history or from the answer of &#x60;POST api/2.0/ai/threads/append-user-message&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **messageId** | query | **String** | The globally unique chat message identifier. | [required] [example: 22222222-2222-2222-2222-222222222222] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The message, or an empty body when no message has that ID. | [**AiThreadMessageLike**](../newai.md#model-aithreadmessagelike) | - |
| **400** | &#x60;messageId&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiThreadMessageLike**](../newai.md#model-aithreadmessagelike)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
