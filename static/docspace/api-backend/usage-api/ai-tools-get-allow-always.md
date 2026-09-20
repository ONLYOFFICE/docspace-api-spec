# aiToolsGetAllowAlways

Referenced types are defined in the [full reference](../aichat.md).

> List aiToolsGetAllowAlways(entityId)

`GET /api/2.0/ai/tools/get-allow-always`

Get allow always

Returns the always-allow list of the scope - the tools whose calls run without pausing the round for approval. &#x60;entityId&#x60; picks the scope and omitting it reads the portal-wide setting. An empty answer means every tool call has to be approved through &#x60;POST api/2.0/ai/ai/approve-tool-call&#x60;. Use &#x60;GET api/2.0/ai/tools/is-allow-always&#x60; to ask about a single tool.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The tools that run without an approval pause. An empty list means every call needs approval. | **List** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

**List**

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
