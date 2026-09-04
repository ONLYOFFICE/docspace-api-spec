# aiAiSendCustom

Referenced types are defined in the [full reference](../newai.md).

> AiThreadMessageLike aiAiSendCustom(aiAiSendCustom\_request)

`POST /api/2.0/ai/ai/send-custom`

Send custom

Runs a free-form one-turn call against a caller-supplied system prompt. No thread, no history and no persistence. The profile is the explicit &#x60;profileId&#x60; when it resolves, otherwise the &#x60;Default&#x60; assignment slot.

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
