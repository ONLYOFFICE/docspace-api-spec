# aiThreadsOpenOrCreate

Referenced types are defined in the [full reference](../newai.md).

> AiOpenOrCreateResult aiThreadsOpenOrCreate(aiThreadsOpenOrCreate\_request)

`POST /api/2.0/ai/threads/open-or-create`

Open or create

Opens a chat thread and returns it with its history, or creates one whose title is generated from the first message supplied in the request. That first message is not persisted: follow up with &#x60;POST api/2.0/ai/threads/append-user-message&#x60; to store it, or start the round directly with &#x60;POST api/2.0/ai/ai/send-with-stream&#x60;. Unlike &#x60;create&#x60; this takes a whole resolved &#x60;profile&#x60; object rather than an ID, and a request without one answers 404 because no model could be bound. A supplied &#x60;entityId&#x60; has to be a room the caller can open; anything that is not an agent room folds to the global scope instead of being rejected.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsOpenOrCreate\_request** | body | [**aiThreadsOpenOrCreate_request**](../newai.md#model-aithreadsopenorcreate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The thread that was opened or created, with its prior messages. A created one carries the generated title. | [**AiOpenOrCreateResult**](../newai.md#model-aiopenorcreateresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **404** | The &#x60;entityId&#x60; names a room the caller cannot open, or no live AI profile is bound to it. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiOpenOrCreateResult**](../newai.md#model-aiopenorcreateresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
