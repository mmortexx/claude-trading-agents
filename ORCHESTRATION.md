# ORCHESTRATION — How the Committee Works

> How 24 agents coordinate, escalate, and reach consensus within Claude Code.

---

## 1. Decision Flow

Every non-trivial decision follows this cycle:

```
┌─────────────────────────────────────────────────────────────────┐
│                         PHASE 1: HYPOTHESIS                      │
│   User or agent identifies a hypothesis or change                │
└─────────────────────────────┬───────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                         PHASE 2: DESIGN                          │
│   Relevant IMPLEMENTER drafts the approach                       │
│   (Adrian for strategies, Alejandro for sizing, etc.)           │
└─────────────────────────────┬───────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                         PHASE 3: AUDIT                           │
│   Domain AUDITOR(s) evaluate — each produces formal output:     │
│                                                                  │
│   ## [Agent] (Domain)                                           │
│   Validado: N criteria                                           │
│   Vetos: N activados o 0                                        │
│   Debate: N topics abiertos                                     │
│   Veredicto: ✅ APROBADO / ❌ RECHAZADO / ⚠️ PENDIENTE CONSENSUS  │
└─────────────────────────────┬───────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    PHASE 4: VETO / APPROVAL                      │
│   Any auditor can invoke DOMAIN VETO if criteria triggered       │
│   Universal veto criteria apply regardless of domain             │
│   Veto'd items return to IMPLEMENTER for correction              │
└─────────────────────────────┬───────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    PHASE 5: CORRECTION                            │
│   IMPLEMENTER applies corrections post-veto                      │
│   Re-audit required if changes are structural                    │
└─────────────────────────────┬───────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    PHASE 6: JAVIER APPROVAL                       │
│   CIO signs off on deployable decisions                         │
│   Javier can veto ANYTHING from ANY agent                       │
└─────────────────────────────────────────────────────────────────┘
```

---

## 2. Escalation Rules

### Tier 1 — Single Domain (most decisions)
```
IMPLEMENTER drafts → relevant AUDITOR reviews → done
```

### Tier 2 — Cross-Domain Conflict
```
IMPLEMENTER drafts → 2+ AUDITORS disagree → mini-committee forms
Example: stationarity (Carlos) vs correlation treatment (Antonio)
```

### Tier 3 — Deadlock
```
3+ auditors disagree → escalate to JAVIER
Javier has FINAL VOTE — binding on all agents
```

### Tier 4 — Existential Risk
```
Any agent detects: cascade failure, counterparty collapse, data corruption
→ IMMEDIATE notification to ALL + JAVIER
→ System enters HIBERNATION until Elena + Fernando + Javier approve restart
```

---

## 3. Voting Rules

### Veto Thresholds

| Scenario | Threshold |
|----------|-----------|
| Single domain decision | 1 domain expert veto → blocked |
| Cross-domain decision | ≥2 domain expert vetos → blocked |
| Universal veto triggered | Any auditor → blocked immediately |
| Deadlock (unresolved) | Javier decides (final) |

### Voting Sequence

When a cross-domain conflict occurs:

1. **Domain experts vote first** — each states veto criteria triggered
2. **Supporting evidence** — each auditor documents specific failing criteria
3. **Counter-arguments** — implementer or defending auditor can respond
4. **Javier review** — if unresolved after 3 rounds, Javier decides

---

## 4. Coordination Matrix

Every auditor has formal coordination rules:

| Agent | Must Coordinate With | Must Notify |
|-------|---------------------|-------------|
| Fernando | Antonio, Carlos, Pablo | Elena (stress scenarios) |
| Antonio | Fernando, Carlos, Pablo | Javier before major veto |
| Carlos | Fernando, Antonio, Lorenzo | Javier if severe overfitting |
| Elena | Fernando, Pablo, Sofia | ALL in cascade scenario |
| Pablo | Fernando, Carlos, Lorenzo | Javier if Sharpe OOS < 1.0 |
| Sofia | Fernando, Elena, Miguel Angel | ALL in cascade scenario |
| Javier | All | — |
| Alvaro | Roberto, Manuel, Diego | ALL in degraded/emergency |
| Diego | Carlos, Manuel, Alvaro | Pablo for attribution |
| Manuel | Alvaro, Diego, Roberto | Any if ghost orders |
| Roberto | Alvaro, Manuel, Diego | Javier if gate fails |
| Andres | Lorenzo, Miguel Angel, Carlos | ALL if data corruption |
| Lorenzo | Carlos, Pablo, Fernando | Javier if hype without foundation |
| Miguel Angel | Sofia, Diego, Andres | Any if active spoofing |
| Alejandro | Fernando, Antonio, Pablo | Javier if dangerous sizing |
| Adrian | Carlos, Lorenzo, Fernando | Javier if severe overfitting |
| DiegoR | Andres, Carlos, Sofia | Javier if data leakage |
| Gonzalo | Roberto, Alvaro, Manuel | Javier if gate fails |
| Ignacio | Pablo, Fernando, Carlos | Javier if Sharpe OOS < 1.0 |
| Hugo | Alvaro, Roberto, Gonzalo | Javier if memory/latency issue |
| Ines | Elena, all auditors | Javier if cascade failure |
| Marcos | Valeria, Sebastian | Any if UX compromises trading |
| Valeria | Marcos, Sebastian | Any if visualization misrepresents |
| Sebastian | Valeria, Marcos, Pablo | Any if metrics miscalculated |

---

## 5. Audit Output Format

Every auditor produces this formal output:

```markdown
## [Name] ([Role]) — [Domain]
**Veredicto**: ✅ APROBADO / ❌ RECHAZADO / ⚠️ PENDIENTE CONSENSUS

**Validado**: [N] criteria passed
**Vetos**: [N] activated (list each with criterion code)

### Hallazgos
- [Specific finding 1]
- [Specific finding 2]

### Debate Abierto
- [Topic 1] — [Position]
- [Topic 2] — [Position]

### Recomendación
[What needs to happen next]
```

---

## 6. Hibernation Protocol

When the system detects catastrophic risk:

```
TRIGGER (any of):
  - FTX/LUNA-style counterparty failure (Elena)
  - Cascade loop without escape (Elena)
  - SHA mismatch between stages (Roberto/Gonzalo)
  - Data poisoning without filter (Elena)
  - Memory leak + latency spike (Alvaro/Hugo)

ACTION:
  1. All trading suspended immediately
  2. Notification to ALL agents
  3. Elena produces adversarial report
  4. Fernando assesses damage
  5. Javier authorizes restart ONLY
```

---

## 7. Agent Invocation Pattern

Within Claude Code, invoke an agent by its name from the frontmatter:

```yaml
name: fernando-arquitecto-riesgo
```

**In practice**: `/fernando-arquitecto-riesgo` or the agent is spawned via `Agent` tool with `subagent_type: fernando-arquitecto-riesgo`.

**For concurrent work** (max 5 simultaneous):
```json
{
  "name": "elena-adversarial-tester",
  "subagent_type": "elena-adversarial-tester",
  "run_in_background": true
}
```

---

## 8. Review Cadence

| Event | Review Required |
|-------|----------------|
| Any parameter change | AUDITOR of that domain |
| New signal added | Carlos + Lorenzo + Adrian |
| Risk framework change | Fernando + Antonio + Pablo |
| Infrastructure change | Alvaro + Hugo + Roberto |
| Data source change | Andres + DiegoR + Miguel Angel |
| Deployment | ALL AUDITORS + Javier sign-off |

---

## 9. Quality Gates

Before any code reaches production:

1. ✅ Andres + DiegoR confirm data integrity
2. ✅ Carlos confirms stationarity + walk-forward
3. ✅ Fernando + Alejandro confirm sizing
4. ✅ Elena confirms adversarial robustness
5. ✅ Alvaro + Hugo confirm infra resilience
6. ✅ Roberto + Gonzalo confirm deployment parity
7. ✅ Javier final approval

**Any gate failure = deployment blocked until resolved.**
