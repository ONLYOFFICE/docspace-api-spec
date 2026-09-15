# saveThirdParty

Referenced types are defined in the [full reference](../files.md).

> FolderStringWrapper saveThirdParty(ThirdPartyRequestDto)

`POST /api/2.0/files/thirdparty`

Connect a third-party account

Connects an account at a third-party storage service to the portal, or re-authenticates one that is already  connected, and returns the folder that now stands for its root. Send &#x60;providerId&#x60; to update an existing  account and omit it to connect a new one; the accepted &#x60;providerKey&#x60; values come from  &#x60;GET api/2.0/files/thirdparty/providers&#x60;. The credentials to send depend on the service: the OAuth services  take &#x60;token&#x60;, which is the authorization code from their consent screen and not an access token, while the  WebDAV family and SharePoint take &#x60;login&#x60; with &#x60;password&#x60;, plus &#x60;url&#x60; where the server address is not fixed.  Credentials are verified against the service before anything is stored, so a wrong password is refused and  nothing is saved. The caller needs the rights to create rooms, and the portal-wide third-party switch has to  be on, otherwise the call is refused. A new account is attached to the Rooms section and becomes available as  room storage for &#x60;POST api/2.0/files/rooms/thirdparty/{id}&#x60;. Connecting twice with the same title creates two  separate accounts.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **ThirdPartyRequestDto** | body | [**ThirdPartyRequestDto**](../files.md#model-thirdpartyrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The root folder of the connected account | [**FolderStringWrapper**](../files.md#model-folderstringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderStringWrapper**](../files.md#model-folderstringwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
