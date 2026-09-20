# aiAttachmentsSaveFile

Referenced types are defined in the [full reference](../aichat.md).

> AiAttachment aiAttachmentsSaveFile(aiAttachmentsSaveFile\_request)

`POST /api/2.0/ai/attachments/save-file`

Save file

Stores one file attachment as a draft and returns it, so its ID can be attached to a message later. &#x60;input&#x60; carries the host &#x60;path&#x60; - the DocSpace entry ID the AI backend resolves server-side - the text &#x60;content&#x60; already extracted from that file, the ONLYOFFICE numeric file &#x60;type&#x60;, and optionally a &#x60;title&#x60;; the text is what the model reads, so this operation does not open the file itself. Archives are refused outright, whatever their declared name says. Drafts are not bound to a conversation until &#x60;POST api/2.0/ai/attachments/link-to-message&#x60; is called, so an unlinked draft outlives the round that created it.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsSaveFile\_request** | body | [**aiAttachmentsSaveFile_request**](../aichat.md#model-aiattachmentssavefile-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The stored draft, whose ID links it to a message later. | [**AiAttachment**](../aichat.md#model-aiattachment) | - |
| **400** | The attachment payload is malformed. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiAttachment**](../aichat.md#model-aiattachment)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
