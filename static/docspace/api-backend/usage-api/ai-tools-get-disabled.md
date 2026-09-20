# aiToolsGetDisabled

Referenced types are defined in the [full reference](../aichat.md).

> Map aiToolsGetDisabled(entityId)

`GET /api/2.0/ai/tools/get-disabled`

Get disabled

Returns the tools switched off in the scope, as a map of server type to tool names. &#x60;entityId&#x60; picks the scope and omitting it reads the portal-wide setting. An absent server type means nothing is switched off for it, so an empty answer means every tool is on offer. Use &#x60;GET api/2.0/ai/tools/is-tool-disabled&#x60; to ask about one tool instead of reading the whole map.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The switched-off tools as a map of server type to tool names. An absent type means nothing is switched off for it. | **Map** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

**Map**

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
