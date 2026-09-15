# startMigration

Referenced types are defined in the [full reference](../api.md).

> startMigration(MigrationApiInfo)

`POST /api/2.0/migration/migrate`

Start migration

Starts the import itself: the users, the groups and the files selected in the request body are created on this  portal from the backup that the parse pass has read. Run &#x60;POST api/2.0/migration/init/{migratorName}&#x60; first  and wait for &#x60;isCompleted&#x60; in &#x60;GET api/2.0/migration/status&#x60;, then send &#x60;parseResult&#x60; from that answer back  here with &#x60;shouldImport&#x60; set on the users and groups to take and the &#x60;import...Files&#x60; flags set for the  content to copy. A DocSpace administrator is required, and importing a user as &#x60;DocSpaceAdmin&#x60; additionally  requires the caller to be the portal owner unless a user with that email is an administrator of this portal  already, otherwise the whole call is rejected with 403 before anything is imported. The job is queued and the  call answers with an empty body at once: watch &#x60;progress&#x60;, &#x60;successedUsers&#x60;, &#x60;failedUsers&#x60; and &#x60;error&#x60; in  &#x60;GET api/2.0/migration/status&#x60; and read what each step did from &#x60;GET api/2.0/migration/logs&#x60;. The import  writes to the portal and cannot be undone, and a repeat is no help: a call made while the job runs is ignored,  and once the job has ended the uploaded backup is deleted, so a new call has nothing to read until the archive  is uploaded and parsed again. When the import is done, close it with &#x60;POST api/2.0/migration/finish&#x60;, which can  also mail the imported users their activation link.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **MigrationApiInfo** | body | [**MigrationApiInfo**](../api.md#model-migrationapiinfo) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The import has been queued; the response carries no content and the progress is read from &#x60;GET api/2.0/migration/status&#x60; | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The request body is missing or could not be read as a parse result | - | - |
| **403** | The caller is not a DocSpace administrator, or is not the portal owner and asked to import a user as &#x60;DocSpaceAdmin&#x60; who is not an administrator of this portal yet | - | - |
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

- **Content-Type**: application/json
- **Accept**: application/json
