# getMigrationLogs

Referenced types are defined in the [full reference](../api.md).

> getMigrationLogs()

`GET /api/2.0/migration/logs`

Get migration logs

Downloads the log of the parse or import the portal currently holds - the step-by-step record behind the  numbers and the single error message of &#x60;GET api/2.0/migration/status&#x60;, and the place where the reason for a  skipped user or file is written. The portal has to hold such a job, started by  &#x60;POST api/2.0/migration/init/{migratorName}&#x60; or &#x60;POST api/2.0/migration/migrate&#x60; and not yet removed by  &#x60;POST api/2.0/migration/clear&#x60; or &#x60;POST api/2.0/migration/finish&#x60;, otherwise the call answers 404; a DocSpace  administrator is required and the call is read-only and idempotent. The body is not JSON: it is  &#x60;text/plain; charset&#x3D;UTF-8&#x60; sent as an attachment named &#x60;migration.log&#x60;, one line per step with the progress  it reported. Each job writes its own log, so this always returns the log of the job that  &#x60;GET api/2.0/migration/status&#x60; describes, and while that job runs the file keeps growing - a call made early  returns only the part written so far and may be repeated later for the rest.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The log of the current job as a &#x60;text/plain&#x60; attachment named &#x60;migration.log&#x60; | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator | - | - |
| **404** | The portal holds no parse or import whose log could be returned | - | - |
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
