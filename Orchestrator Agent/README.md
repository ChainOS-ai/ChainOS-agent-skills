# Orchestrator Agent (大总管 Agent)

## What it does

The Orchestrator Agent is the central “General Manager” of ChinaOS. Instead of calling each individual skill (Product Selection, Supplier Discovery, Document & Finance, Listing & Advertising, SEO & GEO, Operational Automation) separately, you simply describe your business goal in plain English or Chinese. The Orchestrator:

- **Understands** your intent (e.g., “Research portable blender market, find suppliers, then write a listing”).
- **Decomposes** the goal into a sequence (or parallel set) of sub‑tasks.
- **Routes** each sub‑task to the appropriate specialised Agent.
- **Monitors** progress and reports back in real time.
- **Aggregates** all results into a single, downloadable report (HTML/Markdown/PDF).

This turns six independent skills into one seamless, automated workflow.

---

## Quick start

1. **Place this folder** in your AI agent’s skills directory (e.g., `~/.openclaw/skills/`).
2. **Ensure the six sub‑skills are also installed** (Product Selection, Supplier Discovery, Document & Finance, Listing & Advertising, SEO & GEO, Operational Automation). The Orchestrator will automatically discover them via their `skill.json` files.
3. **Restart your agent**.
4. **Ask a high‑level question**, for example:
   - *“Analyze the market for portable blenders, then find 3 suppliers on 1688, and finally generate an Amazon listing.”*
   - *“Run my weekly operational check: hijacking monitoring, price tracking, and daily sales report.”*
   - *“Optimise my existing article for AI search engines and create 50 location pages.”*

The Orchestrator will reply with a task ID and a progress dashboard. You can pause, resume, or cancel at any time.

---

## Dependencies

- **All six ChinaOS sub‑skills** must be installed and accessible.
- **LLM with strong planning capability** (Kimi K2.5 or Claude 3.7+ recommended) – used for intent parsing and task decomposition.
- **WebSocket or polling support** – for real‑time progress updates (optional; falls back to polling).
- **Notification channels** (Feishu / WeChat Work / Email) – required for async alerts (configured per sub‑skill).

No additional API keys are needed for the Orchestrator itself – it uses the same environment variables as the sub‑skills.

---

## How it works (high level)

| Step | Component | What happens |
| :--- | :--- | :--- |
| 1 | **Intent Parser** | Your natural language goal is converted into a structured task JSON. |
| 2 | **Task Planner** | The JSON is broken into a DAG (directed acyclic graph) of sub‑tasks. |
| 3 | **Scheduler** | Sub‑tasks are executed in order (serial) or in parallel, respecting dependencies. |
| 4 | **Context Store** | Outputs from one sub‑task (e.g., a product score) are passed as inputs to the next. |
| 5 | **Report Generator** | After all sub‑tasks succeed, a single report is created with summaries and file links. |
| 6 | **Notification** | The final report is pushed to your Feishu/WeChat/Email (configurable). |

If any sub‑task fails, the Orchestrator automatically retries (up to 2 times) and, if still failing, pauses the whole workflow and notifies you.

---

## Example workflow (full e‑commerce launch)

**User input:**  
*“Research the market for a portable blender, score it, find me 3 suppliers on 1688 with good ratings, then write a COSMO‑optimised Amazon listing, and finally create 50 GEO‑optimised blog posts for US cities.”*

**Orchestrator actions (behind the scenes):**

1. **Product Selection Agent** → returns feasibility score (82/100, 大吉) + radar chart + competitor data.
2. **Supplier Discovery Agent** → takes keywords from step 1, returns 3 suppliers with risk labels (🟢/🟡/🔴) and contact info.
3. **Listing & Advertising Agent** → uses both previous outputs to generate a full Amazon listing (title, bullets, A+, backend keywords) with COSMO semantic coverage.
4. **SEO & GEO Agent** → takes the product name and core selling points, generates 50 unique location pages (e.g., “Best portable blender in New York”), each with a human‑review gate.

**Final output:** A single HTML report with all four sections, downloadable files (Excel/CSV), and a direct “Publish to WordPress” button (if CMS integration is configured).

---

## Configuration

The Orchestrator reads the `skill.json` of every sub‑skill installed in the same skills directory. No additional configuration is required for basic serial workflows.

For advanced use (parallel execution, cron triggers, webhooks), set the following environment variables:

```bash
# Optional: enable parallel scheduling (default: serial)
export ORCHESTRATOR_PARALLEL=true

# Optional: cron schedule for auto‑execution (24‑hour format)
export ORCHESTRATOR_CRON="0 9 * * *"   # runs daily at 9 AM

# Optional: webhook URL for completion callbacks
export ORCHESTRATOR_WEBHOOK="https://your-server.com/callback"
