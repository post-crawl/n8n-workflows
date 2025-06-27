# WhatsApp Echo Ping Bot Workflow

This n8n workflow creates a WhatsApp bot that automatically responds to incoming messages by echoing them back with " ping" appended to the end.

## Description

When someone sends a message to your WhatsApp Business number, this workflow:
1. Receives the message via webhook
2. Processes the text and appends " ping" to it
3. Sends the modified message back to the sender
4. Acknowledges the webhook request

For example:
- User sends: "Hello"
- Bot responds: "Hello ping"

## Prerequisites

- n8n instance (self-hosted or cloud)
- WhatsApp Business Account
- Meta Business Account
- WhatsApp Business API access
- Phone number registered with WhatsApp Business
- Valid WhatsApp Business API credentials

## Setup Instructions

### 1. Set Up WhatsApp Business API

1. Create a Meta Business Account at [business.facebook.com](https://business.facebook.com)
2. Create a WhatsApp Business App in the Meta Developer Console
3. Add a phone number to your WhatsApp Business Account
4. Generate a permanent access token for your app
5. Note down your:
   - Phone Number ID
   - WhatsApp Business Account ID
   - Access Token
   - App Secret (for webhook verification)

### 2. Import the Workflow

1. Copy the contents of `whatsapp-echo-ping-workflow.json`
2. In n8n, go to Workflows → Add Workflow → Import from JSON
3. Paste the JSON content and click Import

### 3. Configure WhatsApp Credentials

1. In the workflow, click on the "Send WhatsApp Message" node
2. Click on "Create New Credential"
3. Enter your WhatsApp Business API credentials:
   - Access Token
   - Phone Number ID
4. Save the credentials

### 4. Configure the Webhook

1. In the workflow, click on the "WhatsApp Webhook" node
2. Copy the Production webhook URL (it will look like: `https://your-n8n-instance.com/webhook/whatsapp-bot-webhook`)
3. If using n8n cloud, copy the Test webhook URL for testing

### 5. Register the Webhook with WhatsApp

1. Go to your WhatsApp App in the Meta Developer Console
2. Navigate to WhatsApp → Configuration → Webhooks
3. Add your webhook URL
4. Enter a Verify Token (any string you choose)
5. Subscribe to the following webhook fields:
   - `messages`
   - `message_status` (optional, for delivery reports)

### 6. Handle Webhook Verification

The workflow includes code to handle WhatsApp's webhook verification process automatically.

### 7. Activate the Workflow

1. Click the "Active" toggle in n8n to activate the workflow
2. Your WhatsApp Echo Ping bot is now ready!

## Testing

1. Send a message to your WhatsApp Business number
2. You should receive the same message back with " ping" appended
3. Check the workflow executions in n8n to see the data flow

## Troubleshooting

### Bot not responding
- Verify the webhook URL is correctly registered in Meta Developer Console
- Check that the workflow is active
- Ensure your WhatsApp Business API credentials are valid
- Check n8n execution logs for errors

### Webhook verification failing
- Make sure the webhook URL is accessible from the internet
- Check that the verification code in the Process Message node is working
- Verify your n8n instance allows incoming webhooks

### Authentication errors
- Regenerate your access token if it has expired
- Verify your Phone Number ID is correct
- Check that your WhatsApp Business Account is properly verified

### Message not sending
- Ensure the recipient has initiated conversation with your business (24-hour window rule)
- Check that your phone number is registered and active
- Verify you're not hitting rate limits

## Customization Ideas

- Modify the appended text from " ping" to something else
- Add conditional logic based on message content
- Integrate with other services (databases, APIs, etc.)
- Add media handling (images, documents, etc.)
- Implement a menu system with quick replies
- Add user session management
- Create automated responses based on keywords
- Add language detection and multi-language support

## Security Considerations

- Keep your WhatsApp API credentials secure
- Use environment variables for sensitive data in production
- Implement rate limiting to prevent abuse
- Validate and sanitize incoming messages
- Consider implementing user allowlists for sensitive operations
- Enable webhook signature verification for production use
- Monitor for suspicious activity or spam

## WhatsApp Business API Considerations

- **24-hour window**: You can only send messages to users who have messaged you within the last 24 hours
- **Message templates**: For messages outside the 24-hour window, use approved message templates
- **Rate limits**: Be aware of WhatsApp's rate limiting policies
- **Compliance**: Ensure your bot complies with WhatsApp Business Policy
- **Opt-out handling**: Implement proper opt-out mechanisms
- **Privacy**: Handle user data according to privacy regulations

## Resources

- [WhatsApp Business API Documentation](https://developers.facebook.com/docs/whatsapp)
- [n8n WhatsApp Node Documentation](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.whatsapp/)
- [Meta for Developers](https://developers.facebook.com/)
- [WhatsApp Business Policy](https://www.whatsapp.com/legal/business-policy)
- [n8n Webhook Documentation](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/)