---
name: grilling
description: Grill the user relentlessly about a plan, decision, or idea. Use when the user shares a plan or decision and asks to review, check or stress-test it (감사계획, 블로그 기획, 세무·회계 처리 방향, 사업 계획 등), asks 허점·빈틈·리스크 찾아줘 or 검토해줘 about their own plan, or uses any 'grill' trigger phrases. Do not use for simple factual questions.
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the whole frontier in one round: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Word each question so "yes" accepts your recommended answer.

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent with a fresh context window to find it; don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report; ask the rest of the frontier now. The _decisions_ are the user's: put each to them and wait.

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Do not act on it until the user confirms you have reached a shared understanding.

## Use in this repository

- Ask in Korean, in business style, and keep each round short (3–5 questions) for mobile reading.
- When a recommended answer rests on a rule (세법, K-IFRS, 감사기준), cite it and label anything uncertain 추정 or 확인 필요.
- If the user says to skip the interview and just answer, stop grilling and answer.

<!-- Adapted from mattpocock/skills (MIT, (c) 2026 Matt Pocock), commit abeeaf9. See .claude/THIRD_PARTY_NOTICES.md -->
