
---

### 📁 operational-automation-agent/README.md

```markdown
# Operational Automation Agent (运营自动化 Agent)

## What it does
**7×24 background monitoring** for:
- **Hijacking alerts** (Buy Box changes) – every 1–2 hours.
- **Price drops** (competitors) – every 4–6 hours.
- **Email classification** (returns/complaints/inquiries) – every 30 min.
- **Daily sales report** – every morning at 09:00.

You configure rules **once**, then the agent runs forever. Alerts are pushed to Feishu/WeChat/Email only when something changes.

## Quick start
1. Place folder in skills directory.
2. Configure once: *“Monitor hijackers for ASIN B08P227CJP, every 2 hours, push to Feishu”*
3. Done. Check alerts the next day.

## Dependencies
- **Playwright MCP** (for Buy Box & price checks)
- **Amazon SP-API** (optional, for daily sales report)
- **Gmail API** (for email classification)
- **Feishu / WeChat Work / SMTP** (for pushes – at least one)

## Configuration
Add your API keys and webhooks to environment variables (see agent documentation).

## Output example
- Feishu card: “🚨 Hijacking Alert – ASIN B08P227CJP, hijacker: shop1234”
- Daily report card: “$2,847 revenue, 142 orders, +12% vs yesterday”

## Troubleshooting
- **No alerts for >12 hours** → Agent sends a heartbeat message to confirm it’s alive.
- **Scraping fails** → Check if Amazon changed page structure; agent will retry and then notify.
- **False positives** → Adjust “consecutive checks” threshold (default 2).
