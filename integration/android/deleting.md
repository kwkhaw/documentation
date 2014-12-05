# Deleting messages

The Layer SDK supports the deletion of both conversations and messages. Deletion of a conversation deletes the conversation object and all associated messages. Deletion of a messages only affects that individual message and it's parts.

The Layer SDK supports 2 deletion modes: Local and All Participants:

layerClient.deleteMessage will remove the deleted object from ONLY the current device. This is not a synchronized delete, rather just a delete of the object from the local DB. So please note, if the user logs out and logs back in, the deleted object will reappear as we dump the local db on logout and do a complete sync on next login.

layerClient.deleteConversation will tombstone the deleted object from all devices of all participants. The deleted object can be considered to be completely deleted.

```java
// Deletes a messages.
layerClient.deleteMessage(Message message, DeletionMode deletionMode);

// Deletes a conversation.
layerClient.deleteConversation(Conversation conversation, DeletionMode deletionMode);
```