# aiAiSendCustom

Referenced types are defined in the [full reference](../newai.md).

> AiThreadMessageLike aiAiSendCustom(aiAiSendCustom\_request)

`POST /api/2.0/ai/ai/send-custom`

Send custom

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiSendCustom\_request** | body | [**aiAiSendCustom_request**](../newai.md#model-aiaisendcustom-request-body) |  | [required] |

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
