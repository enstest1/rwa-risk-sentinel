# Sentinel — Founder House / Robinhood Chain Submission Draft

## Project
Sentinel

## One-line description
24/7 deterministic risk intelligence and email alerting for Robinhood Chain Stock Tokens.

## Live product
https://rwa-risk-sentinel.up.railway.app

## Public repository
https://github.com/enstest1/rwa-risk-sentinel

## Builder
Christopher Tomich / pelpa

GitHub: https://github.com/enstest1  
X: https://x.com/pelpa333

## What Sentinel does
Sentinel continuously evaluates Robinhood Chain Stock Token conditions and converts observable market and tokenization signals into an explainable 0-100 risk score. Users or autonomous agents can check an asset before execution, monitor a selected watchlist, and receive daily email summaries or threshold alerts when conditions materially change.

## Why Robinhood Chain
Robinhood Chain is purpose-built around tokenized financial assets and 24/7 onchain access. That creates a need for guardrails that understand when the underlying market, Stock Token mint/burn window, asset metadata, and onchain contract state may not all be in their normal operating condition.

Sentinel is built specifically around Robinhood Chain mainnet and reads the canonical deployment/multiplier onchain alongside Robinhood reference data.

## What is live today
- Robinhood Chain mainnet integration
- Deterministic scoring; no LLM controls the risk score
- Read-only wallet/address setup
- Stock Token watchlists
- Five-minute automated monitoring
- Explainable reasons and action guidance
- Snapshot history
- Daily email briefs and threshold-transition alert logic
- Agent-facing risk API
- Product hero animation
- Discord / Telegram / X roadmap placeholders

## AI approach
The core product does not require AI. Optional model-based research is designed only to add contextual summaries around filings, earnings, corporate actions, halts, announcements, and macro events. It is intentionally isolated from the deterministic risk score.

## Why this fits Founder House
Sentinel sits directly at the intersection of tokenization and autonomous-agent infrastructure. It is an early working product focused on making Robinhood Chain Stock Tokens safer to monitor and easier for both humans and agents to reason about before execution.

## Next milestones
1. Complete production email sender/domain configuration.
2. Add Discord, Telegram, and X delivery.
3. Add authenticated user profiles and database-backed history.
4. Add wallet holding discovery and expanded execution/liquidity signals.
5. Add optional cited event-research enrichment and agent policy hooks.

## Current status
Live MVP on Robinhood Chain mainnet. Read-only; no custody or trade permissions.
