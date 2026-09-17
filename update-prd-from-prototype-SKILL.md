---
name: update-prd-from-prototype
description: Create or update a Chinese PRD from approved prototype images, Axure/Figma exports, mind maps, an existing PRD, or product-rule changes. Use for scoped requirement edits, screenshot synchronization, three-column PRDs, PRD integrated boards with screenshots/arrows/requirement cards, and explicit activity-logic validation. This skill consumes approved prototype images; it does not generate or edit single-state prototype PNGs.
---

# Update PRD From Prototype

## Contract And Ownership

Use the latest PRD as the baseline, preserve its current presentation mode, and change only the requested requirement surfaces.

- `三列表格模式`: `需求模块 / 原型截图 / 需求描述`.
- `PRD 一体画板模式`: approved prototype screenshots, labelled interaction arrows, and complete editable requirement cards on one Pencil board.
- This skill owns requirement reasoning, PRD/DOCX/TAPD text, requirement cards, PRD integrated-board composition, writeback, and readback.
- It may crop or place approved prototype images, but must not generate, redraw, patch, or promote single-state prototype PNGs. Use `activity-prototype-image2-workflow` for that work.
- An `原型状态大画板` is the prototype skill's multi-state visual overview; it is not a `PRD 一体画板` and does not replace requirement cards.

## Cross-Model And Capability Policy

Apply the same evidence priority, modes, scope, validation depth, and readback gates on GPT-5, GPT-6, and later models.

- GPT-6 must preserve the same three-column/PRD-integrated-board routing and the exact five-column activity-validation format defined below. It must not invent a new output shape or status.
- Detect Documents, Pencil, TAPD, Enterprise WeChat, rendering, and other capabilities from tools actually callable in the current runtime; a newer model does not imply a plugin or permission exists.
- Adapt only to documented tool schemas. Never invent arguments, silently switch to an unofficial connector, or treat a successful write response as proof without reading the target back.
- Keep prompts model-neutral: identify source, affected scope, retained content, requested mutation, and verification criteria.

## Reference Routing

Load only what the task requires:

- Read `references/prd-output-modes.md` when creating a PRD, resolving/changing its mode, composing a PRD integrated board, or replacing a TAPD table with a board image.
- Also read `references/pencil-integrated-board-delivery.md` when exporting, compressing, packaging, or regenerating a PRD integrated board. It is the canonical source for dimensions, the 8192 export gate, 5 MB sharing, Pencil dependencies, package layout, and final readback.
- Read relevant sections of `references/activity-prd-completeness.md` for activity PRDs. Run its full checklist only when the user explicitly asks to校验、检查 or走查活动逻辑.
- Read `references/activity-prd-document-structure.md` when creating or normalizing an activity PRD's document-level headings.
- Read `references/family-glory-prd-pattern.md` for family荣耀远征/守擂战.
- Read `references/axure-activity-requirement-patterns.md` for complex Axure activities with multi-stage rankings, regional/global timing, live-room surfaces, invitation/assistance, or draws. Reuse patterns, never source-specific values.

## Evidence And Product-Rule Gates

Treat completeness references as internal question checklists, never as product-rule sources.

1. Use this evidence priority: explicit user correction/confirmation → latest PRD → explicit rule document or mind map → visible/interactive prototype evidence. Older files and patterns may reveal conflicts but may not fill current gaps.
2. Before writing, build an internal map with `module / proposed statement / source artifact / exact evidence / status`. Do not expose it in the formal PRD.
3. Ask before filling a missing decision that changes eligibility, scoring, time, rewards, inventory, budget, settlement, state transitions, interaction ownership, or display frequency. Consolidate blockers into one short round.
4. Use `[001]`, `[002]`, and so on for configurable costs, thresholds, counts, caps, durations, rank capacities, reward amounts, and settlement times unless final values are explicitly confirmed. Preserve formulas and structural numbering.
5. For gift-scoring activities, the standing default is all supported room types (`多人房`, `单人房`, `永续房`), IM, and `贴吧` gift sending unless the current source explicitly narrows it. Still resolve sender/receiver ownership and scoring dimension.
6. When gift metadata is maintained in a separate configuration sheet, missing gift ID, formal name, or icon is not a PRD gap. The PRD must still explain the evidence-backed gift/scoring/display behavior.
7. For live-room popups, panels, and education prompts, when no narrower display restriction is defined, write the direct trigger `用户进入任意直播间时展示...`. This does not define frequency, deduplication, App/device scope, participation, ranking, rewards, scoring, blacklist, or settlement.
8. Every gameplay module must state global unified time or configured regional local time, plus any relevant reset/start/end/settlement point. Ask rather than infer when the time basis is absent or conflicting.
9. For a zero-cost claim path, treat anti-abuse as a module-level decision. Present device, IP, anti-scalper blacklist, and malicious-refund blacklist only as options; never select them automatically.
10. During explicit activity validation, resolve external activity integration, activity-progress aggregation, startup page, and home banner as four yes/no decisions. During ordinary scoped editing, do not interrupt unrelated work solely to collect them.
11. Keep `活动对象`, general blacklist logic/list/IDs, and global version eligibility in the independent document-level `活动对象` section. Module rows contain only module-specific exceptions.
12. Keep audits, validation prompts, `异常说明`, `评审检查点`, and similar internal material out of the formal PRD unless the source or user explicitly requires a user-facing exception or separate review deliverable.

## Workflow

### 1. Ground In The Current Artifact

- Open the user-provided/current DOCX, TAPD story, or editable board first; do not assume an older generated file is current.
- Resolve `presentation_mode = three_column | prd_integrated_board` from the artifact or explicit request. Preserve an existing mode unless the user requests conversion. If neither mode can be inferred, ask once after completing source inspection.
- For TAPD integrated-board placement, resolve `image_insertion_owner = assistant | user` only when it is not already known.
- Compare embedded images with the approved prototype source when screenshot synchronization is in scope. A text-only edit must not silently replace or delete images.
- For a prototype visual change that adds/removes a data-bearing or clickable element, consume only the approved state PNG and update requirement logic only when PRD/requirement synchronization is in scope. Cosmetic changes do not justify invented logic.

### 2. Define The Scoped Change

- Locate the exact row, card, page, panel, popup, backend section, or version record to change.
- Keep a scoped edit scoped; do not turn it into a full rewrite, full activity audit, mode conversion, image-generation task, or external publication.
- For a deletion request, separate `field/value`, `visual affordance`, `click action`, `destination state`, and `reward/settlement logic`. Remove only the confirmed layers.
- Lock actor and dimension before writing: user/host/guild/agent and personal/guild/regional/global. Scan affected content for contradictory old terms after a change.
- When the user explicitly declines an open item or says not to supplement it, treat that item as intentionally omitted. Do not repeatedly raise it or invent adjacent fallback logic unless later evidence creates a direct conflict.

### 3. Author The Requirement

- Follow `prd-output-modes.md` for the selected presentation. Both modes must contain the same evidence-backed rule depth.
- In three-column mode, update only the relevant `需求描述` cell and use actual readable prototype crops when available.
- In PRD integrated-board mode, update only the corresponding requirement card and confirmed interaction arrows. Requirement cards are full PRD surfaces, not captions.
- Use dynamic, non-empty sections such as `页面说明`, `展示规则`, `交互说明`, and `数据口径`; omit unsupported headings.
- For every visible clickable control, state the exact label/location, destination, default state, close/return position, and whether the action changes filters, progress, records, inventory, rewards, or settlement.
- Keep page-facing display/interaction rules separate from backend payout, settlement, configuration, and save validation.
- Verify module ownership before adding an interaction. Similar controls on another leaderboard, panel, popup, or gameplay page are not evidence.
- For reward-related controls, distinguish the reward field, page-level preview, row-level help affordance, popup, result/history surface, and settlement logic.
- For an activity panel that displays rewards, confirm the visible set, order/grouping, single-view count, and whether a carousel exists. If a carousel is confirmed, also resolve direction, auto/manual switching, interval, looping, and swipe/arrow support.
- Do not infer a destination, carried state, priority, or settlement effect from a control label alone.

### 4. Write Back Safely

- Preserve unrelated screenshots, tables, headings, rich text, backend configuration, and recent user edits.
- Save local DOCX output under a clear new suffix instead of overwriting the latest source.
- For TAPD, read the latest story and save a timestamped HTML backup before writing. If its modification time changes, re-read and reapply the scoped edit.
- Update the existing named version row for meaningful behavior/image/flow changes; never auto-increment beyond a user-specified version.
- If highlighting is requested without a style, use light yellow only on text changed in the current update.

### 5. Validate And Deliver

- DOCX: verify table count, headers, target text, required/stale phrases, embedded-media count, and render when available. Preserve East Asian fonts and paragraph structure.
- TAPD: read back the live story and run the image-surface and version-row checks in `prd-output-modes.md`; also verify story id/title, target keywords, old-term absence, unrelated sections, image counts, and `data:image=0`. New images must use `/tfl/captures/...`.
- PRD integrated board: run the structure, geometry, Pencil, dependency, export, packaging, and visual checks in its two routed references.
- Calibrate checks to scope: focused readback for a small edit; full structural/render verification for a new document, mode conversion, or integrated-board delivery.
- Return the final file/board link first, followed by changed scope, passed checks, intentional non-changes, and any real limitation.

## Explicit Activity-Logic Validation

Enter this mode only when the user explicitly asks to校验、检查 or走查活动逻辑. Do not run it automatically after PRD generation.

1. Validate the latest delivered PRD and load baseline/common checklist sections plus only the gameplay sections actually present.
2. Use the exact table shape: `序号 / 校验类型 / 校验点 / 是否覆盖（已覆盖/缺失） / 补充说明/待确认项`.
3. Use only `必须校验` or `按需校验` for type and only `已覆盖` or `缺失` for status. If any required subpoint is absent, mark the item `缺失` and state both covered and missing parts. Do not add `当前证据`, `影响范围`, `部分覆盖`, `无需校验`, or `不适用`. Omit an untriggered `按需校验` item.
4. Report covered items, confirmation items, and optional improvements. Keep the detailed matrix internal unless the user asks to see it.
5. Ask whether to补充/修订 unresolved items. Do not edit the PRD merely because gaps were found; update only after the user confirms the items to add.
6. If the user declines an item, record it internally as intentionally omitted and do not repeatedly raise it unless later requirements conflict.

## Output Boundary

Return either the three-column PRD or the PRD integrated board unless the user explicitly requests both. After delivering a draft, wait for an explicit request before running activity-logic validation or a broader Requirements Skill Suite review.
