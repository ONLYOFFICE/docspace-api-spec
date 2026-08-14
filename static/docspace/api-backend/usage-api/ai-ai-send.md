# aiAiSend

Referenced types are defined in the [full reference](../newai.md).

> AiThreadMessageLike aiAiSend(aiAiSend\_request)

`POST /api/2.0/ai/ai/send`

Send

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiSend\_request** | body | [**aiAiSend_request**](../newai.md#model-aiaisend-request-body) |  | [required] |

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
