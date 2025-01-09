# Daily Commit Bot 🤖

A simple automation project that ensures daily commits on GitHub while sharing a motivational quote every day. This helps maintain your GitHub streak with minimal effort!

## Features ✨
- Fetches a random motivational quote daily from the [ZenQuotes API]((https://zenquotes.io/api/today ))..
- Automatically commits the quote to your GitHub repository.
- Uses GitHub Actions to run the process daily.

---

## Project Structure 🗂
```
.
├── daily_quote.py          # Python script to fetch and save the quote
├── daily_quote.txt         # File where the daily quote is stored
└── .github/
    └── workflows/
        └── daily_commit.yml  # GitHub Actions workflow file
```

---

## How It Works ⚙️
1. The `daily_quote.py` script fetches a random quote from the Quotable API.
2. The quote is saved to a `daily_quote.txt` file.
3. GitHub Actions runs the script daily at 6:30 AM IST (Indian Standard Time) and commits the updated file to your repository.

---

## Setup Instructions 🛠️

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/daily-commit-bot.git
cd daily-commit-bot
```

### 2. Add the Workflow File
Ensure the `.github/workflows/daily_commit.yml` file exists with the following content:

```yaml
name: Daily Commit

on:
  schedule:
    - cron: '0 1 * * *'  # Runs daily at 6:30 AM IST (1:00 AM UTC)

jobs:
  commit:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.x'

      - name: Install dependencies
        run: pip install requests

      - name: Run Python script
        run: python daily_quote.py

      - name: Commit changes
        run: |
          git config user.name "your-username"
          git config user.email "your-email@example.com"
          git add .
          git commit -m "Daily quote commit"
          git push
```
---

## Dependencies 📦
- Python 3.x
- `requests` library

Install dependencies by running:
```bash
pip install requests
```

---

## License 🖍️
This project is open-source and available under the MIT License.

---

Feel free to modify and improve this project. Happy coding! 🚀
