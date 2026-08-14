# aiExportTextToDocx

Referenced types are defined in the [full reference](../newai.md).

> aiExportTextToDocx_200_response aiExportTextToDocx(aiExportTextToDocx\_request)

`POST /api/2.0/ai/text-to-docx`

Start markdown → docx export

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiExportTextToDocx\_request** | body | [**aiExportTextToDocx_request**](../newai.md#model-aiexporttexttodocx-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiExportTextToDocx_200_response**](../newai.md#model-aiexporttexttodocx-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiExportTextToDocx_200_response**](../newai.md#model-aiexporttexttodocx-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIPreferencesApi
