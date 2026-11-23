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

## Agents in this repo

| Agent | Use for | Source |
|---|---|---|
| `cpa-fact-checker` | Verifying rules, rates, deadlines, citations | Original |
| `naver-blog-writer` | Naver blog drafts | Original |
| `seo-specialist` | SEO audit of this site | ECC (MIT), adapted |
| `marketing-agent` | Campaigns and copy | ECC (MIT), adapted |

Only these parts of ECC were adopted, on purpose. Its language-specific code reviewers, its TDD and 80%-coverage rules, and its rule to call agents automatically do not fit this repository. See `.claude/THIRD_PARTY_NOTICES.md` for the licence.
