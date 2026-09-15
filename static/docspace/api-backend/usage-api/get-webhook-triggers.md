# getWebhookTriggers

Referenced types are defined in the [full reference](../api.md).

> WebhookTriggerArrayWrapper getWebhookTriggers()

`GET /api/2.0/settings/webhook/triggers`

Get the webhook triggers

Returns the catalogue of events a webhook subscription can listen to, in the order the portal presents them:  user events, then group, file, folder, room, form and agent ones. Each entry carries the event name as it  appears in a payload, such as &#x60;file.created&#x60;, the bit value to put into the &#x60;triggers&#x60; bitmask of a  subscription, and &#x60;available&#x60;, telling whether the caller&#39;s own role may subscribe to that event at all: a  &#x60;User&#x60; cannot subscribe to the creation of users, groups or rooms, for instance, while a &#x60;RoomAdmin&#x60; can. Add  the bit values of the wanted events together to build &#x60;triggers&#x60;; the entry named &#x60;*&#x60; has the value 0 and  stands for every event, so it is used on its own rather than added. Events unavailable to the caller are  listed all the same, but passing one to &#x60;POST api/2.0/settings/webhook&#x60; or &#x60;PUT api/2.0/settings/webhook&#x60; is  rejected as an invalid request. This is fixed reference data: the same for every portal, not paginated,  changing only with the product version, and readable by any authenticated caller, a &#x60;Guest&#x60; included. Nothing  is written.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The triggers a webhook may subscribe to, each marked available for the caller&#39;s role or not | [**WebhookTriggerArrayWrapper**](../api.md#model-webhooktriggerarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WebhookTriggerArrayWrapper**](../api.md#model-webhooktriggerarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
