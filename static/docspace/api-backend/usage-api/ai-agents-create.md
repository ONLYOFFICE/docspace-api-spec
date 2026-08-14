# aiAgentsCreate

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerWrapper aiAgentsCreate(aiAgentsCreate\_request)

`POST /api/2.0/ai/agents`

Create an agent

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsCreate\_request** | body | [**aiAgentsCreate_request**](../newai.md#model-aiagentscreate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerWrapper**](../newai.md#model-aifolderintegerwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderIntegerWrapper**](../newai.md#model-aifolderintegerwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
