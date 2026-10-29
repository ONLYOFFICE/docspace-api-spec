# getQuotaPaymentInformation

> QuotaWrapper getQuotaPaymentInformation(refresh)

`GET /api/2.0/portal/payment/quota`

Get the current plan and limits

Returns the quota the portal is on - its paid plan or the free one - with the limits its features grant and how  much of each is already used. Any signed-in member except a guest may call it. The call is read-only; the plan  comes from the cache, and `refresh=true` re-reads it from the billing service, a remote call meant for right  after a purchase. The answer is trimmed to the caller's user type: a DocSpace administrator or the owner gets  the price, the due date and all features, a room administrator only the `manager`, `room`, `total_size` and  `statistic` features, and a user only `total_size`. For both of the latter `price` is an empty object and  `dueDate` is omitted, while the storage quota settings (`usersQuota`, `roomsQuota`, `aiAgentsQuota`,  `tenantCustomQuota`) come back as for an administrator. The quotas that could be bought instead are  `GET api/2.0/portal/payment/quotas`. A guest is refused with 403.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Whether the answer is fetched from the billing service instead of the portal cache. The cached copy is what a  start-up needs and costs nothing; asking for a fresh one makes a remote call, so use it right after a  purchase or a top-up and not on every read. | [optional] [example: `true`] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The quota the portal is on with its limits and current usage, trimmed to what the caller's user type may see | [**QuotaWrapper**](../../models/quota-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is a guest of this portal | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**QuotaWrapper**](../../models/quota-wrapper.md)

## Authorization

[Basic](../portal.md#basic), [OAuth2](../portal.md#oauth2) (scopes: read, write), [ApiKeyBearer](../portal.md#apikeybearer), [asc_auth_key](../portal.md#asc_auth_key), [Bearer](../portal.md#bearer), [OpenId](../portal.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
