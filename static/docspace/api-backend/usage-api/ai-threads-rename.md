# aiThreadsRename

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiThreadsRename(aiThreadsRename\_request)

`PUT /api/2.0/ai/threads/rename`

Rename

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsRename\_request** | body | [**aiThreadsRename_request**](../newai.md#model-aithreadsrename-request-body) |  | [required] |

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
