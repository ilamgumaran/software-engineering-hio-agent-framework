# Tool: cross-repo-link-validator

## Name and purpose

Walks every repo in the family, reads each `AGENTS.md` and the central `multi-repo-orchestration/` files, and verifies that all trace links resolve.

## Invocation contract

```
cross-repo-link-validator [--repo <owner/name>] [--strict]
```

| Argument | Type | Default | Notes |
|---|---|---|---|
| `--repo` | string | (all in registry) | Limit to a single repo |
| `--strict` | flag | off | Fail on warnings (e.g., link to a non-canonical branch) |

## Behavior

1. Read `multi-repo-orchestration/repo-registry.md` to enumerate the family
2. For each repo, fetch `AGENTS.md` from the default branch
3. Extract every link that targets another repo in the family or the central spec
4. Resolve each link via GitHub API (HEAD request)
5. Build a report: repo, link, status, suggested fix if any

## Outputs

Markdown report to stdout. Sections:

- Summary counts
- Failures (404s, redirects, missing files)
- Warnings (links to feature branches, fragile path references)

## Errors

| Code | Meaning |
|---|---|
| 0 | All links resolve |
| 10 | One or more failures |
| 20 | One or more warnings, only fails when `--strict` |
| 30 | Cannot read registry |

## Permissions

- Read access to all repos in the family
- No write access (this tool is read-only)
