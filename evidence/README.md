# PRTS-525 — Qwen Code status integration: live evidence

Captured 2026-08-05 on the Orca dev build compiled from this branch, with
`qwen` (Qwen Code) 0.21.5 running in an Orca-managed terminal
(`qwen-evidence`). The sidebar worktree card lists Qwen Code as a status
agent with the same three-state treatment as Kimi.

## Images

| File | Shows |
|---|---|
| `agent-cards-working.png` | Card row `qwen-evidence – Qwen Code` mid-turn: orange working indicator, label resolves to **Qwen Code** (not the `qwen-code` slug), alongside two earlier `done` rows |
| `agent-cards-done.png` | Same row after the turn: green done check with the turn's prompt preview (`# A History of …`) |
| `full-window-working.png` | Full dev-app window during the working state |
| `full-window-done.png` | Full dev-app window after the turn completed |

## CLI evidence (same session)

`orca-dev terminal wait --for tui-idle` on the idle qwen pane resolves via the
ready-prompt fast path:

```json
{"handle": "term_b22ac49c-4fc8-4336-b92f-9a481f74e465", "condition": "tui-idle", "satisfied": true, "status": "running", "exitCode": null}
```

`orca-dev worktree ps --json` agents[] during the turn:

```json
{"agentType": "qwen-code", "state": "working", "prompt": "list 5 fruits, one per line", "toolName": "glob"}
```

and after the turn: `{"agentType": "qwen-code", "state": "done", ...}` with
`lastAssistantMessage` populated.

This folder is evidence-only; it can be dropped on merge if maintainers prefer
screenshots hosted elsewhere.
