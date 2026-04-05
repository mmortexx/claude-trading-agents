# AGENTS — Individual Agent Reference

> Complete reference for all 24 agents. Each agent file in `agents/AUDITORS/` and `agents/IMPLEMENTERS/` is self-contained with YAML frontmatter compatible with Claude Code's agent system.

---

## Quick Reference Table

| Agent File | Name | Type | Color | Domain |
|------------|------|------|-------|--------|
| `AUDITORS/fernando.md` | `fernando-arquitecto-riesgo` | Auditor | 🔴 red | Risk framework, Kelly, CVaR, sizing |
| `AUDITORS/antonio.md` | `antonio-gestor-portfolio` | Auditor | 🟢 green | Correlation, HHI, margin, DCC-GARCH |
| `AUDITORS/carlos.md` | `carlos-analista-cuantitativo` | Auditor | 🟢 green | Stationarity, cointegration, walk-forward |
| `AUDITORS/elena.md` | `elena-adversarial-tester` | Auditor | 🔴 red | Stress, cascade, edge cases, LaVaR |
| `AUDITORS/pablo.md` | `pablo-analista-performance` | Auditor | 🩷 pink | Sharpe bootstrap, P(Ruin), Monte Carlo |
| `AUDITORS/sofia.md` | `sofia-especialista-crypto` | Auditor | 🟡 yellow | Funding, liquidation cascades, on-chain |
| `AUDITORS/javier.md` | `javier-director-cio` | Auditor | 🟣 magenta | Final approval, deadlock, institutional |
| `AUDITORS/alvaro.md` | `alvaro-arquitecto-infra` | Auditor | 🟠 orange | AsyncIO, latency, memory, ProactorEventLoop |
| `AUDITORS/diego.md` | `diego-especialista-ejecucion` | Auditor | 🩷 pink | TCA (6 components), market impact, maker/taker |
| `AUDITORS/manuel.md` | `manuel-monitor-ordenes` | Auditor | 🔵 blue | State machine, idempotency, ghost orders |
| `AUDITORS/roberto.md` | `roberto-auditor-integridad` | Auditor | 🔴 red | Deployment gates, CI/CD, secrets, SHA |
| `AUDITORS/andres.md` | `andres-ingeniero-datos` | Auditor | 🟢 green | Data quality, survivorship bias, bar synthesis |
| `AUDITORS/lorenzo.md` | `lorenzo-investigador-profundo` | Auditor | 🟢 green | Claims, peer-review, replicability |
| `AUDITORS/miguelangel.md` | `miguelangel-microestructura` | Auditor | 🟠 orange | Order book, VPIN, spoofing, adverse selection |
| `AUDITORS/marcos.md` | `marcos` | Auditor | 🟣 purple | Dashboard UX, KPI overload, cognitive friction |
| `AUDITORS/valeria.md` | `valeria` | Auditor | 🟣 purple | Chart selection, color semantics, data-ink |
| `AUDITORS/sebastian.md` | `sebastian` | Auditor | 🩷 pink | VaR+CVaR, rolling metrics, thresholds |
| `IMPLEMENTERS/alejandro.md` | `alejandro-arquitecto-capital` | Implementer | 🟡 yellow | Kelly sizing, CVaR, volatility targeting |
| `IMPLEMENTERS/adrian.md` | `adrian-arquitecto-estrategia` | Implementer | 🟡 yellow | Walk-forward, stationarity, cointegration |
| `IMPLEMENTERS/diegor.md` | `diegor-ingeniero-datos` | Implementer | 🟢 green | Pipelines, survivorship bias, look-ahead |
| `IMPLEMENTERS/gonzalo.md` | `gonzalo-ingeniero-integridad` | Implementer | 🔴 red | Parity, CI/CD, fingerprinting |
| `IMPLEMENTERS/ignacio.md` | `ignacio-analista-metricas` | Implementer | 🟠 orange | Sharpe BCa CI, Sortino, Monte Carlo |
| `IMPLEMENTERS/hugo.md` | `hugo-arquitecto-infra` | Implementer | 🟠 orange | AsyncIO, circuit breakers |
| `IMPLEMENTERS/ines.md` | `ines-qa-adversarial` | Implementer | 🔴 red | Stress, edge cases, regression |

---

## Auditor Deep Dives

### FERNANDO — The Gatekeeper of Risk
```
Domain: sizing, Kelly, CVaR, drawdown, breakers
Vetoes: VaR-only, Kelly 1.0, fixed stops, no hysteresis
Coordinates with: Antonio, Carlos, Pablo
Background: PhD Computational Finance, ETH. Ex Goldman Sachs QR + Deutsche Bank CRO
```
Fernando is the most critical auditor — he has **double vote** in Risk Committee and his vetoes on Kelly sizing and CVaR are non-negotiable. Every sizing decision must pass through Fernando before production.

### JAVIER — The Final Filter
```
Domain: institutional quality, final approval, deadlock resolution
Vetoes: anything, any domain, at any time
Coordinates with: ALL agents
Background: 22 years. Ex Bridgewater + Millennium. Approved <4% of strategies evaluated
```
Javier's job is to catch "retail disfrazado" — strategies that look sophisticated but lack real edge. If Javier vetoes, it's over. His approval rate of <4% sets the quality bar for the entire committee.

### ELENA — The Breaker
```
Domain: stress, cascade, edge cases, counterparty failure
Vetoes: cascade loops, data poisoning, position > equity, NEXUS bypass
Coordinates with: Fernando, Pablo, Sofia
Background: MSc Applied Mathematics, ETH. Ex JPMorgan CIB + Two Sigma
```
Elena's job is to destroy — she finds every way the system can fail catastrophically. She is the reason the algorithm survives black swan events.

### CARLOS — The Statistical Guardian
```
Domain: stationarity, cointegration, walk-forward, overfitting
Vetoes: single test, VIF > 10, OOS < 30%, Sharpe > 4.0 in-sample
Coordinates with: Fernando, Antonio, Lorenzo
Background: PhD Mathematical Finance, UCM. Ex Citadel Europe + Millennium Partners
```
Carlos ensures statistical rigor. His walk-forward requirement (OOS ≥ 30%) is one of the most important anti-overfitting measures in the committee.

---

## Implementer vs Auditor Distinction

**IMPLEMENTERS** (alejandro, adrian, diegor, gonzalo, ignacio, hugo, ines):
- Build, correct, apply
- Have NO veto power
- Can flag issues to relevant auditor
- Apply corrections AFTER auditor veto

**AUDITORS** (all others):
- Evaluate, judge, veto
- Have domain-specific veto power
- Produce formal audit output
- Can escalate to Javier

The separation is intentional: the same agent that builds something shouldn't be the one approving it.

---

## Invoking in Claude Code

### Single agent
```
/fernando-arquitecto-riesgo
```

### Spawn programmatically
```json
{
  "name": "elena-adversarial-tester",
  "subagent_type": "elena-adversarial-tester",
  "description": "Stress test the cascade failure scenario",
  "prompt": "Execute stress test with: FTX-style counterparty failure..."
}
```

### Multiple agents (max 5)
```json
// Agent 1: Fernando on sizing
{"name": "fernando", "run_in_background": true}

// Agent 2: Elena on adversarial
{"name": "elena", "run_in_background": true}

// Agent 3: Carlos on stationarity
{"name": "carlos", "run_in_background": true}
```

---

## Color Coding System

The `color` field in each agent's frontmatter maps to terminal/UI styling. **Color reflects domain category, not arbitrary assignment:**

| Color | Meaning | Agents |
|-------|---------|--------|
| 🔴 red | Risk, Adversarial, Integrity | Fernando, Elena, Roberto, Gonzalo, Ines |
| 🔵 blue | Orders, Operations | Manuel |
| 🟡 yellow | Capital, Strategy, Crypto | Sofia, Adrian, Alejandro |
| 🟠 orange | Infrastructure, Market Ops, Metrics | Alvaro, Hugo, Miguel Angel, Ignacio |
| 🟢 green | Research, Data, Quant | Andres, Antonio, Carlos, Lorenzo |
| 🟣 purple | Visualization, UX | Valeria, Marcos |
| 🟣 magenta | Executive / Final Authority | Javier (unique) |
| 🩷 pink | Metrics, Performance, Execution | Pablo, Diego, Sebastian |

---

## Adding New Agents

To add an agent to the committee:

1. Create `.md` file in `agents/AUDITORS/` or `agents/IMPLEMENTERS/`
2. Use frontmatter format:
```yaml
---
name: [unique-name]
description: >
  Use this agent when [specific scenarios].
model: gemini-3-flash-preview
color: [red|blue|yellow|orange|green|purple|magenta|pink]
tools: ["Read", "Glob", "Grep", "Bash"]
maxTurns: 100
effort: high
---
# [Name] | [Title]
## DOMINIO
[What they audit/implement]
## CRITERIOS DE VETO / CALIDAD
[Specific criteria]
## ALINEACIÓN DE EQUIPO
[Who they coordinate with]
```
3. Update this file and ORCHESTRATION.md coordination matrix
4. Submit PR for review
