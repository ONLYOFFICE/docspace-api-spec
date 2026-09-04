# aiPromptsMove

Referenced types are defined in the [full reference](../newai.md).

> AiPromptMutationResult aiPromptsMove(aiPromptsMove\_request)

`PUT /api/2.0/ai/prompts/move`

Move

Moves a saved prompt into another folder, or to the root. The name is re-validated in the target folder, so the move fails when a prompt of that name is already there.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsMove\_request** | body | [**aiPromptsMove_request**](../newai.md#model-aipromptsmove-request-body) |  | [required] |

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
