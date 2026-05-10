# Tool: vocab-translator

## Name and purpose

Applies the vocabulary translation table in `repo-registry.md` to a block of text, normalizing terms when work crosses repos.

## Invocation contract

```
vocab-translator --from <repo> --to <repo> [--input <path>] [--output <path>]
```

| Argument | Type | Default | Notes |
|---|---|---|---|
| `--from` | string | required | Source repo whose vocabulary the input uses |
| `--to` | string | required | Target repo whose vocabulary should be applied |
| `--input` | path | stdin | Markdown or plaintext |
| `--output` | path | stdout | Translated text |

## Behavior

1. Read the translation table from `repo-registry.md`
2. For each row where source and target repos both have entries, perform a whole-word substitution from the source term to the target term
3. Annotate every substitution inline with a comment: `<!-- vocab: <source-term> -> <target-term> -->`
4. If a term appears in the input but is not in the translation table, leave it untouched and add a `<!-- vocab: unknown <term> -->` marker

## Outputs

Translated text. Substitution annotations preserved by default; strip with `--strip-comments`.

## Errors

| Code | Meaning |
|---|---|
| 0 | Success |
| 10 | `--from` or `--to` not in registry |
| 20 | No translations applied (warn only) |

## Permissions

- Read access to `repo-registry.md`
- No network access
