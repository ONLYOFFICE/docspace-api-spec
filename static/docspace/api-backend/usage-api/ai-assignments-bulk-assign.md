# aiAssignmentsBulkAssign

Referenced types are defined in the [full reference](../newai.md).

> AiBulkAssignmentResult aiAssignmentsBulkAssign(request\_body)

`PUT /api/2.0/ai/assignments/bulk-assign`

Bulk assign

Applies many action-to-profile bindings in one write, which is how a settings screen saves the whole set. The body is a plain map of action type to profile ID, and every entry is validated before anything is written: one unknown action or one non-string profile ID rejects the request whole, so the set is never left half-applied. Each entry behaves as the single assign operation does, capability checks included. The answer carries the resulting assignment set.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** | A map of action type to profile ID. Every key has to be a known action type and every value a profile ID; one bad entry rejects the whole map. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the set was stored, with &#x60;errors&#x60; listing the entries that were refused. | [**AiBulkAssignmentResult**](../newai.md#model-aibulkassignmentresult) | - |
| **400** | The body is not a map of action type to profile ID, or one of its keys is not a known action type. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiBulkAssignmentResult**](../newai.md#model-aibulkassignmentresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
