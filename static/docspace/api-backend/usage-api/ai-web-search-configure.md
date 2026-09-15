# aiWebSearchConfigure

Referenced types are defined in the [full reference](../newai.md).

> AiWebSearchMutationResult aiWebSearchConfigure(aiWebSearchConfigure\_request)

`PUT /api/2.0/ai/web-search/configure`

Configure and verify web search

Validates a web-search configuration against the live provider and stores it only if the provider answers, which makes it the safe way to save a form in one step. &#x60;entityId&#x60; scopes the configuration to a room and has to name one the caller can open; omitting it configures the portal. A &#x60;baseUrl&#x60; pointing at a private network address is refused. Use &#x60;PUT api/2.0/ai/web-search/set-active-config&#x60; when the configuration should be stored without a provider round trip.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiWebSearchConfigure\_request** | body | [**aiWebSearchConfigure_request**](../newai.md#model-aiwebsearchconfigure-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the configuration was stored, after the provider answered. | [**AiWebSearchMutationResult**](../newai.md#model-aiwebsearchmutationresult) | - |
| **400** | The provider URL is missing, malformed, or points at a private network address. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **404** | The referenced object does not exist, or the caller cannot access it - the two are deliberately indistinguishable, so a room the caller may not open answers 404 rather than 403. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiWebSearchMutationResult**](../newai.md#model-aiwebsearchmutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
