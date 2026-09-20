# aiPromptsList

Referenced types are defined in the [full reference](../aichat.md).

> List aiPromptsList(folderId)

`GET /api/2.0/ai/prompts/list`

List saved prompts

Lists the caller&#39;s saved prompts, newest first. &#x60;folderId&#x60; scopes the answer to one folder, and omitting it - or sending it empty - lists the prompts that sit at the root rather than every prompt, because the client fetcher cannot tell an absent value from a null one. There is therefore no way to ask for the whole library in one call: walk the folders from &#x60;GET api/2.0/ai/prompts/list-folders&#x60;, or take everything at once with &#x60;GET api/2.0/ai/prompts/export&#x60;. The prompts of other users are never included.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **folderId** | query | **String** | The prompt folder identifier. Omit to list the prompts that sit outside any folder. | [optional] [example: 44444444-4444-4444-4444-444444444444] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The prompts of the scope, newest first. | [**List**](../aichat.md#model-aiprompt) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**List**](../aichat.md#model-aiprompt)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
