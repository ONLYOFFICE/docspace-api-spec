# aiThreadsAppendUserMessage

Referenced types are defined in the [full reference](../newai.md).

> AiThreadMessageLike aiThreadsAppendUserMessage(aiThreadsAppendUserMessage\_request)

`POST /api/2.0/ai/threads/append-user-message`

Append user message

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsAppendUserMessage\_request** | body | [**aiThreadsAppendUserMessage_request**](../newai.md#model-aithreadsappendusermessage-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThreadMessageLike**](../newai.md#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiThreadMessageLike**](../newai.md#model-aithreadmessagelike)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
