# aiPreferencesIsDeepModeSet

Referenced types are defined in the [full reference](../aichat.md).

> Boolean aiPreferencesIsDeepModeSet(entityId)

`GET /api/2.0/ai/preferences/is-deep-mode-set`

Is deep mode set

Tells whether a scope has an explicitly persisted extended-thinking setting of its own, as opposed to inheriting the configured default. &#x60;entityId&#x60; picks a room and omitting it asks about the portal-wide preference. A true answer means a value was stored, whether that value is on or off - read the value itself with &#x60;GET api/2.0/ai/preferences/get-deep-mode&#x60;. This is the check a settings screen uses to show an explicit override rather than an inherited state.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the scope has a preference of its own, whichever way that preference is set. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

**Boolean**

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
