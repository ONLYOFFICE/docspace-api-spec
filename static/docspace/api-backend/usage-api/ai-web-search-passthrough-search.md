# aiWebSearchPassthroughSearch

Referenced types are defined in the [full reference](../newai.md).

> Map aiWebSearchPassthroughSearch(request\_body)

`POST /api/2.0/ai/websearch/v1/search`

Web search passthrough

Runs a web search on behalf of the document editor&#39;s AI plugin, which holds only a placeholder configuration - the portal&#39;s active provider and its key are resolved here, so neither ever reaches the browser. The portal-wide configuration is used, and a portal without one answers 404. The &#x60;entityId&#x60; and &#x60;entityKind&#x60; query parameters name the document the search is billed to; with the ONLYOFFICE provider the entry is resolved under the caller&#39;s credentials and sent to the gateway as the request &#x60;metadata&#x60; (&#x60;source_id&#x60; / &#x60;source_type&#x60; / &#x60;source_title&#x60;), and an entry the caller cannot open sends none. The provider&#39;s own status, body and content type are relayed as they stand, so a provider that rate-limits answers 429 and one that is unreachable answers 502. Closing the connection aborts the upstream request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** | A search request in the shape the portal&#39;s active web-search provider expects, forwarded to it unchanged. The endpoint and the key come from the stored configuration and must not be sent here. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The provider&#39;s own response, relayed verbatim with its status and content type. | **Map** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **404** | Web search is not configured for this portal. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **429** | Relayed verbatim from the AI provider, which is rate-limiting this portal&#39;s key. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **502** | The AI provider could not be reached, or answered with a failure of its own. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**Map**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
