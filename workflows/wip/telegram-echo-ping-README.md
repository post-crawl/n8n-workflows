# Telegram Echo Ping Workflow

This n8n workflow creates a simple Telegram bot that responds to any text message by echoing it back with "ping" appended.

## Prerequisites

1. **n8n instance** running and accessible
2. **Telegram Bot Token** from @BotFather

## Setup Instructions

### 1. Create a Telegram Bot

1. Open Telegram and search for @BotFather
2. Send `/newbot` command
3. Follow the prompts to create your bot
4. Save the bot token provided by BotFather

### 2. Import the Workflow

1. Open your n8n instance
2. Go to Workflows > Import
3. Import the `telegram-echo-ping-workflow.json` file

### 3. Configure the Workflow

1. **Add Telegram Credentials:**
   - Go to Credentials > New
   - Select "Telegram API"
   - Enter your bot token
   - Save the credentials

2. **Set up Webhook:**
   - Copy the webhook URL from the Telegram Webhook node
   - It will look like: `https://your-n8n-instance.com/webhook/telegram-webhook`

3. **Register Webhook with Telegram:**
   ```bash
   curl -X POST "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/setWebhook" \
        -H "Content-Type: application/json" \
        -d '{"url": "https://your-n8n-instance.com/webhook/telegram-webhook"}'
   ```

### 4. Activate the Workflow

1. Click the toggle switch to activate the workflow
2. Your bot is now ready to receive messages!

## Testing

1. Open Telegram and find your bot by its username
2. Send any text message
3. The bot will reply with your message + " ping"

### Example:
- You send: "Hello"
- Bot replies: "Hello ping"

## Troubleshooting

### Bot not responding?
- Check if the workflow is activated
- Verify webhook URL is correctly registered
- Check n8n logs for incoming webhook requests
- Ensure your n8n instance is publicly accessible

### Webhook registration failed?
- Verify your bot token is correct
- Ensure your n8n instance has a valid SSL certificate
- Check that the webhook URL is publicly accessible

## Customization Ideas

- Modify the appended text from "ping" to something else
- Add conditional responses based on keywords
- Integrate with other services (databases, APIs, etc.)
- Add user authentication or command handling

## Security Considerations

- Keep your bot token secret
- Consider adding rate limiting
- Implement user whitelisting if needed
- Monitor for abuse or spam

## Resources

- [Telegram Bot API Documentation](https://core.telegram.org/bots/api)
- [n8n Telegram Node Documentation](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.telegram/)
- [n8n Webhook Documentation](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/)