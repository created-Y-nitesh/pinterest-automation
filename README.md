# PinScheduler: AI-Powered Pinterest Automation Bot

An automated pipeline that ingests affiliate or product links via a private Telegram bot, utilizes Google Gemini to generate highly optimized viral Pinterest copy, structures a fixed-interval queue inside Google Sheets, and programmatically publishes content to Pinterest boards.

## 🏗️ System Architecture

1. **Ingestion (Telegram Bot API):** Collects product or affiliate links directly from the operator.
2. **AI Enrichment (Gemini API):** Scrapes the product landing page and uses generative AI to extract titles, optimize descriptions for SEO, and generate high-engagement hashtags.
3. **Queue Management (Google Sheets Web App):** Appends the processed payload to a scheduling matrix, assigning the post to the next available fixed time slot (06:00, 09:00, 12:00, 15:00, 18:00, 21:00).
4. **Publishing Engine (Pinterest API v5):** A background cron script checks the spreadsheet queue at regular intervals and programmatically posts ready content via the Pinterest API.

## 🛠️ Tech Stack & Dependencies

* **Language:** Python 3.10+
* **Core Libraries:** `python-telegram-bot` (or `telebot`), `requests`, `google-generativeai`
* **Storage / Database:** Google Sheets API via Google Apps Script Web App
* **Scheduling:** Linux Crontab / Server-side Cron Engine

## ⚙️ Environment Configuration

To run this application locally or deploy it to a server, secure the following variables in a `.env` file:

```env
TELEGRAM_BOT_TOKEN="your_telegram_bot_token"
GEMINI_API_KEY="your_google_gemini_api_key"
APPS_SCRIPT_URL="[https://script.google.com/macros/s/XXXXX/exec](https://script.google.com/macros/s/XXXXX/exec)"
PINTEREST_ACCESS_TOKEN="your_pinterest_developer_token"
PINTEREST_BOARD_ID="your_target_board_id"
