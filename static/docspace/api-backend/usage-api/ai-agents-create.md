# aiAgentsCreate

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerWrapper aiAgentsCreate(aiAgentsCreate\_request)

`POST /api/2.0/ai/agents`

Create an agent

Creates an AI agent room and binds a model to it, in that order. &#x60;profileId&#x60; is required, has to be a UUID, has to name an existing profile, and that profile has to support chat - an image-only model is refused here rather than failing on every later request. &#x60;prompt&#x60; is required and is stored on the room as its standing instruction with any markup stripped, so it cannot round-trip HTML into another user&#39;s reply. The two steps are not atomic: when the room is created but the model binding fails, the call reports an error and the room is left behind, so re-bind it with &#x60;PUT api/2.0/ai/agents/{id}&#x60; rather than creating a second one.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsCreate\_request** | body | [**aiAgentsCreate_request**](../newai.md#model-aiagentscreate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The created agent room, with the model already bound to it. | [**AiFolderIntegerWrapper**](../newai.md#model-aifolderintegerwrapper) | - |
| **400** | &#x60;profileId&#x60; is missing, is not a UUID, names no existing profile, or names one that does not support chat; or &#x60;prompt&#x60; is missing. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
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
