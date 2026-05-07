# Cost Policy — HIO

## Principles
1. Developers should never have to think about which model to use — routing
   in `model-routing.md` decides.
2. Cost controls are levers, not gates. Tighten or loosen centrally.
3. Cost outcomes (cost/ticket, cost/repo) matter more than raw token counts.

## Budgets
- Default per-session token budget: 200K input / 32K output (Sonnet tier).
- Opus tier: 300K input / 64K output, gated on escalation criteria.
- Soft alert at 80% of session budget; hard cap at 100% with summarize-and-resume.

## Escalation Criteria for Opus
At least one of:
- Change spans ≥ 3 services.
- Change touches database schema in production path.
- Security-sensitive code (auth, crypto, PII handling).
- Architectural decision affecting ≥ 2 teams.

## Monitoring
Centrally tracked: token spend per developer/week (by tier), per repo/week,
cost per ticket, model tier distribution, rejected agent output rate.

## Alerts
- Single session > 2× average token budget.
- Opus usage > 30% of total weekly tokens (likely misrouted).
- Rising rejected output rate (skills or context likely stale).
