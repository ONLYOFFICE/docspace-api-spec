# aiToolsGetCustomServer

Referenced types are defined in the [full reference](../newai.md).

> Object aiToolsGetCustomServer(name, entityId)

`GET /api/2.0/ai/tools/get-custom-server`

Get custom server

Returns the stored configuration of one registered custom MCP server. The name is required and is read from the query; &#x60;entityId&#x60; picks the scope, and omitting it reads the portal-wide registry. A name that is not registered answers a null body with status 200 rather than 404. The configuration of a system server is returned empty on purpose: those run server-side only, so neither their endpoint nor their credentials are handed to a browser.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **name** | query | **String** | The custom MCP server name. | [required] [example: acme-mcp] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The stored configuration, empty for a system server and null when the name is not registered. | **Object** | - |
| **400** | The server name is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**Object**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
