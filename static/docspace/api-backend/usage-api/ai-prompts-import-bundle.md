# aiPromptsImportBundle

Referenced types are defined in the [full reference](../aichat.md).

> AiImportResult aiPromptsImportBundle(aiPromptsImportBundle\_request)

`POST /api/2.0/ai/prompts/import-bundle`

Import bundle

Writes a bundle produced by &#x60;GET api/2.0/ai/prompts/export&#x60; back into the caller&#39;s library. &#x60;mode&#x60; decides how: &#x60;replace&#x60; deletes the current prompts and folders before writing, and &#x60;merge&#x60; writes the bundle on top of what is already there. The folder references inside the bundle are validated before anything is written, so a corrupt bundle is rejected whole rather than applied halfway. &#x60;replace&#x60; is destructive and cannot be undone - export first if the current library matters.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsImportBundle\_request** | body | [**aiPromptsImportBundle_request**](../aichat.md#model-aipromptsimportbundle-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the bundle was written, how many prompts it imported, and what was refused. | [**AiImportResult**](../aichat.md#model-aiimportresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiImportResult**](../aichat.md#model-aiimportresult)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
