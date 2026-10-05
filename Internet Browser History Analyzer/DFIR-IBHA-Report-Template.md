<!--
DFIR-IBHA Report Template — Markdown v1.3
──────────────────────────────────────────────────────────────────────────────
INSTRUCTIONS FOR LLM:
1. Copy this entire file.
2. Replace every {{PLACEHOLDER}} with the value from your analysis.
3. Fill every table — write "No findings in this category." if a section
   is empty. Do not delete table headers.
4. Remove all comment blocks (<!-- ... -->) before final output.
5. Risk indicators: 🔴 CRITICAL   🟠 HIGH   🟡 MEDIUM   🟢 LOW   ⚪ INFO

PLACEHOLDER KEY:
{{CASE_REF}}        — e.g. IBHA-2026-001
{{CLASSIFICATION}}  — CONFIDENTIAL / RESTRICTED / INTERNAL
{{DATE_FROM}}       — Start of analysis period
{{DATE_TO}}         — End of analysis period
{{REPORT_DATE}}     — Today's date
{{DEVICE_SOURCE}}   — Device identifier or "Not specified"
{{SUBJECT_DOMAIN}}  — Corporate email domain e.g. @company.com
{{ANALYST}}         — DFIR-IBHA v1.3 (Cognitive Analysis)
{{OVERALL_RISK}}    — 🔴 CRITICAL / 🟠 HIGH / 🟡 MEDIUM / 🟢 LOW
{{RISK_SCORE}}      — Numeric score, e.g. 34.2
{{TOTAL_FINDINGS}}  — Total flagged events count
{{CRITICAL_COUNT}}  — Count of CRITICAL findings
{{HIGH_COUNT}}      — Count of HIGH findings
{{CHAIN_COUNT}}     — Number of critical chains detected
{{FLIGHT_RISK}}     — 🔴 CRITICAL / 🟠 HIGH / 🟡 MEDIUM / 🟢 LOW
{{FLIGHT_SCORE}}    — Numeric flight risk score
{{ROWS_SCANNED}}    — Total rows read from file
{{ROWS_IN_SCOPE}}   — Rows after date filter
{{SCAN_STATUS}}     — FULL SCAN / PARTIAL SCAN — [reason]
-->

---

# DFIR-IBHA — Internet Browsing History Analysis

| Field | Value |
|---|---|
| **Case Reference** | {{CASE_REF}} |
| **Classification** | {{CLASSIFICATION}} |
| **Analysis Period** | {{DATE_FROM}} to {{DATE_TO}} |

---

# DFIR-IBHA — Internet Browsing History Analysis

| Field | Value |
|---|---|
| **Case Reference** | {{CASE_REF}} |
| **Classification** | {{CLASSIFICATION}} |
| **Analysis Period** | {{DATE_FROM}} to {{DATE_TO}} |
| **Report Date** | {{REPORT_DATE}} |
| **Device / Source** | {{DEVICE_SOURCE}} |
| **Subject Domain** | {{SUBJECT_DOMAIN}} |
| **Prepared By** | {{ANALYST}} |

---

## SECTION 1 — EXECUTIVE SUMMARY

### Overall Risk Rating

> ## {{OVERALL_RISK}}
> **Risk Score:** {{RISK_SCORE}} &nbsp;|&nbsp;  
> **Total Findings:** {{TOTAL_FINDINGS}} &nbsp;|&nbsp;  
> **Critical:** {{CRITICAL_COUNT}} &nbsp;|&nbsp;  
> **High:** {{HIGH_COUNT}} &nbsp;|&nbsp;  
> **Chains:** {{CHAIN_COUNT}} &nbsp;|&nbsp;  
> **Flight Risk:** {{FLIGHT_RISK}} (score: {{FLIGHT_SCORE}})

---

### What Was Analyzed

<!-- One or two sentences: how many records, what period, what perspectives. -->
{{WHAT_WAS_ANALYZED}}

---

### Key Findings

<!-- List HIGH and CRITICAL findings only. Plain English. No raw URLs. No module names.
     One bullet per category. Max 8 bullets. Format: bold category label + sentence. -->
{{KEY_FINDINGS_LIST}}


{{KEY_FINDINGS_LIST}}

---

### Correlated Events

<!-- Only include this section if critical chains were detected.
     Write 2–3 sentences describing the most significant chain. Omit section if no chains. -->

> **⚠ CHAIN ALERT:** {{CHAIN_SUMMARY}}

---

### Recommended Actions

<!-- 3–5 numbered actions. Specific to findings — do not use generic text. -->
{{RECOMMENDED_ACTIONS}}

---

### Limitations

> This analysis is based solely on internet browsing history. It cannot confirm
> what data, if any, was uploaded, transmitted, or accessed at destination sites.
> Findings are indicators requiring corroboration before any disciplinary, legal,
> or termination action. This report does not constitute legal evidence on its own.

---

## SECTION 2 — DETAILED OBSERVATIONS

### 2.1 Data Theft Findings

#### 2.1.1 Email Services

| Domain | Risk | First Visit | Last Visit | Visits | Typed | After-Hours |
|---|---:|---|---|---:|---:|---:|
| <!-- fill one row per domain found --> | | | | | | |
| {{EMAIL_DOMAIN_1}} | {{RISK_1}} | {{FIRST_1}} | {{LAST_1}} | {{V_1}} | {{T_1}} | {{AH_1}} |


### 2.1.1 Email Services

| Domain | Risk | First Visit | Last Visit | Visits | Typed | After-Hours |
|---|---:|---|---|---:|---:|---:|
| <!-- fill one row per domain found --> | | | | | | |
| {{EMAIL_DOMAIN_1}} | {{RISK_1}} | {{FIRST_1}} | {{LAST_1}} | {{V_1}} | {{T_1}} | {{AH_1}} |

<!-- Add rows as needed. Use 🔴 🟠 🟡 🟢 ⚪ for risk column. -->

**Extracted email addresses from page titles:**

| Email Address | Appearances | Corporate? | Risk |
|---|---:|---|---:|
| {{EMAIL_ADDR_1}} | {{COUNT_1}} | {{CORP_1}} | {{R_1}} |

<!-- Add rows as needed. Corporate = Yes/No. -->

---

#### 2.1.2 File Transfer & Cloud Storage

| Timestamp (UTC) | Domain | URL Path (truncated) | Title (truncated) | Visits | Upload Signal | Risk |
|---|---|---|---|---:|---|---|
| {{FT_TS_1}} | {{FT_DOMAIN_1}} | {{FT_PATH_1}} | {{FT_TITLE_1}} | {{FT_V_1}} | {{FT_UP_1}} | {{FT_R_1}} |

---

#### 2.1.3 Paste & Code Sharing Sites

| Timestamp (UTC) | Domain | Title (truncated) | Visits | Risk |
|---|---|---|---:|---|
| {{PS_TS_1}} | {{PS_DOMAIN_1}} | {{PS_TITLE_1}} | {{PS_V_1}} | {{PS_R_1}} |

---

#### 2.1.4 AI Tools & LLM Platforms


#### 2.1.4 AI Tools & LLM Platforms

**Foreign Jurisdiction AI Platforms (CRITICAL):**

| Timestamp (UTC) | Platform | Title (truncated) | Visits | Upload Signal | Risk |
|---|---|---|---:|---|---|
| {{AI_F_TS_1}} | {{AI_F_PLAT_1}} | {{AI_F_TITLE_1}} | {{AI_F_V_1}} | {{AI_F_UP_1}} | 🔴 CRITICAL |

<!-- Note: Data submitted to foreign AI platforms may be subject to government access laws. -->

**Other AI Platforms:**

| Timestamp (UTC) | Platform | Title (truncated) | Visits | Upload Signal | Risk |
|---|---|---|---:|---|---|
| {{AI_TS_1}} | {{AI_PLAT_1}} | {{AI_TITLE_1}} | {{AI_V_1}} | {{AI_UP_1}} | {{AI_R_1}} |

---

#### 2.1.5 Document Processing & Conversion Tools

| Timestamp (UTC) | Site | Document Title in Page | Action | Sensitive? | Risk |
|---|---|---|---|---|---|
| {{DP_TS_1}} | {{DP_SITE_1}} | {{DP_TITLE_1}} | {{DP_ACT_1}} | {{DP_SEN_1}} | {{DP_R_1}} |

> **Investigator note:** Document processing site visits indicate files were uploaded to a third-party server outside organizational control. Document titles visible in browser history are corroborating evidence of what was processed.

---

### 2.2 Insider Threat Findings

#### 2.2.1 Flight Risk Indicators

**Flight Risk Score: {{FLIGHT_SCORE}} — {{FLIGHT_RISK}}**

| Signal Category | Platforms Observed | First Seen | Last Seen | Total Visits | Score Contribution |
|---|---|---|---|---:|---:|


**Flight Risk Score: {{FLIGHT_SCORE}} — {{FLIGHT_RISK}}**

| Signal Category | Platforms Observed | First Seen | Last Seen | Total Visits | Score Contribution |
|---|---|---|---|---:|---:|
| Job Boards | {{FR_JOB_PLATFORMS}} | {{FR_JOB_F}} | {{FR_JOB_L}} | {{FR_JOB_V}} | {{FR_JOB_S}} pts |
| Freelance Platforms | {{FR_FREE_PLATFORMS}} | {{FR_FREE_F}} | {{FR_FREE_L}} | {{FR_FREE_V}} | {{FR_FREE_S}} pts |
| Resume Builders | {{FR_RES_PLATFORMS}} | {{FR_RES_F}} | {{FR_RES_L}} | {{FR_RES_V}} | {{FR_RES_S}} pts |
| Comp Research | {{FR_COMP_PLATFORMS}} | {{FR_COMP_F}} | {{FR_COMP_L}} | {{FR_COMP_V}} | {{FR_COMP_S}} pts |
| Competitor Career Pages | {{FR_COMP_CAREER}} | {{FR_CC_F}} | {{FR_CC_L}} | {{FR_CC_V}} | {{FR_CC_S}} pts |
| **TOTAL** | | | | | **{{FLIGHT_SCORE}}** |

**Sustained Job-Seeking Pattern:**

| Date | Job Boards | Freelance | Resume | Comp Research | Daily Total |
|---|---:|---:|---:|---:|---:|
| {{FR_D1}} | {{FR_JB1}} | {{FR_FL1}} | {{FR_R1}} | {{FR_CR1}} | {{FR_DT1}} |
| {{FR_D2}} | {{FR_JB2}} | {{FR_FL2}} | {{FR_R2}} | {{FR_CR2}} | {{FR_DT2}} |

<!-- Add a row for each day that had flight risk activity. -->

---

### 2.3 Asset Misuse Findings

#### 2.3.1 Remote Access Tools

| Timestamp (UTC) | Domain | URL Indicator | Session Confirmed | Visits | Risk |
|---|---|---|---|---:|---|
| {{RA_TS_1}} | {{RA_DOMAIN_1}} | {{RA_PATH_1}} | {{RA_SES_1}} | {{RA_V_1}} | {{RA_R_1}} |

---

#### 2.3.2 Social Media & Communication Platforms

| Platform | Business-Hours Visits | After-Hours Visits | Total Visits | Exfil-Capable | Risk |
|---|---:|---:|---:|---|---|
| {{SM_PLAT_1}} | {{SM_BH_1}} | {{SM_AH_1}} | {{SM_T_1}} | {{SM_EX_1}} | {{SM_R_1}} |

<!-- Exfil-Capable: Yes/No. Mark Discord CDN attachment URLs with CRITICAL. -->

---


#### 2.3.3 NSFW & Adult Content

> **Note:** Full domain list is in **Appendix C (RESTRICTED)**. Distribution limited to authorized HR/Legal personnel only.

| Metric | Value |
|---|---|
| Total access events | {{NSFW_TOTAL}} |
| During business hours | {{NSFW_BH}} ({{NSFW_BH_PCT}}%) |
| After hours | {{NSFW_AH}} |
| Categories present | {{NSFW_CATS}} |
| Full domain list | Appendix C [RESTRICTED] |
| Risk Assessment | {{NSFW_RISK}} |

---

#### 2.3.4 Streaming & Gaming

| Platform | Total Visits | Business-Hours % | Risk |
|---|---:|---:|---|
| {{SG_PLAT_1}} | {{SG_V_1}} | {{SG_BH_1}}% | {{SG_R_1}} |

---

### 2.4 Temporal Analysis

| Metric | Value |
|---|---|
| Total visits in scope | {{TA_TOTAL}} |
| Business hours visits | {{TA_BH}} ({{TA_BH_PCT}}%) |
| After-hours visits | {{TA_AH}} ({{TA_AH_PCT}}%) |
| Weekend visits | {{TA_WE}} |
| Spike days detected | {{TA_SPIKES}} |

**Activity Spike Days** (visits > mean + 2σ):

| Date | Visit Count | Notable Flagged Activity |
|---|---:|---|
| {{SP_D1}} | {{SP_C1}} | {{SP_ACT_1}} |
| {{SP_D2}} | {{SP_C2}} | {{SP_ACT_2}} |

**After-Hours High-Risk Events:**


**After-Hours High-Risk Events:**

| Timestamp (UTC) | Domain | Category | Risk |
|---|---|---|---|
| {{AH_TS_1}} | {{AH_DOMAIN_1}} | {{AH_CAT_1}} | {{AH_R_1}} |

---

### 2.5 Critical Chains

<!-- Repeat this block for each chain detected. -->

---

##### 🔴 CHAIN-{{CHAIN_NUM}} — {{CHAIN_TITLE}}

| Field | Value |
|---|---|
| **Risk** | {{CHAIN_RISK}} |
| **Confidence** | {{CHAIN_CONF}} |
| **Window** | {{CHAIN_START}} to {{CHAIN_END}} ({{CHAIN_SPAN}} minutes) |
| **Modules** | {{CHAIN_MODULES}} |

**Event Sequence:**

| # | Timestamp (UTC) | Site / Domain | Page Title (truncated) | What it represents |
|---:|---|---|---|---|
| 1 | {{CE_TS_1}} | {{CE_SITE_1}} | {{CE_TITLE_1}} | {{CE_WHAT_1}} |
| 2 | {{CE_TS_2}} | {{CE_SITE_2}} | {{CE_TITLE_2}} | {{CE_WHAT_2}} |
| 3 | {{CE_TS_3}} | {{CE_SITE_3}} | {{CE_TITLE_3}} | {{CE_WHAT_3}} |

**Analysis:**

> {{CHAIN_NARRATIVE}}

**Recommended action:** {{CHAIN_ACTION}}

---


### 2.6 MITRE ATT&CK Mapping

| Technique ID | Technique Name | Modules Triggered | Finding Count | Risk |
|---|---|---|---:|---|
| T1048.003 | Exfil Over Alternative Protocol (email) | Email Services | {{M_T1}} | {{M_R1}} |
| T1567.002 | Exfil Over Web Service: Cloud Storage | File Transfer | {{M_T2}} | {{M_R2}} |
| T1567.003 | Exfil Over Web Service: Code Repository | Paste Sites | {{M_T3}} | {{M_R3}} |
| T1219 | Remote Access Software | Remote Access | {{M_T4}} | {{M_R4}} |
| T1071.001 | Web Protocols (C2 via Discord/Telegram) | Social Media | {{M_T5}} | {{M_R5}} |
| T1213 | Data from Information Repositories | AI, Doc Processing | {{M_T6}} | {{M_R6}} |
| T1005 | Data from Local System (OCR of screenshots) | Doc Processing | {{M_T7}} | {{M_R7}} |
| T1591 | Gather Victim Org Information | Flight Risk | {{M_T8}} | {{M_R8}} |

---

## SCAN COMPLETENESS STATEMENT

| Metric | Value |
|---|---|
| Total rows visible in session | {{ROWS_SCANNED}} |
| Rows within date filter | {{ROWS_IN_SCOPE}} |
| Full file scanned | {{SCAN_COMPLETE}} |
| Scan status | {{SCAN_STATUS}} |

> This analysis was performed by cognitive row scanning (no code execution).
> All findings are based solely on rows visible in this analysis session.
> Cross-validate HIGH and CRITICAL findings using the CodeInterpreter or Agentic version of DFIR-IBHA on the complete dataset before using this report as the sole basis for any action.

---

## APPENDIX A — All Flagged Events (Complete Evidence Table)

| Finding ID | Module | Risk | Confidence | Timestamp (UTC) | Domain | Page Title (truncated) | Visits | After-Hours |
|---|---|---|---|---|---|---|---:|---|
| IBHA-001 | {{APP_MOD_1}} | {{APP_R_1}} | {{APP_C_1}} | {{APP_TS_1}} | {{APP_DOM_1}} | {{APP_TITLE_1}} | {{APP_V_1}} | {{APP_AH_1}} |


---

## APPENDIX B — Extracted Email Addresses

| Email Address | Appearances | First Seen | Last Seen | Corporate? | Risk |
|---|---:|---|---|---|---|
| {{EA_1}} | {{EA_C_1}} | {{EA_F_1}} | {{EA_L_1}} | {{EA_C_01}} | {{EA_R_1}} |

---

## APPENDIX C — NSFW Domain List

> **🔒 RESTRICTED — AUTHORIZED PERSONNEL ONLY**
> **Distribution:** HR Director, Legal Counsel, Authorized Investigator
> **Do not include this appendix in shared report versions.**

| Domain (hostname only) | Category | Access Events | Business-Hours Events |
|---|---|---:|---:|
| {{NC_DOM_1}} | {{NC_CAT_1}} | {{NC_EV_1}} | {{NC_BH_1}} |

---

*End of Report — {{CASE_REF}} — {{REPORT_DATE}}*
