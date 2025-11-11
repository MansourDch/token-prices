# 🚀 DEPLOYMENT GUIDE - Token Prices Bot

## Quick Deploy to Render (5 Minutes)

### Step 1: Create Render Account
1. Go to: https://dashboard.render.com
2. Sign up with GitHub
3. Authorize Render to access your GitHub account

### Step 2: Create Web Service
1. Click "New +" → "Web Service"
2. Select "Deploy from a Git Repository"
3. Connect your GitHub: `https://github.com/MansourDch/token-prices`

### Step 3: Configure Service

**Settings:**
- Name: `token-prices-bot`
- Environment: `Node`
- Region: Choose closest to you
- Branch: `main`
- Build Command: `bun install`
- Start Command: `bun start`
- Plan: Free (or Starter for $7/month)

### Step 4: Add Environment Variables

Click "Environment" and add:

```
API_PROVIDER=coingecko
COINGECKO_API_KEY=
TOWNS_BOT_TOKEN=your_bot_token_here
DATABASE_URL=sqlite:///./price_data.db
PORT=3000
NODE_ENV=production
```

### Step 5: Deploy
1. Click "Create Web Service"
2. Render automatically deploys from GitHub
3. Wait 2-3 minutes for deployment to complete
4. You'll get a live URL: `https://token-prices-bot.onrender.com`

---

## Deploying to Railway (Alternative)

1. Go to: https://railway.app
2. Click "New Project"
3. Select "Deploy from GitHub Repo"
4. Connect `MansourDch/token-prices`
5. Add same environment variables
6. Deploy!

---

## After Deployment

### 1. Register Bot with Towns Protocol
1. Go to: https://developer.towns.com
2. Click "Create Bot"
3. Fill in:
   - Name: `Token Prices`
   - Webhook URL: `https://token-prices-bot.onrender.com/webhook`
   - Events: Message Create
4. Get your Bot Token
5. Add to .env: `TOWNS_BOT_TOKEN=your_token`
6. Redeploy on Render

### 2. Add to Your Towns Community
1. Go to your Web3 Towns community
2. Click Settings ⚙️
3. Find "Integrations" or "Bots"
4. Add bot token
5. Select channels
6. Save!

---

## Testing the Bot

Once added to Towns, users can test:

```
/price BTC
/price ETH
/alert BTC 50000 above
/history SOL 7
```

---

## Monitoring & Logs

### On Render:
- Go to your service dashboard
- Click "Logs" tab
- See real-time bot activity
- Monitor errors and performance

### Commands:
```bash
# View logs
render logs token-prices-bot

# Restart service
render restart token-prices-bot

# Check status
render status token-prices-bot
```

---

## Cost

- **Free Tier**: $0/month (limited uptime)
- **Starter Plan**: $7/month (always on)
- **Pro Plan**: $12+/month (better performance)

**Recommended**: Start with Free, upgrade if needed

---

## Troubleshooting

### Bot not responding
1. Check deployment status in Render
2. Verify environment variables are set
3. Check bot logs for errors
4. Ensure bot token is correct

### API errors
1. Verify CoinGecko API is accessible
2. Check rate limits
3. Switch to Binance API if needed

### Database errors
1. Check DATABASE_URL is set
2. Verify SQLite path is writable
3. Check disk space on Render

---

## Keeping Bot Running

### Auto-restart on failure
Render automatically restarts failed services

### Regular updates
1. Make code changes in GitHub
2. Push to main branch
3. Render auto-deploys (if enabled)

### Scaling up
- Upgrade to Starter/Pro plan
- Add database for persistence
- Set up monitoring alerts

---

## Next Steps

1. ✅ Deploy to Render (15 minutes)
2. ✅ Get bot token from Towns
3. ✅ Add bot to Web3 Towns
4. ✅ Test all commands
5. ✅ Monitor and iterate

**You're live!** 🎉
