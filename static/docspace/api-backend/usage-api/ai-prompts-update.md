# aiPromptsUpdate

Referenced types are defined in the [full reference](../newai.md).

> AiPromptMutationResult aiPromptsUpdate(aiPromptsUpdate\_request)

`PUT /api/2.0/ai/prompts/update`

Update a saved prompt

Changes a saved prompt and returns the stored result. Only the fields present in &#x60;updates&#x60; are written, so a partial object leaves the rest of the prompt alone. The name and the folder reference are re-validated whenever either changes, which means an update can fail on a name another prompt in the same folder already uses. Use &#x60;PUT api/2.0/ai/prompts/move&#x60; to change only the folder.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsUpdate\_request** | body | [**aiPromptsUpdate_request**](../newai.md#model-aipromptsupdate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the prompt was updated, with the stored prompt in &#x60;prompt&#x60;. | [**AiPromptMutationResult**](../newai.md#model-aipromptmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiPromptMutationResult**](../newai.md#model-aipromptmutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AISettingsApi
