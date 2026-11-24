---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up. Use when the user asks to wrap up, 정리, 인수인계, 이어서 하기, or to continue the work in a new session, or when a long task is about to be split across sessions.
argument-hint: "What will the next session be used for?"
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS (`$TMPDIR`, else `/tmp`; `%TEMP%` on Windows) - not the current workspace.

Include a "suggested skills" section in the document, naming which skills the next agent should call the Skill tool for.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.

## Use in this repository

- Never save the handoff in the repository root: GitHub Pages would publish it.
- In a cloud session, save it to the session scratchpad and also show the full text in chat, because the user cannot open `/tmp`.
- Write it in Korean.

<!-- Adapted from mattpocock/skills (MIT, (c) 2026 Matt Pocock), commit abeeaf9. See .claude/THIRD_PARTY_NOTICES.md -->
