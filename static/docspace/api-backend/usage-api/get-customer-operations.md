# getCustomerOperations

Referenced types are defined in the [full reference](../api.md).

> ReportWrapper getCustomerOperations(offset, limit, ServiceName, StartDate, EndDate, ParticipantName, Credit, Debit, Type, Status, OrderBy, OrderType)

`GET /api/2.0/portal/payment/customer/operations`

Get the customer operations

Returns the report of customer operations from the accounting service.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **offset** | query | **Integer** (int32) | The number of items to skip for pagination. The default value is 0. | [optional] [example: 0] |
| **limit** | query | **Integer** (int32) | The maximum number of items to return for pagination. The default value is 25. | [optional] [example: 25] |
| **ServiceName** | query | **List** | The service name list. A single string is also accepted for backward compatibility. | [optional] [example: [backup]] |
| **StartDate** | query | **Date** (date-time) | The report start date. | [optional] [example: 2024-01-01T00:00:00Z] |
| **EndDate** | query | **Date** (date-time) | The report end date. | [optional] [example: 2024-01-31T23:59:59Z] |
| **ParticipantName** | query | **String** | The participant name. | [optional] [example: My Own Corporation] |
| **Credit** | query | **Boolean** | Specifies whether to include credit operations in the report. | [optional] [example: true] |
| **Debit** | query | **Boolean** | Specifies whether to include debit operations in the report. | [optional] [example: false] |
| **Type** | query | **OperationType** | The operation type to filter by. | [optional] [example: ServicePayment] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19] |
| **Status** | query | **OperationStatus** | The operation status to filter by. | [optional] [example: Completed] [enum: 0, 1, 2, 3] |
| **OrderBy** | query | **String** | The field to order by. | [optional] [example: StartDate] |
| **OrderType** | query | **OperationOrderType** | Order direction: Ascending or Descending. | [optional] [example: Descending] [enum: 0, 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The customer operations | [**ReportWrapper**](../api.md#model-reportwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **404** | Service could not be found | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ReportWrapper**](../api.md#model-reportwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
