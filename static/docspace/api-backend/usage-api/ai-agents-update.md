# aiAgentsUpdate

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerWrapper aiAgentsUpdate(id, aiAgentsUpdate\_request)

`PUT /api/2.0/ai/agents/{id}`

Update an agent

Changes an AI agent room - its title, tags or standing instruction - and optionally rebinds its model. The ID has to be the room&#39;s integer identifier. &#x60;profileId&#x60; is not part of the room contract: it is taken out of the forwarded body and applied afterwards as the agent&#39;s assignment, and it has to be a UUID naming an existing chat-capable profile. An instruction sent as &#x60;chatSettings.prompt&#x60; has its markup stripped, as on create; note that when &#x60;chatSettings&#x60; is present the upstream service still requires the rest of that object to be valid, so send it whole.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] [example: 1234] |
| **aiAgentsUpdate\_request** | body | [**aiAgentsUpdate_request**](../newai.md#model-aiagentsupdate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The updated agent room. | [**AiFolderIntegerWrapper**](../newai.md#model-aifolderintegerwrapper) | - |
| **400** | The agent ID is not a positive integer, or &#x60;profileId&#x60; is not a UUID, names no existing profile, or names one that does not support chat. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderIntegerWrapper**](../newai.md#model-aifolderintegerwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
