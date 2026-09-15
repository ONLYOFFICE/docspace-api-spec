# createWebhook

Referenced types are defined in the [full reference](../api.md).

> WebhooksConfigWrapper createWebhook(CreateWebhooksConfigRequestsDto)

`POST /api/2.0/settings/webhook`

Create a webhook

Creates a webhook subscription for the current portal: a target URL that the portal calls with a signed JSON  payload whenever one of the subscribed events happens. The target is checked before anything is stored, so it  has to be an absolute &#x60;http&#x60; or &#x60;https&#x60; address outside the installation&#39;s own network, and it has to answer a  HEAD request with a success code, redirects not being followed. &#x60;secretKey&#x60; is mandatory here, has to satisfy  the portal password rules published by &#x60;GET api/2.0/settings/security/password&#x60;, and signs the payloads; it  does not appear in any response. &#x60;triggers&#x60; is a bitmask of the subscribed events with 0 standing for all of  them; a flag the caller&#39;s role may not use is rejected, so take the allowed set from  &#x60;GET api/2.0/settings/webhook/triggers&#x60;. &#x60;ssl&#x3D;true&#x60; additionally demands an &#x60;https&#x60; target with a valid  certificate, while &#x60;ssl&#x3D;false&#x60; leaves the certificate unchecked. Set &#x60;targetId&#x60; to deliver events about a  single entity only. A subscription fires only for events its creator is allowed to see, and only while it is  enabled. Any role except &#x60;Guest&#x60; may create one, and each call adds another subscription rather than replacing  an existing one.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CreateWebhooksConfigRequestsDto** | body | [**CreateWebhooksConfigRequestsDto**](../api.md#model-createwebhooksconfigrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The created webhook subscription, without its secret key | [**WebhooksConfigWrapper**](../api.md#model-webhooksconfigwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The target URL is unusable or unreachable, or the secret key or a trigger flag was rejected | - | - |
| **403** | The caller is a &#x60;Guest&#x60;, or a non-admin caller while the developer tools are restricted | - | - |
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
