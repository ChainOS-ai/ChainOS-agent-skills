# Listing & Advertising Agent (Listing 工程 + 广告诊断 Agent)

## What it does
- **Generates COSMO‑aware Amazon listings** (title, 5 bullets, A+, backend keywords) based on 15 semantic relationships.
- **Diagnoses advertising performance** (ACoS, CTR, CVR) via Amazon Ads API.
- **Outputs actionable optimization lists** (what to change, in priority order).

## Quick start
1. Place folder in skills directory.
2. Ask: *“Optimize my listing for ASIN B08P227CJP for COSMO”*
3. For ads: authorize Amazon Ads API once.

## Dependencies
- **Playwright MCP** (to scrape competitor listings)
- **Amazon Advertising API key** (optional, only for ad diagnosis)
- Basic LLM with long context (Kimi K2.5 / Claude recommended)

## Output example
- Optimized title: `[Main keyword] + [material] + [usage] + [size]`
- COSMO coverage radar chart (5 layers)
- Ad anomaly list: “Keyword ‘blender cheap’ ACoS 45% > margin → pause”

## Configuration
Add Amazon Ads API credentials to your agent’s environment:
```bash
export AMAZON_ADS_CLIENT_ID="..."
export AMAZON_ADS_CLIENT_SECRET="..."
