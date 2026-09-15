# aiPromptsMove

Referenced types are defined in the [full reference](../newai.md).

> AiPromptMutationResult aiPromptsMove(aiPromptsMove\_request)

`PUT /api/2.0/ai/prompts/move`

Move a prompt to a folder

Moves a saved prompt into another folder, or to the root when &#x60;folderId&#x60; is omitted or null. The name is re-validated in the target folder, so the move fails when a prompt of that name already sits there - rename it first with &#x60;PUT api/2.0/ai/prompts/update&#x60;. Nothing about the prompt other than its folder changes. The answer carries the moved prompt.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsMove\_request** | body | [**aiPromptsMove_request**](../newai.md#model-aipromptsmove-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the prompt was moved, with the moved prompt in &#x60;prompt&#x60;. | [**AiPromptMutationResult**](../newai.md#model-aipromptmutationresult) | - |
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
