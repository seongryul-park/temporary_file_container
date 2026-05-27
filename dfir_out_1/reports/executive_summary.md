# DFIR Executive Summary
**Case ID:** CASE-???
**Operator:** Unknown
**Generated:** 2026-05-27T11:21:16Z
**Evidence Integrity:** UNVERIFIED
**E01 SHA-256:** `n/a`
**E01 MD5:** `n/a`

> **EVIDENCE INTEGRITY: UNVERIFIED** — no chain-of-custody anchor was supplied. SHA-256 was computed but not matched.


## Run Capability Matrix

| Capability | Available |
|---|---|
| Authenticode validator | no |
| Registry parser | no |
| EVTX parser | no |
| NSRL hash allowlist | no |
| Prefetch parser (PECmd) | no |
| AmCache parser | no |
| ShimCache parser | no |

## Key Findings Summary

Each row's severity is derived from (1) the producing step's execution status, (2) the underlying evidence quality, and (3) the detector's reliability class. A row of `_coverage gap_` means the question this row exists to answer could not be answered on this run — it is **not** an 'all clear' result.

| Dimension | Count | Severity |
|---|---|---|
| Unknown executables (NSRL miss) | _coverage gap_ | INDETERMINATE (completed_empty) |
| Unsigned / bad-signature PE files | _coverage gap_ | INDETERMINATE (tool_unavailable) |
| Scheduled tasks for analyst review (non-Microsoft) | 0 | _no findings_ |
| RDP lateral movement sessions | _coverage gap_ | INDETERMINATE (degraded_upstream) |
| Candidate C2 / staging URLs (after CRL/OCSP suppression) | _coverage gap_ | INDETERMINATE (degraded_upstream) |
| Candidate C2 IPs (after reserved/version suppression) | _coverage gap_ | INDETERMINATE (degraded_upstream) |
| Staging archives | 5 | LOW |
| Accounts created during incident window | _coverage gap_ | INDETERMINATE (degraded_upstream) |
| Prefetch execution records | _coverage gap_ | INDETERMINATE (completed_empty) |
| Registry EoE records (AmCache/ShimCache/BAM/UserAssist) | 0 | _no findings_ |

## Coverage Gaps

- **No incident window** — every 'during incident' filter ran without time scoping. Counts are not constrained to the relevant period.

## Steps With Untrustworthy Output

| Step ID | Status | Degradation Flags |
|---|---|---|
| STEP-0-4 | degraded | cmd:1:exit=12 |
| STEP-1-1-1 | degraded | command_failed:command 1 exited 1; missing_artifact:bodyfile_txt |
| STEP-1-5-1 | completed_empty | postcondition:prefetch_status:not_registered |
| STEP-2-1-2 | completed_empty | postcondition:evtx_json_dir_listing:dir_total_size_2556<4096 |
| STEP-2-1-3 | degraded_upstream | degraded_upstream:STEP-2-1-2:completed_empty |
| STEP-3-3 | completed_empty | postcondition:nsrl_status_txt:sentinel:'nsrl_set_unavailable' |
| STEP-3-4 | tool_unavailable | tool_unavailable:has_authenticode:Need sigcheck / osslsigncode / disitool to verify PE signatures. |
| STEP-3-5 | degraded_upstream | degraded_upstream:STEP-3-3:completed_empty |

## IOC Suppression Audit

- URLs suppressed as PKI/CRL/OCSP infrastructure: **0**
- Scheduled tasks suppressed as Microsoft baseline: **7**
- Suppression is auditable: `urls_found.suppressed.txt`, `tasks_baseline.txt` preserve the line-for-line decisions.

## Recommended Immediate Actions

1. Review the **Coverage Gaps** block above before treating any 'no findings' row as confirmation of absence.
2. Inspect each `_coverage gap_` row's underlying step in `_summaries/<STEP-ID>.json` to identify the missing capability.
3. For rows with non-zero counts and non-INDETERMINATE severity, pivot from the artifact path recorded in `evidence_mapping.md`.
4. Recompute Authenticode / NSRL / RegRipper coverage on a host with the missing tools, then `--resume` against the same `${OUT}`.
