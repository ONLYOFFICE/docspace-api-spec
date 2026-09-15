# aiPreferencesGetDeepMode

Referenced types are defined in the [full reference](../newai.md).

> Boolean aiPreferencesGetDeepMode(entityId)

`GET /api/2.0/ai/preferences/get-deep-mode`

Get deep mode

Returns the deep-mode toggle of a scope, as a bare boolean: whether the stored extended-thinking depth is above &#x60;off&#x60;. &#x60;entityId&#x60; picks a room and omitting it reads the portal-wide preference. A scope that has never had a value stored falls back to the configured default, so the answer never distinguishes off from unset - ask &#x60;GET api/2.0/ai/preferences/is-deep-mode-set&#x60; for that. This is a read-only operation.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether deep mode is on, falling back to the configured default when the scope has no value of its own. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**Boolean**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
