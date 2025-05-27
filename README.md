# HR Chatbot Trainer

A secure, self-contained HR chatbot training system that allows your HR team to create personalized AI assistants without exposing API keys.

## 🎯 Problem Solved

Your HR team wants to experiment with AI chatbots, but you can't give them direct access to API keys. This solution provides:

- **🔒 Secure Backend**: API keys stay on your server
- **📱 Simple Frontend**: Single HTML file your team can use anywhere
- **🎭 Personality Customization**: Easy-to-use interface for creating different chatbot personalities
- **💰 Cost Control**: You maintain full control over usage and costs

## 🏗️ Architecture

```
HR Team's Computer          Your Vercel Server          OpenAI
┌─────────────────┐        ┌─────────────────┐        ┌─────────────┐
│                 │        │                 │        │             │
│ HTML File       │───────▶│ API Endpoint    │───────▶│ GPT Model   │
│ (No API Keys)   │        │ (Secure Keys)   │        │             │
│                 │        │                 │        │             │
└─────────────────┘        └─────────────────┘        └─────────────┘
```

## 🚀 Quick Start

1. **Deploy the backend** (5 minutes):
   ```bash
   npm install -g vercel
   vercel login
   vercel
   vercel env add OPENAI_API_KEY
   vercel --prod
   ```

2. **Update the HTML file** with your Vercel URL

3. **Distribute** `hr-chatbot-trainer.html` to your team

📖 **[Full Deployment Guide](DEPLOYMENT.md)**

## ✨ Features

- **🎭 5 Personality Presets**: Friendly, Professional, Mentor, Casual, Detailed
- **💬 Conversation Memory**: Maintains context throughout the chat
- **📱 Responsive Design**: Works on desktop, tablet, and mobile
- **🔄 Real-time Chat**: Instant responses with loading indicators
- **🎨 Beautiful UI**: Modern, professional interface
- **🛡️ Error Handling**: Graceful error messages and recovery

## 🎭 Personality Examples

**Friendly & Warm**: "Hi there! 😊 I'm so excited to help you today! What's on your mind?"

**Strictly Professional**: "Good day. I am here to assist you with your HR-related inquiries. How may I help you?"

**Mentor & Coach**: "That's a great question! Before I give you an answer, let me ask - what do you think might be the best approach here?"

## 🔧 Customization

### Adding New Personalities
Edit the `personalities` object in the HTML file:

```javascript
const personalities = {
  custom: "You are a [describe personality here]...",
  // ... existing personalities
};
```

### Changing LLM Provider
Modify `api/chat.js` to use different providers:
- OpenAI GPT-4
- Anthropic Claude
- Google Gemini
- Local models

### Styling
The HTML file contains all CSS inline - easy to customize colors, fonts, and layout.

## 💰 Cost Estimates

- **GPT-3.5-turbo**: ~$0.01-0.05 per conversation
- **1000 conversations/month**: ~$10-50
- **Vercel hosting**: Free tier sufficient for most use cases

## 🛡️ Security

- ✅ API keys never leave your server
- ✅ CORS enabled for cross-origin requests
- ✅ Input validation and sanitization
- ✅ Rate limiting protection
- ✅ Error handling without exposing internals

## 📊 Monitoring

Track usage through:
- Vercel function logs
- OpenAI usage dashboard
- Custom analytics (optional)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

MIT License - feel free to use this in your organization!

---

**🎉 Give your HR team the power of AI while keeping your API keys secure!** 