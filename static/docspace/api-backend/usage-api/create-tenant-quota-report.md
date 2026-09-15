# createTenantQuotaReport

Referenced types are defined in the [full reference](../api.md).

> DocumentBuilderTaskWrapper createTenantQuotaReport()

`POST /api/2.0/settings/docscloud/tenant/quota/report`

Start the DocsCloud quota report

Queues a background job that renders the current DocsCloud user quota of the portal into an xlsx file and  saves that file in the My documents folder of the calling user; the report lists the editor and the viewer  users with the type and the expiration date of each, and summarizes the internal, external and remaining users  against the license limits. The file is not ready when the response arrives: poll  &#x60;GET api/2.0/settings/docscloud/tenant/quota/report&#x60; until &#x60;isCompleted&#x60; is true, then take the file from  &#x60;resultFileId&#x60; or &#x60;resultFileUrl&#x60;, and use &#x60;DELETE api/2.0/settings/docscloud/tenant/quota/report&#x60; to cancel a  job that is still running. The caller must be a portal administrator allowed to edit the portal settings. The  portal should have an activated DocsCloud tenant: this call does not check that, and without a tenant the job  itself fails and reports the reason in the &#x60;error&#x60; of the status response. One report per caller runs at a  time: while a report of this user is still being built, the call describes that running job and no second  generation is started, so a repeated call is safe. What comes back is the initial state of the job, with  &#x60;percentage&#x60; 0 and a created &#x60;status&#x60;, not the report; the report is a point-in-time snapshot and carries the  generation date in its file name. To read the same data as JSON, without building a file, use  &#x60;GET api/2.0/settings/docscloud/tenant/quota&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The initial state of the queued report generation job, with zero progress and an uncompleted status | [**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not allowed to edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
