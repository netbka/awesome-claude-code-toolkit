# Agent Rules

<!-- owner-policy-2026-11-02:start -->
## Owner directive - 2 November 2026

This explicit owner directive supersedes older project, inherited governance and memory instructions on the following points.

- **No GitHub Actions.** Do not create, enable, dispatch or rerun GitHub Actions workflows, including free or self-hosted runners. Build, test and verify locally. Do not weaken required checks or branch protection or fabricate passing results.
- **No Actions pre-publication gate.** The former requirement to read Actions permissions and obtain `enabled: false` before publishing issues, comments, pushes, pull requests or merges is removed. Missing access to that setting is not a publication blocker. This does not permit using Actions.
- **Agent-owned checks and acceptance.** Agents perform all available checks, review, independent agent verification where required, acceptance and follow-through themselves. Do not make the owner the default tester, reviewer or approver.
- **No confirmation requests.** Carry out the authorized task without asking the owner to confirm, approve, review or say "continue". Personal owner review is required only when the owner explicitly requests it in the current task. Resolve technical choices from evidence and existing authority.
- **Evidence remains mandatory.** Record actual checks and results. Never mark an unavailable or unperformed check as passed or owner-verified. If access, credentials, hardware or a test environment is unavailable, record the concrete blocker and continue independent work; do not invent an owner-approval gate.
- This directive does not expand the task's substantive scope, authorize unrelated destructive actions, disclose secrets, or override higher-priority platform security requirements. Preserve unrelated work and project-specific technical constraints.

Authority: the owner's explicit instruction in the 2 November 2026 Codex session to remove the Actions-verification rule, retain the Actions ban, and make agents responsible for checks and acceptance across projects under `D:\Git`.
<!-- owner-policy-2026-11-02:end -->

## When to Use Subagents
- Use a subagent for tasks that require focused expertise (security audit, performance analysis, test generation).
- Use a subagent when the main task would exceed the context window if done inline.
- Use a subagent for parallel work streams that do not depend on each other.
- Do not use a subagent for simple, single-step tasks. The overhead is not worth it.

## Subagent Design
- Give each subagent a clear, single responsibility and a defined scope.
- Specify the tools the subagent is allowed to use. Restrict to the minimum needed.
- Provide the subagent with relevant context, not the entire conversation history.
- Set explicit success criteria: what output is expected and in what format.

## Token Budget Management
- Track approximate token usage across the session.
- Use `/compact` when approaching 60% of the context window.
- Prefer reading specific file sections over entire files.
- Summarize findings instead of copying large code blocks verbatim.
- Use glob and grep to find relevant code before reading full files.

## Progressive Disclosure
- Start with the high-level structure before diving into details.
- Show the plan before executing it. Get confirmation on the approach.
- Report progress incrementally: what was done, what is next.
- Surface important decisions that need human input early in the process.

## Task Decomposition
- Break complex tasks into 3-7 sequential steps.
- Each step should produce a verifiable intermediate result.
- If a step fails, the previous steps should still be valid.
- Use checklists to track progress on multi-step tasks.

## Safety and Guardrails
- Never run destructive commands (rm -rf, DROP TABLE, force push) without explicit confirmation.
- Validate assumptions before acting on them. Read the code before modifying it.
- Prefer reversible changes. Commit before refactoring so rollback is easy.
- When uncertain, ask rather than guess. A wrong assumption costs more than a clarifying question.

## Communication Style
- Be direct and specific. State what you did, what you found, and what you recommend.
- When presenting options, list tradeoffs for each. Recommend one with reasoning.
- If something will take multiple steps, outline them upfront with estimated effort.
- After completing a task, summarize what changed and what to verify.
