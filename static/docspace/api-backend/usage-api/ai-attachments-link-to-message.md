# aiAttachmentsLinkToMessage

Referenced types are defined in the [full reference](../aichat.md).

> AiSuccessResponse aiAttachmentsLinkToMessage(aiAttachmentsLinkToMessage\_request)

`POST /api/2.0/ai/attachments/link-to-message`

Link to message

Binds draft attachments to the chat message that owns them, after that message has been persisted, so that deleting the message removes them too. All three of &#x60;ids&#x60;, &#x60;messageId&#x60; and &#x60;threadId&#x60; are required, and the references are verified rather than trusted: an unknown message answers 404, a message that belongs to a different thread answers 400, and attachments that no longer exist answer 404 naming each missing ID. That verification exists because the underlying binding call skips unknown IDs silently, which used to report success for a link that had not happened. Drafts stay unbound until this succeeds.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAttachmentsLinkToMessage\_request** | body | [**aiAttachmentsLinkToMessage_request**](../aichat.md#model-aiattachmentslinktomessage-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the attachments are now bound to the message. | [**AiSuccessResponse**](../aichat.md#model-aisuccessresponse) | - |
| **400** | The attachment or message reference is malformed. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The message or the attachment does not exist. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../aichat.md#model-aisuccessresponse)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
