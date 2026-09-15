# getCustomerOperations

Referenced types are defined in the [full reference](../api.md).

> ReportWrapper getCustomerOperations(offset, limit, ServiceName, StartDate, EndDate, ParticipantName, Credit, Debit, Type, Status, OrderBy, OrderType)

`GET /api/2.0/portal/payment/customer/operations`

Get the wallet operations

Lists the money movements on the portal&#39;s wallet - top-ups, the charges of the wallet services, refunds and  corrections - one page at a time, which is what a billing history is built from. Only a DocSpace administrator  may read it, a portal with no billing customer answers with an empty result, and the call is read-only. Every  filter is optional: &#x60;startDate&#x60; and &#x60;endDate&#x60; are read in the portal time zone and default to the portal  creation date and the present moment, &#x60;serviceName&#x60; narrows to particular wallet services and fails with 404  on a name this installation does not sell, &#x60;participantName&#x60;, &#x60;type&#x60; and &#x60;status&#x60; narrow to who caused a  movement and how it ended, and &#x60;credit&#x60; and &#x60;debit&#x60; include or exclude the two directions. &#x60;offset&#x60; and  &#x60;limit&#x60; page through the result and default to 0 and 25, &#x60;orderBy&#x60; and &#x60;orderType&#x60; sort it, and the answer  repeats them next to &#x60;totalQuantity&#x60;, &#x60;totalPage&#x60; and &#x60;currentPage&#x60; so a client can page without counting. The  same data as a downloadable file is &#x60;POST api/2.0/portal/payment/customer/operationsreport&#x60;, and the figures  added up per service are &#x60;GET api/2.0/portal/payment/customer/usage&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **offset** | query | **Integer** (int32) | The number of movements to skip before the first one returned, for walking through a long history page by  page. Counted after the filters and the ordering are applied, and starts at 0 when omitted. | [optional] [example: 0] |
| **limit** | query | **Integer** (int32) | The maximum number of movements returned in one page. Defaults to 25 when omitted; the answer echoes the  window back next to &#x60;totalQuantity&#x60;, &#x60;totalPage&#x60; and &#x60;currentPage&#x60;, so the next &#x60;offset&#x60; can be computed  without counting the items. | [optional] [example: 25] |
| **ServiceName** | query | **List** | The wallet services whose movements are kept, named the way the billing catalogue names them - &#x60;backup&#x60;,  &#x60;ai-tools&#x60;, &#x60;ai-search&#x60;, &#x60;disk-storage&#x60;, &#x60;docscloud&#x60;. Take the values from the &#x60;serviceName&#x60; field of  &#x60;GET api/2.0/portal/payment/walletservices&#x60;; the match ignores case, a name this installation does not sell  fails the call with 404, and an omitted list keeps every service. A bare string is accepted in place of an  array for backward compatibility. | [optional] [example: [backup]] |
| **StartDate** | query | **Date** (date-time) | The beginning of the reported period, inclusive. Read in the portal time zone rather than in UTC, so a  movement at the edge of the period falls where the portal sees it; defaults to the portal creation date. | [optional] [example: 2024-01-01T00:00:00Z] |
| **EndDate** | query | **Date** (date-time) | The end of the reported period, inclusive. Read in the portal time zone rather than in UTC, and defaults to  the moment the call is made. | [optional] [example: 2024-01-31T23:59:59Z] |
| **ParticipantName** | query | **String** | The participant whose movements are kept - the account the accounting service records as the cause of a  movement. A movement caused by a portal user carries that user ID here, and one caused by the portal itself  carries the customer name; surrounding whitespace is trimmed, and an omitted value keeps every participant. | [optional] [example: My Own Corporation] |
| **Credit** | query | **Boolean** | Whether movements that add money to the wallet - top-ups, refunds and corrections in the portal&#39;s favour -  are kept. Both directions are reported when neither this nor &#x60;debit&#x60; is given. | [optional] [example: true] |
| **Debit** | query | **Boolean** | Whether movements that take money out of the wallet - the charges of the wallet services - are kept. Both  directions are reported when neither this nor &#x60;credit&#x60; is given. | [optional] [example: false] |
| **Type** | query | **OperationType** | The kind of movement to keep, which says what caused the money to move rather than how it ended. Every kind  is reported when it is omitted. | [optional] [example: ServicePayment] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19] |
| **Status** | query | **OperationStatus** | The outcome to keep. A movement that is still being settled is reported as pending and may change later,  while the other outcomes are final; every outcome is reported when this is omitted. | [optional] [example: Completed] [enum: 0, 1, 2, 3] |
| **OrderBy** | query | **String** | The name of the field the movements are sorted by, spelled as the accounting service names it, such as  &#x60;StartDate&#x60; or &#x60;ServiceName&#x60;. Surrounding whitespace is trimmed, and the accounting service applies its own  ordering when this is omitted. | [optional] [example: StartDate] |
| **OrderType** | query | **OperationOrderType** | The direction the field named in &#x60;orderBy&#x60; is sorted in. Newest or largest first is what the accounting  service does by default, so leaving this out sorts the same way as asking for descending explicitly. | [optional] [example: Descending] [enum: 0, 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | A page of wallet movements with its paging information, or an empty result when the portal has no billing customer | [**ReportWrapper**](../api.md#model-reportwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | One of the names in &#x60;serviceName&#x60; is not a wallet service of this installation | - | - |
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
