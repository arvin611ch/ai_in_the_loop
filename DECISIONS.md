# Decisions Log

## 2026-09-21 — Initial code steward
**What:** C.W. Arvin Chiang (arvin611ch) is the initial code steward for the team.
**Why:** Arvin created and initialized the team's shared repository during the Week 3 setup.

## 2026-11-24 — Adopt the course PR template (Week 12)
**What:** Replace `.github/PULL_REQUEST_TEMPLATE.md` with the Week 12 course template at `.github/pull_request_template.md`, keeping our Decision block at the end.
**Why:** Our old template only asked what the PR does and whether a decision was made. Across PRs #1–#5 every PR was AI-assisted, but none said what the author changed after the AI or how the change was checked, and every approval was empty or "ok". The new template asks for both.
**Alternative rejected:** Keeping both files. GitHub picks one template, and two files with names that differ only in case is confusing.
**Led by:** C.W. Arvin Chiang

## 2026-11-24 — Make three AI usage rules checkable from a PR; approve Claude Code (Week 12)
**What:** Rewrite rules 1.1 (approved tools), 2.1 (AI assistance in every PR) and 3.1 (an approval explains the change) in `AI_USAGE_GUIDELINES.md`, and add Claude Code to the approved tools.
**Why:** In PRs #1–#5, three PRs used Claude Code while the guidelines named only Codex. No PR said what the author changed after the AI, and all seven approvals were empty or "ok". The Week 3 wording could not be checked from a PR.
**Alternative rejected:** Keep the Week 3 wording and remind each other in LINE.
**Led by:** C.W. Arvin Chiang
