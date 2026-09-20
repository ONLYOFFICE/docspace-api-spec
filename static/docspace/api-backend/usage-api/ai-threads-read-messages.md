# aiThreadsReadMessages

Referenced types are defined in the [full reference](../aichat.md).

> List aiThreadsReadMessages(threadId, count, cursor, direction)

`GET /api/2.0/ai/threads/read-messages`

Read messages

Reads the messages of one thread, oldest first, with the same string-encoded JSON cursor as the thread list. &#x60;direction&#x60; turns the read around, and only the exact value &#x60;desc&#x60; does so - anything else, including a misspelling, reads forward. Omitting &#x60;threadId&#x60; is not an error: the call answers 200 with an empty list, so an empty result does not distinguish a thread with no messages from a request that forgot the ID. A malformed cursor is ignored and the read starts from the beginning.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **threadId** | query | **String** | The chat thread identifier. | [required] [example: 11111111-1111-1111-1111-111111111111] |
| **count** | query | **Integer** | The maximum number of items to return in one page. | [optional] [example: 20] |
| **cursor** | query | **String** | The keyset pagination cursor: the JSON-encoded sort key of the last item already received. Omit for the first page. | [optional] [example: {"id":"11111111-1111-1111-1111-111111111111","lastEditDate":1767225600000}] |
| **direction** | query | **String** | The order the message page is read in. Only desc turns the read around and pages back from the newest message; omit for the forward read. | [optional] [example: desc] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The thread&#39;s messages, oldest first unless &#x60;direction&#x60; reversed them. An empty list also means the request carried no thread ID. | [**List**](../aichat.md#model-aithreadmessagelike) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**List**](../aichat.md#model-aithreadmessagelike)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
