# aiAgentsNews

Referenced types are defined in the [full reference](../newai.md).

> AiNewItemsAgentNewItemsArrayWrapper aiAgentsNews()

`GET /api/2.0/ai/agents/news`

List agent news items

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiNewItemsAgentNewItemsArrayWrapper**](../newai.md#model-ainewitemsagentnewitemsarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiNewItemsAgentNewItemsArrayWrapper**](../newai.md#model-ainewitemsagentnewitemsarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
