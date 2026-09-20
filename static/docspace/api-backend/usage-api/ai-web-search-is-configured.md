# aiWebSearchIsConfigured

Referenced types are defined in the [full reference](../aichat.md).

> Boolean aiWebSearchIsConfigured(entityId)

`GET /api/2.0/ai/web-search/is-configured`

Is configured

Tells whether web search is available in a scope, as a bare boolean, which is the cheap check for hiding or showing the feature. &#x60;entityId&#x60; picks a room and has to name one the caller can open. It reports the same state as &#x60;GET api/2.0/ai/web-search/get-active-config&#x60; without transferring the configuration itself. A true answer means a provider is stored, not that the provider is currently reachable - probe that with &#x60;POST api/2.0/ai/web-search/test-connection&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether a web-search provider is stored for the scope. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The referenced object does not exist, or the caller cannot access it - the two are deliberately indistinguishable, so a room the caller may not open answers 404 rather than 403. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

**Boolean**

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
