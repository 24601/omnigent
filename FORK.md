# 24601/omnigent

This is a fork of [omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent).

## Branches

- `main` mirrors upstream `main`. It only fast-forwards. Nothing else is committed to it.
- `modyl` is upstream `main` plus the patches below. It takes upstream `main` by merge, never by rebase, so every commit pinned from it stays reachable.
- `patch/<name>` holds one patch as a single commit on upstream `main`. It is the branch an upstream pull request would come from.

## Patches carried on `modyl`

| Branch | Change | Upstream status |
| --- | --- | --- |
| `patch/trace-context-keep-active-parent` | `trace_context_for_response` keeps a valid, sampled active trace parent instead of always rooting a response-derived trace. | Not proposed |
| `patch/stream-input-stable-id` | The session stream keeps the `input_stable_id` the runner stamps on a turn's `in_progress` and terminal events, so a sender can tell which turn answered its message. | Not proposed |

## Adding a patch

1. Branch `patch/<name>` from upstream `main` and commit the change with its test.
2. Merge it into `modyl` with `git merge --no-ff patch/<name>`.
3. Add a row to the table above, on `modyl`.

When upstream merges an equivalent change, the next merge of upstream `main` into `modyl` absorbs it. Delete the `patch/` branch and its row then.

## GitHub Actions

Actions is disabled on this fork. Upstream's workflows target GitHub-hosted runners and do not run here.
