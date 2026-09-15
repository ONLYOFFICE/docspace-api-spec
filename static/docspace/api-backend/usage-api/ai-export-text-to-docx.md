# aiExportTextToDocx

Referenced types are defined in the [full reference](../newai.md).

> aiExportTextToDocx_202_response aiExportTextToDocx(aiExportTextToDocx\_request)

`POST /api/2.0/ai/text-to-docx`

Start markdown → docx export

Queues a markdown-to-docx export and answers 202 as soon as the job is accepted, without waiting for it. &#x60;title&#x60;, &#x60;content&#x60; and &#x60;folderId&#x60; are all required, and a &#x60;content&#x60; of only whitespace counts as missing even though it is not empty. The conversion runs in the AI worker, which saves the .docx into the target folder - an agent room resolves to its own result-storage subfolder - so there is nothing to poll here: completion arrives as the ordinary folder-modified socket event. This route accepts a body of up to 15 MB rather than the 100 KB the rest of the API allows, because a whole thread transcript is sent in one request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiExportTextToDocx\_request** | body | [**aiExportTextToDocx_request**](../newai.md#model-aiexporttexttodocx-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **202** | Confirms the export was queued. The .docx arrives in the target folder later, announced by a folder-modified socket event. | [**aiExportTextToDocx_202_response**](../newai.md#model-aiexporttexttodocx-202-response) | - |
| **400** | &#x60;title&#x60;, &#x60;content&#x60; or &#x60;folderId&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The transcript is larger than 15 MB, this route&#39;s own parser limit. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiExportTextToDocx_202_response**](../newai.md#model-aiexporttexttodocx-202-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIOpenAIPassthroughApi
