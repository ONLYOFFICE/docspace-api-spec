# aiPreferencesSetDeepMode

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiPreferencesSetDeepMode(aiPreferencesSetDeepMode\_request)

`PUT /api/2.0/ai/preferences/set-deep-mode`

Set deep mode

Persists the deep-mode toggle of the scope. Idempotent - there is no need to check whether a value already exists.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPreferencesSetDeepMode\_request** | body | [**aiPreferencesSetDeepMode_request**](../newai.md#model-aipreferencessetdeepmode-request-body) |  | [required] |

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

## AIProfilesApi
