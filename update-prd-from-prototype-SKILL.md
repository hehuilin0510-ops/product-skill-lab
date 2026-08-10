---
name: update-prd-from-prototype
description: Update or generate a Chinese table-style PRD from prototype screenshots, Axure/Figma exports, mind maps, or product-rule changes. Use when the user asks to create, supplement, revise, or polish a PRD while preserving or producing the structure `需求模块 / 原型截图 / 需求描述`, inserting real prototype screenshots, using dynamic numbered requirement descriptions, tracing every rule to current evidence, and keeping completeness checks internal.
---

# Update PRD From Prototype

## Overview

Use this skill to revise an existing PRD from fresh prototype evidence or a new product-rule clarification. If no source DOCX is provided, create a new table-style PRD from the supplied mind map and prototype images. Preserve the latest PRD as the source of truth when one exists, make targeted updates, and always produce a new versioned DOCX rather than overwriting.

For the family荣耀远征 / 守擂战 pattern, also read `references/family-glory-prd-pattern.md`.
For guild/agent competitions or other complex Axure activities with multi-stage rankings, regional/global timing, live-room panels, invitation/assistance, or draws, treat `references/axure-activity-requirement-patterns.md` as the priority requirement reference. Reuse its completeness and interaction-writing patterns before considering looser generic patterns, but never inherit source-specific dates, thresholds, rank capacities, reward values, or frequency limits.
For every activity-type PRD, also read `references/activity-prd-completeness.md`. Use it as a completeness audit inside the existing three-column rows; it must improve rule precision without changing the output structure `需求模块 / 原型截图 / 需求描述`.
The activity checklist also covers pursuit battles, elimination tournaments, PK variants, free/paid gift packs, inventory, external activity integrations, activity-progress aggregation, startup pages, and home banners. Load only the matching checks and keep them internal.
For the document-level heading structure of an activity PRD, also read `references/activity-prd-document-structure.md`. The default structure is `活动基础信息 → 活动对象 → 背景 → 思维导图 → 原型图 → 需求详情`; the three-column tables begin only under `需求详情`.

<HARD-GATE>
Treat completeness references as internal question checklists, never as product-rule sources.

Every statement written into the formal PRD must be traceable to one of these sources, in priority order: the user's explicit correction or confirmation, the latest PRD, an explicit rule document or mind map, or visible/interactive prototype evidence. Older PRDs and bundled reference patterns may help locate conflicts or missing decisions, but may not override or fill the current source.

Apply one user-confirmed standing default for gift-scoring activities: unless the current source explicitly excludes or changes a channel, activity-gift sending/receiving is counted across all supported room types (`多人房`, `单人房`, `永续房`), IM, and `贴吧` gift sending. Use these exact channel names in Chinese PRDs. Current-source exclusions override this default. For multi-person rooms, still resolve the sender/receiver role and whether score belongs to the sender or recipient.

Before writing, build an internal evidence map with `module / proposed statement / source artifact / exact evidence / status`. Write only evidence-backed statements. If a missing decision changes eligibility, scoring, time, reward, inventory, budget, settlement, state transition, or interaction ownership, ask the user first and do not write a guessed rule into the PRD.

For any zero-cost benefit such as a free gift pack, free lottery ticket, or free reward, treat anti-abuse as a module-level hard gate. If the current source does not define anti-abuse, ask the user to choose or provide controls before drafting that module. Present device, IP, anti-scalper blacklist, and malicious-refund blacklist only as options; never select them automatically. Paid-only benefits do not trigger this gate unless they also contain a free claim or zero-cost path.

Before drafting any activity PRD, resolve whether it integrates with each of these four capabilities: external activity integration, activity-progress aggregation, startup page, and home banner. Treat an explicit yes/no in the current source as resolved. If any are absent, ask about all unresolved capabilities in one compact round. Do not infer an integration or write its behavior without confirmation.

Keep negative integration confirmations internal by default. Do not create a generic `关联能力` section listing capabilities that are not connected. Write a confirmed integration into the PRD only when it is enabled and has product behavior to specify, or write an explicit non-integration only when the current document has a dedicated scope/configuration row or the user asks to record it.

Treat `活动对象`, general blacklist logic/list/IDs, and global version eligibility as document-level baseline information. Put them in the independent `活动对象` section outside all three-column requirement tables. Do not place or duplicate them in `活动公共框架`, `后台配置要求`, or another generic table row. A module row may contain only a module-specific eligibility or blacklist exception that differs from the activity-wide baseline.

Do not output an `异常说明`, `异常/限制`, `评审检查点`, `审核清单`, or internal validation section merely to satisfy a template. Include an exception, failure, restriction, or fallback only when the current source or the user explicitly defines it. Keep completeness, review, and validation checks internal rather than exposing them to development or QA readers.
</HARD-GATE>

## Workflow

1. Ground in the latest artifact.
   - Open the user-provided DOCX first; do not assume an older generated file is current.
   - Locate affected rows by module names such as `守擂奖励 / 弹层`, `轮播入口资源位`, `皇城 PK 秒杀`, `后台配置`.
   - Inspect pasted/provided screenshots and identify whether they are full prototypes, cropped row references, or desired writing-format examples.
   - If the user provides a mind map plus a prototype overview image, treat the mind map as rule/source-of-truth input and the prototype as screenshot/state evidence.
   - Build the internal evidence map before drafting. Record the exact source for each proposed rule and mark unsupported completeness-check findings as questions, not PRD content.
   - Apply source priority consistently: explicit user correction/confirmation → latest PRD → explicit rule document or mind map → current prototype evidence. Use older files and bundled patterns only to detect conflicts or gaps.
   - For gift-scoring modules, prefill the confirmed default channel coverage in the evidence map, then replace or narrow it only when the current source explicitly does so.
   - Resolve external activity integration, activity-progress aggregation, startup page, and home banner as four explicit yes/no decisions for every activity. Reuse current-source answers; otherwise ask once for the unresolved set before drafting.
   - Detect every free or zero-cost benefit path. If anti-abuse is unresolved, pause only the affected module, ask for the applicable controls and limits, and continue only after confirmation.
   - If no DOCX exists, create a new PRD with a header/evidence section plus the table `需求模块 / 原型截图 / 需求描述`.
   - For an activity PRD, first establish or normalize the top-level structure using `activity-prd-document-structure.md`. If activity audience, blacklist, or version rules are currently embedded in a requirement row, migrate them to the independent `活动对象` section, remove the duplicate table wording, and renumber later top-level headings without changing their content.
   - When updating an existing PRD/TAPD from a current prototype folder, compare the target document images against the latest state-image directory or user-confirmed screenshots before editing. Flag old images, missing states, unreadable combined images, wrong image order, and stale captions.
   - If the requested update is text-only and images are intentionally not changed, record that decision in the final response so reviewers know stale-looking images were left unchanged on purpose.
   - Before any deletion or “去掉” request, decompose the target into separate layers: `展示字段/数值`, `图标或问号等视觉入口`, `点击交互`, `打开后的页面/弹窗状态`, and `奖励/结算业务逻辑`. Write a short keep/remove matrix and do not treat these layers as one object.
   - If wording such as `去掉金豆奖励`, `取消奖励说明`, or `不要奖励入口` could refer to more than one layer, stop and confirm the exact object. Never infer that removing a help icon or explanation page also removes the reward field, amount, ratio, pool, or settlement rule.
   - For a matching complex Axure activity, use this fixed analysis order before drafting: `whole-activity lifecycle` → `module/stage states` → `time basis` → `actor and data ownership` → `ranking dimension and snapshot behavior` → `display rules` → `complete interaction chains` → `reward delivery` → `message/notification triggers`.
   - Produce three compact internal working matrices before writing prose: `lifecycle/state`, `time + actor + ranking dimension`, and `interaction chain`. If invitations/assistance exist, also produce an internal invitation-state matrix. Leave an item unresolved when the source does not define it; do not convert a checklist cell into a product rule.

2. Preserve the PRD shape.
   - Keep the table format `需求模块 / 原型截图 / 需求描述` unless the user explicitly asks for a new structure.
   - The three-column shape applies to the tables under `需求详情`, not to document-level metadata. Keep `活动基础信息`, `活动对象`, `背景`, `思维导图`, and `原型图` as independent content outside those tables.
   - Treat this three-column table as the fixed final output shape. Put only confirmed product requirements into the relevant `需求描述` cells; do not expose the internal evidence map or completeness checklist, and do not expand the document into a separate generic multi-section PRD.
   - Preserve existing screenshots, tables, headings, and backend configuration sections when the change is local.
   - Save a new output DOCX with a clear suffix such as `_补充奖励动态展示逻辑`, `_含轮播入口`, or `_补充xx逻辑`; do not overwrite the user’s latest source file.
   - The `原型截图` column must contain actual images when prototype screenshots are available. Do not leave this column as text-only `原型截图建议`.
   - For prototype overview boards, crop module/state-specific screenshots for each row when possible instead of repeatedly inserting the entire overview image.
   - For TAPD rich-text updates, preserve existing `/tfl/captures/...` images outside the target section. Upload/replace only the intended images, and after update verify no `data:image` remains in the saved description.
   - If a change affects玩法结构,核心逻辑,交互链路, or a batch of screenshots, update the top version-record table unless the user explicitly says not to. Keep the version row high-level: what changed, what is now synchronized, and whether PRD/TAPD/prototype/big board were changed. When the user names a target version, merge the change into that version and never auto-increment beyond it.
   - If the user asks to highlight updates, confirm the intended scope first. Unless they specify otherwise, apply light-yellow highlighting only to text added or changed in the current update; do not color entire rows, screenshots, or unchanged copy.

3. Update the affected module only.
   - Replace or append text in the relevant `需求描述` cell.
   - Use dynamic numbering and include only sections that contain real, source-backed requirements. Typical section labels are:
     - `1. 页面说明：...`
     - `i. ...`
     - `ii. ...`
     - `2. 展示规则：...`
     - `3. 交互说明：...`
     - `4. 数据口径：...`
   - Before drafting each affected row, check three core content types:
     - `展示逻辑`: what is visible, when it is visible, and what each confirmed state displays.
     - `交互逻辑`: what the user clicks, what opens, and what state remains after closing or returning.
     - `数据口径`: the statistical subject, calculation or value definition, and update timing required to understand the displayed data.
   - Include only content types that are real and evidence-backed. Omit empty headings and do not write placeholders such as `无交互` or `无数据口径`.
   - Write short, direct sentences. Keep one rule per bullet, avoid repeated reasoning, and do not expand a simple product rule into an unconfirmed technical design.
   - Keep page-facing rows focused on display, interaction, and the minimum data definition needed to interpret displayed values. Put payout, settlement, tier matching, backend save validation, and other configuration behavior in the relevant backend row. If one change affects both surfaces, write separate scoped requirements rather than copying backend logic into the page row.
   - Omit any empty or unsupported section. Do not add `异常说明/限制`, `评审检查点`, `审核清单`, or internal validation details to the formal PRD.
   - For activity rows, use `activity-prd-completeness.md` only to audit participants/identities, activity gifts and scoring sources, time zone and reset, region/blacklist/anti-abuse, reward delivery/inventory/budget, external activity surfaces/integrations, lifecycle states, and module-specific decisions. Ask about boundary-changing gaps before writing; never turn the checklist itself into additional numbered PRD content.
   - The confirmed all-room/IM/post-community gift-channel default is the only checklist-derived rule allowed to enter the PRD without case-specific source evidence. State it in the relevant scoring/data section and honor any explicit current-source exclusion.
   - In `3. 交互说明`, write developer-readable operation chains, not vague interaction labels. For every visible clickable control, state: `点击什么入口/按钮` → `打开哪个页面/弹窗/面板` → `默认定位到哪个 Tab/榜单/状态` → `关闭/返回后停留在哪里` → `是否改变当前筛选、进度、结算或服务端状态`.
   - Use the exact visible control name and location from the prototype, such as `页面右侧「奖励预览」按钮`. Do not shorten a known control to vague terms such as `奖励入口`, `按钮`, or `点击查看`.
   - Apply a module-ownership gate before adding an interaction: verify that the control is visibly present in that exact page/module or explicitly confirmed by the user. Do not copy a leaderboard control into an activity panel, live-room popup, or gameplay page merely because another module has a similar action.
   - When the user names an exact page, panel, popup, backend row, or other target surface, update only that surface. Do not synchronize the same wording into adjacent modules unless the user or current evidence explicitly requires it.
   - For reward-related controls, always disambiguate the destination:
     - `奖励预览` / `活动奖励`: specify whether it opens a global activity reward view, a module reward view, or the `榜单奖励弹窗`; if the source does not identify the destination or default tab, ask before writing it.
     - `榜单奖励`: specify the target reward type, such as `公会区域榜奖励`, `公会全球榜奖励`, `用户榜奖励`, or `主播榜奖励`; for guild rewards, state whether the selected region/global type and faction tab follow the current榜单 context.
     - `奖池榜单` / `历史记录`: specify the current pool/period popup and the historical-record popup separately.
     - `获奖记录`: specify whether it is the current玩法 record, a global record, or a separate record for 神迹寻秘 / 神殿抽奖 / 众神祈福.
   - For live-room and panel actions, specify the concrete target only when evidenced. Examples of the required precision are: `去支持/去送礼` opens a confirmed gift panel and `去祈福` opens a confirmed gameplay page. Do not infer activity-gift priority, carried opportunities, or destination state from the control label alone.
   - For modal-only controls such as `活动规则`, `祈福规则`, `抽奖说明`, and reward previews, state that they are read-only popups if applicable and do not trigger settlement, reward delivery, draw/prayer/search actions, or progress changes.
   - For complex interaction updates, create or embed a compact interaction-chain matrix in the affected section when prose would be ambiguous. Use columns like `入口/按钮`, `所在页面`, `点击后打开`, `默认定位`, `关闭/返回`, and `是否改变筛选/进度/结算`.
   - When removing a clickable affordance, update both sides explicitly: `2. 展示规则` must state what remains visible and what no longer appears; `3. 交互说明` must state which click path was removed and which confirmed path remains. Replacing a screenshot alone does not count as updating display logic or interaction logic.

4. Keep facts, inferred logic, and open points clean.
   - Treat explicit user corrections as source of truth.
   - Do not silently invent reward, eligibility, quota, or state-transition rules.
   - If a missing rule changes implementation boundaries, ask before editing. Do not use a silent or clearly stated assumption inside the formal PRD to fill eligibility, scoring, time, reward, inventory, budget, settlement, state-transition, or interaction-ownership gaps.
   - If the user explicitly asks to proceed without resolving a non-boundary detail, omit that unsupported detail from the PRD and mention it only in the delivery summary.
   - If the user explicitly says `不用管`, `不要补充`, or otherwise drops an open point, mark it internally as intentionally omitted and stop inferring or repeatedly asking about adjacent fallback logic. Reopen it only if later confirmed requirements create a direct contradiction or make the requested update impossible.
   - Lock the business actor and dimension before writing: user vs 主播 vs 公会, and personal vs guild vs global dimensions. If this is ambiguous, ask the user.
   - When a rule changes dimension, remove contradictory old terms from all affected rows. Examples: after changing 公会祈福 to 主播个人祈福, remove `公会祈福值`, `所属公会祈福`, `未入会主播`, and similar stale phrases.
   - When a structural or naming rule changes, scan all affected rows for stale terms before delivery. Common stale-term groups include node counts/groups (`30节点/5组` vs `18节点/3组`), period naming (`今日/昨日/日榜` vs `本期/上期/期次`), scope (`区域榜` vs `全球榜`), actor dimension (`用户/主播/公会/代理`), and reward-surface names (`奖励预览/活动奖励/榜单奖励/奖池榜单/获奖记录`).
   - Historical version rows may preserve old wording as history, but the live requirement-detail body must not contain contradictory old and new口径 for the same behavior.
   - Use `[001]`, `[002]`, etc. for configurable business values by default unless the user explicitly confirms final numbers. Do not hard-code thresholds, costs, counts, reward amounts, settlement times, or rank capacities just because they appear in a draft prototype.
   - Keep formulas as formulas when they express logic, e.g. `个人当日神令数 / 全服当日神令总数 * 当日奖池`; only replace configurable numeric constants with placeholders.
   - When rewards are involved, state whether they are automatic or manual, who receives them, and whether the display is preview, result, or settlement.

5. Run the internal completeness and evidence audit.
   - Keep review checks, audit lists, and validation steps outside the formal PRD table. Use them only to verify evidence coverage, state/data ownership, priority/conflict rules, stale-copy removal, and interaction destinations.
   - Confirm each final numbered statement has an evidence-map entry and that no checklist prompt was copied into the PRD as an invented rule.
   - For subtraction changes, internally verify both removed and retained layers. Do not append this audit as `评审检查点` unless the user explicitly requests a separate review deliverable.

6. Validate the DOCX.
   - Confirm table count, target row text, key phrases, and embedded media count with `python-docx`/zip inspection.
   - Try render QA with the Documents skill renderer when available.
   - If LibreOffice rendering fails because of local dependencies, use QuickLook plus structural checks and disclose that limitation.
   - For screenshot-backed PRDs, confirm image/drawing count did not drop and that the `原型截图` column is not text-only.
   - Validate that required new phrases are present and stale phrases are absent. For example, after switching to personal-dimension blessing, check for `个人祈福值` and ensure `公会祈福值` is absent.
   - Validate configurable placeholders: confirm all intended `[NNN]` placeholders are present and fixed business numbers are not left behind accidentally.

7. Validate TAPD rich text when TAPD is the target.
   - Before writing, read the latest story, record its story id, modification time, and image count, and save the current `description` HTML as a timestamped backup. If the modification time changes before writeback, re-read and reapply the scoped change instead of overwriting the newer正文.
   - Read back the story after every TAPD正文 update. Confirm the title/story id, target section keywords, old-term absence in the live requirement-detail body, and that unrelated recent sections were not overwritten.
   - Confirm `data:image=0` after readback and `/tfl/captures/` image count did not decrease unless the user explicitly asked to delete images.
   - For screenshot updates, confirm each target section has the expected number of images and labels, and that newly uploaded images converted from base64/data URIs into `/tfl/captures/...`.
   - Compare before/after image sources and require the changed-image count to match the intended replacement list. Verify both the top prototype overview and the `需求详情` row screenshots when the user expects both surfaces to stay current.
   - Run a requirement-surface matrix after update: `原型图/顶部总览/需求详情截图`, `展示逻辑`, `交互逻辑`, `数据口径`, `发奖/结算`, `后台配置`, and `版本记录`. Mark each as changed, intentionally unchanged, or not applicable; do not assume one updated surface implies the others were synchronized.
   - For version-record updates, confirm the intended version row exists exactly once and that older rows were not rewritten unless explicitly requested.
   - In the final reply, state what changed, what was intentionally not changed, the readback/structural checks that passed, and the backup path when one was created.

## DOCX Editing Notes

- Use the bundled workspace Python and `python-docx` for local edits.
- Avoid broad rewrites. Keep original formatting by editing only the target cell or appending review bullets.
- For table cells, rebuild paragraphs instead of stuffing long text into one paragraph.
- Maintain East Asian fonts and paragraph indentation when possible:
  - top-level numbered lines: no indent, bold acceptable
  - roman sublines: small left indent

## Prototype Screenshot Handling

- For a full prototype board, make row-specific crops before inserting images into the PRD.
- If a row covers multiple states, crop a band containing those states; if the band becomes unreadable, insert two smaller screenshots in the same cell.
- Keep a short caption above each inserted screenshot, such as `神迹寻秘-遗迹详情三态`.
- Preserve existing inserted screenshots when only copy/rules change.

## Configurable Value Policy

- Default to placeholders for business values the user may later configure:
  - costs, thresholds, progress increments, stage thresholds, rank capacity, reward counts, payout time, caps, durations.
- Use sequential bracket placeholders such as `[001]`, `[002]`.
- Do not replace structural numbers unless the user asks. Examples: `三大玩法 Tab`, section numbers, row numbers, and numbered requirement headings can remain literal.
- After replacement, scan for hard-coded remnants like `10水晶球`, `100积分`, `前 3`, or `10 条`.

## Common Activity PRD Pitfalls

- Do not confuse activity dimensions:
  - 用户行为 can generate contribution or points.
  - 主播 can receive gifts, hold points, and perform actions.
  - 公会 can aggregate only when the rule explicitly says it is guild-level.
- Do not assume participation restrictions. Write `所有主播均可参与`, `仅入会主播可参与`, or `后台配置范围` only after the user or source confirms it.
- Do not assume reward delivery. Ask whether it is `自动下发`, `手动领取`, or another confirmed method when the distinction changes implementation.
- Do not write reward names, thresholds, quotas, or `后台配置` as a substitute when they are absent from the source. Ask about boundary-changing gaps; otherwise omit unsupported detail.
- Do not leave interaction text at the level of `点击奖励入口查看奖励` or `点击按钮跳转`. Developers need the exact destination and default state: for example, `点击公会榜奖励入口打开榜单奖励弹窗，默认定位当前榜单类型对应的公会区域榜/公会全球榜奖励，阵营跟随当前选中阵营；关闭后返回当前榜单筛选状态`.
- Do not use the same vague term for different reward surfaces. Distinguish `奖励预览`, `活动奖励`, `榜单奖励`, `奖池榜单`, `历史记录`, and `获奖记录`, and state whether each is preview-only, settlement result, or historical record.
- Do not use `奖励入口` when the actual control name is known. Write the exact label and page location, for example `用户榜页面右侧「奖励预览」按钮`; also state that it is not the reward field, row-level help icon, or activity-panel card.
- Do not collapse a reward field and its help affordance into one requirement. A request to remove `?` normally removes only the icon, click target, and confirmed explanation popup; the reward label, amount/ratio, pool, threshold, virtual reward, and settlement logic remain unless separately removed.
- Do not create a popup, page, or interaction just because a reference screenshot contains a help icon. Confirm the destination exists in the current requirement or ask the user.
- Do not copy interactions across modules. In particular, a leaderboard page's `奖励预览` does not imply that an activity panel, half-screen leaderboard, live-room popup, or gameplay card also has that control.
- Distinguish user-facing activity-rule copy from implementation requirements. Rule popups should contain concise participant-facing rules; backend ownership, service configuration, readback QA, and implementation explanations belong in PRD/TAPD正文, not the visible rule copy.
- Do not trust that existing screenshots in a PRD/TAPD are current. If the prototype has been revised, check whether the target document still points to older state images, missing new states, or compressed combined screenshots that are no longer readable.
- Do not update the requirement-detail body while leaving the top version record silent for meaningful behavior, image, or interaction-chain changes. The version record is a reviewer navigation aid, not only a release note.

## Common Output

Return only the final user-facing file links and a short summary:

- what changed
- where it changed
- what validation passed
- any render limitation

The final PRD remains a three-column table: `需求模块 / 原型截图 / 需求描述`. The added completeness standard changes the precision and coverage of the content, not the presentation format.

After delivering the PRD draft, ask whether the user wants a Requirements Skill Suite review. Do not start that review without explicit approval.
