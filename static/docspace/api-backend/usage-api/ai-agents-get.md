# aiAgentsGet

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerWrapper aiAgentsGet(id)

`GET /api/2.0/ai/agents/{id}`

Get an agent

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** |  | [required] |

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
