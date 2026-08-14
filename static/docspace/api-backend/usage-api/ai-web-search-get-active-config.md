# aiWebSearchGetActiveConfig

Referenced types are defined in the [full reference](../newai.md).

> AiWebSearchConfig aiWebSearchGetActiveConfig(entityId)

`GET /api/2.0/ai/web-search/get-active-config`

Get active config

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **entityId** | query | **String** |  | [required] |

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
