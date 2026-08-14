# aiThreadsReadMessages

Referenced types are defined in the [full reference](../newai.md).

> List aiThreadsReadMessages(threadId, count, cursor)

`GET /api/2.0/ai/threads/read-messages`

Read messages

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **threadId** | query | **String** |  | [required] |
| **count** | query | **String** |  | [required] |
| **cursor** | query | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](../newai.md#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**List**](../newai.md#model-aithreadmessagelike)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
