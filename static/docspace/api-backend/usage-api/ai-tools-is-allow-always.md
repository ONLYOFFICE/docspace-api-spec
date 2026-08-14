# aiToolsIsAllowAlways

Referenced types are defined in the [full reference](../newai.md).

> Boolean aiToolsIsAllowAlways(serverType, toolName, entityId)

`GET /api/2.0/ai/tools/is-allow-always`

Is allow always

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **serverType** | query | **String** |  | [required] |
| **toolName** | query | **String** |  | [required] |
| **entityId** | query | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **Boolean** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**Boolean**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
