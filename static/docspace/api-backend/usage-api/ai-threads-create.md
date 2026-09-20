# aiThreadsCreate

Referenced types are defined in the [full reference](../aichat.md).

> AiThread aiThreadsCreate(aiThreadsCreate\_request)

`POST /api/2.0/ai/threads/create`

Create a chat thread

Creates a chat thread with a title supplied by the caller and returns it. A scoped thread requires that &#x60;entityId&#x60; names a room the caller can open, and a model has to resolve for the scope - an explicit &#x60;profileId&#x60;, or the room&#39;s &#x60;Chat&#x60; assignment - otherwise there is nothing to run the thread against and the call answers 404. In an agent room the agent&#39;s own assignment overrides any &#x60;profileId&#x60; sent with the request, so a thread there always starts on the agent&#39;s model. Use &#x60;POST api/2.0/ai/threads/open-or-create&#x60; instead when the title should be generated from the first user message.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsCreate\_request** | body | [**aiThreadsCreate_request**](../aichat.md#model-aithreadscreate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The created thread. | [**AiThread**](../aichat.md#model-aithread) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The &#x60;entityId&#x60; names a room the caller cannot open, or no live AI profile is bound to it, so there is no model to run the thread against. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiThread**](../aichat.md#model-aithread)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
