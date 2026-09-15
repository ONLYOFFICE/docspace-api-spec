# getTenantQuotaReport

Referenced types are defined in the [full reference](../api.md).

> DocumentBuilderTaskWrapper getTenantQuotaReport()

`GET /api/2.0/settings/docscloud/tenant/quota/report`

Get the DocsCloud quota report status

Returns the state of the DocsCloud user quota report that the current user started with  &#x60;POST api/2.0/settings/docscloud/tenant/quota/report&#x60;, so that the caller can follow the generation and pick  up the resulting file. It reports the caller&#39;s own job only: a report started by another administrator is not  visible here, and an empty result means this user has no job, because none was started, because it was  terminated, or because a finished one has already been cleared (a job state is kept for a day, and starting a  new report drops the previous finished one); that is a normal state and not an error. The caller must be a  portal administrator allowed to edit the portal settings. The call is read-only and idempotent, and it is  meant to be polled while the job runs. In the result, &#x60;percentage&#x60; goes from 0 to 100 and &#x60;isCompleted&#x60;  becomes true both on success and on failure, so check &#x60;error&#x60;: it is empty when the report was built and  carries the failure message otherwise;  &#x60;resultFileId&#x60;, &#x60;resultFileName&#x60; and &#x60;resultFileUrl&#x60; are filled in only once the file exists, and that file  also stays in the My documents folder of the caller. Use the &#x60;POST&#x60; operation on this path to start a report  and the &#x60;DELETE&#x60; one to cancel it.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the DocsCloud quota report job of the caller, or an empty result if there is no such job | [**DocumentBuilderTaskWrapper**](../api.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
