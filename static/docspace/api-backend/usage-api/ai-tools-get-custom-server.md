# aiToolsGetCustomServer

Referenced types are defined in the [full reference](../newai.md).

> Object aiToolsGetCustomServer(name, entityId)

`GET /api/2.0/ai/tools/get-custom-server`

Get custom server

Returns the configuration of one custom MCP server, or an empty result when it is not registered.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **name** | query | **String** | The custom MCP server name. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Object** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**Object**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
