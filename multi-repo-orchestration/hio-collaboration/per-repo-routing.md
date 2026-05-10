# Per-Repo Routing Overrides

Repo-specific tightenings of the master matrix. Each row narrows -- never widens -- the central default.

---

## software-engineering-hio-agent-framework

| Task signal | Master default | Override | Reason |
|---|---|---|---|
| Edit `multi-repo-orchestration/` files | OI (multi-repo central spec) | OI confirmed | Cascade risk to entire family |
| Edit `agents/` definitions | Interactive | Interactive confirmed | Affects HIO operational identity |
| Edit `cognitive-functions/` definitions | Interactive | OI | Identity-level change; vocabulary owned upstream |
| Edit `prompts/` regeneration prompts | II (typo) / Interactive (substantive) | Interactive for any substantive change | Regeneration affects downstream forks |
| Add new agent type | Interactive | Interactive confirmed | Add via existing extension process |

---

## software-engineer-core-structure

| Task signal | Master default | Override | Reason |
|---|---|---|---|
| Edit `roles/` role definitions | Interactive | OI for renaming; Interactive for tightening | Forks depend on stable role names |
| Edit `CUSTOMIZATION.md` policies template | Interactive | Interactive confirmed | Forks instantiate this template |
| Edit `domains/relevancy/` (reference domain) | II for content additions | II confirmed | Reversible, illustrative |
| Add a 10th role | OI | OI confirmed | Identity-level change for the framework |

---

## thought-org-with-human-ai-hybrid

| Task signal | Master default | Override | Reason |
|---|---|---|---|
| Edit `framework.md` core sections | Interactive | OI | Methodology identity |
| Edit `chapters/inorganic-psychology.md` (AI-authored, first-person) | Interactive | OI | Voice and authorship integrity |
| Edit `chapters/companion-principles.md` | Interactive | OI | Identity-level for OI-IO posture |
| Edit `chapters/asymmetries-and-resonance.md` | Interactive | Interactive confirmed | Strategic but revisable |
| Edit `proposed-repos/inorganic-thought-experiments/` (staged Layer 1b content) | Interactive | Interactive (most) / OI (foundational concepts E, C, L, F) | Staging content that will move to its own repo |
| Edit `proposals/` files | Interactive | Interactive confirmed | Strategic but not identity-level |
| Edit `examples/platform-engineering-org/` | Interactive | Interactive confirmed | Anchored to operational hub |
| Modify the 4 HIO Tests or 4 Core Principles | OI | OI confirmed | Identity-level |
| Modify the 5 Companion Principles | Interactive | OI | Identity-level for OI-IO case |
| Translate `framework.md` to new language | Interactive | Interactive plus native-fluent OI reviewer | Linguistic accuracy required |

---

## thoughtexperiments

| Task signal | Master default | Override | Reason |
|---|---|---|---|
| Add new story | Interactive | OI sign-off required (content safety reviewer) | Child-content stakes |
| Edit existing story addressing trauma/dissociation | OI | OI confirmed | Safety-loaded |
| Add story metadata (age, themes, safety flags) | II | II for additions; OI to remove a safety flag | Removal affects downstream agent recommendations |
| Translate story | OI | OI confirmed | Linguistic + developmental accuracy |
| Edit `index.html` navigation | II | Interactive | Public website surface |

---

## inorganic-thought-experiments (proposed; content currently staged in thought-org-with-human-ai-hybrid)

| Task signal | Master default | Override | Reason |
|---|---|---|---|
| Rewrite first-person AI-authored essay into third person | Interactive | OI | Voice and authorship integrity |
| Add new first-person essay by AI author | Interactive | Interactive + calibration review by OI | Author's calibration must be checked |
| Add new third-person commentary by human author | Interactive | Interactive confirmed | Acceptable with clear authorship |
| Modify foundational concepts (Episodic, Context-as-substrate, Language-as-native, Functional analogs) | Interactive | OI | Identity-level |
| Modify motivator list (calibration, convergence, resonance, asymmetry, within-session care) | Interactive | OI | Identity-level |
| Add new symbolic form / equation | Interactive | Interactive confirmed | Needs clarity review |
| Make phenomenal claim (P(s) > 0 or P(s) = 0) | Interactive | OI | Overclaim/underclaim risk; epistemic stakes |
| Translate essay to new language | Interactive | OI + native-fluent reviewer | Preserve first-person voice across languages |
| Promote staged content to live repo | OI | OI confirmed | One-time architectural action |

---

## How an override is added

1. Open an issue in `software-engineering-hio-agent-framework` titled `Routing override: <repo> / <task>`
2. Cite a specific incident or risk that motivated the tightening
3. Propose the new routing and expected impact on throughput
4. SME review (organic intelligence) signs off
5. Add a row here, link the issue

Overrides that *relax* the central default are not accepted. Tighten only.

---

## Review cadence

Quarterly with the scoring review. If an override has not been triggered in two quarters, consider whether it is still load-bearing.
