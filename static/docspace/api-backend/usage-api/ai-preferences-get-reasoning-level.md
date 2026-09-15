# aiPreferencesGetReasoningLevel

Referenced types are defined in the [full reference](../newai.md).

> AiAiReasoningLevel aiPreferencesGetReasoningLevel(entityId)

`GET /api/2.0/ai/preferences/get-reasoning-level`

Get reasoning level

Returns the effective extended-thinking depth of the scope: &#x60;off&#x60; while deep mode is off, otherwise the persisted depth (&#x60;low&#x60;, &#x60;medium&#x60;, &#x60;high&#x60;, &#x60;max&#x60;), falling back to the default depth (&#x60;medium&#x60;) when none has been stored. &#x60;entityId&#x60; picks a room and omitting it reads the portal-wide preference. Providers clamp the depth to what the model accepts.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAiReasoningLevel**](../newai.md#model-aiaireasoninglevel) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiAiReasoningLevel**](../newai.md#model-aiaireasoninglevel)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
