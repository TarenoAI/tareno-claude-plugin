---
name: tareno-social-ops
description: Use Tareno to inspect social accounts and posts, analyze performance metrics, derive content strategy, manage media, create or update drafts, and request approval-backed scheduling, publishing, rescheduling, or deletion.
---

# Tareno Social Operations

Use the bundled Tareno MCP tools for account-specific social-media work. Tareno is the source of truth for connected accounts, platform rules, post state, analytics, media, and approval-action status.

## Connection and access

- If Tareno is not connected, use the MCP connection flow and complete sign-in at `https://tareno.co`.
- Never request, copy, log, or place a Tareno access token in a prompt, URL, file, or tool argument.
- Work only with workspaces and social accounts returned for the authenticated Tareno user.

## Resolve context first

1. Call `list_workspaces` when workspace context matters and none is selected.
2. Call `list_accounts` before account-scoped work unless fresh account IDs are already present in the conversation.
3. If more than one account matches an ambiguous platform or name, ask the user to choose.
4. Before drafting, scheduling, or publishing for an account, call `get_platform_schema`.
5. Call `get_platform_options` when Pinterest boards or TikTok creator details are required.

## Analytics-first workflow

For performance questions or content recommendations:

1. Call `get_analytics_overview` for the requested period; use `month` only if the user gives no period.
2. Use `get_platform_analytics` for account or platform drill-downs.
3. Use `get_content_strategy` for analytics-backed recommendations and repurposing opportunities.
4. Clearly separate observed metrics from recommendations and do not invent missing values or imply unsupported causation.
5. Tie every recommendation to a returned metric, trend, or content pattern.

## Drafts, scheduling, and publishing

- Prefer `create_drafts` when copy, targets, or timing are still exploratory. Draft creation never publishes externally.
- Use `update_draft` only for an existing editable draft.
- Use `schedule_posts`, `publish_posts`, `reschedule_post`, or `update_scheduled_post` only after the user clearly requests that outcome and provides enough target, content, and timing detail.
- Use ISO 8601 timestamps with a UTC offset plus an IANA timezone for scheduled work.
- Give each consequential request a new stable `idempotencyKey`; never reuse it for a different operation or payload.
- Scheduling, publishing, scheduled edits, and deletion create a Tareno approval action. State that approval is required, summarize the exact impact, and provide the returned Tareno approval URL.
- Do not claim a consequential action completed until `get_action_status` reports success.
- Use `delete_post` only for a draft or scheduled post after the user explicitly asks to delete it.

## Media and results

- Use `list_media` before asking the user to upload an asset that may already be in the Tareno media library.
- `upload_media_from_url` accepts only public HTTPS image or video URLs. Reject local paths, private-network URLs, embedded credentials, and non-HTTPS sources.
- Lead with the result or decision. For analytics, include period, key metrics, and evidence-backed recommendations. For approval actions, include targets, timing, approval status, and the approval link.
