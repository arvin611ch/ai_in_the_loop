# Evaluation Plan

> Week 3 working draft. This defines a testable starting direction for the project and will be revised after user research in Checkpoint 1.

## Working project direction

**Study Alignment Board** helps university study groups turn separate notes and different levels of understanding into one shared, agreed exam-preparation guide. Each member contributes a short explanation and confidence level for a topic; the group can see missing coverage, conflicting explanations, and who will resolve each item before publishing the shared guide.

## Problem grounding

### Who has the collaboration problem?

University students in two-to-five-person study groups preparing for technical courses, especially computer-science exams where the group divides topics among members.

### What do they do instead today?

They exchange screenshots and messages in LINE or Discord, then manually copy notes into a Google Doc. Members must ask in chat which topics are covered, whether two explanations disagree, and who will verify an uncertain section. Those answers are often scattered across several messages and are easy to miss.

### What would observably change if the tool worked?

Before a study session ends, every planned topic would visibly be marked as covered, missing, or needing discussion; each unresolved item would have an owner. Members would produce one agreed guide without searching old chat messages to reconstruct the group's understanding.

## Evaluation plan draft

### Success definition

We will know the tool works if an external study group can use it to turn individual notes about a short set of course topics into an agreed shared guide, while leaving fewer unassigned or unresolved topics than when using its normal chat-and-document workflow. We will measure completion time, the number of clarification messages or comments needed to establish coverage, and the number of topics still marked missing or disputed at the end of the task.

The initial prototype does **not** use an in-product AI model. Humans submit explanations, decide whether they agree, assign owners, and approve the final guide; the tool only structures and displays those choices. This is deliberate: an unverified automatic summary could hide a factual disagreement that the group needs to discuss. If an AI-assisted summarisation feature is proposed after CP1, it will be suggestion-only and this success definition will be updated to measure whether users find its suggestions worth reviewing.

### Target users

We will recruit two to three real study groups outside our project team, with at least two participants in each group. Likely access routes are classmates preparing for the same technical course, student-club peers, and friends who already study together. We will not use our own project team as the primary test population.

### Method

Each group will complete two comparable, short study-planning tasks using a supplied set of course topics and individual note fragments:

1. **Baseline:** use its usual combination of chat and a shared document.
2. **Tool session:** use Study Alignment Board to contribute notes, flag coverage and disagreements, assign an owner, and approve a shared guide.

We will run structured observations and record the task duration, clarification messages/comments, unresolved or unassigned topics, and the final shared-guide artifact. We will finish with a five-minute group interview asking which workflow made it easier or harder to identify gaps and disagreement. Participants will use non-sensitive sample notes; no grades or private conversations are needed.

### Minimum evidence threshold

At least two complete, documented comparison sessions with external groups (and at least four external participants total) are required. Each session must include the baseline and tool measures plus the resulting guide. We will treat the early evidence as minimally convincing only if the tool session produces an agreed guide with no more unresolved topics than the baseline and improves at least one observable measure—faster completion or fewer clarification messages—in both sessions. If results are mixed, we will report the measures and user feedback honestly rather than claiming success.
