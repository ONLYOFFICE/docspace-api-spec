# aiWebSearchGetActiveConfig

Referenced types are defined in the [full reference](../newai.md).

> AiWebSearchConfig aiWebSearchGetActiveConfig(entityId)

`GET /api/2.0/ai/web-search/get-active-config`

Get active config

Returns the web-search configuration active in the scope, or an empty result when web search is not configured.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** | The DocSpace entity the request is scoped to - the room, folder or agent workspace the chat is invoked from. Omit for the portal-wide scope. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiWebSearchConfig**](../newai.md#model-aiwebsearchconfig) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiWebSearchConfig**](../newai.md#model-aiwebsearchconfig)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
