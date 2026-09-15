# enableWebhook

Referenced types are defined in the [full reference](../api.md).

> WebhooksConfigWrapper enableWebhook(UpdateWebhooksConfigRequestsDto)

`PUT /api/2.0/settings/webhook/enable`

Switch a webhook on or off

Switches one webhook subscription on or off, leaving the rest of its parameters as they are. Only &#x60;id&#x60; and  &#x60;enabled&#x60; are read from the body: &#x60;name&#x60;, &#x60;uri&#x60;, &#x60;secretKey&#x60;, &#x60;ssl&#x60;, &#x60;triggers&#x60; and &#x60;targetId&#x60; are demanded by  the schema but ignored here, so change any of them with &#x60;PUT api/2.0/settings/webhook&#x60; instead. Switching a  subscription on re-checks what is already stored, probing the saved URL with a HEAD request and re-validating  the saved secret against the current portal password rules, and the call is refused with 400 when either  fails: a subscription whose target has gone away, or whose secret predates a tightening of the password rules,  cannot be switched on until it is updated. Switching one off is not validated. While a subscription is off its  events are dropped rather than queued, so nothing arrives from that period once it is switched on again. A  &#x60;DocSpaceAdmin&#x60; may switch any subscription in the portal, anyone else only their own, and a &#x60;Guest&#x60; is  refused. The response carries the subscription in its new state, and repeating the call changes nothing  further.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **UpdateWebhooksConfigRequestsDto** | body | [**UpdateWebhooksConfigRequestsDto**](../api.md#model-updatewebhooksconfigrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The webhook subscription in its new state, without its secret key | [**WebhooksConfigWrapper**](../api.md#model-webhooksconfigwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The saved target no longer answers, or the saved secret no longer passes the password rules | - | - |
| **403** | The subscription belongs to another member, or the caller may not use webhooks at all | - | - |
| **404** | No webhook subscription with this ID exists in the portal | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WebhooksConfigWrapper**](../api.md#model-webhooksconfigwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
