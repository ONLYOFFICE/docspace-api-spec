# createCustomerMonthlyUsageReport

Referenced types are defined in the [full reference](../api.md).

> DocumentBuilderTaskWrapper createCustomerMonthlyUsageReport(CustomerMonthlyUsageReportRequestDto)

`POST /api/2.0/portal/payment/customer/usage/monthly/report`

Start the monthly usage report

Queues the wallet spending added up per calendar month as an &#x60;xlsx&#x60; file and returns the task that will build  it; the file is not ready when the response arrives. The portal needs a billing customer and the caller has to  be a DocSpace administrator. The body takes only the period - &#x60;startDate&#x60; and &#x60;endDate&#x60;, both inclusive - and  an empty body covers everything from the portal creation date to now; the months are cut in the portal time  zone, exactly as in &#x60;GET api/2.0/portal/payment/customer/usage/monthly&#x60;. Poll  &#x60;GET api/2.0/portal/payment/customer/usage/monthly/report&#x60; until &#x60;isCompleted&#x60; is true, then take the file  from &#x60;resultFileUrl&#x60; or open &#x60;resultFileId&#x60;: the finished file is saved into the caller&#39;s own My documents  section, where it counts against the portal storage like any other file. One monthly usage report per user is  tracked at a time - a call made while the previous one is still running answers with that task - and  &#x60;DELETE api/2.0/portal/payment/customer/usage/monthly/report&#x60; stops it. There is no service filter here: for a  report per service use &#x60;POST api/2.0/portal/payment/customer/usage/report&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CustomerMonthlyUsageReportRequestDto** | body | [**CustomerMonthlyUsageReportRequestDto**](../api.md#model-customermonthlyusagereportrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The queued task, to be polled until &#x60;isCompleted&#x60; is true | [**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | This portal has no billing customer yet | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
