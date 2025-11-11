# 🔑 API Keys & Market Data Integration Guide

## Quick Answer: YES, You Need API Keys!

✅ **YES** - The token-prices bot requires API keys from market data providers to fetch real-time cryptocurrency prices.

❌ **NOT** - You cannot use free public data without proper APIs - they're too limited and unreliable for production bots.

---

## 📊 Required APIs for the Bot

### **1. Primary Price Data API (REQUIRED)**

You must choose ONE of these providers:

#### **Option A: CoinGecko API** ⭐ RECOMMENDED

**Cost**: Free + Premium tiers

**Pricing**:
- Free tier: 10-15 calls/second
- Pro: $0.50-$2.00/month
- Enterprise: Custom pricing

**Features**:
- ✅ No credit card required for free tier
- ✅ 10,000+ cryptocurrencies
- ✅ Historical data (free)
- ✅ Market cap, volume, price change
- ✅ Excellent documentation
- ✅ High reliability

**API Key**: NO KEY NEEDED for free tier!

**Website**: https://www.coingecko.com/en/api

**Documentation**: https://docs.coingecko.com/reference/intro

---

#### **Option B: CoinMarketCap API**

**Cost**: Free + Paid tiers

**Pricing**:
- Free tier: 333 calls/day
- Basic: $99/month (10,000 calls/day)
- Professional: $199/month (50,000 calls/day)
- Enterprise: Custom

**Features**:
- ✅ 20,000+ cryptocurrencies
- ✅ Professional data
- ✅ Real-time prices
- ✅ Market cap & volume
- ✅ Ratings and filters

**API Key**: YES - Required (get from dashboard)

**Website**: https://coinmarketcap.com/api/

**Setup**:
1. Sign up at https://coinmarketcap.com/api
2. Get your free API key
3. Add to .env file

**Environment Variable**:
```
COINMARKETCAP_API_KEY=your_api_key_here
```

---

#### **Option C: Binance Public API** ⭐ BEST FOR VOLUME/LIQUIDITY

**Cost**: FREE (with rate limits)

**Pricing**:
- Free: 1,200 requests/minute
- No account needed

**Features**:
- ✅ Real exchange data
- ✅ No API key required
- ✅ Extremely reliable
- ✅ Low latency
- ✅ Order book data
- ✅ Trading data

**API Key**: NO KEY NEEDED

**Website**: https://www.binance.com/en/binance-api

**Base URL**: https://api.binance.com/api/v3

---

#### **Option D: Kraken API**

**Cost**: Free tier available

**Pricing**:
- Free: 15 requests/second
- Starter: $27/month
- Intermediate: $54/month
- Pro: $108/month

**Features**:
- ✅ Exchange trading data
- ✅ OHLCV candlestick data
- ✅ Reliable and secure

**Website**: https://docs.kraken.com/rest/

---

## 🏆 RECOMMENDED SETUP

### **Best Free Option: CoinGecko + Binance**

```
Primary API: CoinGecko (Free)
├─ Price data
├─ Market cap
├─ 24h change
└─ Historical data

Secondary API: Binance (Backup)
├─ Real exchange prices
├─ Trading volume
└─ Order book data
```

**Why?**
- ✅ Completely FREE (no credit card)
- ✅ No API keys needed
- ✅ Highly reliable
- ✅ Covers 20,000+ tokens
- ✅ Production-ready

---

## 🚀 Setup Instructions

### **Step 1: Choose Your API Provider**

**For Beginners (FREE)**:
```bash
# Use CoinGecko (no setup needed!)
API_PROVIDER=coingecko
COINGECKO_API_KEY=  # Leave empty for free tier
```

**For Production (Small Monthly Cost)**:
```bash
# Use CoinMarketCap
API_PROVIDER=coinmarketcap
COINMARKETCAP_API_KEY=your_api_key_here
```

### **Step 2: Get Your API Key (if needed)**

#### **CoinMarketCap Setup**:
1. Go to: https://coinmarketcap.com/api
2. Click "Get free API key"
3. Sign up with email
4. Copy your API key
5. Add to .env file

#### **CoinGecko Setup** (NO KEY NEEDED):
1. Go to: https://www.coingecko.com/en/api
2. Read the free API docs
3. Start using it immediately!

### **Step 3: Create .env File**

Create a `.env` file in your project root:

```env
# API Configuration
API_PROVIDER=coingecko
COINGECKO_API_KEY=  # Empty for free tier

# OR if using CoinMarketCap
# API_PROVIDER=coinmarketcap
# COINMARKETCAP_API_KEY=your_api_key_from_coinmarketcap

# OR if using both (recommended)
COINGECKO_API_KEY=
COINMARKETCAP_API_KEY=your_optional_key_here
BINANCE_API_KEY=  # Leave empty (not needed)

# Towns Protocol Configuration
TOWNS_BOT_TOKEN=your_towns_bot_token

# Database Configuration  
DATABASE_URL=sqlite:///./price_data.db

# Server Configuration
PORT=3000
NODE_ENV=development
```

### **Step 4: Install Dependencies**

```bash
bun install
```

### **Step 5: Start the Bot**

```bash
bun dev
```

---

## 📋 API Integration in Code

### **CoinGecko Implementation**:

```typescript
// src/services/priceService.ts
import axios from 'axios';

const getCoinGeckoPrice = async (tokenSymbol: string) => {
  const response = await axios.get(
    `https://api.coingecko.com/api/v3/simple/price`,
    {
      params: {
        ids: tokenSymbol.toLowerCase(),
        vs_currencies: 'usd',
        include_market_cap: true,
        include_24hr_vol: true,
        include_24hr_change: true
      }
    }
  );
  return response.data;
};
```

### **CoinMarketCap Implementation**:

```typescript
// src/services/priceService.ts
import axios from 'axios';

const getCoinMarketCapPrice = async (tokenSymbol: string) => {
  const response = await axios.get(
    `https://pro-api.coinmarketcap.com/v1/cryptocurrency/quotes/latest`,
    {
      params: {
        symbol: tokenSymbol.toUpperCase(),
        convert: 'USD'
      },
      headers: {
        'X-CMC_PRO_API_KEY': process.env.COINMARKETCAP_API_KEY
      }
    }
  );
  return response.data;
};
```

### **Binance Implementation**:

```typescript
// src/services/priceService.ts
const getBinancePrice = async (tokenSymbol: string) => {
  const response = await axios.get(
    `https://api.binance.com/api/v3/ticker/price`,
    {
      params: {
        symbol: `${tokenSymbol.toUpperCase()}USDT`
      }
    }
  );
  return response.data;
};
```

---

## 💰 Cost Comparison

| Provider | Cost | API Key | Calls/sec | Coins |
|----------|------|---------|-----------|-------|
| **CoinGecko** | FREE ✅ | NO | 10-15 | 10,000+ |
| **Binance** | FREE ✅ | NO | 1,200/min | Major pairs |
| **CoinMarketCap** | $99+/mo | YES | 333/day free | 20,000+ |
| **Kraken** | FREE trial | NO | 15/sec | Major pairs |

---

## ⚠️ Important Notes

1. **Rate Limits**: Never exceed API rate limits or your key gets banned
2. **Caching**: Store prices locally to reduce API calls
3. **Backup**: Have a fallback API if primary fails
4. **Monitoring**: Track API usage on your dashboard
5. **Security**: Never commit .env files to Git

---

## 🔄 Multi-API Fallback Strategy

**Recommended Implementation**:

```
Try CoinGecko (free, fast, reliable)
  ↓
If fails → Try CoinMarketCap (if key available)
  ↓
If fails → Try Binance (always free, always works)
  ↓
If all fail → Use cached price from database
```

---

## ✅ Checklist for Setup

- [ ] Choose API provider (CoinGecko recommended)
- [ ] Sign up and get API key (if needed)
- [ ] Create .env file
- [ ] Add API keys to .env
- [ ] Install npm dependencies
- [ ] Test API connection
- [ ] Deploy to production
- [ ] Monitor API usage
- [ ] Set up alerts for rate limits

---

## 🆘 Troubleshooting

### **"API key invalid" Error**
- Check .env file spelling
- Verify API key is copied correctly
- Ensure key hasn't expired

### **"Rate limit exceeded" Error**
- Reduce API call frequency
- Implement caching
- Upgrade to paid tier

### **"API not responding" Error**
- Check internet connection
- Switch to backup API
- Check API status page

---

## 📚 Resources

- CoinGecko Docs: https://docs.coingecko.com/reference/intro
- CoinMarketCap Docs: https://coinmarketcap.com/api/documentation/v1/
- Binance Docs: https://binance-docs.github.io/apidocs/
- Kraken Docs: https://docs.kraken.com/rest/

---

## 🎯 Final Recommendation

**For Development**: Use **CoinGecko Free API** (no cost, no setup)

**For Production**: Use **CoinGecko Free + CoinMarketCap Paid** (dual source for reliability)

**For High Volume**: Use **CoinMarketCap Pro** ($199/month for 50,000 calls/day)

---

**Start with CoinGecko - it's free and production-ready!** ✅
