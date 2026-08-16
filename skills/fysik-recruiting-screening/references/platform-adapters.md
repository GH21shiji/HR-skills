# Platform adapters

Use these as live-page inspection starting points. The platform can change its DOM; verify the active title, filters, and candidate identity before relying on any selector.

## BOSS 沟通 / 新招呼

- Candidate rows commonly expose `.geek-item[data-id]`; retain `data-id` across scroll batches.
- Select a row on the left and read the structured resume in the right-side conversation panel. A click often does not change the URL.
- A virtual list may mount only a window of rows. Trigger scrolling, wait for the list to render, and collect IDs into one map.
- Treat the job-specific filter as the scope. A global `沟通` or `新招呼` counter is not candidate coverage for the selected role.

## BOSS 推荐牛人

- Recommendation cards may be inside `iframe[src*=recommend]` and expose `[data-geekid]` or `[data-geek]`.
- Reconfirm the requested recommendation tab and city setting before reporting any count.
- The feed is dynamic. Persist the candidate ID, name, tab, batch, and classification; a refresh or tab change can replace the current cards.

## 猎聘搜索结果

- Results may be inside `iframe[name=searchFrame]` and use incremental `点击加载更多` loading.
- Filter expected work location before detailed work-history review.
- Review cards first and open details only for candidates that pass the hard gates.

## Evidence record

Use a row per deduplicated candidate:

| Field | Required content |
|---|---|
| candidate_id | Stable platform ID or `unavailable` |
| page_scope | Platform, active job, tab/queue, batch |
| hard_filter_result | Pass/fail plus decisive reason |
| classification | 高匹配 / 高迁移 / 待核验 / 淘汰 |
| evidence | One factual sentence from the current resume/card |
| action | `none` unless the user explicitly authorizes contact |
