# aiPromptsCreate

Referenced types are defined in the [full reference](../aichat.md).

> AiPromptMutationResult aiPromptsCreate(AiCreatePromptInput)

`POST /api/2.0/ai/prompts/create`

Save a prompt

Saves a new prompt in the caller&#39;s own prompt library and returns it. The name has to be non-empty and unique inside its folder, and &#x60;folderId&#x60; has to name an existing folder - omit it to save the prompt at the root. Prompts are per-user: another user&#39;s library is never visible here, and no permission beyond having AI enabled is needed. The answer carries the stored prompt including the ID to use with the update, move and delete operations.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiCreatePromptInput** | body | [**AiCreatePromptInput**](../aichat.md#model-aicreatepromptinput) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the prompt was saved, with it in &#x60;prompt&#x60;. | [**AiPromptMutationResult**](../aichat.md#model-aipromptmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiPromptMutationResult**](../aichat.md#model-aipromptmutationresult)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
