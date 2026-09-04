# aiOpenaiImagesGenerations

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiOpenaiImagesGenerations(profileId, request\_body)

`POST /api/2.0/ai/openai/{profileId}/v1/images/generations`

OpenAI-compatible image generation proxied to the profile&#39;s provider

OpenAI-compatible image generation for the document editor&#39;s AI plugin. As with the chat-completions passthrough, the profile&#39;s credentials are attached server-side and the body reaches the provider unchanged.

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

## AIPreferencesApi
