# getWebhooksLogs

Referenced types are defined in the [full reference](../api.md).

> WebhooksLogArrayWrapper getWebhooksLogs(deliveryFrom, deliveryTo, hookUri, configId, eventId, groupStatus, userId, trigger, count, startIndex)

`GET /api/2.0/settings/webhooks/log`

Get webhook logs

Returns the logs of the webhook activities.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **deliveryFrom** | query | **Date** (date-time) | The delivery start time for filtering webhook logs. | [optional] [example: 2024-01-15T10:30:00Z] |
| **deliveryTo** | query | **Date** (date-time) | The delivery end time for filtering webhook logs. | [optional] [example: 2024-01-15T10:30:00Z] |
| **hookUri** | query | **String** | The destination URL where webhooks are delivered. | [optional] [example: https://example.com/webhook] |
| **configId** | query | **Integer** (int32) | The webhook configuration identifier. | [optional] [example: 1] |
| **eventId** | query | **Integer** (int32) | The unique identifier of the event that triggered the webhook. | [optional] [example: 1] |
| **groupStatus** | query | **WebhookGroupStatus** | The status of the webhook delivery group. | [optional] [example: NotSent] [enum: 0, 1, 2, 4, 8, 16] |
| **userId** | query | **UUID** (uuid) | The identifier of the user associated with the webhook event. | [optional] [example: {}] |
| **trigger** | query | **WebhookTrigger** | The type of event that triggered the webhook. | [optional] [example: 0] [enum: 0, 1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096, 8192, 16384, 32768, 65536, 131072, 262144, 524288, 1048576, 2097152, 4194304, 8388608, 16777216, 33554432, 67108864, 134217728, 268435456, 536870912, 1073741824] |
| **count** | query | **Integer** (int32) | The maximum number of webhook log records to return in the query response. | [optional] [example: 1] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | Specifies the starting index for retrieving webhook logs.  Used for pagination in the webhook delivery log queries. | [optional] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Logs of the webhook activities | [**WebhooksLogArrayWrapper**](../api.md#model-webhookslogarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | Access denied | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WebhooksLogArrayWrapper**](../api.md#model-webhookslogarraywrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
