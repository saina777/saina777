# AGENTS.md

## Mission
Build a safe AI-assisted MT5 paper-trading system for EURUSD and XAUUSD.

## Scope
This repository is for:
- market data ingestion
- feature engineering
- backtesting
- deterministic risk checks
- paper execution
- trade journaling
- MCP tool exposure for Codex

This repository is not for:
- unrestricted autonomous live trading
- hidden discretionary logic
- free-text order execution

## Operating rules
- V1 is paper trading only.
- No live trading path is enabled by default.
- No trade may execute from natural language alone.
- Every trade must follow:
  intent -> schema -> strategy validation -> risk validation -> execution approval -> routing -> logging
- Risk logic must be deterministic.
- Research logic may advise, but never bypass risk or execution checks.
- Prefer small safe changes over large speculative rewrites.
- If requirements are unclear, choose the safer implementation and explain assumptions.

## Symbols
- EURUSD
- XAUUSD

## Allowed strategy families
- trend-following
- breakout
- mean-reversion

## Required filters
- ATR
- EMA
- RSI
- ADX
- spread guard
- session filter
- drawdown guard
- macro/news placeholder block

## Risk rules
- hard stop-loss required
- per-trade risk cap from config
- total open risk cap from config
- daily drawdown cap from config
- weekly drawdown cap from config
- pause symbol after repeated failures
- trigger kill switch on abnormal drawdown, execution anomaly, or data-quality failure

## Repo layout
- `src/` core shared code
- `mcp/` MCP servers
- `strategies/` strategy rules
- `backtests/` backtesting logic
- `risk/` risk engine and veto logic
- `execution/` paper routing and order schemas
- `journal/` audit logs and summaries
- `configs/` settings loaders
- `tests/` tests
- `skills/` Codex skills

## Commands
- Install deps: `pip install -r requirements.txt`
- Run tests: `pytest`
- Run lint: add command when configured
- Run one MCP server: `python mcp/market_data_server.py`

## Engineering conventions
- Use typed Python where practical.
- Validate external inputs with pydantic.
- Return structured JSON from MCP tools.
- Fail closed on invalid trade intents.
- Do not hide exceptions silently.
- Log approvals, rejections, and execution events.

## Done means
A task is done only when:
- code is added or updated
- relevant tests are added or updated
- commands to run the change are documented
- logs and rejection reasons are explicit
- no unsafe execution path was introduced
