# aiOpenaiChatCompletions

Referenced types are defined in the [full reference](../aichat.md).

> Map aiOpenaiChatCompletions(profileId, request\_body)

`POST /api/2.0/ai/openai/{profileId}/v1/chat/completions`

OpenAI chat completions passthrough

OpenAI-compatible chat completions for the document editor&#39;s AI plugin. The profile is resolved server-side, its credentials are attached, and the body is forwarded to the provider verbatim - the payload is owned by the plugin&#39;s SDK on one end and the provider on the other. A client disconnect cancels the provider call.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **profileId** | path | **String** | The AI provider profile identifier. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **request\_body** | body | **Map** | An OpenAI Chat Completions request, forwarded to the provider byte for byte. The shape is the provider&#39;s, not this API&#39;s, so consult the provider&#39;s own reference; the model and the credentials come from the profile in the path and must not be sent here. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The provider&#39;s own response, relayed verbatim with its status and content type. | **Map** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**aiOpenaiChatCompletions_403_response**](../aichat.md#model-aiopenaichatcompletions-403-response) | - |
| **404** | No profile with this identifier exists for the caller. | [**aiOpenaiChatCompletions_403_response**](../aichat.md#model-aiopenaichatcompletions-403-response) | - |
| **413** | The request body is larger than this route accepts. | [**aiOpenaiChatCompletions_403_response**](../aichat.md#model-aiopenaichatcompletions-403-response) | - |
| **429** | Relayed verbatim from the AI provider, which is rate-limiting this portal&#39;s key. | [**aiOpenaiChatCompletions_403_response**](../aichat.md#model-aiopenaichatcompletions-403-response) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**aiOpenaiChatCompletions_403_response**](../aichat.md#model-aiopenaichatcompletions-403-response) | - |
| **502** | The AI provider could not be reached, or answered with a failure of its own. | [**aiOpenaiChatCompletions_403_response**](../aichat.md#model-aiopenaichatcompletions-403-response) | - |

## Return type

**Map**

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
