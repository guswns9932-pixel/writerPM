---
name: start-novel-project
description: Start and safely manage a new original novel project from a natural-language premise, for any genre or setting. Use when Codex must create a novel concept, initialize story and character bibles, plan or write the first episode/chapter, continue an approved serial in bounded batches, apply feedback, or preserve canon, continuity, versioning, approvals, and review records throughout a fiction project.
---

# Start a Novel Project

Build an original novel through explicit approval gates. Treat “episode” and “chapter” as equivalent units and adapt labels to the user's format.

## Load the rules

Read [references/workflow-rules.md](references/workflow-rules.md) before every task. Read [references/project-files.md](references/project-files.md) before initializing a project or producing narrative text.

If the active repository provides `AGENTS.md`, `HARNESS_ROUTER.md`, `REQUIRED_OUTPUTS_MATRIX.md`, `REPORT_FORMAT.md`, policies, or templates, read and obey them first. More specific repository instructions override this skill.

## Classify before changing files

1. Classify the request as one or more of: `audit_only`, `plan_only`, `review_only`, `proposal_only`, `concept_generation`, `bible_generation`, `episode_outline`, `episode_draft`, `revision`, `batch`, `canon_change_request`, `recovery_plan`, or `packaging`.
2. Define the exact files permitted by the request.
3. Make no file changes for review-only, audit-only, plan-only, or proposal-only requests unless the user explicitly asks for written artifacts.
4. Inspect the approval state before outlines, prose, revisions, final candidates, batches, or canon changes. Stop and report what approval is missing if the state is absent, stale, ambiguous, or contradictory.

## Start a project

When the user asks to begin a new novel:

1. Derive a filesystem-safe `project_id`; ask only for information that is genuinely blocking.
2. Record the premise, genre, intended length/format, target reader, content boundaries, creative goals, and prohibited elements in `brief.md`.
3. Initialize the control and continuity files listed in [references/project-files.md](references/project-files.md). Use repository templates when present.
4. Set `approval_state.json` to the narrowest stage actually authorized by the request.
5. If the user has not chosen a concept, create three distinct concept candidates by default. Include title, genre, logline, core pleasure, differentiator, opening hook, long-form potential, and originality risk. Stop for selection.
6. After concept approval, build the bibles and ledgers. Stop for review unless the request explicitly and safely includes the first narrative unit.
7. Never invent subsequent chapters merely to fill ledgers or previews.

## Produce the first narrative unit

Proceed from concept through the first final candidate only when approval and required context permit it.

1. Read the story, character, rules/ability, canon, timeline, foreshadowing, style, rolling-context, voice, approval, and registry files.
2. Write an outline, then a draft. Ensure an opening hook, a consequential protagonist choice, reader reward, and a forward-driving ending.
3. Review continuity, rules, characterization, timeline, voice, originality, content risk, and repetitive patterns.
4. Record review findings and revision notes. Revise only within the authorized scope.
5. Create a new versioned final candidate; never overwrite an existing final.
6. Synchronize status, final registry, relevant ledgers, and the run-report index.
7. Stop in `awaiting_user_review` state.

## Continue or revise

- Require explicit approval before the second narrative unit.
- Limit continuation to three units per batch even if more are requested; list the remainder only as a possible next task.
- Allow one automatic revision pass per unit by default. Ask before further passes.
- Log feedback and classify its impact. Unless the user says to apply it immediately, write a feedback application plan first.
- Treat changes to premise, character identity/motivation, world rules, power rules, or established facts as canon changes. Write a canon change request and wait for approval.
- Preserve every existing final as read-only. Increment the version and create a revision note for any change, however small.

## Halt safely

Do not create a final, package, export, or next batch when any critical issue exists. Record a `halt_reason_code` and recovery plan containing the problem, impact, files involved, reversible remedy, user decision, and smallest safe resume point.

Critical issues include scope overrun, missing approval, registry/status mismatch, final overwrite risk, canon conflict, rule violation, character drift, timeline error, originality or rights risk, unmanageable cast/foreshadowing, and degraded reader reward from repetition.

## Report completion

Follow the repository's report format. Otherwise report:

- request type and approved scope;
- work performed and every created/modified file;
- validation and review results;
- approval, final/version, canon, ability/rules, continuity, payoff, voice, and originality status;
- user decisions still required;
- possible next tasks only, without drafting their scenes, dialogue, plot, or canon.
