# aiAgentsUpdateQuota

Referenced types are defined in the [full reference](../aichat.md).

> AiFolderArrayWrapper aiAgentsUpdateQuota(aiAgentsUpdateQuota\_request)

`PUT /api/2.0/ai/agents/agentquota`

Update agents&#39; quota

Sets the storage quota of the listed AI agent rooms in one call, forwarding &#x60;roomIds&#x60; and &#x60;quota&#x60; to the DocSpace AI service unchanged. The answer is that service&#39;s payload, one updated room per entry. A quota applies to the room&#39;s stored files, not to the model usage of its chats. Use &#x60;PUT api/2.0/ai/agents/resetquota&#x60; to return rooms to the portal default instead of naming a number.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsUpdateQuota\_request** | body | [**aiAgentsUpdateQuota_request**](../aichat.md#model-aiagentsupdatequota-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The updated agent rooms, one entry each. | [**AiFolderArrayWrapper**](../aichat.md#model-aifolderarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiFolderArrayWrapper**](../aichat.md#model-aifolderarraywrapper)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIAssignmentsApi
