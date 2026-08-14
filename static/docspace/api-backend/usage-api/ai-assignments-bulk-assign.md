# aiAssignmentsBulkAssign

Referenced types are defined in the [full reference](../newai.md).

> AiBulkAssignmentResult aiAssignmentsBulkAssign(request\_body)

`PUT /api/2.0/ai/assignments/bulk-assign`

Bulk assign

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiBulkAssignmentResult**](../newai.md#model-aibulkassignmentresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiBulkAssignmentResult**](../newai.md#model-aibulkassignmentresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
