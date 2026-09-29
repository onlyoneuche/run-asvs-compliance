# Source and team use

## Official default

Use the CSV asset from OWASP's fixed [ASVS 5.0.0 stable release](https://github.com/OWASP/ASVS/releases/tag/v5.0.0_release). The release is the authority for the control IDs, wording, and levels. Check the asset and version at review time. Do not use the release labeled Bleeding Edge or the moving repository branch as a substitute. If OWASP publishes a new stable version, keep 5.0.0 as the default until this skill is explicitly updated, so prior reports remain comparable. Record the exact asset URL and checksum in the report when available.

If a team provides an annotated checklist, preserve its notes as team data while checking that its ASVS IDs and wording match the stated version. Do not treat the team's previous pass/fail values as evidence of current behavior.

## How a team starts

In Codex, invoke `$run-asvs-compliance` from the open repository. In Claude Code, invoke `/run-asvs-compliance`. In ChatGPT, use `@run-asvs-compliance`. No configuration prompt is needed. The agent reviews current changes when it can identify them; otherwise it runs a focused baseline review. A developer can optionally narrow the task: “Review authentication in this API with the skill.”

The team only needs to open the repository. It may optionally provide a target level, checklist, architecture notes, test command, deployment details, or comparison base. Without a selected level, use controls relevant to detected changes or the baseline paths and mark all other controls **not reviewed**. Do not choose an ASVS level on behalf of the organization.

## What happens

1. Detect changes or choose a focused baseline, then identify relevant controls from the fixed official checklist.
2. Trace each control through code, configuration, tests, and documentation.
3. Run safe local tests where possible; record tests not run and runtime assumptions.
4. Produce a control table, prioritized findings, and a verification plan. Include the source version and repository revision so the team can repeat the review.

The review is read-only by default. A team can request a second task to write tests or fixes, then rerun the evidence review on the changed revision. The result states whether the reviewed change meets its applicable ASVS controls based on available evidence, does not meet them, or remains undetermined. Human reviewers confirm runtime behavior and approve security decisions; the result does not claim whole-application coverage.
