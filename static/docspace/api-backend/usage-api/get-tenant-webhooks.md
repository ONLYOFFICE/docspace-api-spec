# getTenantWebhooks

Referenced types are defined in the [full reference](../api.md).

> WebhooksConfigWithStatusArrayWrapper getTenantWebhooks()

`GET /api/2.0/settings/webhook`

Get the portal webhooks

Returns the webhook subscriptions of the current portal, each together with the outcome of its most recent  delivery. The portal owner and a &#x60;DocSpaceAdmin&#x60; see every subscription in the portal, while a &#x60;RoomAdmin&#x60; or  a &#x60;User&#x60; sees only the ones they created themselves, so the same call answers differently depending on who  asks. A &#x60;Guest&#x60; may not use webhooks at all and is refused, and so is any non-admin caller while the portal  keeps the developer tools restricted, which &#x60;GET api/2.0/settings/devtoolsaccess&#x60; reports. Every entry pairs  the stored configuration with &#x60;status&#x60;, the HTTP status code the target answered on the last attempt, where 0  means nothing has been delivered yet, while the secret key is not part of the response. The list is neither  paginated nor ordered, and an empty list simply means no subscription exists for the caller. Nothing is  written and the call is safe to repeat. Create a subscription with &#x60;POST api/2.0/settings/webhook&#x60;, and  inspect single deliveries with &#x60;GET api/2.0/settings/webhooks/log&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The webhook subscriptions visible to the caller, each with the status of its last delivery | [**WebhooksConfigWithStatusArrayWrapper**](../api.md#model-webhooksconfigwithstatusarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is a &#x60;Guest&#x60;, or a non-admin caller while the developer tools are restricted | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WebhooksConfigWithStatusArrayWrapper**](../api.md#model-webhooksconfigwithstatusarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
