# Sentinel — Founder House / Robinhood Chain Submission Draft

## Project
Sentinel

## One-line description
24/7 deterministic risk intelligence with AI catalyst monitoring for Robinhood Chain Stock Tokens.

## Live product
https://rwa-risk-sentinel.up.railway.app

## Public repository
https://github.com/enstest1/rwa-risk-sentinel

## Builder
Christopher Tomich / pelpa

GitHub: https://github.com/enstest1  
X: https://x.com/pelpa333

## What Sentinel does
Sentinel continuously evaluates Robinhood Chain Stock Token conditions and converts observable market and tokenization signals into an explainable 0-100 risk score. Users or autonomous agents can check an asset before execution, monitor a selected watchlist, and review a separate AI Catalyst Watch that searches current news, SEC filings, earnings, corporate actions, trading halts, company announcements, and macro events.

## Why Robinhood Chain
Robinhood Chain is purpose-built around tokenized financial assets and 24/7 onchain access. That creates a need for guardrails that understand when the underlying market, Stock Token mint/burn window, asset metadata, and onchain contract state may not all be in their normal operating condition.

Sentinel is built specifically around Robinhood Chain mainnet and reads the canonical deployment/multiplier onchain alongside Robinhood reference data.

## What is live today
- Robinhood Chain mainnet integration
- Deterministic 0-100 scoring; no LLM controls the risk score
- Read-only wallet/address setup
- Stock Token watchlists
- Five-minute automated monitoring
- Explainable reasons and action guidance
- Snapshot history
- Agent-facing risk and history APIs
- AI Catalyst Watch using Perplexity Sonar Pro through OpenRouter
- Catalyst direction, confidence, materiality, summary, and cited source links
- Product hero animation
- Discord / Telegram / X roadmap placeholders
- Email verification, daily brief, and threshold-alert logic implemented; production email provider configuration is still pending

## AI approach
Perplexity Sonar Pro via OpenRouter is live as Sentinel's Catalyst Intelligence layer. It researches current news, SEC filings, earnings, corporate actions, trading halts, company announcements, and macro events, then classifies catalyst direction, confidence, and materiality with citations.

This AI layer is intentionally isolated from the deterministic 0-100 market-risk score and cannot modify that score.

## Why this fits Founder House
Sentinel sits directly at the intersection of tokenization, RWA infrastructure, and autonomous-agent tooling. It is a working Robinhood Chain product designed to help humans and agents understand both execution conditions and emerging real-world catalysts before acting.

## Next milestones
1. Complete production email sender/domain configuration.
2. Add Discord, Telegram, and X delivery.
3. Add authenticated user profiles and database-backed history.
4. Add wallet holding discovery and expanded execution/liquidity signals.
5. Add a second AI review/critic pass before high-severity catalyst alerts are sent.

## Current status
Live MVP on Robinhood Chain mainnet. Read-only; no custody or trade permissions.
