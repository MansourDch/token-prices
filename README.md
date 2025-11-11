# 💰 Token Prices Bot

A powerful Towns Protocol bot that fetches and displays cryptocurrency token prices in real-time. Built with Towns SDK for community-driven token price tracking and market intelligence.

## 🎯 Features

- **Real-time Price Tracking**: Fetch live cryptocurrency prices from multiple data sources
- **Multi-Token Support**: Track prices for multiple tokens simultaneously
- **Slash Commands**: Easy-to-use `/price` command for instant price lookup
- **Price Alerts**: Set alerts for price changes across specified tokens
- **Historical Data**: View price history and trends
- **Community Driven**: Built for Towns protocol to enable group-based price tracking
- **Persistent Storage**: Database integration for storing user preferences and alert settings

## 📋 Prerequisites

- **Node.js** 18.0.0 or higher
- **Bun** (recommended runtime)
- **TypeScript** knowledge
- Towns Protocol account and developer setup
- Code Editor (VS Code or Cursor recommended)

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/MansourDch/token-prices.git
cd token-prices
```

### 2. Install Dependencies

```bash
bun install
```

### 3. Configure Environment Variables

Create a `.env` file in the root directory:

```env
TOWNS_BOT_TOKEN=your_bot_token_here
COINGECKO_API_KEY=your_coingecko_api_key
DATABASE_URL=your_database_url
PORT=3000
```

### 4. Set Up Database

```bash
bun run setup:db
```

### 5. Start the Bot Locally

```bash
bun dev
```

## 📁 Project Structure

```
token-prices/
├── src/
│   ├── commands/          # Slash command handlers
│   │   ├── price.ts       # /price command
│   │   ├── alert.ts       # /alert command
│   │   └── history.ts     # /history command
│   ├── handlers/          # Event handlers
│   │   ├── messages.ts    # Message handling
│   │   └── reactions.ts   # Reaction handling
│   ├── services/          # Business logic
│   │   ├── priceService.ts   # Price fetching logic
│   │   ├── alertService.ts   # Alert management
│   │   └── dataService.ts    # Database operations
│   ├── utils/             # Utility functions
│   │   ├── formatters.ts  # Data formatting
│   │   ├── validators.ts  # Input validation
│   │   └── logger.ts      # Logging utility
│   ├── bot.ts             # Main bot initialization
│   └── index.ts           # Entry point
├── .env.example           # Environment variables template
├── .gitignore             # Git ignore rules
├── package.json           # Project dependencies
├── tsconfig.json          # TypeScript configuration
└── README.md              # This file
```

## 🔧 Available Commands

### `/price [token]`
Fetch the current price of a token.

Example:
```
/price BTC
/price ETH
/price TOWNS
```

### `/alert [token] [price] [condition]`
Set a price alert for a token.

Example:
```
/alert BTC 50000 above
/alert ETH 2000 below
```

### `/history [token] [days]`
View price history for a token.

Example:
```
/history BTC 7
/history ETH 30
```

## 🔄 Workflow

1. **User sends command** → Bot receives via Towns protocol
2. **Command parsing** → Extract token symbol and parameters
3. **Data fetching** → Call price API (CoinGecko, etc.)
4. **Processing** → Format and calculate required data
5. **Response** → Send formatted message back to Towns chat
6. **Storage** → Save to database for history/analytics

## 🗄️ Database Schema

- **users** - User preferences and settings
- **alerts** - Active price alerts
- **price_history** - Historical price data cache
- **price_queries** - Analytics on frequently queried tokens

## 🔐 Security Considerations

- API keys stored in environment variables
- Rate limiting on API calls
- Input validation for all commands
- Admin-only commands for bot management
- Encrypted sensitive data in database

## 📚 Towns Protocol Integration

This bot follows the Towns Protocol Bot SDK standards:

- **Bot SDK Version**: 1.0.0+
- **Message Format**: JSON-encoded Towns protocol messages
- **Event Handling**: Uses Towns event emitters
- **Deployment**: Ready for Render deployment

## 🚢 Deployment

### Deploy to Render

1. Push code to GitHub
2. Connect Render to your GitHub repository
3. Set environment variables in Render dashboard
4. Deploy and monitor

```bash
# Build command
bun install && bun build

# Start command
bun start
```

## 🛠️ Development

### Run in Development Mode

```bash
bun dev
```

### Run Tests

```bash
bun test
```

### Format Code

```bash
bun format
```

### Lint Code

```bash
bun lint
```

## 📖 Learning Resources

- [Towns Protocol Documentation](https://docs.towns.com/)
- [Towns Protocol Academy](https://towns.com/academy)
- [Bot SDK Guide](https://docs.towns.com/sdk/bot)
- [CoinGecko API](https://www.coingecko.com/api)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

MIT License - See LICENSE file for details

## 🙋 Support

For issues and questions:
- Open a GitHub issue
- Check existing documentation
- Visit Towns Protocol Discord community

## 🎓 Built with

- [Towns Protocol SDK](https://github.com/towns-protocol)
- [TypeScript](https://www.typescriptlang.org/)
- [Bun](https://bun.sh/)
- [CoinGecko API](https://www.coingecko.com/)

---

**Happy tracking! 📊**
