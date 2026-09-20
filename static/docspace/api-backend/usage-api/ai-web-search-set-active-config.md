# aiWebSearchSetActiveConfig

Referenced types are defined in the [full reference](../aichat.md).

> AiSuccessResponse aiWebSearchSetActiveConfig(aiWebSearchConfigure\_request)

`PUT /api/2.0/ai/web-search/set-active-config`

Set active config

Stores a web-search configuration without contacting the provider first, for a form that has already validated its input or for restoring a known-good configuration. &#x60;entityId&#x60; scopes it to a room and has to name one the caller can open. A &#x60;baseUrl&#x60; pointing at a private network address is still refused, because that check is local. Nothing guarantees the stored provider works: follow up with &#x60;POST api/2.0/ai/web-search/test-connection&#x60;, or use &#x60;PUT api/2.0/ai/web-search/configure&#x60; to have the store gated on a live probe.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiWebSearchConfigure\_request** | body | [**aiWebSearchConfigure_request**](../aichat.md#model-aiwebsearchconfigure-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the configuration was stored, unverified. | [**AiSuccessResponse**](../aichat.md#model-aisuccessresponse) | - |
| **400** | The provider URL is missing, malformed, or points at a private network address. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The referenced object does not exist, or the caller cannot access it - the two are deliberately indistinguishable, so a room the caller may not open answers 404 rather than 403. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../aichat.md#model-aisuccessresponse)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
