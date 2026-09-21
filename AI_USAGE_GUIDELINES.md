# AI Usage Guidelines

> Working draft for Week 3. The team will revise these guidelines as the project and its risks become clearer.

## 1. Planned AI tools and permitted uses

### OpenAI Codex

We will use OpenAI Codex to:

- brainstorm and compare implementation or architecture options before the team makes a decision;
- generate small boilerplate components, first-draft unit tests, and documentation drafts; and
- help diagnose reproducible development errors or explain unfamiliar code.

We will not use Codex to:

- make the final architecture, product, or merge decision for the team;
- generate authentication, authorization, secrets-handling, payment, or other security-sensitive code without a human designing and carefully reviewing it; or
- merge code, approve a pull request, or replace the required human review.

All AI-generated material must be understood, edited as needed, and verified by a team member before it enters the repository. If the team wants to introduce another AI tool or a materially different use, we will first discuss it and update this document through a pull request.

## 2. Documenting AI interactions

Each team member maintains an individual prompt engineering log. A log entry is required whenever an AI interaction produces code, tests, documentation, configuration, user-facing text, or a decision that is retained in the project. The entry records:

- the prompt and relevant model output verbatim;
- the tool and model used;
- what was kept, changed, or rejected; and
- the human judgment behind that choice.

One-off syntax lookups or debugging questions do not need a log entry unless their output is committed or changes a project decision.

Every pull request states whether AI contributed to the change. When it did, the description identifies the tool used and the related prompt-log entry; it does not need to duplicate the full transcript. If an AI suggestion changes the team's actual design, scope, workflow, or evaluation approach, the reasoning is also recorded in `DECISIONS.md`. `DECISIONS.md` is the collaboration record for significant team choices, while the prompt log records the interaction itself.

## 3. Resolving disagreements about AI output quality

The current code steward has final responsibility for deciding whether AI-assisted work is ready to merge. A decision to merge requires evidence, not a vote: the change must pass the relevant tests and checks, meet the pull-request review requirements, follow the project's conventions, and be explainable by someone other than the person who prompted the AI.

For a disagreement about correctness, the team will reproduce the behavior and add or run a test that distinguishes the competing claims. For a disagreement about style, the existing formatter, linter, and documented project conventions take precedence. If evidence does not settle a significant disagreement, the code steward makes the final call and records the choice and rationale in `DECISIONS.md`.
