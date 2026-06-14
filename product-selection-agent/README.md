# Product Selection Agent (选品算命 Agent)

## What it does
Fully automated product research. Given a keyword or ASIN, the agent:
- Scans TikTok, Reddit, and Amazon for demand signals.
- Analyzes top 10 competitors (price, reviews, LQS).
- Calculates profit margin (FBA + 1688 reference).
- Outputs a **score (0–100)** and a **“大吉 / 中吉 / 小凶”** recommendation.

## Quick start
1. Place this folder in your AI agent’s skills directory (e.g., `~/.openclaw/skills/`).
2. Restart the agent.
3. Ask: *“Run product selection for portable blender, budget $20–30”*

## Dependencies
- **Tavily Search** or **Brave Search** (for social/trend data)
- **Playwright MCP** (optional, for scraping Amazon listings)
- Basic file I/O (CSV/Excel output)

## Output example
- Score: 82/100 (大吉)
- Radar chart: Demand 98, Competition 65, Profit 85
- Action list: “Optimize title with ‘personal smoothie’ – low LQS opportunity”

## Configuration
None required if your agent already has search and file tools. For Playwright scraping, ensure `playwright-mcp` is installed.

## Troubleshooting
- **No search results** → Check your search API key (Tavily/Brave).
- **Scraping fails** → Switch to manual listing input or install Stealth plugin for Playwright.
