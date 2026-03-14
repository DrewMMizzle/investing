# Daloopa Financial Analysis Toolkit

A Python-based financial analysis toolkit for hedge fund analysts, powered by Daloopa's institutional-grade financial data via MCP.

## Project Type

CLI/Script toolkit — no web frontend. All analysis is performed via Python scripts and Claude Code slash commands.

## Architecture

- **Language**: Python 3.12
- **Data Source**: Daloopa MCP server (`mcp.daloopa.com`) for SEC filings, earnings, fundamentals
- **Market Data Fallback**: `infra/market_data.py` via yfinance
- **Output Formats**: HTML reports, Excel (.xlsx), Word (.docx), PDF

## Key Directories

- `infra/` — Infrastructure scripts (charts, Excel, Word, PDF, market data)
- `recipes/` — Direct API access scripts
- `reports/` — Generated output files (gitignored)
- `templates/` — Word document templates
- `daloopa_docs/` — Local copy of Daloopa API documentation
- `scripts/` — Utility scripts

## Dependencies

All installed via pip (see `requirements.txt`):
- `yfinance` — Market data fallback
- `openpyxl` — Excel file generation
- `python-docx`, `docxtpl`, `docxcompose` — Word document generation
- `matplotlib` — Chart generation
- `fredapi` — FRED risk-free rate data
- `requests`, `beautifulsoup4`, `html2text`, `markdown` — Data fetching and rendering

## Environment Variables

See `.env.example`:
- `DALOOPA_EMAIL` — Daloopa account email (for direct API access)
- `DALOOPA_API_KEY` — Daloopa API key (for direct API access)
- `FRED_API_KEY` — Optional, for DCF/WACC risk-free rate; defaults to 4.5%

MCP authentication uses OAuth (no API key needed for MCP mode).

## MCP Configuration

`.mcp.json` configures two MCP servers:
- `daloopa` — Financial data (fundamentals, KPIs, SEC filings)
- `daloopa-docs` — Daloopa documentation

## Workflow

The "Start application" workflow is a console workflow confirming the toolkit is ready. The actual work is done via Claude Code slash commands (e.g., `/earnings AAPL`, `/build-model MSFT`).
