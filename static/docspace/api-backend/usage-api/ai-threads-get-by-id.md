# aiThreadsGetById

Referenced types are defined in the [full reference](../newai.md).

> AiThread aiThreadsGetById(threadId)

`GET /api/2.0/ai/threads/get-by-id`

Get a chat thread

Returns one thread by its ID, without its messages - read those with &#x60;GET api/2.0/ai/threads/read-messages&#x60;. &#x60;threadId&#x60; is required and an unknown one answers 404, so the result is never an empty body. The answer carries the thread&#39;s title, its model binding and its last-edit date. This is a read-only operation and does not bump that date.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **threadId** | query | **String** | The chat thread identifier. | [required] [example: 11111111-1111-1111-1111-111111111111] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The thread, without its messages. | [**AiThread**](../newai.md#model-aithread) | - |
| **400** | &#x60;threadId&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **404** | No thread has this ID. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiThread**](../newai.md#model-aithread)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
