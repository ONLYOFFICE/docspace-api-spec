# updateWebhook

Referenced types are defined in the [full reference](../api.md).

> WebhooksConfigWrapper updateWebhook(UpdateWebhooksConfigRequestsDto)

`PUT /api/2.0/settings/webhook`

Update a webhook

Replaces the stored parameters of one webhook subscription, which is addressed by &#x60;id&#x60; in the body rather than  in the path. Every field of the request overwrites the stored one, so a payload that leaves out &#x60;enabled&#x60;,  &#x60;ssl&#x60;, &#x60;triggers&#x60; or &#x60;targetId&#x60; resets them to off, all events and no target: read the current values with  &#x60;GET api/2.0/settings/webhook&#x60; first and send back whatever should stay. &#x60;secretKey&#x60; is the one exception, an  empty value keeping the existing secret and a new one having to satisfy the portal password rules. The new  target is validated exactly as on creation, that is it must sit outside the installation&#39;s own network and  answer a HEAD request, and trigger flags the caller&#39;s role may not use are rejected. That validation runs  before the subscription is looked up, so an unusable payload is refused with 400 even when no subscription  with this &#x60;id&#x60; exists. A &#x60;DocSpaceAdmin&#x60; may update any subscription in the portal, anyone else only their  own, and a &#x60;Guest&#x60; is refused. Sending the same payload twice leaves the same state. Use  &#x60;PUT api/2.0/settings/webhook/enable&#x60; to switch a subscription on or off without touching anything else.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **UpdateWebhooksConfigRequestsDto** | body | [**UpdateWebhooksConfigRequestsDto**](../api.md#model-updatewebhooksconfigrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The updated webhook subscription, without its secret key | [**WebhooksConfigWrapper**](../api.md#model-webhooksconfigwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The target URL is unusable or unreachable, or the secret key or a trigger flag was rejected | - | - |
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

## SettingsWebpluginsApi
