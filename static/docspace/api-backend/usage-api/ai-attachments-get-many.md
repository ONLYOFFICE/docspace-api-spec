# aiAttachmentsGetMany

Referenced types are defined in the [full reference](../newai.md).

> List aiAttachmentsGetMany(request\_body)

`POST /api/2.0/ai/attachments/get-many`

Get many

Returns several attachments in one call, aligned by position with the &#x60;ids&#x60; that were sent, so the answer can be zipped straight onto the request. An ID that no longer exists leaves its slot empty rather than shortening the list, which is how a caller tells which of them are gone. &#x60;ids&#x60; has to be present and non-empty - an empty batch is rejected rather than answered with an empty list. Nothing is changed by the call.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **List** | The IDs of the attachments to read, as a bare JSON array of strings. The answer is aligned with this array by position. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The attachments, aligned by position with the IDs that were sent. A missing one leaves its slot empty. | [**List**](../newai.md#model-aiattachment) | - |
| **400** | The list of attachment IDs is malformed. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
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
