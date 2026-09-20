# aiToolsAddCustomServer

Referenced types are defined in the [full reference](../aichat.md).

> AiToolsMutationResult aiToolsAddCustomServer(aiToolsAddCustomServer\_request)

`POST /api/2.0/ai/tools/add-custom-server`

Add custom server

Registers a custom MCP server under the given name so the model may call its tools. The name becomes a URL path segment, so it may not be &#x60;.&#x60;, &#x60;..&#x60;, or contain a path separator or a control character. &#x60;config&#x60; may be omitted in two cases: a name matching a host-configured system server pins the entry to that server&#39;s canonical settings as a whitelist marker, and a name already registered portal-wide copies the portal-level configuration into this scope; anything else without a config is rejected. &#x60;entityId&#x60; scopes the registration and has to name a room the caller can open - a room that is not an agent room folds to the portal-wide scope, while an unreachable one is refused so it cannot silently rewrite the portal&#39;s own registry.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsAddCustomServer\_request** | body | [**aiToolsAddCustomServer_request**](../aichat.md#model-aitoolsaddcustomserver-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the server was registered, with the stored entry. | [**AiToolsMutationResult**](../aichat.md#model-aitoolsmutationresult) | - |
| **400** | The server name is missing or is not routable. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The referenced object does not exist, or the caller cannot access it - the two are deliberately indistinguishable, so a room the caller may not open answers 404 rather than 403. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiToolsMutationResult**](../aichat.md#model-aitoolsmutationresult)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
