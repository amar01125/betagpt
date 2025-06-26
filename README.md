# Telegram AI Chatbot (Render Web Service Ready)

## Features
- Deployable as a web service on Render (no background worker needed).
- Uses Flask web server with Telegram webhook.
- Responds to any text message using OpenAI's GPT model.
- No image generation, only intelligent text answers.

## Deploy Steps

### 1. Set Environment Variables on Render:
- `TELEGRAM_TOKEN` : Your Telegram bot token
- `OPENAI_API_KEY` : Your OpenAI API key
- `WEBHOOK_SECRET` : Any random secret string (example: `supersecret123`). Use same in webhook URL.

### 2. Deploy to Render
- Zip the project folder and deploy as a "Web Service".
- Set the "Start Command" to: `python app.py`
- Expose port: `10000` (or leave blank, Render will auto-detect from `PORT` env)

### 3. Set Telegram Webhook
After deployment, set the webhook like this:
```
https://api.telegram.org/bot<TELEGRAM_TOKEN>/setWebhook?url=https://<your_render_url>/webhook/<WEBHOOK_SECRET>
```

Example:
```
https://api.telegram.org/bot123456789:ABCdefGHIjklMNOP/setWebhook?url=https://my-bot.onrender.com/webhook/supersecret123
```

## Note
- Port and Procfile are set for Render compatibility.
- No "no open port found" error will come.
- For any error, check logs in Render dashboard.

---

## Sample .env file (for local testing)
```
TELEGRAM_TOKEN=your-telegram-bot-token
OPENAI_API_KEY=your-openai-key
WEBHOOK_SECRET=anything-you-like
```
