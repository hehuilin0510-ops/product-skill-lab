---
name: activity-prototype-image2-workflow
description: Generate complete low-fidelity activity prototype image sets from activity plan text, optional reference images, or an existing version folder. Use when the user asks to create an activity prototype, interaction-state flow, gameplay UI board, full set of state PNGs, gameplay mind map, image2 low-fidelity screens, or to revise an existing activity prototype. The required workflow is activity brief to prototype_blueprint.md plus mindmap.md to user confirmation to image2 state PNG generation to QA gates to HTML/board/preview/handoff delivery.
---

# Activity Prototype Image2 Workflow

## Core Contract

Generate complete activity prototype image sets, not only version-management artifacts. Start from the activity plan and produce a confirmed page/state blueprint before generating images. All single-state prototype PNGs must be generated or regenerated with image2, including main pages, popups, masks, dropdowns, banners, icons, ranking cards, reward cells, and revised UI regions. "Source-image-native reconstruction" means image2 using a confirmed source image as the baseline; it does not mean drawing the UI with code. Use scripts only for deterministic document initialization, checks, board stitching, file organization, size optimization, and QA boards. Never script-paint, canvas-draw, HTML/CSS-render, SVG-draw, PIL-compose, cover, patch, or manually paste the main UI or any single-state PNG content. If any visible semantic UI changes, regenerate the whole affected state with image2 from a clean source/baseline; do not paste a partial replacement over the old state.

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
   - If the user provides `mindmap.md`, use it as the primary gameplay-structure source and derive `prototype_blueprint.md` from it plus the activity plan.
   - If references are insufficient, proceed with a low-fidelity draft and label it as not a high-similarity reconstruction.

2. **Create the blueprint first**
   - Write `prototype_blueprint.md` before batch image generation.
   - Include activity overview, module order, page/state list, popup/exception states, state numbers, filenames, page purpose, source/baseline, and interaction flow.
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
   - Before image generation, define a project-level popup mask token in `project_rules.md` and `version_rules.md`: color, opacity, blur/dim treatment, dialog shadow, close/confirm control style, and the source state it was copied from. If no approved source exists, use one explicit default for the whole version (`#000000` at `55%` opacity, no blur) and record it before the first popup. Do not let individual states invent their own mask color or opacity.

5. **Generate state PNGs with image2**
   - Hard gate: create every single-state prototype PNG with image2. Do not use code, HTML/CSS screenshots, canvas/SVG, PIL, Photoshop-style patch scripts, or deterministic drawing as the generation path for any state PNG or changed UI region.
   - Image2 materialization gate: a successful generation response is not a completed state. Save the generated full-state image as a real local candidate under `04_素材源图与调试`, verify that the file exists and opens, then inspect it before touching the formal state directory. Never claim that a state was updated while the result exists only inside the tool response or conversation.
   - If an image2 result does not expose a usable local file immediately, inspect the tool result and use the available image-generation output mechanism to persist it. Retry the image2 workflow when necessary; do not silently switch to PIL, HTML/CSS, patching, or text-only delivery.
   - Candidate promotion order is fixed: `image2 generates full state` → `candidate saved locally` → `dimensions verified` → `visual/semantic QA passed` → `old formal state archived` → `candidate promoted to formal state` → `board rebuilt` → `main board inspected` → `TAPD/PRD synchronized`. Do not reorder or skip these gates.
   - Do not update TAPD screenshots, requirement copy that claims the visual is complete, or delivery boards before the formal local state has passed the candidate gate.
   - Scripts may only prepare prompts, inspect files, validate dimensions/counts, stitch existing image2 PNGs into boards, optimize already-approved delivery images, and organize folders. If a script output contains a visible UI page, popup, mask, card, icon, or text layer that did not come from image2, discard it and regenerate with image2.
   - Patch/paste decision rule: if the change affects text, buttons, tabs, cards, icons, reward cells, ranking rows, banners, popup bodies, masks, dropdowns, layout, spacing, state labels, or any semantically meaningful UI, regenerate the full affected state PNG with image2 from the latest clean source. Do not paste the changed element on top of the old state.
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
   - Reuse shared source assets for repeated reward placeholders, gift icons, and reward grid cells within the same project/version. Do not redraw a new placeholder icon for every popup or board cell.
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
   - Reject final state PNGs with partial pasted replacements, pasted text strips, overlaid icons, covered buttons, or patched popup/mask regions. Only review-only annotations may be pasted, and they must live outside the final state set.
   - Inspect rule/instruction popups for close behavior: they should not show bottom `OK` buttons by default.
   - Inspect repeated reward placeholders and reward grid cells for asset consistency. If the same reward-placeholder role appears across states, it should use the same shared asset and sizing rules.
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
