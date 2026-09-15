# setFileExternalLink

Referenced types are defined in the [full reference](../files.md).

> FileShareWrapper setFileExternalLink(id, FileLinkRequest)

`PUT /api/2.0/files/file/{id}/links`

Set a file external link

Creates an external link to a file, or changes or revokes an existing one, and answers with the link as it now  stands. &#x60;linkId&#x60; decides which: an identifier that is not yet in use, the empty one included, creates a link,  while the identifier of an existing link rewrites it, so the whole set of parameters is applied every time and  a field left out is reset rather than kept. &#x60;access&#x60; carries the rights the link grants, and &#x60;access&#x60; set to  the value that denies everything revokes the link instead - the answer is then empty, and a revoked primary  link is not recreated by a later read. &#x60;title&#x60; names the link for the people who manage it, &#x60;expirationDate&#x60;  limits its lifetime and is refused when it lies more than a few years ahead, &#x60;password&#x60; asks visitors for a  secret, &#x60;denyDownload&#x60; leaves them with viewing only, &#x60;internal&#x60; admits signed-in members alone, and  &#x60;primary&#x3D;true&#x60; makes it the primary link of the file. The caller needs the right to share the file and is  otherwise refused, an unknown file being answered as not found. The call is mutating.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The file the link points at. | [required] [example: 1] |
| **FileLinkRequest** | body | [**FileLinkRequest**](../files.md#model-filelinkrequest) | The settings of the link. They are applied in full, so a field left out is reset rather than kept. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The link as it now stands, or nothing when it was revoked | [**FileShareWrapper**](../files.md#model-filesharewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FileShareWrapper**](../files.md#model-filesharewrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
