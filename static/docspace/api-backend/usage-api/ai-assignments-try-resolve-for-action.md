# aiAssignmentsTryResolveForAction

Referenced types are defined in the [full reference](../newai.md).

> AiResolvedAssignment aiAssignmentsTryResolveForAction(actionType, entityId)

`GET /api/2.0/ai/assignments/try-resolve-for-action`

Try resolve for action

Resolves the profile bound to an AI action exactly like &#x60;resolve-for-action&#x60;, but answers with an empty result instead of failing when nothing is configured.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** | The AI action the request applies to - one of Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision. | [required] |
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiResolvedAssignment**](../newai.md#model-airesolvedassignment) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiResolvedAssignment**](../newai.md#model-airesolvedassignment)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
