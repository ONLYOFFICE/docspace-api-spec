# retryWebhook

Referenced types are defined in the [full reference](../api.md).

> WebhooksLogWrapper retryWebhook(id)

`PUT /api/2.0/settings/webhook/{id}/retry`

Retry a webhook delivery

Sends one past webhook delivery again. The &#x60;id&#x60; in the path is that of a delivery record from  &#x60;GET api/2.0/settings/webhooks/log&#x60;, not of a subscription, and the payload kept in that record is sent once  more to the subscription it belongs to. The work is asynchronous: a fresh delivery record is created and  queued at once, and the response describes that new record, with an identifier of its own and with &#x60;status&#x60;  and &#x60;delivery&#x60; not filled in yet. To learn the outcome, read &#x60;GET api/2.0/settings/webhooks/log&#x60; with  &#x60;eventId&#x60; set to the returned identifier until &#x60;delivery&#x60; appears. The original record stays as it is, and  every call queues one more attempt, so this is not safe to repeat blindly. A &#x60;DocSpaceAdmin&#x60; may retry any  delivery in the portal, anyone else only deliveries of the subscriptions they created, and a &#x60;Guest&#x60; is  refused. An &#x60;id&#x60; of 0 is rejected as an invalid request and an unknown one gives 404. The operation is rate  limited, so a burst of calls is answered with 429; to retry several records use  &#x60;PUT api/2.0/settings/webhook/retry&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The identifier of the object the operation acts on, as the listing operation of that kind of object reports  it. It has to match the shape the route declares - a GUID where the route is typed as one - since a value of  another shape does not match the route at all and is answered as not found. | [required] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The newly queued delivery record, with its status and delivery moment not filled in yet | [**WebhooksLogWrapper**](../api.md#model-webhookslogwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The delivery record identifier is 0 | - | - |
| **403** | The delivery belongs to another member&#39;s subscription, or the caller may not use webhooks | - | - |
| **404** | No delivery record with this ID exists in the portal | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WebhooksLogWrapper**](../api.md#model-webhookslogwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
