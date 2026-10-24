# 24601/omnigent

This is a fork of [omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent).

## Branches

- `main` mirrors upstream `main`. It only fast-forwards. Nothing else is committed to it.
- `modyl` is upstream `main` plus the patches below. It takes upstream `main` by merge, never by rebase, so every commit pinned from it stays reachable.
- `patch/<name>` holds one patch as commits on upstream `main`. It is the branch an upstream pull request would come from.

## Patches carried on `modyl`

| Branch | Change | Upstream status |
| --- | --- | --- |
| `patch/trace-context-keep-active-parent` | `trace_context_for_response` keeps a valid, sampled active trace parent instead of always rooting a response-derived trace. The turn's AGENT span carries `omnigent.response.id`, so a response stays findable when its trace id no longer derives from the response id. | Not proposed |

## Adding a patch

1. Branch `patch/<name>` from upstream `main` and commit the change with its test.
2. Merge it into `modyl` with `git merge --no-ff patch/<name>`.
3. Add a row to the table above, on `modyl`.

When upstream merges an equivalent change, the next merge of upstream `main` into `modyl` absorbs it. Delete the `patch/` branch and its row then.

## GitHub Actions

Only `.github/workflows/ci.yml` runs on this fork. Every other upstream workflow is disabled, and the fork's sync job disables any new one each cycle. The default `GITHUB_TOKEN` is read-only, and runs for pull requests from outside contributors need approval.

[Pull request #1](https://github.com/24601/omnigent/pull/1), `modyl` into `main`, stays open so CI runs on every push to `modyl`. It is never merged.
