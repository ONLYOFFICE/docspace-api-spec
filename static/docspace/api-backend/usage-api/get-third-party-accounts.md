# getThirdPartyAccounts

Referenced types are defined in the [full reference](../files.md).

> ThirdPartyParamsArrayWrapper getThirdPartyAccounts()

`GET /api/2.0/files/thirdparty`

Get the third-party accounts

Lists the third-party storage accounts the caller has connected, one element per account, with the title it  was saved under, the storage service behind it and the portal section it is attached to. Accounts connected by  other members are not included, and neither is the portal backup account of  &#x60;GET api/2.0/files/thirdparty/backup&#x60;, even for an administrator. The &#x60;providerId&#x60; of an element is the value  to send to &#x60;DELETE api/2.0/files/thirdparty/{providerId}&#x60; and, as &#x60;providerId&#x60; in  &#x60;POST api/2.0/files/thirdparty&#x60;, the way to re-authenticate that same account instead of connecting a new one.  Credentials are never disclosed: &#x60;auth_data&#x60; comes back empty for every element. An element with  &#x60;roomsStorage&#x60; set is available as storage for a room, while &#x60;corporate&#x60; marks an account inherited from the  legacy Common section. The call is read-only, returns a plain array with no paging and no contractual  ordering, and answers with an empty array when the caller has connected nothing. To browse the content of an  account, take the folder ID from the answer of the operation that connected it or from  &#x60;GET api/2.0/files/@root&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The third-party accounts the caller has connected | [**ThirdPartyParamsArrayWrapper**](../files.md#model-thirdpartyparamsarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ThirdPartyParamsArrayWrapper**](../files.md#model-thirdpartyparamsarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
