# aiThreadsRegenerateTitle

Referenced types are defined in the [full reference](../newai.md).

> aiThreadsRegenerateTitle_200_response aiThreadsRegenerateTitle(aiThreadsRegenerateTitle\_request)

`POST /api/2.0/ai/threads/regenerate-title`

Regenerate title

Asks the model to produce a title from the thread&#39;s first user message, stores it, and returns the new title. Both &#x60;threadId&#x60; and a resolved &#x60;profile&#x60; object are required; a thread with no user message yet has nothing to title and fails. This costs a model call, unlike &#x60;POST api/2.0/ai/threads/rename&#x60;, which just stores the string it is given. An &#x60;entityMeta&#x60; sent with the request is only read for its &#x60;entityId&#x60; hint - the source itself is resolved server-side under the caller&#39;s credentials, so a client cannot attribute the call to somebody else&#39;s room.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsRegenerateTitle\_request** | body | [**aiThreadsRegenerateTitle_request**](../newai.md#model-aithreadsregeneratetitle-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The newly generated title, already stored on the thread. | [**aiThreadsRegenerateTitle_200_response**](../newai.md#model-aithreadsregeneratetitle-200-response) | - |
| **400** | &#x60;threadId&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiThreadsRegenerateTitle_200_response**](../newai.md#model-aithreadsregeneratetitle-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
