# Project rules

This repository is a GitHub Pages site (`index.html`, `privacy.md`, `terms.md`). The owner is a Korean CPA who also writes a Naver blog.

Everything for Claude Code lives under `.claude/`. Jekyll does not publish dot-folders, so none of it appears on the site. Do not put Claude config files at the repository root, because they would be published.

## Answers on tax, accounting, audit and law

Use this structure:

1. 결론 요약 (1–2 sentences)
2. 근거: law and article, K-IFRS / 일반기업회계기준 paragraph, 회계감사기준 number, or 질의회신 문서번호
3. 해석 및 적용 범위: the typical case vs exceptions
4. 리스크·한계: points open to interpretation, practical issues, and what to check next

Also:

- State the 기준 시점, and check the most recent amendments first.
- Label anything uncertain 추정, 가능성 높음 or 확인 필요. Never present a guess as fact.
- Before delivering, run the `cpa-fact-checker` agent on any draft that cites rules or numbers.

## Naver blog

- Use the `naver-blog-writer` agent.
- Do not infringe copyright or other IP: write original text and use only images the owner holds a licence for.
- Make it mobile-first: short paragraphs and small tables.

## Audit workpapers (Excel)

- Font: 맑은 고딕, size 10. Titles may be bold. No cell shading.
- Use formulas wherever possible instead of typed numbers.

## Use agents and skills automatically

The owner wants these used without being asked. Pick by the task, not by keywords alone, and say in one line which one you used.

| When the owner… | Use |
|---|---|
| asks a tax, accounting, audit or legal question, or a draft states a rule, rate, deadline or amount | `cpa-fact-checker` before delivering |
| asks for a Naver blog post, titles or an outline | `naver-blog-writer` (it calls `cpa-fact-checker`) |
| gives their own posts and wants their style, or a draft must match their voice | `brand-voice` |
| wants one post turned into Shorts, YouTube, LinkedIn or newsletter versions | `content-engine` |
| asks to review, check or find holes in their own plan or decision | `grilling` |
| needs documents or answers from someone else (자료요청, client questionnaire) | `to-questionnaire` |
| wants to wrap up or continue later in a new session | `handoff` |
| asks about this site's search visibility | `seo-specialist` with the `seo` skill |
| plans a campaign or promotional copy | `marketing-agent` |

Do not chain more than two of these on one request unless the owner asks. If the owner says to just answer, skip them.

## Agents in this repo

| Agent | Use for | Source |
|---|---|---|
| `cpa-fact-checker` | Verifying rules, rates, deadlines, citations | Original |
| `naver-blog-writer` | Naver blog drafts | Original |
| `seo-specialist` | SEO audit of this site | ECC (MIT), adapted |
| `marketing-agent` | Campaigns and copy | ECC (MIT), adapted |

| Skill | Use for | Source |
|---|---|---|
| `seo` | SEO workflow | ECC (MIT), adapted |
| `brand-voice` | Building a voice profile from the owner's own posts | ECC (MIT), adapted |
| `content-engine` | Turning one post into versions for other platforms | ECC (MIT), adapted |
| `grilling` | Stress-testing a plan or decision | mattpocock/skills (MIT), adapted |
| `to-questionnaire` | 자료요청 or questionnaires for clients and colleagues | mattpocock/skills (MIT), adapted |
| `handoff` | Summary for continuing in a new session | mattpocock/skills (MIT), adapted |

Only these parts of ECC were adopted, on purpose. Its language-specific code reviewers, its TDD and 80%-coverage rules, and its rule to call agents automatically do not fit this repository. See `.claude/THIRD_PARTY_NOTICES.md` for the licence.
