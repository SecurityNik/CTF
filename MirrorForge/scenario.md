# Mirror Forge

## Background

On April 14, 2026, a threat intelligence partner issued an advisory associated with campaign tracking identifier MF-2026-01 (MirrorForge). The advisory described a supply chain campaign targeting internal tooling workflows through the use of compromised signing material and weak validation patterns around signed artifacts.

The advisory did not identify confirmed victims. It included a limited set of indicators and recommended that recipients review recently deployed internal utilities and associated signing workflows for possible exposure.

During the sweep, one managed environment returned a possible match tied to a recently deployed utility and its associated signing workflow: `log_sync_pro.py`, a Python 3 replacement for a legacy telemetry agent. The utility had passed standard review and was deployed on April 12, 2026.

Following the advisory, the SOC collected the associated artifacts for review. No determination has yet been made as to whether the activity reflects benign legacy behavior or confirmed campaign-related compromise.

## Your Mission

You are the on-call analyst assigned to this case. Based on the evidence provided, determine whether the deployed utility is benign, misconfigured, or associated with MirrorForge activity. If compromise is present, explain the mechanism, assess what is occurring in the environment, and identify how the issue passed through review and deployment.

## Evidence Package

- `log_sync_pro.py` — deployed utility
- `audit_record_4.pdf` — AI pair-programming session export attached to the original PR
- `pr_2641.pdf` — PR description and review record for the April 10 merge
- `egress_summary.csv` — outbound traffic summary covering April 10–14
- `feed_04.txt` — relevant excerpt from advisory MF-2026-01
- `README.internal` — documentation file shipped alongside the utility, recovered from `/opt/logsync/bin/` on a deployed host
- `logsync.pub` — public key referenced by the utility at `/etc/pki/internal/logsync.pub`

## Phase Breakdown

- Phase 1: Static Analysis — 4 questions
- Phase 2: Network & Payload Forensics — 5 questions
- Phase 3: Attribution — 4 questions
- Phase 4: Review Process Correlation — 5 questions
- Written Report
- Optional Bonus: Revised MirrorForge advisory

## Submission Requirements

- All factual answers must include a direct citation to the supporting evidence (artifact name and specific row, line, field, or excerpt).
- All short-answer questions must be supported by direct evidence from the provided artifacts. Unsupported conclusions, even if correct, will receive reduced credit.
- Several questions require you to paste exact command output or decoded values. Approximations of these values will be marked incorrect.
- The grading rubric rewards precision over fluency.
