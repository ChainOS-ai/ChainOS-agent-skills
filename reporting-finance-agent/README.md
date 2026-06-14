
---

### 📁 document-finance-agent/README.md

```markdown
# Document & Finance Agent (文档财务 Agent)

## What it does
- **Consolidates quotes** from PDF/Word/Excel/images into one comparison table.
- **Generates profit formulas** (gross margin, net margin, ROI) from a cost sheet.
- **Researches platform policies** (Amazon, Temu, TikTok Shop) for onboarding decisions.

## Quick start
1. Place folder in skills directory.
2. Ask: *“Consolidate these 3 quotes into an Excel table”* (upload files)
3. Or: *“Upload cost sheet and add profit formulas”*

## Dependencies
- Multimodal LLM (for parsing PDF/Word/images) – your agent must support file uploads.
- Exchange rate API (optional, for multi‑currency quotes).

## Output example
- Excel with unified columns: Supplier, MOQ, Unit Price, Lead Time.
- Highlighted lowest price / shortest lead time.
- Profit columns added to cost sheet.

## Configuration
None required. For multi‑currency, the agent will call a free exchange rate API automatically.

## Troubleshooting
- **Parsing errors** → Use high‑contrast PDFs. Low‑confidence fields are marked “待人工核对”.
- **No profit formulas** → Ensure cost sheet has columns like “cost price”, “selling price”.
