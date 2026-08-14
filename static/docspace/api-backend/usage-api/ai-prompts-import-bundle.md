# aiPromptsImportBundle

Referenced types are defined in the [full reference](../newai.md).

> AiImportResult aiPromptsImportBundle(aiPromptsImportBundle\_request)

`POST /api/2.0/ai/prompts/import-bundle`

Import bundle

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
