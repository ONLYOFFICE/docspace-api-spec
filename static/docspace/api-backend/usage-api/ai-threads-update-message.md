# aiThreadsUpdateMessage

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiThreadsUpdateMessage(aiThreadsUpdateMessage\_request)

`PUT /api/2.0/ai/threads/update-message`

Update message

Replaces the content of one stored message, which is how the edit and regenerate flows change a message outside the streaming lifecycle. The whole message is overwritten by the one supplied rather than merged, so send a complete object. Neither the ID nor the payload is validated here, so a malformed request surfaces as an error relayed from storage rather than as a 400. The answer only confirms the write.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsUpdateMessage\_request** | body | [**aiThreadsUpdateMessage_request**](../newai.md#model-aithreadsupdatemessage-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the replacement was stored. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIToolsApi
