# aiToolsIsAllowAlways

Referenced types are defined in the [full reference](../newai.md).

> Boolean aiToolsIsAllowAlways(serverType, toolName, entityId)

`GET /api/2.0/ai/tools/is-allow-always`

Is allow always

Tells whether one named tool runs without an approval pause in the scope. Both &#x60;serverType&#x60; and &#x60;toolName&#x60; are required and are read from the query; &#x60;entityId&#x60; picks the scope. The answer is a bare boolean. A false answer means a call to that tool pauses the round, and the caller resumes it with the approve or deny operation.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **serverType** | query | **String** | The MCP server type the tool belongs to. | [required] [example: docspace] |
| **toolName** | query | **String** | The tool name. | [required] [example: docspace_get_folder] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether that one tool runs without an approval pause. | **Boolean** | - |
| **400** | &#x60;serverType&#x60; or &#x60;toolName&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
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
