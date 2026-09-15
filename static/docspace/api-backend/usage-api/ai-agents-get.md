# aiAgentsGet

Referenced types are defined in the [full reference](../newai.md).

> aiAgentsGet_200_response aiAgentsGet(id)

`GET /api/2.0/ai/agents/{id}`

Get an agent

Returns one AI agent room, enriched with the &#x60;profileId&#x60; currently bound to it so an edit form can prefill its model selector. The ID is the room&#39;s integer identifier, and a non-integer value is refused rather than passed on to fail opaquely upstream. The binding lives in an assignment rather than on the room, so it is looked up separately: a missing or unreadable assignment simply leaves &#x60;profileId&#x60; out of the answer instead of failing the call. The standing instruction comes back on the room as &#x60;chatSettings.prompt&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] [example: 1234] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The agent room, with &#x60;profileId&#x60; added when a model is bound to it. | [**aiAgentsGet_200_response**](../newai.md#model-aiagentsget-200-response) | - |
| **400** | The agent ID is not a positive integer. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiAgentsGet_200_response**](../newai.md#model-aiagentsget-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
