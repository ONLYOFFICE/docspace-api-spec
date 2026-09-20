# startFileConversion

Referenced types are defined in the [full reference](../files.md).

> ConversationResultArrayWrapper startFileConversion(fileId, CheckConversionRequestDto)

`PUT /api/2.0/files/file/{fileId}/checkconversion`

Start file conversion

Queues the conversion of a file into the portal&#39;s own editable format and answers with the conversion entry  the caller is to poll. The whole body may be omitted, in which case the defaults apply. &#x60;outputType&#x60; names the  target format and, left empty, the portal&#39;s default for that kind of document is used; &#x60;password&#x60; unlocks a  protected source file; &#x60;version&#x60; converts an older version instead of the current one. &#x60;createNewIfExist&#x60;  decides where the result goes: with &#x60;true&#x60; a new file is created beside the source, while with &#x60;false&#x60;, the  default, the converted file that already exists is replaced. &#x60;sync&#x3D;true&#x60; converts inside the request and  answers with the finished result instead of a queue entry, which is only sensible for small documents.  Otherwise poll &#x60;GET api/2.0/files/file/{fileId}/checkconversion&#x60; until &#x60;progress&#x60; reaches 100 and take the  converted file from &#x60;file&#x60;. Only formats the portal has to convert are accepted; anything already editable,  and anything it cannot convert, is answered without work being queued or rejected as an invalid request. The  caller needs read access to the file. The call is mutating and not idempotent.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **Integer** (int32) | The file to convert. | [required] [example: 1] |
| **CheckConversionRequestDto** | body | [**CheckConversionRequestDto**](../files.md#model-checkconversionrequestdto) | The parameters of the conversion. The whole body may be omitted, in which case the defaults of the portal  apply. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The conversion entry to poll, or the finished result when the conversion is synchronous | [**ConversationResultArrayWrapper**](../files.md#model-conversationresultarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ConversationResultArrayWrapper**](../files.md#model-conversationresultarraywrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **fileId** | path | **String** | The file to convert. | [required] [example: 1] |
| **ThirdPartyCheckConversionRequestDto** | body | [**ThirdPartyCheckConversionRequestDto**](../files.md#model-thirdpartycheckconversionrequestdto) | The parameters of the conversion. The whole body may be omitted, in which case the defaults of the portal  apply. | [optional] |


## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
