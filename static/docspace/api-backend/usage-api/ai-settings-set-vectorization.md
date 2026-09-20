# aiSettingsSetVectorization

Referenced types are defined in the [full reference](../aichat.md).

> AiVectorizationSettingsWrapper aiSettingsSetVectorization(request\_body)

`PUT /api/2.0/ai/config/vectorization`

Update vectorization settings

Replaces the portal&#39;s vectorization settings and returns the stored result. The body is proxied unchanged to the DocSpace AI service, which validates it, so a rejected value is reported with that service&#39;s own verdict rather than being checked here. Changing the embedding provider does not re-index anything already indexed - start that separately with &#x60;POST api/2.0/ai/vectorization/tasks&#x60;. This is a portal-wide setting and requires the permissions the AI service demands for it.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** | The portal&#39;s vectorization settings, proxied unchanged to the DocSpace AI service, which owns and validates the shape. Read the current one with &#x60;GET api/2.0/ai/config/vectorization&#x60; and send it back changed. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The stored vectorization settings. | [**AiVectorizationSettingsWrapper**](../aichat.md#model-aivectorizationsettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiVectorizationSettingsWrapper**](../aichat.md#model-aivectorizationsettingswrapper)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIThreadsApi
