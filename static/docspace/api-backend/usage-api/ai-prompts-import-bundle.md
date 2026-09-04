# aiPromptsImportBundle

Referenced types are defined in the [full reference](../newai.md).

> AiImportResult aiPromptsImportBundle(aiPromptsImportBundle\_request)

`POST /api/2.0/ai/prompts/import-bundle`

Import bundle

Restores a prompt bundle. &#x60;replace&#x60; wipes the current prompts and folders before writing the bundle, &#x60;merge&#x60; writes the bundle on top of what is already there; both validate the folder references inside the bundle before any write, so a corrupt bundle is rejected whole.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPromptsImportBundle\_request** | body | [**aiPromptsImportBundle_request**](../newai.md#model-aipromptsimportbundle-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiImportResult**](../newai.md#model-aiimportresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiImportResult**](../newai.md#model-aiimportresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
