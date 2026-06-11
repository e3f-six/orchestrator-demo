# orchestrator-demo

Animated, self-contained demo of the **PR Conveyor Belt** agent orchestrator — a
GitHub-centered conveyor belt for autonomous coding agents.

→ **[View the rendered demo](https://e3f-six.github.io/orchestrator-demo/)** —
a single static HTML page (no dependencies, works offline), hosted via GitHub Pages.

The pipeline:

```
Design doc → Planner → Coder → Reviewers (Claude + Codex) → Babysitter → Arbiter → Merge gate
```

GitHub labels are the durable state machine
(`agent:ready → in-progress → pr-open → review-needed → approved → merge-ready → done`,
with the `changes-requested`/`patching` loop, an `arbitration` escalation, and a rare
`blocked` terminal). A single work item flows along the belt. When reviewers request
changes the card loops back through the **Babysitter** for one cheap patch round and
rejoins the review queue (`MAX_REVIEW_ROUNDS=2`); if it still doesn't converge, the
**Arbiter** — an agent with final authority — breaks the deadlock (SHIP or REDO). No
human dead-ends: `agent:blocked` is the rare last resort.

Open `index.html` directly, or view it via the link above.

Source orchestrator: <https://github.com/e3f-six/orchestrator>
