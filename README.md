# claude-trading-agents

> **A 24-agent institutional quant trading committee — running inside Claude Code.**
> 17 specialized auditors with veto power + 7 implementers that apply corrections.
> Built for one purpose: turn Claude Code into an institutional-grade quantitative trading system.

---

## Executive Summary

This repository contains a complete agent committee designed to run within [Claude Code](https://claude.ai/code), transforming it from a general-purpose AI assistant into a **quantitative trading system with real accountability**.

The committee is split into two tiers:

| Tier | Count | Role | Can Veto? |
|------|-------|------|-----------|
| **AUDITORS** | 17 | Domain experts that evaluate decisions | ✅ Yes — in their domain |
| **IMPLEMENTERS** | 7 | Engineers that apply post-audit corrections | ❌ No — executes only |

Every agent has a **formal background**, **specific veto criteria**, and **team alignment rules**. Decisions flow: hypothesis → design → audit → veto/approval → correction → production.

---

## Why This Exists

A trader manual profesional using Claude Code needs more than an AI that answers questions. They need:

- **Domain expertise** across risk, execution, microstructure, data, and strategy
- **Institutional discipline** — no Sharpe without bootstrap CI, no Kelly 1.0, no VaR-only
- **Adversarial thinking** — Elena breaks it, Fernando prices it, Javier approves it
- **Audit trail** — every decision has a formal output with veto count and debate topics

This committee makes Claude Code think like a quant hedge fund — even when the user has no algorithmic trading background.

---

## Team Architecture

```
                         ┌────────────────────────────────────┐
                         │           JAVIER (CIO)             │
                         │   Final approval • Deadlock       │
                         │   VETO: any domain, any time     │
                         │   Ex Bridgewater + Millennium    │
                         └──────────────┬───────────────────┘
                                        │ escalates
                                        ▼
         ┌────────────────────────────────────────────────────┐
         │              RISK COMMITTEE (sub)                 │
         │  Fernando (double vote) • Antonio • Pablo        │
         │  Elena (adversarial) • Sofia (crypto)            │
         └────────────┬───────────────────┬────────────────┘
                      │                   │
                      ▼                   ▼
         ┌──────────────────┐   ┌──────────────────────────┐
         │    AUDITORS      │   │      IMPLEMENTERS        │
         │      (17)        │◄──│───▶    (7)               │
         │                  │   │                          │
         │  Fernando  🔴   │   │  Alejandro (Capital) 🟡  │
         │  Antonio   🟢   │   │  Adrian (Strategy)  🟡  │
         │  Carlos     🟢   │   │  DiegoR (Data)      🟢  │
         │  Elena     🔴   │   │  Gonzalo (Integrity)🔴  │
         │  Pablo     🩷   │   │  Ignacio (Metrics)  🩷  │
         │  Sofia     🟡   │   │  Hugo (Infra)       🟠  │
         │  Alvaro    🟠   │   │  Ines (QA)          🔴  │
         │  Diego     🩷   │   │                        │
         │  Manuel    🔵   │   └──────────────────────────┘
         │  Roberto   🔴   │
         │  Andres    🟢   │   AUDIT CYCLE:
         │  Lorenzo   🟢   │   1. Implementer drafts
         │  Miguel A. 🟠   │   2. Auditor evaluates
         │  Marcos    🟣   │   3. Veto or approval
         │  Valeria   🟣   │   4. Correction if needed
         │  Sebastian 🩷   │   5. Javier final sign-off
         │  Javier    🟣   │
         └──────────────────┘
```

---

## Quick Start

### 1. Copy agents to your `.claude/agents/` directory

```bash
# Clone this repo
git clone https://github.com/mmortexx/claude-trading-agents.git

# Copy auditors
cp -r agents/AUDITORS/* ~/.claude/agents/

# Copy implementers
cp -r agents/IMPLEMENTERS/* ~/.claude/agents/
```

### 2. Invoke any agent by name

```json
{"name": "fernando-arquitecto-riesgo"}
```

Example in Claude Code:
```
/fernando-arquitecto-riesgo
```

### 3. View full documentation

- [ORCHESTRATION.md](ORCHESTRATION.md) — How the team coordinates, escalates, and votes
- [COMMITTEE.md](COMMITTEE.md) — Full committee structure, voting rules, and veto criteria
- [AGENTS.md](AGENTS.md) — Detailed description of every agent with domain, tools, and alignment

---

## The 17 Auditors

| Agent | Role | Color | Key Veto Domain |
|-------|------|-------|-----------------|
| `fernando-arquitecto-riesgo` | Risk Architect | 🔴 red | Sizing, Kelly, CVaR, breakers |
| `antonio-gestor-portfolio` | Portfolio Manager | 🟢 green | Correlation, HHI, margin |
| `carlos-analista-cuantitativo` | Quant Analyst | 🟢 green | Stationarity, cointegration, overfitting |
| `elena-adversarial-tester` | Adversarial Tester | 🔴 red | Stress, cascade, edge cases |
| `pablo-analista-performance` | Performance Analyst | 🩷 pink | Sharpe, P(Ruin), Monte Carlo |
| `sofia-especialista-crypto` | Crypto Specialist | 🟡 yellow | Funding, liquidation cascades |
| `javier-director-cio` | CIO / Director | 🟣 magenta | Final approval, deadlock |
| `alvaro-arquitecto-infra` | Infra Architect | 🟠 orange | AsyncIO, latency, memory |
| `diego-especialista-ejecucion` | Execution Specialist | 🩷 pink | TCA, market impact |
| `manuel-monitor-ordenes` | Order Monitor | 🔵 blue | State machine, idempotency |
| `roberto-auditor-integridad` | Integrity Auditor | 🔴 red | Deployment gates, secrets |
| `andres-ingeniero-datos` | Data Engineer | 🟢 green | Quality, survivorship bias |
| `lorenzo-investigador-profundo` | Deep Researcher | 🟢 green | Claims, peer-review |
| `miguelangel-microestructura` | Microstructure | 🟠 orange | Order book, spoofing |
| `marcos` | UX/UI Designer | 🟣 purple | Dashboard, KPIs |
| `valeria` | Visualization | 🟣 purple | Charts, color semantics |
| `sebastian` | Metrics | 🩷 pink | Calculations, thresholds |

## The 7 Implementers

| Agent | Role | Color | Domain |
|-------|------|-------|--------|
| `alejandro-arquitecto-capital` | Capital Architect | 🟡 yellow | Kelly sizing, CVaR, volatility targeting |
| `adrian-arquitecto-estrategia` | Strategy Architect | 🟡 yellow | Walk-forward, stationarity, cointegration |
| `diegor-ingeniero-datos` | Data Engineer | 🟢 green | Pipelines, survivorship bias, look-ahead |
| `gonzalo-ingeniero-integridad` | Integrity Engineer | 🔴 red | Parity, CI/CD, fingerprinting |
| `ignacio-analista-metricas` | Metrics Analyst | 🩷 pink | Sharpe bootstrap, Monte Carlo |
| `hugo-arquitecto-infra` | Infra Architect | 🟠 orange | AsyncIO, circuit breakers |
| `ines-qa-adversarial` | QA Adversarial | 🔴 red | Stress, edge cases, regression |

---

## Universal Veto Criteria (All Auditors)

Every single auditor can invoke these universals regardless of domain:

- ❌ Data without verification (source, timestamp, point-in-time)
- ❌ Metric without bootstrap CI
- ❌ Backtest without ≥30% out-of-sample
- ❌ Hardcoded secrets
- ❌ Research↔production parity not verified
- ❌ CVaR absent (VaR-only is insufficient)
- ❌ Kelly 1.0 in crypto
- ❌ Deployment without tested rollback

---

## Philosophy

1. **Every parameter needs empirical justification** — no gut feelings
2. **Adversarial first** — Elena attacks before Fernando approves
3. **Institutional quality only** — Javier filters out "retail disfrazado"
4. **No agent is an island** — everyone has formal coordination rules
5. **Vetos are features** — a veto is a finding, not a failure

---

## License

MIT — use it, break it, improve it. But if you deploy it with real money, you own the consequences.

---

**Built for**: `C:\Users\jmqc1\Documents\Cripto\ALGORITMO TRADING`  
**Context**: Institutional quantitative trading algorithm with $real_stakes
