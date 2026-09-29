# Run ASVS Compliance

A portable skill for coding agents to review web applications and APIs against OWASP ASVS. It maps selected controls to code, configuration, and tests, then reports evidence, gaps, and checks that need a person or a running environment. Its core workflow is language neutral; it includes review cues for Django and Express and uses the same trace-through-code approach for other stacks.

It uses the CSV from OWASP's [fixed ASVS 5.0.0 release](https://github.com/OWASP/ASVS/releases/tag/v5.0.0_release) by default. Teams can provide another checklist or select specific controls. The official checklist is retrieved for each review; it is not bundled here.

## Use

Place this folder at `~/.agents/skills/run-asvs-compliance` for Codex or `~/.claude/skills/run-asvs-compliance` for Claude Code. Open the application repository. In Codex, type `$run-asvs-compliance`; in Claude Code, type `/run-asvs-compliance`. It reviews current changes and follows affected security paths. If there are no identifiable changes, it runs a focused baseline review. The application repository needs no skill-specific changes.

> $run-asvs-compliance

## Review scope

- **Changes found:** Review uncommitted and staged changes, plus branch changes when a reliable base is available. Follow changed code into related security paths and tests.
- **No changes found:** Run a focused baseline review of exposed paths and shared security controls. This is not a whole-codebase assessment.
- **Full review requested:** Ask for an application-wide review and the target ASVS level, for example: “Use `$run-asvs-compliance` to review the entire application against ASVS 5.0.0 Level 1.” This takes longer and covers all applicable controls at that level.

The review is read-only by default. Its report states whether the reviewed scope meets applicable ASVS controls, does not meet them, or remains undetermined. It cites files and lines, records tests run, and marks controls outside the chosen scope as **not reviewed**. Human reviewers confirm runtime behavior.

See [SKILL.md](SKILL.md) for the agent workflow and [report-format.md](references/report-format.md) for the report structure.
