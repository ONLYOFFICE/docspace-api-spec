# aiAssignmentsGetAssignment

Referenced types are defined in the [full reference](../newai.md).

> String aiAssignmentsGetAssignment(actionType)

`GET /api/2.0/ai/assignments/get-assignment`

Get assignment

Returns the profile bound to one AI action, without applying the &#x60;Default&#x60; fallback - an empty answer means this action has no profile of its own, not that nothing is configured. &#x60;actionType&#x60; is required and is read from the query. Use &#x60;GET api/2.0/ai/assignments/resolve-for-action&#x60; to learn which profile would actually serve the action. This reads the portal-wide binding and accepts no &#x60;entityId&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** | The AI action the request applies to - one of Default, Chat, Code, Summarization, Translation, TextAnalyze, ImageGeneration, OCR, Vision. | [required] [example: Chat] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The profile bound to the action, or an empty result when it has none of its own. | **String** | - |
| **400** | &#x60;actionType&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**String**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
