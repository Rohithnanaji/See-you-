name: Security Audit

on:
  schedule:
    - cron: '0 0 * * 0' # Runs every Sunday at midnight

jobs:
  audit:
    runs-on: ubuntu-latest

      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'

      - name: Install dependencies
        run: npm install

      - name: Run audit
        run: npm audit --audit-level=high
        
