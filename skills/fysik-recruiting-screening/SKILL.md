---
name: fysik-recruiting-screening
description: Screen candidates for Fysik roles on BOSS直聘 or 猎聘 from a supplied JD, chat queue, new-greeting list, recommendation feed, or search-results page. Use for JD-to-criteria decomposition, exhaustive evidence-backed candidate classification, Shanghai expected-location filtering, stable-ID deduplication, shortlist reporting, and optional temporary in-page highlighting. Default to screening only; never contact candidates or schedule interviews without explicit authorization.
---

# 飞捷科思招聘筛选

Turn a live recruiting queue or search result into a traceable shortlist. Report what was actually reviewed; never treat a visible first screen or an all-job counter as full coverage.

## Required inputs

Obtain or confirm:

- The full JD, active position, platform, and target page or queue.
- Any hard conditions: expected work location, degree/school, age, experience, industry, and exclusions.
- The requested result: a bounded sample, full relevant-queue scan, or a target number of matches.
- Whether temporary visual marking is requested. Treat marking as local presentation, not a native platform action.

If a required fact is unavailable, state the limit and request the JD or readable result cards. Do not infer live access or completion.

## Workflow

### 1. Convert the JD into a decision card

Write four short lists before opening resumes:

1. **Hard filters** — failure means reject.
2. **Priority evidence** — rank direct matches.
3. **Migration evidence** — classify separately; never present as a direct match.
4. **Exclusions** — reject even when title or city appears promising.

For technical roles, require project or delivery evidence rather than a keyword-only match. Generate search terms only after the decision card is complete.

### 2. Verify the live context

Check the logged-in browser or platform dependency first. Then verify the active job title, selected tab or queue, applied filters, and visible scope. Re-check after navigation or filter changes because the active position can drift.

Apply hard platform filters early. `期望城市` or `期望工作地=上海` is the Shanghai gate; current residence, employer location, or a Shanghai text mention is not a substitute.

Read [platform-adapters.md](references/platform-adapters.md) for the relevant BOSS or 猎聘 page pattern. Treat selectors as hints and inspect the current DOM before use.

### 3. Collect candidates without overstating coverage

Use a stable platform candidate/resume ID as the deduplication key, not name. For virtual or incrementally loaded lists:

1. Record the initial visible IDs.
2. Scroll in increments and wait for rendering.
3. Append newly observed IDs to a cross-batch record.
4. Stop only at the relevant end-of-list signal or at the user-agreed review bound.

Keep the active-job scope separate from platform-wide counters. For dynamic recommendation feeds, report the reviewed batches and say that absent historical IDs are not currently found.

### 4. Extract evidence and classify

Before reading a right-side detail panel, confirm that its name or stable ID matches the selected card. Do not use a stale panel.

Evaluate hard filters first, then classify each unique candidate as one of:

- `高匹配` — satisfies hard filters and has direct evidence for priority requirements.
- `高迁移` — satisfies hard filters but needs a stated role, industry, or technical transition.
- `待核验` — an essential fact is missing or identity cannot be verified.
- `淘汰` — fails a hard filter or exclusion; record the shortest factual reason.

Store one concise evidence sentence per decision. Never pad a requested count with weak candidates.

### 5. Report and optionally mark

Deliver a table containing candidate ID, name if visible, classification, supporting evidence, and the specific missing fact or rejection reason. Add:

- Active position, page/tab, and filters used.
- Reviewed and deduplicated counts; identified match counts by class.
- A clear coverage statement: full relevant queue, bounded sample, or incomplete with reason.

Only add in-page visual markers when requested. Confirm a marker on a currently rendered target. Explain that injected CSS/DOM markers are temporary, disappear on refresh, and do not alter candidate state.

## Safety boundaries

- Default to read, classify, and report only. Do not click `打招呼`, initiate chat, accept a resume, schedule an interview, or change candidate state without explicit approval.
- Preserve candidate IDs and evidence in the work record when the queue is dynamic.
- Distinguish verified resume facts from external research, and cite external sources when research is used.
- If browser access, an expected-location field, or panel identity cannot be verified, return `待核验` or stop; do not make a positive claim.

## Failure recovery

- **The first screen looks complete:** continue incremental collection and dedupe before claiming full coverage.
- **The selected resume does not change:** wait, verify identity, then retry once; otherwise skip it as `待核验`.
- **The page changes after a filter click:** re-verify active job, tab, and filters before continuing.
- **The live platform cannot be read:** disclose this immediately and ask for result-page screenshots or card text; then classify only the supplied material.
