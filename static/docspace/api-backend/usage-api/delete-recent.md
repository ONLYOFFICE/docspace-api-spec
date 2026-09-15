# deleteRecent

Referenced types are defined in the [full reference](../files.md).

> deleteRecent(BaseBatchRequestDto)

`DELETE /api/2.0/files/recent`

Delete recent files

Removes the listed entries from the Recent section of the calling account, the history of opened files that  &#x60;GET api/2.0/files/recent&#x60; returns. Nothing is deleted from storage and no other member&#39;s history is touched;  access to the entries is not checked at all, so a file the caller can no longer read can still be cleared from  their own history. Only numeric file ids are honoured, so a file on a connected third-party account cannot be  cleared this way, and folder ids are accepted but change nothing because the section lists files only. The  answer carries no body and reports nothing about how many entries were found: an empty request and an id that  was never in the section are accepted alike. Repeating the call is safe, but an entry returns the next time  the file is opened or &#x60;POST api/2.0/files/file/{fileId}/recent&#x60; is called for it. To hide the whole section  instead, call &#x60;PUT api/2.0/files/displayrecent&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **BaseBatchRequestDto** | body | [**BaseBatchRequestDto**](../files.md#model-basebatchrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Empty answer: the listed entries no longer appear in the Recent section | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
