---
name: liepin-candidate-screening
description: Screen Liepin candidates for Chinese recruiting tasks with strict resume-number deduplication, Shanghai expected-location checks, age and education filters, industry exclusions, role-fit judgment, and conservative anti-risk browser behavior. Use when the user asks Codex to search or evaluate candidates on 猎聘/Liepin, especially for embedded software, robotics, embodied AI, smart hardware, consumer electronics, supplier management, or similar hiring searches.
---

# Liepin Candidate Screening

Use this skill to keep Liepin recruiting searches accurate, conservative, and consistent with the user's screening preferences.

## First Principles

- Prioritize quality over count. Do not fill a quota with candidates who fail hard requirements.
- Treat `期望工作地` as a hard field. Do not substitute current city, work history city, company location, or school city for expected work location.
- Keep a running exclusion ledger of all resume IDs already returned in the current thread. Before presenting results, remove any ID that appeared in earlier final answers or candidate lists.
- Distinguish search-hit evidence from confirmed resume evidence. If a keyword such as `RK3588` appears only because the search result matched, but the card does not show the chip/project details, label it as needing detail review.
- Use Chinese in user-facing screening output unless the user asks otherwise.

## Browser Safety

- Use the web-access skill for all network and browser interaction.
- Avoid bulk or high-frequency behavior on Liepin: do not mass-open resumes, rapidly switch keywords, scrape many pages, contact candidates, or perform uncontrolled repeated actions.
- Prefer current-page reading and low-frequency manual-style checks. Insert pauses between searches when continuing.
- Stop and report if the site becomes slow, shows abnormal prompts, asks for verification, or appears to trigger risk controls.
- Do not use screenshots or OCR for resume screening when DOM/text extraction is available.

## Screening Order

Apply these checks in order. Exclude on hard failures before spending effort on softer evaluation.

1. Deduplicate by resume ID against the current thread's exclusion ledger.
2. Confirm `期望工作地` includes Shanghai for Shanghai-based searches.
3. Check age. Prefer candidates from 25 to 40. Treat candidates over 40 as cautious exceptions only when the resume is exceptionally aligned.
4. Check target role fit. For embedded searches, look for embedded software, Linux/RTOS, driver, BSP, kernel, U-Boot, Buildroot/Yocto, board bring-up, MCU, SDK, camera/AI module, edge device, or similar work.
5. Apply industry focus and exclusions.
6. Check education. When requested, prefer `统招211本科以上`; do not treat non-unified, adult, self-study, or junior-college-to-bachelor credentials as strict matches unless the user has relaxed the rule.
7. Check job-seeking urgency when visible. Prefer `急寻新工作`, `离职`, or clearly active candidates, but do not override hard requirements.

## Embedded Candidate Rules

For embedded software searches:

- Prioritize robotics, embodied AI, intelligent hardware, consumer electronics, IoT/edge AI, AI camera, smart devices, drones, industrial smart hardware, or similar industries.
- Exclude automotive industry candidates unless the user explicitly allows them.
- Do not include candidates whose core experience is unrelated software, pure algorithm, testing-only, quality-only, manufacturing-only, or project management-only unless the target request allows it.
- For RK3588, Rockchip, NPU, Linux BSP, or edge AI platform searches, separate:
  - `强匹配`: resume/card clearly shows the platform, chip, board bring-up, BSP, driver, SDK, or relevant project work.
  - `待复核`: search result matched the keyword but the visible card does not show the chip/project evidence.
  - `不推荐`: no visible embedded/platform evidence, wrong expected city, wrong industry, duplicate ID, or hard education/age failure.

## Procurement Candidate Rules

For supplier management or procurement searches:

- Prioritize candidates who can build supplier management or procurement systems from 0 to 1.
- Expand to intelligent hardware and consumer electronics procurement only when relevant to the user's request.
- Exclude automotive industry candidates when the user says not to consider automotive.
- Exclude direct procurement, production procurement, and supplier quality management candidates when the user has ruled them out.
- Prefer candidates around age 35, with the broader age rule of 25 to 40 unless exceptionally matched.

## Output Format

- Provide resume IDs first, with brief reasons only when useful.
- If there are strict and weaker candidates, split them into `推荐` and `待复核/谨慎` rather than mixing them.
- When fewer candidates meet the hard criteria than requested, say so plainly and explain which constraint limited the result.
- Mention explicitly that duplicates were removed.
- Do not claim a candidate is confirmed for a technology, location, education, or urgency unless the visible evidence supports it.
