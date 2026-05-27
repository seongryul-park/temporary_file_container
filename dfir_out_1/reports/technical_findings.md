# Technical Findings

_Confidence labels in this report are derived from the producing step's status, the underlying evidence quality, and the detector's reliability class — not from row counts. A finding that rests on an `unverified` E01 or a `string_match` detector will never render as HIGH no matter how many lines are in the backing artifact._

## F-001: Unknown executables not in NSRL

**Confidence:** INDETERMINATE  
**MITRE ATT&CK:** T1204 User Execution / T1059 Command and Scripting Interpreter  
**Producing step:** `STEP-3-3` (status `completed_empty`)  
**Detector reliability:** `primary_indicator`  
**Evidence quality:** `unverified`  

_The producing step (`STEP-3-3`) reported status `completed_empty`; no finding is rendered. See Coverage Gaps in the executive summary._

## F-002: Unsigned / bad-signature PE files

**Confidence:** INDETERMINATE  
**MITRE ATT&CK:** T1036 Masquerading  
**Producing step:** `STEP-3-4` (status `tool_unavailable`)  
**Detector reliability:** `primary_indicator`  
**Evidence quality:** `unverified`  

_The producing step (`STEP-3-4`) reported status `tool_unavailable`; no finding is rendered. See Coverage Gaps in the executive summary._

## F-003: Candidate C2 / staging URLs (filtered)

**Confidence:** INDETERMINATE  
**MITRE ATT&CK:** T1071.001 Application Layer Protocol: Web Protocols  
**Producing step:** `STEP-3-5` (status `degraded_upstream`)  
**Detector reliability:** `string_match`  
**Evidence quality:** `unverified`  

_The producing step (`STEP-3-5`) reported status `degraded_upstream`; no finding is rendered. See Coverage Gaps in the executive summary._

## F-004: Suspicious scheduled tasks (non-Microsoft baseline)

**Confidence:** LOW  
**MITRE ATT&CK:** T1053.005 Scheduled Task/Job: Scheduled Task  
**Producing step:** `STEP-4-2` (status `completed`)  
**Detector reliability:** `heuristic`  
**Evidence quality:** `unverified`  

_No matching evidence in the producing artifact._

## F-005: RDP lateral movement sessions

**Confidence:** MEDIUM  
**MITRE ATT&CK:** T1021.001 Remote Desktop Protocol  
**Producing step:** `STEP-6-2` (status `completed`)  
**Detector reliability:** `primary_indicator`  
**Evidence quality:** `unverified`  

_No matching evidence in the producing artifact._

## F-006: Data staging archives in user-writable paths

**Confidence:** LOW  
**MITRE ATT&CK:** T1560 Archive Collected Data  
**Producing step:** `STEP-6-3` (status `completed`)  
**Detector reliability:** `heuristic`  
**Evidence quality:** `unverified`  

**Count:** 5

**Artifact:** `/home/sansforensics/Desktop/temporary_file_container/dfir_out_1/scope/exfil/archive_files.txt`

### Sample Evidence

- `/mnt/image/Users/fredr/AppData/Local/Temp/Temp1_StarFury.zip`
- `/mnt/image/Users/fredr/AppData/Local/Temp/Temp2_StarFury.zip`
- `/mnt/image/Users/fredr/AppData/Local/Temp/Temp3_StarFury.zip`
- `/mnt/image/Users/fredr/Downloads/SDelete.zip`
- `/mnt/image/Users/fredr/Downloads/WorkingFiles.zip`

## F-007: Prefetch evidence-of-execution inventory

**Confidence:** INDETERMINATE  
**MITRE ATT&CK:** T1059 (corroboration only — Prefetch confirms execution, not attribution)  
**Producing step:** `STEP-1-5-1` (status `completed_empty`)  
**Detector reliability:** `primary_indicator`  
**Evidence quality:** `unverified`  

_The producing step (`STEP-1-5-1`) reported status `completed_empty`; no finding is rendered. See Coverage Gaps in the executive summary._
