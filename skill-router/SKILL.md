---
name: skill-router
description: Compare and recommend available skills for a user's request. Use when the user asks which skill to use or compare skills, or when several specialist skills plausibly fit and no single skill clearly dominates; works across languages.
---

# Skill Router

Choose the most relevant available skill for the user's actual request, then use it to complete the request. If the user asks only for a recommendation, recommend a skill without carrying out the underlying task.

## Routing

1. Read the user's request in its conversation context. Identify the intended outcome, constraints, and deliverable; match intent rather than isolated keywords.
2. Review the available skill names and descriptions in the current skill catalog. Compare all plausible candidates before choosing; do not stop at the first keyword match. Consult [the skills catalog reference](references/skills-catalog.md) when the live catalog is truncated or unavailable, or when the user asks for a documented inventory of the skills. The live catalog is authoritative if it differs from this dated index.
3. Rank candidates by how directly their stated capability, trigger, and workflow match the requested outcome. Honor an explicitly named skill when it is available and relevant. If one specialist skill clearly covers the task, let that skill handle it rather than invoking this router to repeat the choice.
4. Choose the smallest useful set: use one primary skill when possible, and add another only when it covers a separate required part of the request.
5. Read the selected skill's `SKILL.md` before applying it. Follow its relevant workflow and load linked references only when the current task needs them.
6. If no available skill is a meaningful match, proceed with the general capabilities available. Do not force a weak match or create a skill unless the user asks for one.

## Folder review

For ordinary routing, use the current skill catalog to shortlist candidates; do not read every skill file on every request. If the user explicitly asks to inspect or audit skill folders, enumerate the accessible skill directories and inspect their `SKILL.md` files; the catalog reference is only an index, not an audit. For a request to recommend the best skill from all available skills, compare the full set of names and descriptions in the live catalog, use the reference only if that catalog is incomplete, then read the strongest candidate files before recommending.

Report the limits of the accessible catalog or folders if they prevent an exhaustive comparison. Never claim to have inspected skills or files that were not available to read.

## UI and visual design requests

When the user asks about designing, building, reviewing, or refining a website, screen, or component, use `ui-skills-root` as the UI-specific router before choosing a specialist. Identify the requested outcome and the evidence provided (written brief, reference image or screenshot, existing code, or live interface), then follow that skill's category and specificity rules to choose the smallest useful UI skill set. Examples include using image-to-code for implementing from a design image, a frontend design skill for a new visual direction, or a UI review skill for an existing interface. Do not treat a mention of a site or component as a request to redesign it; recommend skills only when the user asks for a recommendation.

## Response

- For a normal task, apply the selected skill and answer the user's request; do not narrate routine routing or list unrelated candidates.
- When asked which skill is best, name the recommendation and briefly connect its capability to the user's goal. Mention a close alternative only if it helps explain the choice.
- Ask a clarifying question only when the requested outcome is materially ambiguous and that ambiguity changes which workflow should be used. Otherwise make a reasonable choice and continue.
