# createCustomerMonthlyUsageReport

Referenced types are defined in the [full reference](../api.md).

> DocumentBuilderTaskWrapper createCustomerMonthlyUsageReport(CustomerMonthlyUsageReportRequestDto)

`POST /api/2.0/portal/payment/customer/usage/monthly/report`

Start the customer monthly usage report generation

Starts generating a customer monthly usage report as an xlsx file and saves it in Documents.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CustomerMonthlyUsageReportRequestDto** | body | [**CustomerMonthlyUsageReportRequestDto**](../api.md#model-customermonthlyusagereportrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Operation execution status | [**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **404** | Customer could not be found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
