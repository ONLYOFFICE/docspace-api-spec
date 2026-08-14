# aiAgentsDelete

Referenced types are defined in the [full reference](../newai.md).

> AiFileOperationWrapper aiAgentsDelete(id, aiAgentsDelete\_request)

`DELETE /api/2.0/ai/agents/{id}`

Delete an agent

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** |  | [required] |
| **aiAgentsDelete\_request** | body | [**aiAgentsDelete_request**](../newai.md#model-aiagentsdelete-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFileOperationWrapper**](../newai.md#model-aifileoperationwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFileOperationWrapper**](../newai.md#model-aifileoperationwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
