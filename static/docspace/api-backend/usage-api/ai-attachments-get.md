# aiAttachmentsGet

Referenced types are defined in the [full reference](../newai.md).

> AiAttachment aiAttachmentsGet(body)

`POST /api/2.0/ai/attachments/get`

Get

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAttachment**](../newai.md#model-aiattachment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiAttachment**](../newai.md#model-aiattachment)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
