# clearMigration

Referenced types are defined in the [full reference](../api.md).

> clearMigration()

`POST /api/2.0/migration/clear`

Clear migration

Discards a finished import and deletes the data uploaded for it, freeing the portal for the next one. Call it  once &#x60;GET api/2.0/migration/status&#x60; reports &#x60;isCompleted&#x60; for a job whose &#x60;parseResult.operation&#x60; is  &#x60;migration&#x60;; a DocSpace administrator is required. Only the queued job and the temporary upload folder go -  the users, groups and files already imported stay in the portal - so the call destroys migration data alone,  and it is idempotent: clearing twice, or with nothing to clear, still answers 200. Like the other write  operations here it is only queued, and once it has run &#x60;GET api/2.0/migration/status&#x60; returns an empty result  and &#x60;GET api/2.0/migration/logs&#x60; answers 404, so download the log before calling it. A parse that is still  running is not affected - stop that with &#x60;POST api/2.0/migration/cancel&#x60; - and  &#x60;POST api/2.0/migration/finish&#x60; performs the same clean-up itself, which makes this call unnecessary after it.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The clean-up has been queued; the finished import is dropped and the uploaded data deleted. The response carries no content | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
