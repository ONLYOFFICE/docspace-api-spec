# getBackupThirdPartyAccount

Referenced types are defined in the [full reference](../files.md).

> ThirdPartyFolderWrapper getBackupThirdPartyAccount()

`GET /api/2.0/files/thirdparty/backup`

Get the third-party backup folder

Returns the folder of the third-party storage account the portal keeps for backups, so a caller can check  where scheduled and manual backups are written. There is at most one such account per portal, connected by an  administrator through &#x60;POST api/2.0/files/thirdparty/backup&#x60;, and it is deliberately kept out of the personal  list of &#x60;GET api/2.0/files/thirdparty&#x60;. Any authenticated member may ask, and the call is read-only. The body  is &#x60;null&#x60;, with a successful status, in two situations the answer does not distinguish: no backup account has  been connected, and the caller has no read access to the folder of the one that is. When a folder does come  back, its &#x60;id&#x60; is the string ID of a third-party folder and can be used with the folder operations that accept  one, and its &#x60;title&#x60; is the title the account was saved under. Connecting a different account through the  backup operation replaces this one rather than adding a second, and  &#x60;DELETE api/2.0/files/thirdparty/{providerId}&#x60; removes it.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The root folder of the backup storage account, or null when none is connected | [**ThirdPartyFolderWrapper**](../files.md#model-thirdpartyfolderwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ThirdPartyFolderWrapper**](../files.md#model-thirdpartyfolderwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
