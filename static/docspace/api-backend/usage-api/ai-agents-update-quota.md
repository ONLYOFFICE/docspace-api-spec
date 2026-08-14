# aiAgentsUpdateQuota

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerArrayWrapper aiAgentsUpdateQuota(aiAgentsUpdateQuota\_request)

`PUT /api/2.0/ai/agents/agentquota`

Update agents&#39; quota

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsUpdateQuota\_request** | body | [**aiAgentsUpdateQuota_request**](../newai.md#model-aiagentsupdatequota-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerArrayWrapper**](../newai.md#model-aifolderintegerarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderIntegerArrayWrapper**](../newai.md#model-aifolderintegerarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIAssignmentsApi
