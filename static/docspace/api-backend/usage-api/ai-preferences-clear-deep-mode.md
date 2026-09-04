# aiPreferencesClearDeepMode

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiPreferencesClearDeepMode(body)

`DELETE /api/2.0/ai/preferences/clear-deep-mode`

Clear deep mode

Drops the persisted deep-mode toggle of the scope, so later reads fall back to the configured default.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
