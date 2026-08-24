# Project Files

## Contents

- [Minimum project state](#minimum-project-state)
- [Narrative-unit artifacts](#narrative-unit-artifacts)
- [Conditional records](#conditional-records)
- [Initialization defaults](#initialization-defaults)

## Minimum project state

Create these files, or equivalent role documents, before finalizing narrative prose:

| File | Required content |
|---|---|
| `brief.md` | Goals, genre, format, target reader, boundaries, prohibited elements |
| `approval_state.json` | Current stage, approved scope, next allowed unit/batch, review state |
| `story_bible.json` | Premise, genre promise, core conflict, long-term objective |
| `character_bible.json` | Desires, lacks, relationships, behavioral rules |
| `voice_samples.md` | Dialogue/interior-voice principles and approved samples |
| `ability_rules.json` | Magic, technology, profession, organization, or other operative rules; use an explicit “none” state when not applicable |
| `canon_log.json` | Confirmed facts, source/approval, change history |
| `timeline.json` | Pre-story and unit-by-unit chronology |
| `foreshadowing_ledger.json` | Thread ID, introduction, intended payoff, state |
| `payoff_schedule.json` | Target window, prerequisites, delay/completion state |
| `style_guide.json` | Narrative distance, tense, tone, dialogue, prohibited patterns, ending rules |
| `rolling_context.md` | Current summary, unresolved conflict, emotional continuity |
| `final_registry.json` | Pending candidates and approved finals with version/path/status |
| `ability_usage_log.json` | Planned/actual rule usage, cost/limit, review result; retain even when currently empty |
| `reader_reward_ledger.json` | Unit reward type and delivery |
| `quality_trend_log.json` | Comparable unit review scores and drift |
| `run_reports/run_report_index.json` | Run report paths, scope, status |

Use repository templates when available. Do not fill unknown facts merely to make a schema look complete; mark them `pending_user_input`, `not_applicable`, or equivalent.

## Narrative-unit artifacts

For unit `XXX`, keep roles explicit and filenames versioned where applicable:

- `episode_XXX_outline.md`
- `episode_XXX_draft_v1.md`
- `episode_XXX_review.md` or specialized continuity/style/quality reviews
- `episode_XXX_revision_note_vN.md`
- `episode_XXX_final_vN.md` (candidate until approved)
- `episode_XXX_status.md`
- a scoped run report, indexed after creation

Adapt `episode` to `chapter`, `scene`, or another user-selected unit consistently.

## Conditional records

Create or update these only when triggered:

- `canon_change_requests/` for proposed canon changes;
- `feedback_application_plans/` and `user_feedback_log.json` for feedback;
- `recovery_plans/` for critical issues;
- `cast_registry.json` for named-character load and return purpose;
- `episode_pattern_log.json` for repeated openings, conflicts, rewards, and endings;
- `rights_log.md`, `content_risk_check.md`, `platform_policy_check.md`, `sensitivity_check.md`, and real-entity checks when publication, sourced material, sensitive content, or real-person resemblance makes them relevant.

## Initialization defaults

- Start with three concept candidates unless the user chooses a different count.
- Prefer zero to two new named characters per three-unit batch.
- Mark newly created bibles as pending review unless explicitly approved.
- Mark every new final as a candidate, not approved.
- Set the next stage to `awaiting_user_review` after concept selection material, bibles, the first final candidate, or each continuation batch.
- Represent absence of supernatural powers through explicit ordinary-world constraints rather than omitting rule checks.
