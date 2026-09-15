# aiAttachmentsSaveFilesMany

Referenced types are defined in the [full reference](../newai.md).

> List aiAttachmentsSaveFilesMany(aiAttachmentsSaveFilesMany\_request)

`POST /api/2.0/ai/attachments/save-files-many`

Save files many

Stores several file attachments as drafts in one round trip and returns them in the order they were sent. Each entry is validated exactly as the single-file operation validates its &#x60;input&#x60;, and the first bad one rejects the whole batch with its index named in the message - nothing is stored. &#x60;inputs&#x60; has to be present and an array: an absent or null value is a malformed request rather than an empty batch, and only an explicit empty array means no files. Follow up with &#x60;POST api/2.0/ai/attachments/link-to-message&#x60; to bind the drafts to a message.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsSaveFilesMany\_request** | body | [**aiAttachmentsSaveFilesMany_request**](../newai.md#model-aiattachmentssavefilesmany-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The stored drafts, in the order they were sent. | [**List**](../newai.md#model-aiattachment) | - |
| **400** | &#x60;inputs&#x60; is not an array, or one of its entries is malformed. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**List**](../newai.md#model-aiattachment)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIEditorToolsApi
