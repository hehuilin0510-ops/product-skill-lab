---
name: activity-prototype-image2-workflow
description: Generate complete low-fidelity activity prototype image sets from activity plan text, optional reference images, or an existing version folder. Use when the user asks to create an activity prototype, interaction-state flow, gameplay UI board, full set of state PNGs, gameplay mind map, image2 low-fidelity screens, or to revise an existing activity prototype. The required workflow is activity brief to prototype_blueprint.md plus mindmap.md to user confirmation to image2 state PNG generation to QA gates to HTML/board/preview/handoff delivery.
---

# Activity Prototype Image2 Workflow

## Core Contract

Generate complete activity prototype image sets, not only version-management artifacts. Start from the activity plan and produce a confirmed page/state blueprint before generating images. All single-state prototype PNGs must be generated or regenerated with image2, including main pages, popups, masks, dropdowns, banners, icons, ranking cards, reward cells, and revised UI regions. "Source-image-native reconstruction" means image2 using a confirmed source image as the baseline; it does not mean drawing the UI with code. Use scripts only for deterministic document initialization, checks, board stitching, file organization, size optimization, and QA boards. Never script-paint, canvas-draw, HTML/CSS-render, SVG-draw, PIL-compose, cover, patch, or manually paste the main UI or any single-state PNG content. If any visible semantic UI changes, regenerate the whole affected state with image2 from a clean source/baseline; do not paste a partial replacement over the old state.

### Change-scope triage and localized regeneration

Before generating or editing any state, classify the request into one of three scopes:

1. `局部视觉缺陷`: black edges, shifted copy, dirty shadows, isolated overlap, malformed icon, or another defect confined to a user-marked region.
2. `页面语义/布局改动`: changed copy, button, tab, card, reward cell, state condition, spacing relationship, or other meaningful UI behavior/structure.
3. `公共组件改动`: activity header, tab strip, shared modal treatment, shared reward placeholder, or another invariant reused by multiple states.

For a user-marked region or an isolated black-edge/offset problem, prefer native Image2 local generation using the latest confirmed full-state PNG as the clean baseline. Local generation must still output a complete full-state PNG; never paste a local result onto the old image afterward. Preserve the header identity, selected tabs, gift carousel contents, reward-card count, buttons, unchanged copy, and major layout anchors outside the edit region. Do not require pixel-level equality unless the user explicitly asks for it. Small rendering differences in anti-aliasing, line weight, whitespace, icon stroke, or a few pixels of spacing are acceptable when the page remains visually consistent and all retained business content is intact.

User-marked local generation may also be used for copy, button, or layout edits when the user has explicitly bounded the exact region. Judge drift by business structure and visible consistency, not by raw pixel differences. Treat missing controls, changed header identity, wrong selected tabs, altered card counts, deleted fields, moved sections, stale copy, or obvious layout deformation as material drift. If material drift repeats, stop and ask the user before switching to full-state regeneration. Do not silently redraw unrelated states or propagate a shared-component change to other states. For unmarked semantic or shared-component changes, regenerate only the explicitly affected state list from the newest clean baseline.

Do not use pixel hashes, pixel-difference ratios, or exact bounding-box equality as a blocking acceptance gate unless the user explicitly requests pixel-level reproduction. These measurements may be recorded for diagnostics, but a user-approved candidate must not be regenerated merely because anti-aliasing, line weight, whitespace, icon rendering, or small proportional details differ. Once the user confirms that the visual effect and business structure are correct, promote that candidate and continue the logic/document synchronization instead of repeatedly redrawing it.

### Visual-to-logic synchronization gate

When an accepted image change adds, removes, or changes a visible data-bearing or interactive element, the image update is not complete by itself. Before rebuilding the delivery board, update the active Pencil requirement card and synchronized requirement documents with the evidence-backed display condition, data definition, click destination, state-dependent behavior, and return-state preservation that the new element requires. Purely cosmetic corrections do not require invented product logic. Read back the editable Pencil card or its exported HTML to confirm the new keywords and rules are actually saved; do not rely only on an in-memory canvas screenshot.

<HARD-GATE>
- Lock activity-gift display names before generation. If a gift's formal name is not confirmed, label it consistently as `活动礼物A`, `活动礼物B`, and so on; never invent a plausible formal name. Keep the gift count evidence-based rather than defaulting to two. After a formal name is confirmed, replace the placeholder across the blueprint, prompts, state-image copy, and handoff text, then reject any stale placeholder or former name.
- Keep one confirmed activity-header region at the top of every activity state PNG. Reuse the same header title, key visual, dimensions, and placement across tabs, detail pages, rankings, and other states. This is a shared region inside every state, not a separate header-state image. Popup and dropdown states must use a clean parent page that already contains the approved header; a normal popup may dim or partially cover it only through the recorded mask/layer behavior.
- Define one project/version reward-placeholder manifest with six categories: `礼物`, `头像框`, `徽章/勋章`, `金豆/金币`, `积分`, and `通用奖励`. Use the matching category asset for each unresolved reward; use `通用奖励` only when the category itself is unknown. Reuse the same source asset and sizing rule everywhere within a category. Generate placeholder art with image2 or use user-approved source assets; never script-draw it. When formal reward art arrives, replace the affected category instances and reject stale placeholders.
</HARD-GATE>

## Default Deliverables

Every complete run should produce:

- single-state PNGs
- `prototype_blueprint.md`
- `mindmap.md`
- `display_order.md`
- `prompts.md`
- `global_rules.md`
- `project_rules.md`
- `version_rules.md`
- `qa_gate.md`
- `handoff_summary.md`
- HTML board
- module/original-layout board PNG
- preview PNG
- high-clarity 50% preview JPG under 5MB when a shareable image is needed
- focused QA comparison PNGs

Organize final outputs before delivery:

- `00_最终交付`: recommended final board, 50% preview, high-clarity 50% JPG preview under 5MB, core QA image, and necessary HTML.
- `01_状态图_xx张`: all numbered single-state PNGs.
- `02_QA检查图`: focused and historical QA images.
- `03_模块高清图`: module-level boards.
- `04_素材源图与调试`: source assets and debugging images.
- `05_历史大画板归档`: old boards, previews, HTML, and non-recommended outputs.
- `06_说明文档`: `display_order.md`, prompts, rules, blueprint, mind map, QA gate, and handoff docs.

Use the original-size 8-column board as the default "big board" deliverable. Shrunk boards are previews only and must not be treated as the main delivery.
When the big board is meant for sharing, keep the original pixel dimensions and control the recommended file under the user's requested size limit when feasible. Do not reduce clarity by shrinking the board; create a same-size optimized delivery file and archive oversized originals.
For dense multi-state boards, also keep a 50% high-clarity JPG preview under 5MB named like `推荐查看_50%高清预览_5M内.jpg`. This file is a standard share/preview deliverable, not a replacement for the HTML board or original-size clear PNG.

If the user asks for a quick draft, still create `prototype_blueprint.md`, `mindmap.md`, `display_order.md`, and `handoff_summary.md`.

## Mandatory Workflow

1. **Read the activity input**
   - Gather activity plan text, gameplay rules, reward structures, ranking logic, reference images, previous version folders, user-provided `mindmap.md`, and style constraints.
   - Resolve the activity-gift count and names, the shared activity-header source, and the reward categories present in the project. Record unresolved gift names with the fixed `活动礼物A/B/...` labels instead of inventing names.
   - If the user provides `mindmap.md`, use it as the primary gameplay-structure source and derive `prototype_blueprint.md` from it plus the activity plan.
   - If references are insufficient, proceed with a low-fidelity draft and label it as not a high-similarity reconstruction.

2. **Create the blueprint first**
   - Write `prototype_blueprint.md` before batch image generation.
   - Include activity overview, activity-gift name map, shared activity-header source/invariants, reward-placeholder asset manifest, module order, page/state list, popup/exception states, state numbers, filenames, page purpose, source/baseline, and interaction flow.
   - Also write `mindmap.md` as a human-readable gameplay mind map for module structure, user flow, rewards, rankings, popups, and exception states, unless the user already provided one.
   - Read `references/activity_blueprint_template.md`, `references/page_taxonomy.md`, `references/state_generation_rules.md`, and `references/recent_lessons.md` while drafting.
   - For guild/agent competitions or complex Axure activities with multi-stage rankings, regional/global states, live-room panels, draws, or invitation/assistance flows, treat `references/axure-activity-visual-patterns.md` as the priority state-coverage and board-composition reference. Reuse its structural and visual grammar, but do not inherit source-specific dates, thresholds, reward values, advancement counts, or frequency limits.
   - Before finalizing the blueprint for a matching activity, create a state-cluster matrix that covers active, future/Coming Soon, historical, eliminated, empty/unranked, blocking Toast, success/result feedback, and identity-owned panel/half-screen states. Mark genuinely inapplicable states instead of silently omitting them.

3. **Get blueprint confirmation**
   - Present the blueprint and mind map to the user for confirmation.
   - Do not start batch state PNG generation until the user confirms the blueprint, unless they explicitly says to skip confirmation for a tiny draft.

4. **Initialize project docs**
   - After blueprint confirmation, create or update `display_order.md`, `prompts.md`, `global_rules.md`, `project_rules.md`, `version_rules.md`, `qa_gate.md`, and `handoff_summary.md`.
   - Use `scripts/init_project_docs.py` when the blueprint follows the template.
   - Record the confirmed activity-gift name map, shared activity-header source/title/key visual/dimensions/placement, and six-category reward-placeholder manifest in `project_rules.md`. Carry version-specific replacements or overrides into `version_rules.md` without changing unrelated state numbering.
   - Before image generation, define a project-level popup mask token in `project_rules.md` and `version_rules.md`: color, opacity, blur/dim treatment, dialog shadow, close/confirm control style, and the source state it was copied from. If no approved source exists, use one explicit default for the whole version (`#000000` at `55%` opacity, no blur) and record it before the first popup. Do not let individual states invent their own mask color or opacity.

5. **Generate state PNGs with image2**
   - Hard gate: create every single-state prototype PNG with image2. Do not use code, HTML/CSS screenshots, canvas/SVG, PIL, Photoshop-style patch scripts, or deterministic drawing as the generation path for any state PNG or changed UI region.
   - Image2 materialization gate: a successful generation response is not a completed state. Save the generated full-state image as a real local candidate under `04_素材源图与调试`, verify that the file exists and opens, then inspect it before touching the formal state directory. Never claim that a state was updated while the result exists only inside the tool response or conversation.
   - If an image2 result does not expose a usable local file immediately, inspect the tool result and use the available image-generation output mechanism to persist it. Retry the image2 workflow when necessary; do not silently switch to PIL, HTML/CSS, patching, or text-only delivery.
   - Candidate promotion order is fixed: `image2 generates full state` → `candidate saved locally` → `dimensions verified` → `visual/semantic QA passed` → `old formal state archived` → `candidate promoted to formal state` → `board rebuilt` → `main board inspected` → `TAPD/PRD synchronized`. Do not reorder or skip these gates.
   - Do not update TAPD screenshots, requirement copy that claims the visual is complete, or delivery boards before the formal local state has passed the candidate gate.
   - Scripts may only prepare prompts, inspect files, validate dimensions/counts, stitch existing image2 PNGs into boards, optimize already-approved delivery images, and organize folders. If a script output contains a visible UI page, popup, mask, card, icon, or text layer that did not come from image2, discard it and regenerate with image2.
   - Patch/paste decision rule: if the change affects text, buttons, tabs, cards, icons, reward cells, ranking rows, banners, popup bodies, masks, dropdowns, layout, spacing, state labels, or any semantically meaningful UI, use Image2 from the latest clean source. A user-bounded local edit may use the localized-generation path above; otherwise regenerate the complete affected state PNG. Never paste the changed element on top of the old state.
   - Pasting/composition is allowed only outside final single-state content: stitching already-approved full state PNGs into boards, adding board labels outside screenshots, file-size optimization with no visual content changes, deterministic crop/resize of preview boards, or review-only QA callouts that are not delivered as final state PNGs. A whole-state PNG may be placed into a board only if that whole state was already approved image2 output.
   - Generate module by module: main pages and shared frame first, then rules/instructions, then results/exception states, then rankings/rewards/history pages.
   - For complex modules, generate a small batch and focused QA image first. Do not generate the whole activity before checking high-risk pages.
   - Use source single-state PNGs, motherboards, or reference images as baselines where available.
   - Reject outputs with old text ghosts, hard masks, pasted patches, malformed Chinese, deformed icons, structural drift, or popup-over-popup.
   - Reject outputs with square-box Chinese, garbled text, visible overlap, compressed/awkward spacing, wrong semantic placement, or stale content from an older state.
   - Apply the popup/floating-layer gate (`弹窗/下拉浮层专项 Gate`) for dialogs, dropdowns, and overlays: normal popups must be generated from the latest confirmed clean parent page (`干净父页面`); never stack a new popup over an old popup, old dropdown, stale mask (`旧蒙层`), or stale list.
   - Keep normal popup masks (`蒙层`) identical within the same project/version: reuse the recorded mask token exactly. Mask color, opacity, blur/dim style, dialog shadow, and close/confirm control treatment must not drift between states.
   - Rule and instruction popups (`规则弹窗` / `说明弹窗`) should use the top-right close control only. Do not add a bottom `OK`/confirm button unless the user explicitly requests a confirmation action.
   - Treat black dirty shadows (`黑影`), hard masks, white blocks, pasted patches (`贴片`), ghost text, old list remnants, stale popup content, and old content remnants (`旧内容残留`) as blockers. Regenerate instead of covering them.
   - Treat date dropdowns, level dropdowns, and filter menus as lightweight floating layers (`下拉浮层`): they may cover ranking rows or content areas, but they must not receive an extra heavy modal mask and must not show black dirty edges, pasted borders, or old content remnants.
   - Keep the approved activity header inside every generated state. Use the same title, key visual, dimensions, and placement across the full state set; popup/floating-layer states must inherit it from the clean parent page instead of redrawing or cropping it away.
   - Reuse the six-category reward-placeholder manifest for reward slots, result popups, reward tables, ranking rewards, and detail pages. Reuse one asset and sizing rule within each category; use `通用奖励` only when the category is unknown.
   - If a business element's module ownership or display form is unclear, ask the user before generating. Do not guess for entries, rewards, rankings, or record fields.
   - Read `references/image2_generation_guide.md` for visual-generation rules.

6. **Run deterministic QA and boards**
   - Run `scripts/qa_check.py` for count, dimensions, display-order coverage, required files, prompts coverage, and forbidden terms.
   - Run `scripts/build_boards.py` for HTML, original-size boards, previews, focused QA images, and organized delivery folders.
   - Run `scripts/init_handoff.py` whenever handoff details need refreshing.

7. **Inspect before delivery**
   - Read `references/qa_gate.md`.
   - Inspect focused QA images yourself before responding.
   - Do not rely on a single huge board for fine-detail review.
   - Inspect popup and floating-layer states as a separate QA gate: verify clean parent page (`干净父页面`), consistent mask style (`蒙层一致`), correct layer order, readable content, and no old UI remnants (`旧内容残留`). For dropdown states, allow content coverage only when it is the intended lightweight floating-layer behavior (`下拉浮层可遮挡`).
   - Inspect the actual state PNGs, not only the board. Reject any state whose visible UI was script-drawn or whose popup mask does not match the recorded project mask token.
   - Compare every promoted image2 candidate against its clean baseline and request checklist. Confirm all required changes are visible and all explicitly retained controls, fields, rows, sticky areas, tabs, and rewards remain present. A visually attractive output that deletes retained business fields is a failed candidate.
   - For localized edits, compare the unchanged business anchors outside the recorded mask against the clean baseline. Confirm that the approved header identity, selected tabs, gift-carousel contents, reward-card count, buttons, unchanged copy, section order, and overall composition remain recognizable and correct. Do not fail a candidate solely because pixels, anti-aliasing, line weights, minor spacing, or proportional rendering differ slightly. If the user confirms that a visually consistent candidate is acceptable, that confirmation overrides a stricter internal similarity preference.
   - Reject final state PNGs with partial pasted replacements, pasted text strips, overlaid icons, covered buttons, or patched popup/mask regions. Only review-only annotations may be pasted, and they must live outside the final state set.
   - Inspect rule/instruction popups for close behavior: they should not show bottom `OK` buttons by default.
   - Inspect gift-name consistency across state images and text artifacts. Reject invented formal gift names, stale `活动礼物A/B/...` labels after confirmation, or multiple names for the same gift slot.
   - Inspect every state for the approved activity header. Reject missing, cropped, shifted, renamed, or independently redrawn headers; for popup states, confirm the clean parent page still contains the header underneath the mask.
   - Inspect repeated reward placeholders and reward grid cells by category. The same category must use the same shared asset and sizing rules, and an unresolved category must use the recorded `通用奖励` asset.
   - Verify the root folder is clean, final files are under `00_最终交付`, state PNG count is correct under `01_状态图_xx张`, and HTML still resolves images.
   - Verify the main big board uses original state dimensions in an 8-column layout; do not deliver a thumbnail/compressed board as the main board.
   - Before the final reply, directly show the changed single-state image or focused QA image and the rebuilt main big-board PNG. A file path or HTML link alone does not prove that the image2 result was promoted into the board.
   - Verify share-ready big boards by actual byte size when a size limit is required. If the original PNG exceeds the limit, provide a same-dimension optimized file as the recommended delivery and move the oversized original to archive.

## Resuming After Context Compression

When resuming an existing prototype folder, read in this order:

1. `handoff_summary.md`
2. `prototype_blueprint.md`
3. `mindmap.md`
4. `project_rules.md`
5. `version_rules.md`
6. `display_order.md`
7. `prompts.md`

If any required file is missing, recreate it from the current folder state and the latest confirmed user request before generating more images. If context was compacted or the agent is unsure, stop generation, rebuild the current facts from these files, then continue.

## References

- `references/activity_blueprint_template.md`: template for the required blueprint.
- `references/mindmap_template.md`: template for the required gameplay mind map.
- `references/page_taxonomy.md`: page/state types to consider when deriving a full prototype.
- `references/state_generation_rules.md`: numbering, naming, order, popup, result, ranking, and reward rules.
- `references/image2_generation_guide.md`: image2/source-native generation boundaries and rejection criteria.
- `references/recent_lessons.md`: recent pitfalls, high-risk page rules, and efficient workflow lessons.
- `references/axure-activity-visual-patterns.md`: reusable state clustering, ranking-row, semantic-color, and live-room overlay patterns learned from complex Axure activity sources.
- `references/rule_templates.md`: four-layer rule templates.
- `references/qa_gate.md`: hard delivery checklist and visual review points.
- `references/handoff_template.md`: context-compression handoff template.
- `references/failure_patterns.md`: common failure modes and fixes.

## Scripts

- `scripts/init_project_docs.py <version-dir> --blueprint prototype_blueprint.md --project-name "<name>"`
- `scripts/qa_check.py <version-dir> [--expected-count N] [--forbidden-terms a,b,c] [--required-files file1,file2] [--check-prompts]`
- `scripts/build_boards.py <version-dir> [--columns 8] [--qa name:01,02,03] [--no-organize]`
- `scripts/init_handoff.py <version-dir> --baseline "<source>" --summary "<short summary>"`

Scripts assume state images start with two digits, e.g. `01_...png`. `build_boards.py` defaults to organized delivery folders; use `--no-organize` only for temporary diagnostics. For other naming schemes, inspect and adapt before use.
