# WORLD CROWN Chapter and Battle Foundation Revision Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Implement the approved WORLD CROWN foundation revision, including standalone-but-connected 1,000+ word chapters, tracked foreshadowing, dramatic champion presentations, stronger antagonist/mystery structure, character arcs, historical integration, pacing controls, and prose QA.

**Architecture:** Add focused rule documents at the canon, champion, reference, planning, template, and QA layers. Revise the existing authority files only where they need to point to or enforce those focused documents. Templates and checklists will turn the narrative requirements into repeatable planning gates without changing the ensemble premise, individualized power system, tournament format, or Crown War endgame.

**Tech Stack:** Markdown canon/planning documents, PowerShell read-only validation, Git.

**Spec:** `docs/superpowers/specs/2026-09-17-world-crown-story-foundation-revision-design.md`

## Global Constraints

- Preserve the ensemble premise: no single permanent main character or hero nation.
- Keep documented history, disputed history, legend, Crown interpretation, and deliberate fiction distinct.
- Champion powers must grow from established identity and history; do not invent unrelated emergency powers.
- Every finished manuscript chapter must contain at least 1,000 words of actual narrative prose; titles, planning notes, metadata, author notes, and QA checklists do not count.
- Every chapter must stand alone through a complete local dramatic movement while connecting to neighboring chapters through payoff, changed state, and forward foreshadowing.
- Every battle must give both champions a dramatic, historically grounded presentation of identity, achievements, Crown Title, capabilities, limits, and unanswered danger before the first meaningful exchange.
- The series planning target is approximately 300 chapters, with immediate opening movement and no slow setup-only start.
- Champion arrival and introduction staging must vary across neighboring battles; no repeated entrance pattern may become the default.
- Use a fast mythic tournament cadence: first complete battle around Chapters 4-6, no more than two setup-only opening chapters, and direct pressure plus a meaningful turn in every battle chapter.
- Draft ideas belong in planning/future-story/story-studio until promoted.
- Do not silently overwrite locked canon; update affected dependent files together.
- Manuscript prose uses close third-person limited by default, with natural dialogue, emotional specificity, varied rhythm, and distinct character voices.

---

### Task 1: Canonize chapter continuity, foreshadowing, and antagonistic pressure

**Files:**
- Create: `01_CANON/ANTAGONIST_STRUCTURE.md`
- Create: `01_CANON/FORESHADOWING_AND_MYSTERY_RULES.md`
- Create: `01_CANON/CHAPTER_AND_BATTLE_CONTINUITY_RULES.md`
- Modify: `01_CANON/MASTER_CANON.md`
- Modify: `01_CANON/NARRATIVE_STRUCTURE.md`

**Interfaces:**
- Consumes: the existing ensemble, Crown mystery, National Collapse, and rotating-POV rules in the two existing canon files.
- Produces: canonical rule references for all later templates, ledgers, saga plans, and QA documents.

- [ ] **Step 1: Add the antagonist hierarchy document.** Define local/minor antagonists, 3–5 recurring antagonistic champions or factions, the Crown Herald progression, post-reveal ideological factions, and the World Crown as the systemic antagonist. For each level, require understandable motives and escalating pressure without making every opponent evil.

- [ ] **Step 2: Add the foreshadowing and mystery rules document.** Define seed categories, the seed-to-payoff lifecycle, minor/medium/major mystery scales, reveal timing by saga, fair-play standards, and the rule that a reveal must create consequence rather than only information.

- [ ] **Step 3: Add the chapter and battle continuity rules document.** Lock the chapter contract: dominant POV, objective/pressure, local conflict or decision, emotional movement, prior-chapter payoff, forward seed, and closing change. Lock the minimum of 1,000 meaningful narrative words and explicitly exclude titles, notes, metadata, author notes, and QA text. Define the Champion Presentation sequence before the first meaningful exchange and require equal narrative dignity for both fighters.

- [ ] **Step 4: Update `MASTER_CANON.md`.** Add concise authority statements for chapter continuity, the word minimum, foreshadowing tracking, and Champion Presentation. Preserve the existing premise, National Collapse, hidden final rule, ensemble canon, Crown Titles, combat identity, and endgame.

- [ ] **Step 5: Update `NARRATIVE_STRUCTURE.md`.** Add the chapter-to-chapter handoff model, quiet-chapter requirements, and the Champion Presentation as the first stage of the major-match mini-story. Keep the existing rotating third-person limited POV and no-plot-armor rules.

- [ ] **Step 6: Validate the canonical layer.** Run:

  ```powershell
  git diff --check
  rg -n "1,000|standalone|foreshadow|Champion Presentation|Crown Herald|counterplay" 01_CANON
  ```

  Expected: no whitespace errors; each required concept appears in at least one focused canonical document; no authority rule contradicts the ensemble or power-system constraints.

- [ ] **Step 7: Commit the canonical layer.**

  ```powershell
  git add 01_CANON
  git commit -m "docs: codify chapter continuity and story pressure"
  ```

### Task 2: Formalize champion arcs and historical identity

**Files:**
- Create: `02_CHAMPIONS/CHARACTER_ARC_FRAMEWORK.md`
- Create: `06_REFERENCES/HISTORY_INTEGRATION_RULES.md`
- Modify: `02_CHAMPIONS/CHAMPION_PROFILE_SCHEMA.md`
- Modify: `02_CHAMPIONS/ENSEMBLE_CAST_RULES.md`

**Interfaces:**
- Consumes: champion power layers from `04_POWER_SYSTEMS/MASTER_POWER_SYSTEM.md`, the new Champion Presentation contract, and existing ensemble relationship rules.
- Produces: required champion-profile fields and history-handling rules used by `CHAMPION_TEMPLATE.md`, `MATCH_TEMPLATE.md`, and the introduction checklist.

- [ ] **Step 1: Add the character arc framework.** Define the required arc fields: Starting Belief, Personal Wound/Regret, Historical Contradiction, Relationship Anchor, First Challenge, Midpoint Crisis, Decisive Choice, Consequence, and End State. State that losing, surrendering, changing sides, or surviving can be valid development without a power-up.

- [ ] **Step 2: Add history integration rules.** Define the five evidence labels—documented history, disputed history, later legend, Crown interpretation, and deliberate fiction—and require each champion profile and battle plan to label them. Require flashbacks to answer a present dramatic question and integrate history through habits, tactics, scars, arguments, records, testimony, or cultural collision.

- [ ] **Step 3: Expand the champion profile schema.** Add immediate reason for fighting, Champion Presentation facts, verified accomplishments, public legend, capability limits, introduction danger/question, voice identity, and chapter handoff hooks. Keep all existing power-system fields, especially Authority condition, limitation, and counterplay.

- [ ] **Step 4: Strengthen ensemble rules.** Add equal-introduction dignity, pre-match relationship setup, historical personhood, and post-elimination continuity. Require every core champion to have one relationship that can be changed by a match result and one connection to civilian or homeland consequences.

- [ ] **Step 5: Validate the champion layer.** Run:

  ```powershell
  git diff --check
  rg -n "Starting Belief|Midpoint Crisis|Documented history|Disputed history|Crown interpretation|Verified accomplishments|Capability limits|Reason for Fighting" 02_CHAMPIONS 06_REFERENCES
  ```

  Expected: all required arc and evidence fields are documented, and the schema still includes every power-layer field from the master power system.

- [ ] **Step 6: Commit the champion/history layer.**

  ```powershell
  git add 02_CHAMPIONS 06_REFERENCES
  git commit -m "docs: formalize champion arcs and historical identity"
  ```

### Task 3: Add pacing, foreshadowing, and plot-twist planning tools

**Files:**
- Create: `08_PLANNING/EMOTIONAL_AND_MYSTERY_PACING.md`
- Create: `08_PLANNING/FORESHADOWING_LEDGER.md`
- Create: `08_PLANNING/PLOT_TWIST_LEDGER.md`
- Modify: `05_TOURNAMENT/FORMAT_AND_PACING.md`
- Modify: `08_PLANNING/SERIES_SAGA_OUTLINE.md`

**Interfaces:**
- Consumes: canonical pressure, mystery, and chapter-continuity rules from Task 1.
- Produces: saga-level pacing gates and ledger schemas that chapter, match, and QA templates can reference.

- [ ] **Step 1: Add emotional and mystery pacing guidance.** Define the required emotional rotation, recovery windows after 2–3 major matches, quiet-chapter functions, mystery escalation, and the rule that no three major fights in sequence may share the same reveal order, flashback timing, rhythm, or emotional ending.

- [ ] **Step 2: Add the foreshadowing ledger template.** Provide exact fields for Seed ID, mystery/reveal, seed text or event, category, first interpretation, reinforcement, misdirection, reveal location, payoff, consequence, responsible chapter/match, and status. Include a completed miniature example using fictional placeholder names that cannot be mistaken for locked canon.

- [ ] **Step 3: Add the plot-twist ledger template.** Provide fields for twist scale, planted evidence, reader-facing interpretation, hidden truth, reinterpretation targets, changed future choice, emotional consequence, rule preservation, and payoff location. Require major twists to pass all six existing architecture tests.

- [ ] **Step 4: Update tournament pacing.** Add chapter-level standalone/handoff checks, 1,000-word minimum guidance for finished chapters, required Champion Presentation time in every match range, and a warning against opening battles with unexplained ability spectacle.

- [ ] **Step 5: Update the saga outline.** Add explicit chapter-contract and foreshadowing progression to each saga, connect Champion Presentation escalation to the tournament phases, and preserve the existing 500–650+ chapter scale and thematic movement.

- [ ] **Step 6: Validate the planning layer.** Run:

  ```powershell
  git diff --check
  rg -n "Seed ID|first interpretation|reinforcement|misdirection|payoff|consequence|1,000|Champion Presentation|2–3|mystery" 05_TOURNAMENT 08_PLANNING
  ```

  Expected: the ledgers contain complete field sets and the tournament/saga documents point to the same chapter and battle rules.

- [ ] **Step 7: Commit the planning layer.**

  ```powershell
  git add 05_TOURNAMENT 08_PLANNING
  git commit -m "docs: add pacing and foreshadowing planning controls"
  ```

### Task 4: Make chapter and battle rules executable through templates

**Files:**
- Create: `07_TEMPLATES/CHAPTER_TEMPLATE.md`
- Create: `07_TEMPLATES/CHAMPION_INTRODUCTION_CHECKLIST.md`
- Modify: `07_TEMPLATES/CHAMPION_TEMPLATE.md`
- Modify: `07_TEMPLATES/MATCH_TEMPLATE.md`

**Interfaces:**
- Consumes: the canonical contracts from Task 1, champion/history fields from Task 2, and ledger fields from Task 3.
- Produces: fillable planning templates for chapter batches, champion profiles, match arcs, and pre-fight introductions.

- [ ] **Step 1: Create the chapter template.** Include chapter number/title, word count, dominant POV, location/time, standalone objective, conflict/pressure, emotional starting and ending states, prior-chapter payoff, current change, next-chapter handoff, forward seed classification, mystery/twist references, history labels, and a prose QA gate.

- [ ] **Step 2: Create the Champion Presentation checklist.** Require the presentation order to cover entrance image/action, name and national entry, era, reason for fighting, Crown Title meaning, accomplishments, legend distortion, Human Art, Regalia/Legacy, capability limits, opponent contrast, unanswered danger, and transition into the first meaningful exchange. Include a “show through drama” check and a “no unforeshadowed power” check.

- [ ] **Step 3: Expand the champion template.** Add presentation-ready accomplishment and legend fields, limits, introduction danger, voice habits, chapter seeds, and evidence labels while preserving the existing power, resonance, weakness, role, and research sections.

- [ ] **Step 4: Expand the match template.** Add Champion Presentation plan, introduction POV/source, accomplishment reveal, title reveal, capability/limit reveal, opponent contrast, foreshadowing payoff, and first-exchange handoff. Keep the existing 10-stage fight structure and outcome consequences.

- [ ] **Step 5: Validate the templates.** Run:

  ```powershell
  git diff --check
  rg -n "Word count|Prior-chapter payoff|Next-chapter handoff|Crown Title|Verified accomplishments|Capability limits|Opponent contrast|Unanswered danger" 07_TEMPLATES
  ```

  Expected: both chapter and match templates can be completed without inventing additional required fields.

- [ ] **Step 6: Commit the template layer.**

  ```powershell
  git add 07_TEMPLATES
  git commit -m "docs: add chapter and champion presentation templates"
  ```

### Task 5: Complete writing rules, QA gates, and project instructions

**Files:**
- Create: `10_QA/PROSE_STYLE_QA.md`
- Create: `00_PROJECT/WRITING_RULE.md`
- Modify: `10_QA/CANON_QA_CHECKLIST.md`
- Modify: `AGENTS.md`

**Interfaces:**
- Consumes: all canon, history, pacing, ledger, and template requirements from Tasks 1–4.
- Produces: the final review gates used before prose is locked or exported.

- [ ] **Step 1: Create the writing rule.** Lock close third-person limited, scene-specific voice, emotional embodiment, natural conversation, dialogue identity, varied rhythm, selective cinematic compression, and the anti-AI-pattern restrictions from the approved spec. Add the 1,000-word minimum and no-padding rule.

- [ ] **Step 2: Create the prose QA document.** Provide checks for POV distance, voice, dialogue, emotional specificity, exposition, repetition, paragraph rhythm, chapter word count, standalone movement, neighboring handoffs, foreshadowing, and ending change.

- [ ] **Step 3: Expand the canon QA checklist.** Add chapter, Champion Presentation, foreshadowing, plot-twist, antagonist, and 1,000-word gates. Make the checklist distinguish planning completeness from prose completion.

- [ ] **Step 4: Update `AGENTS.md`.** Preserve all existing repository hard rules and update Current state to say the foundation revision is implemented. Add the authority order references for the new canon and writing-rule documents without importing any forbidden external canon.

- [ ] **Step 5: Validate the full document set.** Run:

  ```powershell
  git diff --check
  if (rg -n "TBD|TODO|fill in|implement later" --glob "*.md" --glob "!docs/superpowers/**" .) { exit 1 }
  rg -n "1,000|standalone|next-chapter|Champion Presentation|Verified accomplishments|Crown Title|capability limits|counterplay|documented history|disputed history|legend|Crown interpretation" 00_PROJECT 01_CANON 02_CHAMPIONS 05_TOURNAMENT 06_REFERENCES 07_TEMPLATES 08_PLANNING 10_QA AGENTS.md
  ```

  Expected: no placeholder language in the implemented documents; the locked requirements are discoverable across the appropriate layers; no unrelated files are modified.

- [ ] **Step 6: Commit the writing and QA layer.**

  ```powershell
  git add 00_PROJECT 10_QA AGENTS.md
  git commit -m "docs: enforce prose and foundation QA rules"
  ```

### Task 6: Final repository verification

**Files:**
- Modify: none
- Test: all Markdown documents changed by Tasks 1–5

**Interfaces:**
- Consumes: the completed implementation from Tasks 1–5.
- Produces: verified, internally consistent foundation documentation.

- [ ] **Step 1: Inspect the final change set.**

  ```powershell
  git status --short
  git diff HEAD~5..HEAD --stat
  git log -6 --oneline
  ```

  Expected: only the approved foundation documents, templates, QA files, project instructions, and implementation plan are changed; each implementation layer has a focused commit.

- [ ] **Step 2: Check authority consistency.**

  ```powershell
  rg -n "one permanent|hero nation|one champion|National Collapse|Legend Authority|Crown War" 01_CANON 02_CHAMPIONS 04_POWER_SYSTEMS 05_TOURNAMENT 08_PLANNING
  ```

  Expected: the original ensemble, national, power, collapse, and endgame rules remain present and are not replaced by a single-hero structure.

- [ ] **Step 3: Check implementation coverage.**

  ```powershell
  $required = @(
    "01_CANON/ANTAGONIST_STRUCTURE.md",
    "01_CANON/FORESHADOWING_AND_MYSTERY_RULES.md",
    "01_CANON/CHAPTER_AND_BATTLE_CONTINUITY_RULES.md",
    "02_CHAMPIONS/CHARACTER_ARC_FRAMEWORK.md",
    "06_REFERENCES/HISTORY_INTEGRATION_RULES.md",
    "07_TEMPLATES/CHAPTER_TEMPLATE.md",
    "07_TEMPLATES/CHAMPION_INTRODUCTION_CHECKLIST.md",
    "08_PLANNING/EMOTIONAL_AND_MYSTERY_PACING.md",
    "08_PLANNING/FORESHADOWING_LEDGER.md",
    "08_PLANNING/PLOT_TWIST_LEDGER.md",
    "10_QA/PROSE_STYLE_QA.md",
    "00_PROJECT/WRITING_RULE.md"
  )
  $missing = $required | Where-Object { -not (Test-Path -LiteralPath $_) }
  if ($missing) { $missing | ForEach-Object { Write-Error "Missing: $_" }; exit 1 }
  ```

  Expected: no required implementation file is missing.

- [ ] **Step 4: Run final whitespace and status checks.**

  ```powershell
  git diff --check HEAD~5..HEAD
  git status --short
  ```

  Expected: no whitespace errors and a clean working tree.

