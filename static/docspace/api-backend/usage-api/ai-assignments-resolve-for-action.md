# aiAssignmentsResolveForAction

Referenced types are defined in the [full reference](../newai.md).

> AiResolvedAssignment aiAssignmentsResolveForAction(actionType, entityId)

`GET /api/2.0/ai/assignments/resolve-for-action`

Resolve for action

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **actionType** | query | **String** |  | [required] |
| **entityId** | query | **String** |  | [required] |

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
