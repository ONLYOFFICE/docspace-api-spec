# getRoomIndexExport

Referenced types are defined in the [full reference](../files.md).

> DocumentBuilderTaskWrapper getRoomIndexExport()

`GET /api/2.0/files/rooms/indexexport`

Get the room index export

Returns the state of the index export of the calling account, the job started by  &#x60;POST api/2.0/files/rooms/{id}/indexexport&#x60;. The record is not addressed by room: there is at most one per  account, and the answer describes the latest export whichever room it was started for. When the account has  never started one, or its record was cancelled, the body is null rather than an error, so null is the normal  way of saying that there is nothing to report. While the job runs, &#x60;percentage&#x60; moves in coarse steps instead  of smoothly, which makes it a rough hint rather than a measure of the remaining time; &#x60;isCompleted&#x60; is the  field to wait on, and it is also set for a job that failed or was cancelled, so read &#x60;status&#x60; to tell the  outcomes apart and &#x60;error&#x60; for the message. After a successful build, &#x60;resultFileId&#x60;, &#x60;resultFileName&#x60; and  &#x60;resultFileUrl&#x60; point to the spreadsheet saved in the My documents section of the caller. The record survives  completion and is replaced only by the next export.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state of the export, or null when the account has none | [**DocumentBuilderTaskWrapper**](../files.md#model-documentbuildertaskwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocumentBuilderTaskWrapper**](../files.md#model-documentbuildertaskwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
