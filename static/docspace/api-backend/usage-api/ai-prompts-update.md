# aiPromptsUpdate

Referenced types are defined in the [full reference](../newai.md).

> AiPromptMutationResult aiPromptsUpdate(aiPromptsUpdate\_request)

`PUT /api/2.0/ai/prompts/update`

Update

Updates a saved prompt. The name and the folder reference are re-validated whenever either of them changes.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsUpdate\_request** | body | [**aiPromptsUpdate_request**](../newai.md#model-aipromptsupdate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptMutationResult**](../newai.md#model-aipromptmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiPromptMutationResult**](../newai.md#model-aipromptmutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AISettingsApi
