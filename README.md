# Telegram OTP Monitor (Playwright + Python)

This repository contains a production-ready Telegram bot that logs into a virtual-number website (like `ivas.com`), monitors the user's message inbox for OTPs, and forwards them to your Telegram chat — without an official API (uses headless browser automation).

> **Important:** You must have permission from the website owner to automate/scrape their site. Use responsibly.

---

## Features
- Uses **Playwright** (headless) for robust login & scraping.
- Sends status updates to Telegram for:
  - Bot started
  - Login success / failure
  - New OTP received
  - Errors & restarts
- Keeps track of last-sent message to avoid duplicates (persisted to `last_seen.json`).
- Designed to be deployed on platforms such as Render / Docker / GitHub Actions (see notes).

---

## Files
- `main.py` — main application and monitoring loop
- `config.py` — load environment variables & selectors
- `requirements.txt` — Python dependencies
- `.env.example` — example environment variables & selectors
- `.gitignore`
- `last_seen.json` — created at runtime (ignored by git)

---

## Setup (local)
1. Clone:
```bash
git clone https://github.com/your-username/ivas-otp-bot.git
cd ivas-otp-bot

Create & activate a virtual environment (recommended):

python3 -m venv .venv
source .venv/bin/activate


Install Python dependencies:

pip install -r requirements.txt


Install Playwright browsers & dependencies:

# Recommended
playwright install --with-deps
# Or minimal
playwright install

Run the bot:

python main.py


You should receive a Telegram message:
✅ Bot Started Successfully. Initializing configuration and web automation environment.

If login is successful:
🌐 Login Successful! Session established. Starting continuous OTP monitoring loop.
