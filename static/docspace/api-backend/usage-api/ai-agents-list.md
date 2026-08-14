# aiAgentsList

Referenced types are defined in the [full reference](../newai.md).

> AiFolderContentIntegerWrapper aiAgentsList()

`GET /api/2.0/ai/agents`

List agents

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderContentIntegerWrapper**](../newai.md#model-aifoldercontentintegerwrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderContentIntegerWrapper**](../newai.md#model-aifoldercontentintegerwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
