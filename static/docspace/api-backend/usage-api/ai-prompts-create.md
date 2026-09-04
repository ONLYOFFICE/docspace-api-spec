# aiPromptsCreate

Referenced types are defined in the [full reference](../newai.md).

> AiPromptMutationResult aiPromptsCreate(AiCreatePromptInput)

`POST /api/2.0/ai/prompts/create`

Create

Saves a new prompt. The name must be non-empty and unique inside its folder, and &#x60;folderId&#x60; must point at an existing folder - omit it for the root.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiCreatePromptInput** | body | [**AiCreatePromptInput**](../newai.md#model-aicreatepromptinput) |  | [required] |

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
