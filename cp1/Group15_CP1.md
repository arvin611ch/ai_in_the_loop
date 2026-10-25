# CP1 — Group 15

**Team:** 蕭群恩 (114950007)、江晟維 (113611097)、王祥麟 (113304035)、簡惟捷 (110654013)
**Repository:** https://github.com/arvin611ch/ai_in_the_loop
**Project:** Study Alignment Board

---

## 1. Team Charter

### How we make decisions when we disagree

A decision needs evidence, not a vote. For a disagreement about correctness we reproduce the behaviour and add or run a test that distinguishes the competing claims. For a disagreement about style, the existing formatter, linter and documented project conventions take precedence.

If evidence does not settle it, **the current code steward makes the final call** and records the choice and the reasoning in `DECISIONS.md`. The code steward rotates, and everyone serves at least twice, so no single person holds the tie-break for the whole semester. This process is written in `AI_USAGE_GUIDELINES.md` §3 and has been in force since Week 3.

### Definition of done

A piece of work is done when all of the following are true:

1. It is in a pull request, not on `main` directly — `main` has branch protection, so this is enforced rather than agreed.
2. The PR description follows `.github/PULL_REQUEST_TEMPLATE.md`: one sentence on what it does, and if a significant choice was made, the decision, why, and who led it.
3. The relevant tests and checks pass.
4. **Someone other than the person who wrote it can explain it.** This is the bar we use instead of "it works", because it is the one that catches code nobody understands.
5. The PR states whether AI contributed, and names the tool and the prompt-log entry if it did.
6. If the change alters the team's design, scope, workflow or evaluation approach, `DECISIONS.md` gets an entry.
7. A reviewer has approved and the PR is merged.

### How we communicate outside class

**Channel.** A LINE group for day-to-day coordination, and GitHub PR comments for anything about code or a decision. We keep those separate on purpose: LINE is for "I pushed something", the PR is for "here is why".

**How often.** We do not hold a fixed standing meeting. Communication is event-driven: whoever pushes work announces it in the LINE group, and the group converges before each checkpoint deadline.

**What we expect from each other.** A PR announced in the LINE group gets a review **within 24 hours**. Whoever has time claims it first; if nobody has claimed it after 24 hours, the current code steward either reviews it or says in the group when they can.

We set an explicit number because our original arrangement was "whoever has time picks it up", and that has no floor — if everyone is busy in the same week, a PR can sit unreviewed with nobody having broken any agreement. The 24-hour rule plus the code steward as fallback means there is always someone accountable for the next move.

---

## 2. Problem Statement with Evidence

### What the problem is, and who experiences it

University students in two-to-five-person study groups preparing for technical courses, especially computer-science exams where the group divides topics among its members.

The specific failure is this: the group splits the syllabus, each member studies their part, and then **nobody can tell which topics are actually covered, which two explanations contradict each other, and who is responsible for resolving an uncertain one.** Those three facts exist only scattered across chat messages. A member has to ask in the group chat "has anyone done chapter 4?", wait, and often get no clear answer — so the group arrives at the exam believing a topic was handled when the person who claimed it was themselves unsure.

### How we know the problem is real

At the time of submission (Sunday 25 October, end of Week 7) we have **not yet completed** the two required conversations, so this criterion is unsupported in this version. We are saying so plainly rather than filling the section with our own assumptions.

What we have arranged:

- **Interviewee 1 — 盧同學**, a student in the 百川 interdisciplinary bachelor programme who prepares for exams with a study group, and who has agreed to talk with us.
- **Interviewee 2 — 林同學**, a Computer Science student who studies for technical courses in a group, and who has agreed to talk with us.

Both are outside the project team. We will hold the two conversations in the first days of Week 8 and add the write-ups to this section in the repository through a pull request, so that the version on `main` carries the evidence.

For each conversation we will record who the person is (course, year, group size), the concrete thing that went wrong in their own words, what they currently do instead, and what they said they would want. The questions are kept in the past tense so that we get events rather than opinions:

1. Have you prepared for an exam with a group and split the chapters between you? How many people, and which course?
2. After splitting, how did you know whether the others had actually finished their part? Did it ever turn out that nobody had covered something?
3. Did two people ever explain the same thing differently? How was it settled?
4. Did you coordinate over LINE, a shared document, or something else? Which part was the most annoying?

If either person tells us that this problem does not happen to them, we will record that as-is and revise the problem statement to match what we heard.

### Why existing tools do not adequately solve it

Groups today use a combination of **LINE or Discord** for discussion and a **shared Google Doc** for the notes themselves. Each covers half the job and neither covers the gap between them.

- **LINE / Discord.** Coverage and disagreement are discussed, but the answers are embedded in a scrolling conversation. There is no view that answers "which topics have no owner?" — reconstructing it means reading back through the thread, so in practice nobody does.
- **Google Doc.** It holds the final notes well, but it has no notion of *confidence* or *disagreement*. Two contradictory explanations of the same topic sit next to each other as equally authoritative paragraphs, and a reader cannot tell that one of the authors was unsure. Comments can flag a conflict, but nothing tracks whether it was resolved or who owns it.
- **Shared flashcard tools (Anki, Quizlet).** These assume the content is already correct and agreed. They are for memorising a settled answer, not for reaching one.

What is missing in all three is a place where *coverage, disagreement and ownership* are first-class and visible at a glance, rather than being things you have to reconstruct.

---

## 3. Initial Interaction Design Sketch

### What the tool does

**Study Alignment Board** turns a group's separate notes and uneven understanding into one shared, agreed exam-preparation guide. The group lists the topics for an exam. Each member contributes a short explanation for the topics they took, together with how confident they are. The board then shows the group three things it currently cannot see: which topics nobody has covered, which topics have two explanations that disagree, and who is on the hook for resolving each unsettled item. When every topic is either agreed or explicitly owned, the group publishes the shared guide.

### Inputs and outputs

| | |
|---|---|
| **Inputs** | A topic list for the exam (entered once, by anyone). Per topic per member: a short written explanation, and a self-reported confidence level (for example low / medium / high). An optional flag that a member disagrees with an existing explanation. An owner assignment for an unresolved topic. |
| **Outputs** | A per-topic status for the whole group: *covered and agreed*, *covered but disputed*, *covered but low confidence*, or *not covered*. A list of unresolved items with an owner and nothing else needed to chase them. A published shared guide containing the agreed explanation for each topic, with any remaining disagreement shown rather than silently resolved. |

### How two people interact with it

A worked example with two members, A and B:

1. **A** adds the topic list for the exam and takes topics 1–4. **B** takes 5–8.
2. **A** writes an explanation for topic 2 and marks confidence *low*. The board shows topic 2 as *covered but low confidence* to everyone, not just to A.
3. **B** reads A's topic 2, thinks it is wrong, and submits a competing explanation with confidence *high*. The board now shows topic 2 as **disputed** — this is the state that chat and a Google Doc cannot represent.
4. Either member assigns an owner for topic 2. B takes it, because B is the one claiming the correction.
5. B checks the lecture notes, and either confirms their own version or restores A's. B records which, and the topic moves to *agreed*.
6. Neither member can publish the shared guide while any topic is *disputed* or *not covered*. The board makes the remaining work visible, so the decision to publish is explicit rather than accidental.

The key property is that **work passes between the two people through the board rather than through a message**. A does not have to tell B that topic 2 is shaky; B can see it. B does not have to remember to tell A that it was resolved; A can see that too.

---

## 4. Draft Evaluation Plan

### Success definition

We will know the tool works if an external study group can use it to turn individual notes about a short set of course topics into an agreed shared guide, **while leaving fewer unassigned or unresolved topics than when the same group does the same task with its normal chat-and-document workflow.**

We will measure, for each session:

- completion time for the task
- the number of clarification messages or comments needed to establish who covered what
- the number of topics still marked *not covered* or *disputed* at the end

The first and third are about what happens for the group, not about what the tool emits.

### Target users and how we reach them

Two to three real study groups from outside our project team, with at least two participants in each, and at least four external participants in total. We will not use our own team as the primary test population.

Access routes, in the order we will try them: classmates preparing for the same technical course this semester; peers from student clubs; and friends who already study together and have an exam coming up.

### Method and timing

**Structured observation of two comparable tasks per group**, plus a five-minute group interview at the end.

1. **Baseline:** the group completes a short study-planning task using its usual combination of chat and a shared document.
2. **Tool session:** the group completes a comparable task using Study Alignment Board.

We record task duration, clarification messages, unresolved or unassigned topics, and keep the resulting guide. The closing interview asks which workflow made it easier to see gaps and disagreement.

**Timing:** we aim to run the sessions in the weeks between CP1 and CP2, once a usable prototype of the board exists, so the results can inform CP2 rather than only report on it. Participants use non-sensitive sample notes; we do not need anyone's grades or private conversations.

### Minimum evidence threshold

At least **two complete, documented comparison sessions** with external groups, totalling at least four external participants. Each session must include both the baseline and the tool measures, plus the resulting guide.

We will treat the evidence as minimally convincing only if, **in both sessions**, the tool session produces an agreed guide with no more unresolved topics than the baseline *and* improves at least one observable measure — faster completion or fewer clarification messages.

A single good session does not count, because one group's enthusiasm is not evidence. If the results are mixed we will report the measures and the user feedback as they are rather than claiming success.

### Human–AI boundary

**The initial prototype deliberately uses no in-product AI model.** Humans submit the explanations, decide whether they agree, assign owners, and approve the final guide. The tool only structures and displays those choices.

This is a decision, not an omission. An unverified automatic summary could merge two conflicting explanations into one fluent paragraph and hide exactly the factual disagreement the group needs to discuss — which is the problem we set out to solve, so building it in would defeat the tool.

If we propose an AI-assisted summarisation feature after CP1, it will be **suggestion-only**: the AI may draft a merged explanation, and a human must accept it before it enters the guide. We would also update the success definition to measure whether users find the suggestions worth reviewing. One risk we have already identified is that an AI merger would be sensitive to how confidently each explanation is *worded*, and our data model contains a self-reported confidence field, so it could systematically favour the assertive explanation over the correct one.

---

## 5. Repository

**https://github.com/arvin611ch/ai_in_the_loop**

| Requirement | Status |
|---|---|
| Branch protection on `main` | Enabled. `GET /repos/arvin611ch/ai_in_the_loop/branches` reports `main` as `"protected": true`, and the repository has two rulesets configured. |
| PR template in place | `.github/PULL_REQUEST_TEMPLATE.md` — requires a one-sentence summary, and for any significant choice, the decision, the reason, the rejected alternative and who led it. |
| `DECISIONS.md` started | Yes, with a real entry dated 2026-09-21 recording the initial code steward and why. |
| Current code steward recorded | Yes, in `DECISIONS.md`: C.W. Arvin Chiang (`arvin611ch`), who created and initialised the shared repository during Week 3 setup. |

The repository also contains `AI_USAGE_GUIDELINES.md`, which defines our permitted and prohibited AI uses, our prompt-logging requirement, and the disagreement process quoted in §1 of this document.

---

## Open uncertainties

Per the rubric's note that acknowledged uncertainty is never penalised but unsupported claims are:

- **We have not yet run the two user conversations** that §2 requires. They are arranged with the two people named in §2 for the first days of Week 8, and the write-ups will be added to this document through a pull request. Until then, the problem statement above is our own reasoning about a situation we have each experienced, not validated evidence.
- We do not know whether the *disputed* state is something groups will actually use, or whether they will route around it and settle disagreements in chat as they do now. That is the single assumption the evaluation is designed to test.
- The timing in §4 assumes a usable prototype exists before CP2. If it does not, we will run the baseline sessions first so that at least the comparison data is not lost.
