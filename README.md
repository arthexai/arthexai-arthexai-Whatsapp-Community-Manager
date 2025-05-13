# AI-Powered WhatsApp Bot using Python and Flask

This project demonstrates building an AI-powered WhatsApp bot using **Python**, **Flask**, **Meta’s WhatsApp Cloud API**, and **OpenAI’s GPT model**. The bot can receive WhatsApp messages, process them using AI, and send smart responses — all via webhooks.

## 🚀 Features

- Pure **Python + Flask** backend
- **Two-way WhatsApp communication** using Meta’s Cloud API
- **Webhook setup** with token verification
- **AI-generated replies** using OpenAI GPT-3.5
- Uses **ngrok static domains** for local development
- Simple `.env`-based configuration

## 📦 Environment Configuration

Create a `.env` file in the root directory and add the following keys:

```env
ACCESS_TOKEN=your_whatsapp_cloud_api_access_token
YOUR_PHONE_NUMBER=your_registered_whatsapp_number
APP_ID=your_meta_app_id
APP_SECRET=your_meta_app_secret
RECIPIENT_WAID=recipient_whatsapp_id
VERSION=v18.0
PHONE_NUMBER_ID=your_phone_number_id
VERIFY_TOKEN=your_custom_verification_token
OPENAI_API_KEY=your_openai_key
```

## 🧪 Steps to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/your-project.git
cd your-project
```

### 2. Create and activate a virtual environment

For Windows
```bash
python -m venv venv
venv\Scripts\activate
```
For macOS/Linux
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start Flask Server

```bash
python run.py
```

### 5. Run `ngrok` on port 8000 with a static domain

```bash
ngrok http 8000 --domain=your-static-subdomain.ngrok-free.app
```

### 6. Configure Webhooks in Meta Developer Portal

- **Callback URL**: `https://your-static-subdomain.ngrok-free.app/webhook`
- **Verify Token**: Same as `VERIFY_TOKEN` in `.env`
- Subscribe to `messages` and `message_deliveries`

## 💬 AI Response with OpenAI

Use OpenAI’s Chat API to generate intelligent replies:

```python
import openai

openai.api_key = os.getenv("OPENAI_API_KEY")

def get_ai_response(prompt):
    res = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )
    return res["choices"][0]["message"]["content"]
```

## 🛰️ Deployment Options

- Use **Render**, **Railway**, or **VPS** for production
- Replace `ngrok` with HTTPS domain from your hosting
- Configure environment variables in the production environment

## 📌 Notes

- Test numbers must be added in Meta for WhatsApp sandbox use.
- You can upgrade to production after business verification.

## 🪪 License

MIT License. You are free to use, distribute, and modify the project.
