# aiToolsListSystemTools

Referenced types are defined in the [full reference](../newai.md).

> aiToolsListSystemTools_200_response aiToolsListSystemTools(entityId)

`GET /api/2.0/ai/tools/list-system-tools`

List system tools

Lists every tool the scope can offer the model, as a map of server type to tool group. The answer merges two sources - the host-configured system servers and the live tools of the scope&#39;s registered custom MCP servers - and names the system ones separately in &#x60;system&#x60;, so a client can tell the two apart. &#x60;errors&#x60; carries the reason a registered server delivered no tools, which is the text to show on a permission card, because the browser cannot reach a server-executed MCP server to find out for itself. The connections are opened server-side, so one request is enough and the client never speaks MCP itself; the portal&#39;s own built-in server is left out because it is always enabled.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The scope&#39;s tools grouped by server type, the system group keys named in &#x60;system&#x60;, and the reason a registered server delivered none in &#x60;errors&#x60;. | [**aiToolsListSystemTools_200_response**](../newai.md#model-aitoolslistsystemtools-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiToolsListSystemTools_200_response**](../newai.md#model-aitoolslistsystemtools-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
