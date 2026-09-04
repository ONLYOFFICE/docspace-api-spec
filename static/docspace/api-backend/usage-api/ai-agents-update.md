# aiAgentsUpdate

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerWrapper aiAgentsUpdate(id, aiAgentsUpdate\_request)

`PUT /api/2.0/ai/agents/{id}`

Update an agent

Updates an AI agent room - title, tags, instruction. &#x60;profileId&#x60; is not part of the room contract: it is stripped from the forwarded body and re-bound as the agent&#39;s assignment afterwards.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] |
| **aiAgentsUpdate\_request** | body | [**aiAgentsUpdate_request**](../newai.md#model-aiagentsupdate-request-body) |  | [required] |

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
