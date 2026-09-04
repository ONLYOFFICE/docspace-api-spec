# aiOpenaiChatCompletions

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiOpenaiChatCompletions(profileId, request\_body)

`POST /api/2.0/ai/openai/{profileId}/v1/chat/completions`

OpenAI-compatible chat completions proxied to the profile&#39;s provider

OpenAI-compatible chat completions for the document editor&#39;s AI plugin. The profile is resolved server-side, its credentials are attached, and the body is forwarded to the provider verbatim - the payload is owned by the plugin&#39;s SDK on one end and the provider on the other. A client disconnect cancels the provider call.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **profileId** | path | **String** | The AI provider profile identifier. | [required] |
| **request\_body** | body | **Map** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
