---
name: activity-prototype-image2-workflow
description: Create or revise low-fidelity activity prototype state images with the current image-generation capability from an activity plan, approved baselines, optional Starloom annotations, or an existing version folder. Use for full prototype sets, focused state edits, activity panels, live-room popups, and 8-column prototype state boards. This skill owns state-image generation and visual QA; it does not author PRD text or PRD integrated requirement boards.
---

# Activity Prototype Image Workflow

## Contract And Ownership

Generate and visibly deliver the requested prototype state images.

- This skill owns single-state PNG generation/editing, candidate promotion, visual QA, prototype project docs, and the 8-column `原型状态大画板`.
- It does not own three-column PRDs, TAPD requirement text, requirement cards, or the screenshot＋arrow＋requirement-card `PRD 一体画板`. Use `update-prd-from-prototype` when the user explicitly requests requirement synchronization.
- New or changed state PNGs must use the current built-in image-generation/editing capability. Use Images 2.5 when the runtime actually exposes it; the legacy shorthand `Image2/image2` means the available built-in image capability, not proof of a specific submodel.
- Never claim a specific image model, Starloom installation, or plugin route without callable runtime evidence.

## Cross-Model And Capability Policy

Apply the same workflow selection, scope, candidate, QA, visible-delivery, and formal-promotion gates on GPT-5, GPT-6, and later models.

- GPT-6 does not imply Images 2.5, Starloom, a model selector, or any plugin is installed.
- Keep prompts model-neutral: clean baseline, requested change, retained business anchors, dimensions, and rejection criteria.
- Adapt only to documented tool schemas and result formats. Never invent parameters to force a model version.
- A newer model must not broaden the affected state set or skip materialization, visual QA, promotion, or delivery gates.

## Workflow Selection

- `full_production`: create or materially redesign a complete activity set. Build/refresh the blueprint and mind map, generate by module, then rebuild all prototype artifacts.
- `focused_update`: change only named states or the minimal affected state set. Reuse the approved blueprint, baseline, dimensions, and project rules; rebuild only consumers of those states.
- `delivery_recovery`: recover an already generated/approved image that is missing or invisible, validate it, and return that same file. Do not regenerate or rebuild unrelated artifacts.

Choose the smallest route that completes the request. Ask only when ambiguity changes the affected state list, business meaning, visual target, or approved baseline.

## Optional Capability And Starloom Routing

Determine availability from callable tools, not identity, organization, prior use, or screenshots.

- If no image-generation/editing tool is callable, report the concrete capability gap and preserve the requested scope for retry. Do not substitute code rendering, PIL, HTML/CSS screenshots, canvas/SVG, or another visual generator.
- Starloom is available for an action only when the required operation set is callable. Opening requires its open operation; executing an attempt requires its claim/progress/complete/fail operations.
- If Starloom is unavailable, continue the normal prototype workflow with the available image tool. If the user explicitly requested Starloom, disclose the gap and offer the normal route; do not auto-install or fabricate a workspace/receipt.
- When Starloom is available and relevant, load its Skill as the source of truth for thread binding and transaction protocol. A bounded annotation maps to `focused_update` unless the submission explicitly defines another route.
- A Starloom submission authorizes the claimed image operation and result registration only. Formal-state replacement and prototype-board rebuild require explicit delivery/promotion scope or user acceptance of the candidate. PRD, TAPD, and requirement-card synchronization always requires an explicit user request and is routed to `update-prd-from-prototype`.
- Register and show the same validated local image. A Starloom preview or receipt alone is not delivery evidence.

## Reference Routing

Load only references needed by the selected route:

- `references/image2_generation_guide.md`: source priority, full-state generation, localized edits, no-patch boundary, materialization, delivery recovery, and candidate promotion.
- `references/state_generation_rules.md`: numbering/order, panels, live-room popups, masks, dropdowns, headers, reward placeholders, and state-specific construction.
- `references/qa_gate.md`: deterministic/visual QA, blocker patterns, mode-specific deliverables, 8-column prototype state-board delivery, file-size checks, and visible handoff.
- `references/activity_blueprint_template.md`, `references/mindmap_template.md`, and `references/page_taxonomy.md`: new/full blueprint work.
- `references/axure-activity-visual-patterns.md`: complex Axure rankings, identities, regions, live-room overlays, invitations, and draws.
- `references/rule_templates.md`: project/global/version rule documents.
- `references/recent_lessons.md`: non-canonical edge cases and historical failure lessons only.
- `references/handoff_template.md` and `references/failure_patterns.md`: handoff/context recovery and diagnosis.

## Hard Gates

1. Generate every new or changed single-state PNG with the current image tool from the newest clean baseline. Scripts may initialize docs, inspect, validate, organize, stitch whole approved states into boards, optimize delivery files, and add review-only QA callouts; they must not draw or patch state UI.
2. A tool response or preview is not a deliverable. Persist the full-state result as a local candidate, verify it opens and has expected dimensions, inspect it, then promote it through the sequence in `image2_generation_guide.md`.
3. Never regenerate solely to fix missing/collapsed delivery. Use `delivery_recovery` to materialize and visibly return the existing result.
4. Keep a focused update focused. Do not regenerate unrelated states or propagate a shared-component change beyond the user-confirmed affected state list.
5. Judge localized edits by retained business structure and visible consistency rather than pixel hashes. Missing controls, changed header identity, altered card counts, stale copy, deleted fields, moved sections, or obvious deformation are material drift.
6. Lock unconfirmed gift names as `活动礼物A/B/...`; never invent a formal name or fixed gift count. Replace all stale placeholders after confirmation.
7. Keep one approved activity-header region inside every activity state and one six-category reward-placeholder manifest: `礼物`, `头像框`, `徽章/勋章`, `金豆/金币`, `积分`, `通用奖励`.
8. Use clean parent states for popups and overlays. Do not stack a new popup on an old popup, mask, dropdown, or stale layer.
9. The `原型状态大画板` is an original-size multi-state visual overview, normally 8 columns. It is not a PRD integrated board and must not contain or replace full requirement cards.

## Workflow

### 1. Ground And Scope

- Read the activity plan, approved state list, current single-state PNGs, reference images, previous version, style constraints, and current project docs.
- For `full_production`, create or refresh `prototype_blueprint.md` and `mindmap.md` before batch generation. Include module order, states, filenames, purpose, baselines, popup/exception states, and interaction flow.
- For complex Axure work, create a state-cluster matrix covering applicable active, future, historical, eliminated, empty/unranked, blocking, result, and identity-owned views.
- For `focused_update`, identify the minimal affected states and reuse all unchanged project facts. Do not ask the user to reconfirm them.
- Classify the change as `局部视觉缺陷`, `页面语义/布局改动`, or `公共组件改动` and follow the localized/full-state rules in `image2_generation_guide.md`.

### 2. Maintain Only Required Project Docs

- A full production run maintains `prototype_blueprint.md`, `mindmap.md`, `display_order.md`, `prompts.md`, `global_rules.md`, `project_rules.md`, `version_rules.md`, `qa_gate.md`, and `handoff_summary.md`.
- A focused update touches only documents affected by the changed states. A recovery run does not rebuild documents unless recovery reveals an actual mismatch.
- Record gift-name mapping, shared header invariants, reward-placeholder manifest, and the project/version popup mask token in the appropriate rule files.
- Use `scripts/init_project_docs.py` and `scripts/init_handoff.py` when their templates match the current project.

### 3. Generate And Promote

- Generate module by module; use small batches for rankings, rewards, results, history, popups, and other high-risk pages.
- Follow `image2_generation_guide.md` for source priority, localized generation, retained anchors, materialization, recovery, and promotion.
- Follow `state_generation_rules.md` for panel/popup ownership, dimensions, clean parents, masks, headers, placeholders, numbering, and order.
- Do not update formal state folders, boards, or downstream artifacts before the candidate passes dimension and visual/semantic QA.
- Archive the previous formal state before promotion and retain the candidate in the debug/source area for rollback.

### 4. Validate And Build Prototype Artifacts

- Run `scripts/qa_check.py` for deterministic coverage and `scripts/build_boards.py` for HTML, original-size prototype state boards, previews, module boards, and focused QA artifacts.
- Read `references/qa_gate.md` and inspect every changed state at practical zoom. For panels/popups, inspect the complete state and a focused comparison/crop.
- Verify board/order consumers use the newly promoted formal state rather than an older file or chat-only candidate.
- For a full run or shared-artifact change, validate state count, project docs, folder organization, HTML paths, board dimensions, actual bytes, and focused QA. For a small focused update, run only the affected checks plus board placement.

### 5. Handle Logic Changes Without Crossing Ownership

- If an accepted visual change adds/removes a data-bearing or clickable element, write a compact synchronization note containing surface, visible change, display condition, data meaning, click destination, state branch, and return-state implication when evidenced.
- Do not automatically edit PRD, TAPD, or requirement cards. If the user explicitly asks to synchronize requirements, use `update-prd-from-prototype` with the approved image and synchronization note.
- Cosmetic corrections do not require invented product logic.

### 6. Deliver Visibly

- `full_production`: deliver approved state PNGs, project docs, HTML, the original-size 8-column prototype state board, previews, module boards, and focused QA according to `qa_gate.md`.
- `focused_update`: deliver changed full-state PNGs, focused QA, and only affected existing boards/docs.
- `delivery_recovery`: deliver the recovered original-resolution image and its validation result; do not generate a new candidate.
- Show the real changed/recovered image in the current task and link the relevant board/files. A filesystem path, receipt, HTML link, or text-only statement is not visible image delivery.

## Context Recovery

After compaction or interruption, read in order: `handoff_summary.md` → `prototype_blueprint.md` → `mindmap.md` → `project_rules.md` → `version_rules.md` → `display_order.md` → `prompts.md`. Resolve conflicts before generating more images.

## Scripts

- `scripts/init_project_docs.py <version-dir> --blueprint prototype_blueprint.md --project-name "<name>"`
- `scripts/materialize_imagegen_result.py --session <rollout.jsonl> --image-id <ig_...> --out <candidate.png>`
- `scripts/qa_check.py <version-dir> [--expected-count N] [--forbidden-terms a,b,c] [--required-files file1,file2] [--check-prompts] [--check-delivery]`
- `scripts/build_boards.py <version-dir> [--columns 8] [--qa name:01,02,03] [--no-organize]`
- `scripts/init_handoff.py <version-dir> --baseline "<source>" --summary "<short summary>"`

Scripts assume two-digit state-image prefixes. Inspect and adapt before use when a project follows another established naming scheme.
