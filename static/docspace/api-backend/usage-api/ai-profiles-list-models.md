# aiProfilesListModels

Referenced types are defined in the [full reference](../aichat.md).

> List aiProfilesListModels(profileId)

`GET /api/2.0/ai/profiles/list-models`

List models

Lists the models a stored profile&#39;s provider currently offers, asking the provider itself rather than reading a cached list. &#x60;profileId&#x60; is required and is read from the query. A failure is reported with the provider&#39;s own verdict: an unusable key comes back as 400 and a provider that is unreachable or broken as 502, while a missing profile or a caller without access keeps the status the portal gave it. Use &#x60;POST api/2.0/ai/profiles/list-provider-models&#x60; to probe an endpoint that has no profile yet.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **profileId** | query | **String** | The AI provider profile identifier. | [required] [example: 00000000-0000-0000-0000-000000000000] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The models the profile&#39;s provider currently offers. | [**List**](../aichat.md#model-aimodel) | - |
| **400** | &#x60;profileId&#x60; is missing, or the provider rejected the profile&#39;s API key. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **502** | The AI provider could not be reached, or answered with a failure of its own. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**List**](../aichat.md#model-aimodel)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
