# orchestrator-demo

Animated, self-contained demo of the **PR Conveyor Belt** agent orchestrator — a
GitHub-centered conveyor belt for autonomous coding agents.

→ **[View the rendered demo](https://e3f-six.github.io/orchestrator-demo/)** —
a single static HTML page (no dependencies, works offline), hosted via GitHub Pages.

The pipeline:

```
Design doc → Planner → Coder → Reviewers (Claude + Codex) → Babysitter → Merge gate
```

GitHub labels are the durable state machine
(`agent:ready → in-progress → pr-open → review-needed → merge-ready → done`). A single
work item flows along the belt; when the reviewers request changes it loops back through
the **Babysitter** and rejoins the review queue — the core loop of the system.

Open `index.html` directly, or view it via the link above.

Source orchestrator: <https://github.com/e3f-six/orchestrator>
