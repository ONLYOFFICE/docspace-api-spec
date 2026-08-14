# aiAssignmentsAssign

Referenced types are defined in the [full reference](../newai.md).

> AiAssignmentMutationResult aiAssignmentsAssign(aiAssignmentsAssign\_request)

`PUT /api/2.0/ai/assignments/assign`

Assign

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAssignmentsAssign\_request** | body | [**aiAssignmentsAssign_request**](../newai.md#model-aiassignmentsassign-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAssignmentMutationResult**](../newai.md#model-aiassignmentmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiAssignmentMutationResult**](../newai.md#model-aiassignmentmutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
