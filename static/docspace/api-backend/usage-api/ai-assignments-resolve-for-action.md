# aiAssignmentsResolveForAction

Referenced types are defined in the [full reference](../aichat.md).

> AiResolvedAssignment aiAssignmentsResolveForAction(actionType, entityId)

`GET /api/2.0/ai/assignments/resolve-for-action`

Resolve for action

Returns the profile that will serve one AI action, falling back to the &#x60;Default&#x60; slot when the action has no profile of its own. &#x60;actionType&#x60; is required and has to be one of the known actions - an unknown or misspelled value is rejected rather than resolved to the default. &#x60;entityId&#x60; narrows the lookup to a room, and a room with no assignment of its own degrades to the portal-wide one. This fails when neither slot is set or the bound profile is gone, so use &#x60;GET api/2.0/ai/assignments/try-resolve-for-action&#x60; when an unconfigured portal should answer empty instead.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** | The AI action the request applies to - one of Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision. | [required] [example: Chat] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The profile that will serve the action. | [**AiResolvedAssignment**](../aichat.md#model-airesolvedassignment) | - |
| **400** | &#x60;actionType&#x60; is missing. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiResolvedAssignment**](../aichat.md#model-airesolvedassignment)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
