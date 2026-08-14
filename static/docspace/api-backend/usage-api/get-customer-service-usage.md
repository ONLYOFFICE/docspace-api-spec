# getCustomerServiceUsage

Referenced types are defined in the [full reference](../api.md).

> CustomerServiceUsageReportWrapper getCustomerServiceUsage(ServiceName, ParticipantName, Status, StartDate, EndDate, Metadata, offset, limit, OrderBy, OrderType)

`GET /api/2.0/portal/payment/customer/usage`

Get the customer service usage

Returns the customer usage statistics aggregated per service from the accounting service.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **ServiceName** | query | **List** | The service name list. | [optional] [example: [backup]] |
| **ParticipantName** | query | **String** | The participant name. | [optional] [example: My Own Corporation] |
| **Status** | query | **OperationStatus** | The operation status to filter by. | [optional] [example: Completed] [enum: 0, 1, 2, 3] |
| **StartDate** | query | **Date** (date-time) | Start of the period (inclusive). | [optional] [example: 2025-01-01T00:00:00Z] |
| **EndDate** | query | **Date** (date-time) | End of the period (inclusive). | [optional] [example: 2025-12-31T23:59:59Z] |
| **Metadata** | query | **Map** | Metadata key-value pairs to filter by. | [optional] [example: {"key1":"value1","key2":"value2"}] |
| **offset** | query | **Integer** (int32) | The number of items to skip for pagination. The default value is 0. | [optional] [example: 0] |
| **limit** | query | **Integer** (int32) | The maximum number of items to return for pagination. The default value is 25. | [optional] [example: 25] |
| **OrderBy** | query | **String** | The field to order by. | [optional] [example: ServiceName] |
| **OrderType** | query | **OperationOrderType** | Order direction: Ascending or Descending. | [optional] [example: Descending] [enum: 0, 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The customer service usage | [**CustomerServiceUsageReportWrapper**](../api.md#model-customerserviceusagereportwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **404** | Service could not be found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CustomerServiceUsageReportWrapper**](../api.md#model-customerserviceusagereportwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
