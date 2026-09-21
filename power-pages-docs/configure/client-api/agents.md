---
title: Client API for Copilot Studio Agents (Preview)
description: Learn how to use the Power Pages Client API to send messages and invoke events in Copilot Studio agents. Explore syntax, callbacks, responses, and errors.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Use the Client API with Copilot Studio agents (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.agent object

Use the Power Pages Client API `$pages.agent` object and its [SendActivity method](#sendactivity-method) to send messages or invoke events in the Microsoft Copilot Studio agent available to the current user. Response and error callbacks help the site handle the agent's results.

## SendActivity method

The `SendActivity` method sends a message or invokes an event in the specified Copilot Studio agent and uses callback functions to handle responses and errors.

### SendActivity method syntax

```javascript
$pages.agent.SendActivity(
    agentSchemaName: string,
    inputActivity: object,
    responseSubscriber: function,
    errorSubscriber: function
);
```

### SendActivity method parameters

| Parameter Name | Type | Description |
|----------------|----- |-------------|
| `agentSchemaName` | String | Schema name of the bot to which the activity is sent. |
| `inputActivity`   | Object | Object containing the text or event to send to the bot. |
| `responseSubscriber` | function | Callback function that runs when the agent sends a response. |
| `errorSubscriber` | function | Callback function that handles errors. |

The `SendActivity` method returns `void`. To receive a response from the agent, pass a `responseSubscriber` callback function. The method invokes this callback when the agent sends a response. Pass an `errorSubscriber` callback function to handle errors.


### SendActivity response properties

Response object from agent received in the following format:

| Name | Type | Description |
|------|----- |-------------|
| `type` | String | Type of the activity such as message. |
| `text` | String | Optional, message from agent. |
| `textFormat` | String | Optional, format of the message's text such as markdown, plain, or XML. |
| `Id` | String | ID that uniquely identifies the activity. |
| `From` | Object | Specifies the sender of the activity (includes id, name (optional), and role information).|
| `Conversation` | Object | Contains the ID of the conversation to which the activity belongs. |
| `InputHint` | String | Optional, indicates whether the bot is accepting, expecting, or ignoring user input. |
| `replyToId` | String | ID of the reply message.|


## Examples

The following examples show how to define response and error callbacks and use `SendActivity` to send a message or invoke an event.

| Example | Description |
|---------|-------------|
| [Define response and error callbacks](#define-response-and-error-callbacks) | Defines the `responseSubscriber` and `errorSubscriber` callback functions that handle agent responses and errors. |
| [Send message to agent](#send-message-to-agent) | Sends a `Hello!` text activity to the specified agent and uses callback functions to handle the response or an error. |
| [Invoke client event](#invoke-client-event) | Invokes the `AgentEvent` client event and passes a key-value payload to the agent. |

### Define response and error callbacks

Define the `responseSubscriber` and `errorSubscriber` callback functions to handle agent responses and errors.

```javascript
const responseSubscriber = (response) => {
    // Replace with your response handling.
    console.log('Agent response:', response);
};

const errorSubscriber = (error) => {
    // Replace with your error handling.
    console.error('Error:', error);
};

// Replace with your agent schema name.
const agentSchemaName = 'agent SchemaName';
```

### Send message to agent

This example sends a `Hello!` text activity to the specified agent and uses callback functions to handle the response or an error.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const inputActivity = {
        text: 'Hello!' // Message to the agent.
    };

    $pages.agent.SendActivity(agentSchemaName, inputActivity, responseSubscriber, errorSubscriber);
});
```

### Invoke client event

This sample invokes the `AgentEvent` client event and passes a key-value payload to the agent.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const inputActivity = {
        name: 'AgentEvent', // The name of the event to be invoked.
        value: { key1: 'value1', key2: 'value2' } // Open-ended value used to carry additional data or payloads necessary for specific agent operations or responses.
    };

    $pages.agent.SendActivity(agentSchemaName, inputActivity, responseSubscriber, errorSubscriber);
});
```

## Error messages

Here are possible error messages that users can encounter and their potential causes.

| **Error type** | **Cause** | **Error message for user** |
|----|----|----|
| Agent schema validation | Invalid bot schema name provided or user doesn't have access permissions to the agent | `Invalid bot schema name or access denied. Check the bot schema name and try again.` |
| Fetch token error | An error occurred while fetching the direct line token | `Something went wrong while fetching the token. Please try again.` |
| Posting activity error (retry) | An error occurred while posting the activity and a retry is needed. | `Something went wrong while posting the activity: retry.` |
| Posting activity error (timeout) | Timed out while waiting for outgoing message or postActivity | `Timed out while posting activity: Please retry.` |
| Posting activity error (invalid activity) | The input activity doesn't have text or a name to invoke the event. | `Invalid activity: At least one of text, name, or attachments must be provided.` |
| Posting activity error (user ID not found or token not found) | Token isn't found in session storage or user ID isn't found in token | `Error retrieving user ID: {error message}` |
| Posting activity error (general) | An unspecified error occurred while posting the activity | `Something went wrong while posting the activity: Please try again.` |
| Direct line connection error | An error occurred while creating direct line connection with the bot. | `Something went wrong while creating direct line connection: Please try again.`|
| General error | An unexpected error that doesn't fall into the above categories | `An unexpected error occurred while sending activity: Please try again.` |

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
