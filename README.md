# InvestBot2025
Bot for Investing Personally
InvestBot - Local, self-hosted investment idea generator (Windows)

Overview
- Pulls Yahoo Finance price data (via yfinance)
- Reads Reddit discussions for sentiment/mentions (via PRAW)
- Sends Buy/Sell alerts to Telegram
- Stores history in SQLite
- Runs as a long-running Python process

Setup steps (Windows)
1) Prerequisites
- Windows 10/11
- Python 3.10+ installed
- Telegram bot and chat_id (see instructions below)
- Reddit API credentials (client_id, client_secret, user_agent)

2) Prepare the project
- Create the folder: C:\Users\minin\InvestBot
- Copy the files in this repo into that folder (main.py, config.py, etc.)

3) Create and activate a virtual environment
- Open PowerShell
- Run:
  - cd C:\Users\minin\InvestBot
  - py -m venv venv
  - .\venv\Scripts\activate

4) Install dependencies
- With venv active:
  - pip install -r requirements.txt

5) Telegram setup
- Create bot with BotFather and get BOT_TOKEN
- Start a chat with your bot to initialize
- Get chat_id (via https://api.telegram.org/bot<BOT_TOKEN>/getUpdates)
- Set environment variables (recommended) or edit config
  - TELEGRAM_BOT_TOKEN=123:ABC
  - TELEGRAM_CHAT_ID=987654321

6) Reddit setup
- Create a read-only Reddit app to get client_id and client_secret
- Set environment variables:
  - REDDIT_CLIENT_ID=your_id
  - REDDIT_CLIENT_SECRET=your_secret
  - REDDIT_USER_AGENT=invest-bot

7) Optional Twitter
- If you have credentials, set TWITTER_BEARER_TOKEN in environment

8) Run
- In PowerShell, with venv activated:
  - python main.py
- The bot will start and run in a loop, fetching data every FETCH_INTERVAL_MIN minutes (default 60)

9) Troubleshooting
- If you don’t see Telegram messages, verify TOKEN and CHAT_ID
- If Reddit fetch fails, verify credentials and network
- Check invest_bot.db is created in the project folder and that signals are being written

