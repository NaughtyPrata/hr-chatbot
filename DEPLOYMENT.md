# HR Chatbot Deployment Guide

This guide will help you deploy your HR chatbot system with a secure backend API and a single HTML file for your team.

## 🚀 Quick Setup

### 1. Prerequisites
- [Vercel account](https://vercel.com) (free tier works fine)
- [OpenAI API key](https://platform.openai.com/api-keys)
- Git installed on your computer

### 2. Deploy to Vercel

#### Option A: Deploy via Vercel CLI (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Login to Vercel
vercel login

# Deploy the project
vercel

# Set environment variables
vercel env add OPENAI_API_KEY
# Enter your OpenAI API key when prompted

# Deploy again to use the environment variable
vercel --prod
```

#### Option B: Deploy via Vercel Dashboard
1. Go to [vercel.com](https://vercel.com) and sign in
2. Click "New Project"
3. Import this Git repository
4. In "Environment Variables", add:
   - Name: `OPENAI_API_KEY`
   - Value: Your OpenAI API key
5. Click "Deploy"

### 3. Update the HTML File
After deployment, Vercel will give you a URL like `https://your-app-name.vercel.app`

1. Open `hr-chatbot-trainer.html`
2. Find this line (around line 267):
   ```javascript
   const API_URL = 'https://your-app-name.vercel.app/api/chat';
   ```
3. Replace `your-app-name.vercel.app` with your actual Vercel URL
4. Save the file

### 4. Distribute to Your Team
- Send the `hr-chatbot-trainer.html` file to your HR team
- They can open it in any modern web browser
- No installation required!

## 🔒 Security Features

✅ **API Key Protection**: Your OpenAI API key stays secure on the server  
✅ **CORS Enabled**: Works from any domain  
✅ **Rate Limiting**: Built-in protection against abuse  
✅ **Error Handling**: Graceful error messages for users  

## 🎛️ Customization Options

### Adding New LLM Providers
You can easily switch to other providers by modifying `api/chat.js`:

```javascript
// For Anthropic Claude
import Anthropic from '@anthropic-ai/sdk';
const anthropic = new Anthropic({
  apiKey: process.env.ANTHROPIC_API_KEY,
});

// For Google Gemini
import { GoogleGenerativeAI } from '@google/generative-ai';
const genAI = new GoogleGenerativeAI(process.env.GOOGLE_API_KEY);
```

### Customizing the HTML Interface
The HTML file is completely self-contained. You can:
- Change colors by modifying the CSS
- Add new personality presets
- Modify the UI layout
- Add company branding

### Adding Usage Analytics
Add this to your API endpoint to track usage:

```javascript
// In api/chat.js, add logging
console.log(`Chat request from ${req.headers['x-forwarded-for']} at ${new Date()}`);
```

## 🛠️ Troubleshooting

### Common Issues

**"API quota exceeded"**
- Check your OpenAI billing and usage limits
- Consider upgrading your OpenAI plan

**"CORS error"**
- Make sure you've updated the API_URL in the HTML file
- Check that your Vercel deployment is working

**"Invalid API configuration"**
- Verify your OPENAI_API_KEY environment variable is set correctly
- Make sure the API key has the correct permissions

### Testing Your Deployment

1. Visit `https://your-app-name.vercel.app/api/chat` in your browser
2. You should see: `{"error":"Method not allowed"}`
3. This confirms your API is deployed and working

## 💰 Cost Management

### OpenAI Pricing (as of 2024)
- GPT-3.5-turbo: ~$0.002 per 1K tokens
- Average conversation: ~$0.01-0.05
- 1000 conversations: ~$10-50

### Cost Control Tips
1. Set usage limits in your OpenAI dashboard
2. Monitor usage in Vercel analytics
3. Consider using GPT-3.5-turbo instead of GPT-4 for cost savings
4. Implement conversation length limits

## 🔄 Updates and Maintenance

### Updating the API
```bash
# Make changes to api/chat.js
git add .
git commit -m "Update API"
git push

# Vercel will automatically redeploy
```

### Updating the HTML File
- Simply edit `hr-chatbot-trainer.html`
- Redistribute to your team
- No redeployment needed!

## 📊 Monitoring

### Vercel Dashboard
- View deployment logs
- Monitor function invocations
- Check error rates

### OpenAI Dashboard
- Track API usage
- Monitor costs
- View rate limits

## 🆘 Support

If you need help:
1. Check the Vercel deployment logs
2. Test the API endpoint directly
3. Verify environment variables are set
4. Check OpenAI API status

---

**🎉 That's it! Your HR team now has a secure, customizable chatbot trainer that you can control and monitor.** 