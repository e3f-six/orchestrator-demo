# orchestrator-demo

Animated, self-contained demo of the **PR Conveyor Belt** agent orchestrator — a
GitHub-centered conveyor belt for autonomous coding agents.

→ **[View the rendered demo](https://e3f-six.github.io/orchestrator-demo/)** —
a single static HTML page (no dependencies, works offline), hosted via GitHub Pages.

## Pipeline

```
Design doc → Planner → Coder → Reviewers (Claude + Codex) → Babysitter → Arbiter → Merge gate
```

A single work item flows along the belt as one card.

## State machine (GitHub labels)

GitHub labels are the durable state. The happy path (every label is prefixed `agent:`):

```
ready → in-progress → pr-open → review-needed → approved → merge-ready → done
```

Three branches hang off the review stage:

- **Changes requested** — the card loops back through the **Babysitter** for up to two
  cheap patch rounds (re-review between each), then rejoins the review queue
  (`MAX_REVIEW_ROUNDS=3`).
- **Arbitration** — if review still doesn't converge, the **Arbiter** (an agent with
  final authority) breaks the deadlock and decides **SHIP** or **REDO**.
- **Blocked** — the rare human terminal (`agent:blocked`); there are no other dead-ends.

## Run it

Open `index.html` directly, or use the [hosted demo](https://e3f-six.github.io/orchestrator-demo/).

Source orchestrator: <https://github.com/e3f-six/orchestrator>
