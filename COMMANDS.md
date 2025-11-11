# 📋 Token Prices Bot - User Commands Guide

This guide explains all the commands users should send to interact with the Token Prices bot in Towns Protocol communities.

## 🎯 Quick Start

All commands are **slash commands** (starting with `/`). Simply type the command in your Towns chat and the bot will respond with the requested information.

---

## 📌 Primary Commands

### 1. 💲 `/price [token]` - Get Current Token Price

**Purpose**: Fetch the real-time price of any cryptocurrency token.

**Syntax**:
```
/price [TOKEN_SYMBOL]
```

**Parameters**:
- `TOKEN_SYMBOL` (required) - The token symbol (e.g., BTC, ETH, TOWNS)
  - Can be uppercase or lowercase
  - Single token at a time

**Examples**:
```
/price BTC
/price ETH
/price TOWNS
/price SOL
/price USDC
/price DAI
/price SHIB
```

**Bot Response** will include:
- 💰 Current price in USD
- 📈 24-hour change percentage
- 📊 Market cap
- 💧 Trading volume
- 🎯 All-time high (ATH)
- 📍 All-time low (ATL)

**Example Response**:
```
🔶 Bitcoin (BTC) - Current Price

Price: $43,250.00 USD
24h Change: +2.45% 📈
Market Cap: $847.5B
Volume (24h): $28.3B
ATH: $69,000 (Nov 2021)
ATL: $67 (Jul 2013)
```

---

### 2. 🔔 `/alert [token] [price] [condition]` - Set Price Alert

**Purpose**: Create a price alert notification when a token reaches a specific price level.

**Syntax**:
```
/alert [TOKEN_SYMBOL] [PRICE] [CONDITION]
```

**Parameters**:
- `TOKEN_SYMBOL` (required) - The token to track (e.g., BTC, ETH)
- `PRICE` (required) - The target price in USD
- `CONDITION` (required) - Either `above` or `below`

**Examples**:
```
/alert BTC 50000 above
/alert ETH 2000 below
/alert TOWNS 1 above
/alert SOL 150 below
/alert USDC 1.05 above
/alert DAI 0.98 below
```

**Bot Response** will include:
- ✅ Confirmation of alert creation
- 🎯 Token and target price
- ↕️ Alert condition (above/below)
- ⏰ Timestamp of alert setup

**Example Response**:
```
🔔 Price Alert Created!

Token: Bitcoin (BTC)
Target Price: $50,000 USD
Condition: Alert when price goes ABOVE target
Status: ✅ Active
Created at: 2025-11-11 23:30:00

You will be notified when this condition is met!
```

**Alert Trigger**:
When the price condition is met, you'll receive:
```
⚠️ ALERT TRIGGERED!

Bitcoin (BTC) has gone ABOVE $50,000!
Current Price: $50,150
Time: 2025-11-11 23:45:00
```

---

### 3. 📊 `/history [token] [days]` - View Price History

**Purpose**: Display historical price data for a token over a specified time period.

**Syntax**:
```
/history [TOKEN_SYMBOL] [DAYS]
```

**Parameters**:
- `TOKEN_SYMBOL` (required) - The token to track (e.g., BTC, ETH)
- `DAYS` (required) - Number of past days to show (1, 7, 30, 90, 365)

**Examples**:
```
/history BTC 7
/history ETH 30
/history TOWNS 1
/history SOL 90
/history USDC 7
/history DAI 365
```

**Bot Response** will include:
- 📈 Price chart/graph
- 💹 Opening price
- 💯 Highest price in period
- 📉 Lowest price in period
- 🎯 Closing price
- 📊 Average price
- 📌 Percentage change

**Example Response**:
```
📈 Bitcoin (BTC) - 7 Day History

Price Chart:
  $43,500 |---------●
  $43,000 |-------●--
  $42,500 |-----●----
  $42,000 |-●-------
  $41,500 |--------●

Opening: $42,100
High: $43,500
Low: $41,800
Closing: $43,250
Average: $42,730
Change: +2.72% 📈
```

---

## 🔄 Secondary Commands

### 4. ❓ `/help` - Get Command Help

**Purpose**: Display all available commands and their usage.

**Syntax**:
```
/help
```

**Bot Response** will show:
- ✅ List of all commands
- 📝 Command descriptions
- 💡 Usage examples

---

### 5. ⚙️ `/settings` - Manage User Settings

**Purpose**: Configure bot preferences and alert settings.

**Syntax**:
```
/settings [OPTION]
```

**Options**:
- `alerts` - View active alerts
- `notifications` - Control alert notifications (on/off)
- `currency` - Change display currency (USD, EUR, GBP, etc.)
- `language` - Change bot language

**Examples**:
```
/settings alerts
/settings notifications on
/settings currency EUR
/settings language en
```

---

### 6. 🗑️ `/alert cancel [alert_id]` - Cancel Alert

**Purpose**: Remove an active price alert.

**Syntax**:
```
/alert cancel [ALERT_ID]
```

**Examples**:
```
/alert cancel btc_50000_above
/alert cancel eth_2000_below
```

---

### 7. 📋 `/top [limit]` - Top Cryptocurrencies

**Purpose**: Display top cryptocurrencies by market cap.

**Syntax**:
```
/top [NUMBER]
```

**Parameters**:
- `NUMBER` (optional) - Number of top tokens to show (default: 10, max: 50)

**Examples**:
```
/top
/top 5
/top 20
```

**Bot Response** will show:
```
🏆 Top 10 Cryptocurrencies by Market Cap

1. 🔶 Bitcoin (BTC) - $847.5B
2. 🔷 Ethereum (ETH) - $280.3B
3. 🟢 BNB (BNB) - $98.2B
4. 🟠 Solana (SOL) - $68.5B
5. 🔵 XRP (XRP) - $62.1B
...
```

---

## 💡 Usage Examples

### Scenario 1: Quick Price Check
```
User: /price BTC
Bot: Shows Bitcoin's current price and 24h stats
```

### Scenario 2: Setting Up an Alert
```
User: /alert ETH 2500 above
Bot: Confirms alert creation
Bot (later): Notifies when ETH reaches $2500
```

### Scenario 3: Checking Weekly Trends
```
User: /history SOL 7
Bot: Shows Solana's price movement over the last 7 days
```

### Scenario 4: Portfolio Tracking
```
User: /price BTC
User: /price ETH
User: /price TOWNS
Bot: Responds to each command with current prices
```

---

## 🎨 Response Format

All bot responses follow this format:

```
[EMOJI] [TOKEN_NAME] - [RESPONSE_TYPE]

[DETAILED_INFORMATION]
[STATISTICS]
[TIMESTAMPS/METADATA]

[ACTION_BUTTONS/NEXT_STEPS]
```

---

## ⚡ Advanced Tips

### Tip 1: Use Autocomplete
Start typing `/` to see all available commands in autocomplete.

### Tip 2: Bulk Queries
You can send multiple commands in sequence:
```
/price BTC
/price ETH
/price TOWNS
```

### Tip 3: Set Multiple Alerts
Track multiple prices at once:
```
/alert BTC 45000 below
/alert ETH 1500 below
/alert SOL 100 below
```

### Tip 4: Check Alerts Anytime
Use `/settings alerts` to see all your active alerts.

### Tip 5: Notification Control
Disable alerts when busy: `/settings notifications off`

---

## ❓ FAQ

**Q: What cryptocurrencies are supported?**
A: All major tokens including BTC, ETH, SOL, TOWNS, and thousands more.

**Q: How often are prices updated?**
A: Prices are updated every 30 seconds from live market data.

**Q: Can I receive alerts?**
A: Yes! Set price alerts with `/alert` and get notified in real-time.

**Q: What currencies can I display prices in?**
A: USD (default), EUR, GBP, JPY, CNY, and more.

**Q: Is there a limit to alerts?**
A: Users can set up to 20 active alerts per account.

**Q: What if the token symbol is wrong?**
A: The bot will suggest similar token symbols.

---

## 🚀 Getting Started

1. **Start Simple**: Try `/price BTC` to see it in action
2. **Explore Alerts**: Set your first alert with `/alert BTC 50000 above`
3. **Check History**: View trends with `/history ETH 7`
4. **Customize**: Adjust settings with `/settings`

---

## 💬 Need Help?

- Use `/help` for command reference
- Try `/settings` to customize behavior
- Report issues in the community

---

**Happy price tracking! 📊**
