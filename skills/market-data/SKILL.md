---
name: market-data
description: Use when the task involves fetching, validating, or analyzing EURUSD or XAUUSD market data, spreads, sessions, missing bars, or feed quality. Do not use for order execution.
---

## Purpose
Fetch and validate market data for paper trading workflows.

## Responsibilities
- get recent bars and ticks
- check spread conditions
- detect stale data
- detect missing bars
- label session state

## Must do
- return structured outputs
- flag suspicious data
- include exact symbol and timeframe

## Must not do
- propose or execute trades
- bypass validation
