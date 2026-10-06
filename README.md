# Sentinel

**24/7 risk intelligence for Robinhood Chain Stock Tokens.**

Sentinel is a read-only monitoring and alerting prototype for Robinhood Chain. It turns observable market and tokenization conditions into an explainable 0-100 risk score, then sends users a daily email brief and threshold alerts when conditions materially change.

**Live app:** https://rwa-risk-sentinel.up.railway.app

## Why Sentinel

Stock Tokens can remain available outside the underlying market's regular trading session. Users and autonomous agents need a simple pre-execution guardrail that answers: *are conditions normal, or is there something worth reviewing before acting?*

Sentinel is deliberately deterministic at its core. An LLM does not decide whether an asset is SAFE, CAUTION, ELEVATED, or HIGH RISK.

## How the risk engine works

Sentinel reads Robinhood asset metadata and reference quotes, then checks the canonical Robinhood Chain deployment and its onchain multiplier.

Current rules include:

| Condition | Weight |
| --- | ---: |
| No canonical Robinhood Chain deployment | +35 |
| Asset inactive | +45 |
| Trading halt | +80 |
| Quote older than 120 seconds | +30 |
| Quote older than 45 seconds | +12 |
| Bid/ask spread > 1% | +30 |
| Bid/ask spread > 0.5% | +18 |
| Bid/ask spread > 0.2% | +8 |
| Stock Token mint/burn window closed | +12 |
| Underlying not all-day tradable overnight | +18 |
| Limited extended-hours fractional tradability | +10 |
| Pending multiplier / corporate action | +14 |
| REST multiplier differs from onchain multiplier | +28 |

The score is clamped to 0-100:

- **0-20:** SAFE
- **21-40:** CAUTION
- **41-65:** ELEVATED
- **66-100:** HIGH RISK

Action guidance is deterministic too: normal monitoring, verify liquidity, limit size or wait, or wait and review.

## Current MVP

- Robinhood Chain mainnet monitoring
- Read-only wallet/address onboarding; no signature required
- User-selected Stock Token watchlists
- Deterministic 0-100 risk scoring with reasons
- Five-minute automated watcher
- Snapshot history
- Threshold-transition alerts
- Daily email risk brief
- Email verification
- Agent-facing risk/history endpoints
- Looping product animation
- Discord, Telegram, and X shown as **Coming Soon** roadmap integrations

## Optional AI research

AI is not required for Sentinel to function. The deterministic risk engine remains active with no model configured.

A future/optional research layer can use Perplexity directly or through OpenRouter to summarize current earnings, filings, halts, corporate actions, company announcements, and macro events. That context is kept separate from the market-risk score.

## Architecture

```
Robinhood asset metadata + quotes
            |
            v
Robinhood Chain contract state
            |
            v
Deterministic risk rules
            |
            +--> /api/risk/:symbol
            +--> snapshot history
            +--> 5-minute watcher
                    |
                    +--> threshold transition email
                    +--> daily email brief
```

The API service runs as a Railway Function. Subscriber state and snapshots are persisted on a Railway volume. The hero animation is stored in Railway object storage and streamed through the app with byte-range support.

## Public endpoints

```
GET /health
GET /api/assets
GET /api/overview
GET /api/risk/NVDA
GET /api/history/NVDA
GET /api/research/NVDA
POST /api/setup
GET /api/setup/:subscriberId
```

The research endpoint works without an AI key; it reports that enrichment is not configured while deterministic scoring remains active.

## Environment variables

See `.env.example`. Secrets should be configured directly in Railway and never committed.

## Roadmap

- Discord notifications
- Telegram notifications
- X delivery
- Optional event-research enrichment
- Stronger subscriber authentication
- Database-backed state for scale
- Wallet holding discovery
- Additional execution/liquidity signals where reliable data is available

## Important limitations

Sentinel is experimental, read-only research software and is not investment advice. It does not place trades, custody assets, or request transaction-signing permission.

The current prototype stores subscriber profiles by high-entropy ID and uses a Railway volume rather than a production database. Wallet addresses are currently labels/watch addresses; holdings are not automatically discovered.

## License

MIT
