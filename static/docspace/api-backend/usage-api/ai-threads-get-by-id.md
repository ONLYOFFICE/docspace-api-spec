# aiThreadsGetById

Referenced types are defined in the [full reference](../newai.md).

> AiThread aiThreadsGetById(threadId)

`GET /api/2.0/ai/threads/get-by-id`

Get by id

Returns one chat thread, or an empty result when the identifier is unknown.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **threadId** | query | **String** | The chat thread identifier. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThread**](../newai.md#model-aithread) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiThread**](../newai.md#model-aithread)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
