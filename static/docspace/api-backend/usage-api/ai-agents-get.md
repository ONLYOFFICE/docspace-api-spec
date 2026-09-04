# aiAgentsGet

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerWrapper aiAgentsGet(id)

`GET /api/2.0/ai/agents/{id}`

Get an agent

Returns one AI agent room, enriched with the &#x60;profileId&#x60; bound to it so an edit form can prefill the profile selector. A missing assignment simply leaves &#x60;profileId&#x60; out.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The agent identifier. | [required] |

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

- **Content-Type**: Not defined
- **Accept**: application/json
