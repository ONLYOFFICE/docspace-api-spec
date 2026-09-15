# aiAiSendCustom

Referenced types are defined in the [full reference](../newai.md).

> AiThreadMessageLike aiAiSendCustom(aiAiSendCustom\_request)

`POST /api/2.0/ai/ai/send-custom`

Send custom

Runs a free-form one-turn call against a system prompt supplied in the request, with no thread, no history and nothing persisted. The model is the explicit &#x60;profileId&#x60; when it resolves, otherwise the &#x60;Default&#x60; assignment slot. The shape of the answer depends on the body rather than on the route: with &#x60;isStream&#x60; set it arrives as a newline-delimited stream of chat events, and without it as a single JSON document, so a client has to handle both. Use &#x60;POST api/2.0/ai/ai/send&#x60; when the prompt should come from the portal&#39;s own action configuration instead of from the caller.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAiSendCustom\_request** | body | [**aiAiSendCustom_request**](../newai.md#model-aiaisendcustom-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The assistant&#39;s reply as one message, or a newline-delimited stream of chat events when &#x60;isStream&#x60; was set. Nothing was persisted. | [**AiThreadMessageLike**](../newai.md#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiThreadMessageLike**](../newai.md#model-aithreadmessagelike)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
