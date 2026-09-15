# aiAssignmentsUnassign

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiAssignmentsUnassign(body)

`DELETE /api/2.0/ai/assignments/unassign`

Clear an action&#39;s profile

Clears the portal-wide binding of one AI action, after which the action falls back to the &#x60;Default&#x60; slot. &#x60;actionType&#x60; is required and may be sent in the body or as a query parameter. An action whose slot is already empty is not reported as an error - the call answers success either way, so it is safe to repeat. Clearing &#x60;Default&#x60; itself leaves the actions that relied on it unresolvable.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the action now has no profile of its own. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **400** | &#x60;actionType&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIAttachmentsApi
