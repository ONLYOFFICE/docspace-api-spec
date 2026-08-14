# aiAttachmentsSaveFilesMany

Referenced types are defined in the [full reference](../newai.md).

> List aiAttachmentsSaveFilesMany(aiAttachmentsSaveFilesMany\_request)

`POST /api/2.0/ai/attachments/save-files-many`

Save files many

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsSaveFilesMany\_request** | body | [**aiAttachmentsSaveFilesMany_request**](../newai.md#model-aiattachmentssavefilesmany-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](../newai.md#model-aiattachment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**List**](../newai.md#model-aiattachment)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
