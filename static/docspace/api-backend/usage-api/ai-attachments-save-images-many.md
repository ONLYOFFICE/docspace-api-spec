# aiAttachmentsSaveImagesMany

Referenced types are defined in the [full reference](../newai.md).

> List aiAttachmentsSaveImagesMany(aiAttachmentsSaveImagesMany\_request)

`POST /api/2.0/ai/attachments/save-images-many`

Save images many

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsSaveImagesMany\_request** | body | [**aiAttachmentsSaveImagesMany_request**](../newai.md#model-aiattachmentssaveimagesmany-request-body) |  | [required] |

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

## AIExportApi
