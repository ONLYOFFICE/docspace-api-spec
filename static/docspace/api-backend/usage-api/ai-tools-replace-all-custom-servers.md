# aiToolsReplaceAllCustomServers

Referenced types are defined in the [full reference](../newai.md).

> AiToolsBulkResult aiToolsReplaceAllCustomServers(aiToolsReplaceAllCustomServers\_request)

`PUT /api/2.0/ai/tools/replace-all-custom-servers`

Replace all custom servers

Replaces the whole custom MCP server registry of the scope with the supplied map in one write, which makes it the operation a settings screen saves with. &#x60;map&#x60; is required: without it the registry would be emptied, so a missing or non-object value is rejected rather than treated as none. Every name in the map is validated as a routable path segment and every configuration is resolved before anything is written, so a map with one bad entry changes nothing. &#x60;entityId&#x60; has to name a room the caller can open - this is the operation where an unreachable one would otherwise have wiped the portal-wide registry.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsReplaceAllCustomServers\_request** | body | [**aiToolsReplaceAllCustomServers_request**](../newai.md#model-aitoolsreplaceallcustomservers-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the registry was replaced, with &#x60;errors&#x60; listing what was refused. | [**AiToolsBulkResult**](../newai.md#model-aitoolsbulkresult) | - |
| **400** | The body is not a map of server name to configuration, or a name is not routable. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **404** | The referenced object does not exist, or the caller cannot access it - the two are deliberately indistinguishable, so a room the caller may not open answers 404 rather than 403. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiToolsBulkResult**](../newai.md#model-aitoolsbulkresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
