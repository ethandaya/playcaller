# Playcaller

Football shorthand for AI engineering workflows. Tell your agent **how to work**,
not just what to build. One portable skill; no runtime or plugins.

## Install

```sh
npx skills@latest add ethandaya/playcaller --skill calling-plays
```

Choose your agent and installation scope. In an existing Amp thread, reload skills.
For manual installation, copy `skills/calling-plays` into `.agents/skills/`
(Amp/Codex) or `.claude/skills/` (Claude Code).

## Call a play

```text
QB Spider — fix the refresh-token race
```

**Calls execute immediately. Add `?` to plan first, then `QB Set` to start.**
If the task is already clear, just `QB Spider` is enough. Without `QB`, talk normally.

| Call | What it does |
| --- | --- |
| **Hard&nbsp;Count** | Investigate one question; recommend, no edits. |
| **Read&nbsp;Option** | Investigate two questions; recommend next steps and draft commit/PR text, no edits. |
| **RPO** | Compare up to two approaches through experiments, implement the winner, verify. |
| **Spider** | Failing regression test → smallest component fix → verification. |
| **Dive** | Fix a named file/symbol; ask before editing a separate test file. |
| **Mesh** | Coordinate two worker investigations; combine findings, no product edits. |
| **Sneak** | Small localized fix plus its existing regression test; verify. |

## Examples

**Investigate without editing:**
```text
QB Hard Count — why does login slow down after a session refresh
```

**Plan a feature, then start after review:**
```text
QB RPO Red:multiview — add per-pane URL, back, forward and volume controls?
```
Follow with `QB Set` when ready. `Red:multiview` limits edits to that component and its tests.

**Compare without implementing:**
```text
QB Read Option — compare cursor and offset pagination for our activity feed
```

**Fix, verify, and draft the handoff:**
```text
QB Spider Red:auth Ready — reject tokens at their exact expiry time
```
`Ready` adds draft commit/PR text. It does not commit or publish.

## Change or stop a play

- `QB Timeout` — pause new actions; keep work.
- `QB Set` — start a stored plan or resume Timeout.
- `QB Kill` — cancel without deleting or reverting.
- `QB Omaha Ready` — change the finish and resume; preserve the rest.
- `QB Omaha Ready?` — propose the change and pause; repeat without `?` to apply.

Names accept overrides: `Under`/`Gun` for self/workers, `Solo`/`Twins`/`Trips` for
investigation questions, `Goal:`/`Red:`/`Open:` for scope, and `Budget:N` for discovery
limits. Questions are not candidate approaches: RPO still caps candidates at two.
Gun workers investigate; the coordinator owns implementation.

Choose one play per call. No versions or `; Set` suffix. No play grants permission
to push, deploy, delete, or modify shared data. These are agent instructions, not
enforced permissions; use with supervision.

[Full rules and aliases](skills/calling-plays/SKILL.md) · [MIT](LICENSE)
