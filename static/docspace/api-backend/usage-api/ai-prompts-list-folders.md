# aiPromptsListFolders

Referenced types are defined in the [full reference](../aichat.md).

> List aiPromptsListFolders()

`GET /api/2.0/ai/prompts/list-folders`

List folders

Lists every folder of the caller&#39;s prompt library, newest first, with no parameters and no pagination. Folders are flat, so the answer is a single list rather than a tree. The prompts inside them are not included - read those with &#x60;GET api/2.0/ai/prompts/list&#x60; per folder. Another user&#39;s folders are never listed.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Every folder of the caller&#39;s library, newest first. | [**List**](../aichat.md#model-aipromptfolder) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**List**](../aichat.md#model-aipromptfolder)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
