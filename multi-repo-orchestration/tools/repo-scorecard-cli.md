# Tool: repo-scorecard-cli

## Name and purpose

A CLI invocation that runs the `agentic-scorer` skill against a target repo and produces a scorecard.

## Invocation contract

```
repo-scorecard --repo <owner/name> --mode <baseline|re-score> [--previous <path>] [--output <path>]
```

| Argument | Type | Default | Notes |
|---|---|---|---|
| `--repo` | string | required | Owner/name on GitHub |
| `--mode` | enum | required | `baseline` or `re-score` |
| `--previous` | path | none | Required when `--mode=re-score` |
| `--output` | path | `multi-repo-orchestration/scoring/scorecard-<name>.md` | Where to write the result |

## Behavior

1. Resolve the target repo and verify access (read-only)
2. Invoke the `agentic-scorer` skill with the inputs
3. Write the resulting markdown scorecard to `--output`
4. Update `multi-repo-orchestration/scoring/summary.md` with the new row
5. Exit non-zero if the scorer returned any stop conditions

## Outputs

- A scorecard markdown file at `--output`
- An updated `summary.md`
- A printable summary table on stdout: dimension, level, evidence excerpt

## Errors

| Code | Meaning |
|---|---|
| 0 | Success |
| 10 | Repo not found or no read access |
| 20 | Stop condition raised; scorecard partial |
| 30 | `--mode=re-score` without `--previous` |
| 40 | Output path not writable |

## Permissions

- Read access to target repo
- Write access to `multi-repo-orchestration/` in the operational hub repo
- No network access beyond GitHub API
