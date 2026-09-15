# aiSettingsGetVectorization

Referenced types are defined in the [full reference](../newai.md).

> AiVectorizationSettingsWrapper aiSettingsGetVectorization()

`GET /api/2.0/ai/config/vectorization`

Get vectorization settings

Returns the portal&#39;s vectorization settings - the embedding provider and the options used when portal content is indexed for retrieval. It takes no parameters and is proxied unchanged to the DocSpace AI service. Vectorization is a portal-wide setting, so there is no room-scoped form of it. Change it with &#x60;PUT api/2.0/ai/config/vectorization&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The portal&#39;s vectorization settings. | [**AiVectorizationSettingsWrapper**](../newai.md#model-aivectorizationsettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiVectorizationSettingsWrapper**](../newai.md#model-aivectorizationsettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
