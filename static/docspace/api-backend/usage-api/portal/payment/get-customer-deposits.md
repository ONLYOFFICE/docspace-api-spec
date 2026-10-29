# getCustomerDeposits

> DepositReportWrapper getCustomerDeposits(startDate, endDate, status, offset, limit)

`GET /api/2.0/portal/payment/customer/deposits`

Get the wallet top-ups

Lists the top-ups of the portal's wallet - the payments into it - one page at a time, which is what a list of  payments with their invoices is built from. A portal that is not a billing customer yet has no top-ups and  gets an empty result rather than an error. Only the payer or the portal owner may read it, as with the  invoices, and the call is read-only. Every filter is optional: `startDate` and `endDate` default to the  portal creation date and the present moment, a value without `Z` or an offset is read in the portal time  zone, and `status` narrows to how a top-up ended. `offset` and `limit` default to 0 and 25 and are echoed next  to `totalQuantity`, `totalPage` and `currentPage`; a negative `offset` or a `limit` outside 1 to 100 fails  with 400. An empty result means the portal is not a billing customer, has no wallet at the accounting service  yet, or that service could not be read; a period without top-ups gives an empty `collection`. A top-up with  `hasInvoice` true has an invoice, opened with `GET api/2.0/portal/payment/customer/deposits/{id}/invoice`.  For the full wallet history, charges and refunds included, use  `GET api/2.0/portal/payment/customer/operations`.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **startDate** | query | **Date** (date-time) | The beginning of the period, inclusive, as an ISO 8601 timestamp. A value with neither `Z` nor an offset is  read in the portal time zone, not in the caller's; defaults to the portal creation date. | [optional] [example: `2025-01-01T00:00:00Z`] |
| **endDate** | query | **Date** (date-time) | The end of the period, inclusive, as an ISO 8601 timestamp. A value with neither `Z` nor an offset is read in  the portal time zone, not in the caller's; defaults to the moment the call is made. | [optional] [example: `2025-12-31T23:59:59Z`] |
| **status** | query | **OperationStatus** | The outcome to keep. A top-up that is still being settled is reported as pending and may change later, while  the other outcomes are final; every outcome is reported when this is omitted. | [optional] [example: `Completed`] [enum: `0`, `1`, `2`, `3`] |
| **offset** | query | **Integer** (int32) | The number of top-ups to skip before the first one returned, for walking through a long history page by page.  Counted after the filters are applied, and starts at 0 when omitted. | [optional] [example: `0`] [min: 0] [max: 2147483647] |
| **limit** | query | **Integer** (int32) | The maximum number of top-ups returned in one page. Defaults to 25 when omitted; the answer echoes the window  back next to `totalQuantity`, `totalPage` and `currentPage`, so the next `offset` can be computed without  counting the items. | [optional] [example: `25`] [min: 1] [max: 100] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | A page of wallet top-ups with its paging information, or an empty result when the portal is not a billing customer, has no wallet at the accounting service yet, or that service could not be read | [**DepositReportWrapper**](../../models/deposit-report-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | `offset` is negative, `limit` is outside 1 to 100, or a parameter cannot be read, such as a `status` that is not one of its values or a date that is not ISO 8601 | - | - |
| **403** | The caller is neither the payer nor the portal owner, or the portal has no billing service configured | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DepositReportWrapper**](../../models/deposit-report-wrapper.md)

## Authorization

[Basic](../portal.md#basic), [OAuth2](../portal.md#oauth2) (scopes: read, write), [ApiKeyBearer](../portal.md#apikeybearer), [asc_auth_key](../portal.md#asc_auth_key), [Bearer](../portal.md#bearer), [OpenId](../portal.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
