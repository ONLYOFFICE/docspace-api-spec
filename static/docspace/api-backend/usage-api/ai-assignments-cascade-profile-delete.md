# aiAssignmentsCascadeProfileDelete

Referenced types are defined in the [full reference](../aichat.md).

> AiSuccessResponse aiAssignmentsCascadeProfileDelete(aiAssignmentsCascadeProfileDelete\_request)

`DELETE /api/2.0/ai/assignments/cascade-profile-delete`

Cascade profile delete

Detaches a profile from every assignment that points at it, which is the cleanup step before the profile itself is removed. The &#x60;Default&#x60; slot is promoted to the first remaining profile, or dropped when none is left, and every other slot holding the profile is cleared. &#x60;profileId&#x60; is required and may be sent in the body or as a query parameter. &#x60;DELETE api/2.0/ai/profiles/delete&#x60; already does this, so call it directly only when the profile is being removed by some other means.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAssignmentsCascadeProfileDelete\_request** | body | [**aiAssignmentsCascadeProfileDelete_request**](../aichat.md#model-aiassignmentscascadeprofiledelete-request-body) | The profile to detach from every assignment. May be sent as the &#x60;profileId&#x60; query parameter instead of in the body. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms no assignment points at the profile any more. | [**AiSuccessResponse**](../aichat.md#model-aisuccessresponse) | - |
| **400** | &#x60;profileId&#x60; is missing. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../aichat.md#model-aisuccessresponse)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
