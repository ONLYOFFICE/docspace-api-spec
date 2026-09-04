# setKeys

Referenced types are defined in the [full reference](../files.md).

> EncryptionKeyArrayWrapper setKeys(EncryptionKeyRequestDto)

`POST /api/2.0/privacyroom/keys`

Creates and sets encryption keys for the user.

Creates and sets encryption keys for the user.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **EncryptionKeyRequestDto** | body | [**EncryptionKeyRequestDto**](../files.md#model-encryptionkeyrequestdto) | The request object containing public and private key information. | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **201** | The encryption key is created. Answered 200 before DocSpace 4.0; the response body is unchanged | [**EncryptionKeyArrayWrapper**](../files.md#model-encryptionkeyarraywrapper) | - |
| **400** | The key material is missing, blank or too large to be stored | - | - |
| **409** | A key with the same identifier already exists | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EncryptionKeyArrayWrapper**](../files.md#model-encryptionkeyarraywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
