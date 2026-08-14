# aiSettingsGetVectorization

Referenced types are defined in the [full reference](../newai.md).

> AiVectorizationSettingsWrapper aiSettingsGetVectorization()

`GET /api/2.0/ai/config/vectorization`

Get vectorization settings

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiVectorizationSettingsWrapper**](../newai.md#model-aivectorizationsettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiVectorizationSettingsWrapper**](../newai.md#model-aivectorizationsettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
