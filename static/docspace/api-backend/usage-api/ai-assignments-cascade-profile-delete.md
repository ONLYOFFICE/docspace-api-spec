# aiAssignmentsCascadeProfileDelete

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiAssignmentsCascadeProfileDelete(body)

`DELETE /api/2.0/ai/assignments/cascade-profile-delete`

Cascade profile delete

Cleans up the assignments pointing at a profile that is about to be deleted: the &#x60;Default&#x60; slot is promoted to the first remaining profile (or dropped when none is left), and every other slot holding that profile is unbound.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
