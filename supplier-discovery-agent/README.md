# Supplier Discovery Agent (供应商背调 Agent)

## What it does
Finds and vets 1688 suppliers. Automatically:
- Searches 1688 with filters (sales, rating, OEM).
- Extracts company name, MOQ, price range, contact.
- Calls **Tianyancha API** for legal status, capital, lawsuits.
- Outputs an Excel comparison with 🟢/🟡/🔴 risk labels.

## Quick start
1. Place folder in skills directory.
2. Provide your Tianyancha API key (see Configuration).
3. Ask: *“Find 5 power bank suppliers on 1688, rating >4.5, OEM supported”*

## Dependencies
- **Playwright MCP** (for 1688 browsing)
- **Tianyancha API key** (free tier available)

## Configuration
Set environment variable before starting your agent:
```bash
export TIANYANCHA_API_KEY="your_key_here"
