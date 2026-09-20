# aiAssignmentsAssign

Referenced types are defined in the [full reference](../aichat.md).

> AiAssignmentMutationResult aiAssignmentsAssign(aiAssignmentsAssign\_request)

`PUT /api/2.0/ai/assignments/assign`

Bind a profile to an action

Binds a profile to one AI action portal-wide, creating the assignment or replacing it in place, and returns the result. Both &#x60;actionType&#x60; and &#x60;profileId&#x60; are required. The profile&#39;s declared capabilities are checked against the action, so a model that cannot generate images cannot be bound to &#x60;ImageGeneration&#x60; - the &#x60;Default&#x60; slot is exempt, because it stands in for every action. There is no room-scoped form of this write: a room&#39;s own binding is created by the agent that owns it, while reads accept an &#x60;entityId&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAssignmentsAssign\_request** | body | [**aiAssignmentsAssign_request**](../aichat.md#model-aiassignmentsassign-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the binding was stored. A failure is reported in &#x60;error&#x60; rather than as a status. | [**AiAssignmentMutationResult**](../aichat.md#model-aiassignmentmutationresult) | - |
| **400** | &#x60;actionType&#x60; or &#x60;profileId&#x60; is missing. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiAssignmentMutationResult**](../aichat.md#model-aiassignmentmutationresult)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
