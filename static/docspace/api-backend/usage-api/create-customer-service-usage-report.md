# createCustomerServiceUsageReport

Referenced types are defined in the [full reference](../api.md).

> DocumentBuilderTaskWrapper createCustomerServiceUsageReport(CustomerServiceUsageReportRequestDto)

`POST /api/2.0/portal/payment/customer/usage/report`

Start the service usage report

Queues the usage of the wallet services as an &#x60;xlsx&#x60; file and returns the task that will build it; the file is  not ready when the response arrives. The portal needs a billing customer and the caller has to be a DocSpace  administrator. The body takes the same filters as &#x60;GET api/2.0/portal/payment/customer/usage&#x60; - the service  names, the date range, the participant, the operation status, the usage metadata and the ordering - and an  empty body reports every service from the portal creation date to now; a service name this installation does  not sell fails with 404. Poll &#x60;GET api/2.0/portal/payment/customer/usage/report&#x60; until &#x60;isCompleted&#x60; is true,  then take the file from &#x60;resultFileUrl&#x60; or open &#x60;resultFileId&#x60;: the finished file is saved into the caller&#39;s  own My documents section, where it counts against the portal storage like any other file. One service usage  report per user is tracked at a time - a call made while the previous one is still running answers with that  task - and &#x60;DELETE api/2.0/portal/payment/customer/usage/report&#x60; stops it. It is a different report from the  operations one and does not interfere with it: per-movement history is  &#x60;POST api/2.0/portal/payment/customer/operationsreport&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **CustomerServiceUsageReportRequestDto** | body | [**CustomerServiceUsageReportRequestDto**](../api.md#model-customerserviceusagereportrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The queued task, to be polled until &#x60;isCompleted&#x60; is true | [**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | This portal has no billing customer, or one of the names in &#x60;serviceName&#x60; is not a wallet service of this installation | - | - |
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
