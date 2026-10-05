# Internet History Analyzer

> **AI-assisted Internet browsing history analysis for Digital Forensics and Incident Response.**

The **Internet History Analyzer** is a DFIR-IBHA skill for analyzing browser-history CSV data and identifying potentially relevant activity from a digital-forensics and incident-response perspective.

It is designed to analyze browsing activity, identify configured indicators, correlate related events, assess confidence and risk, and produce a structured investigation report.

---

## What It Analyzes

The analyzer works with Internet browsing-history data containing information such as:

- URL
- Page title
- Timestamp
- Visit count, when available

The analysis examines the browsing history for indicators related to:

- Email services
- File-transfer and exfiltration services
- Cloud storage
- Paste and code-sharing services
- Remote-access services
- Social and communication platforms
- AI/LLM services
- Document-processing services
- Restricted-content indicators
- Potential flight-risk activity
- Temporal activity patterns
- Related behavioral activity chains

---

## Investigation Perspectives

The DFIR-IBHA analysis supports the following perspectives:

### Data Theft

Focuses on activity potentially relevant to data handling, transfer, and exfiltration.

### Insider Threat

Focuses on browsing activity that may be relevant to suspicious employee behavior or potential misuse of organizational resources.

### Asset Misuse

Focuses on potentially inappropriate or unauthorized use of systems and services.

### All

Performs the available analysis across the supported investigation perspectives.

---

## Detection Categories

### 1. Email Services

The analyzer checks browsing activity against configured email-service indicators.

This includes:

- Personal free email
- Encrypted or anonymous email
- Disposable email
- Corporate email
- Email addresses appearing in page titles

Email findings include the observed URL, title, timestamp, visit count where available, and risk classification.

---

### 2. File Transfer and Exfiltration Services

The analyzer checks for configured file-transfer and file-sharing services.

Examples of analyzed categories include:

- Anonymous file-sharing services
- File-transfer platforms
- Personal file-sharing services
- Transfer services

A browser-history entry for a file-transfer service is treated as an indicator of service access. It does not by itself prove that a file was successfully uploaded or exfiltrated.

---

### 3. Cloud Storage

The analyzer identifies configured cloud-storage services such as:

- Google Drive
- Microsoft OneDrive

Cloud-storage activity is considered together with surrounding browsing activity where relevant.

---

### 4. Paste and Code Sharing

The analyzer checks configured paste and code-sharing services.

These indicators can be relevant to investigations involving:

- Information sharing
- Code sharing
- Potential data exposure
- Potential staging or transfer activity

---

### 5. Remote Access

The analyzer identifies configured remote-access services, including services such as:

- AnyDesk
- Chrome Remote Desktop

Remote-access activity is considered as an indicator and may become more significant when correlated with other activity.

---

### 6. Social and Communication Services

The analyzer identifies configured social and communication platforms.

These may include:

- Reddit
- Telegram
- Twitter/X
- Instagram
- Facebook
- Pinterest
- Other configured platforms

Social and communication activity is treated as contextual unless additional evidence increases its significance.

---

### 7. AI and LLM Services

The analyzer identifies configured AI/LLM services, including:

- ChatGPT
- Google Gemini
- Claude
- Bing

AI-service activity is considered in combination with other browsing activity when relevant.

A visit to an AI service alone does not establish that sensitive information was submitted to the service.

---

### 8. Document Processing

The analyzer identifies configured document-processing and conversion services.

Examples include:

- iLovePDF
- Smallpdf
- Sejda
- CloudConvert
- iLoveIMG
- Scribd
- SlideShare

Document-processing activity can become more significant when it occurs near other relevant indicators such as AI services, personal email, cloud storage, or file-transfer services.

---

### 9. Restricted Content

The analyzer checks for configured restricted-content indicators.

These findings are reported according to the investigation scope and configured detection rules.

---

### 10. Flight-Risk Indicators

The analyzer can identify configured employment-related browsing indicators, including:

- Job-board activity
- LinkedIn job activity
- Competitor career-page activity

These indicators are analyzed as a contextual flight-risk signal and are not treated as proof of malicious activity.

---

# Temporal Analysis

The analyzer examines the timing of browsing activity.

The analysis includes:

- Business-hours activity
- After-hours activity
- Weekend activity
- Daily activity volume
- Activity spikes
- Repeated activity
- Time-based relationships between events

Activity occurring outside normal hours is treated as a contextual indicator rather than automatically being classified as malicious.

---

# Behavioral Chain Analysis

The analyzer does not rely only on isolated indicators.

It also evaluates configured combinations of activity occurring within defined time windows.

Examples include:

### Document Processing + AI

Document-processing activity followed by AI-service activity within the configured correlation window.

### Personal Email + File Transfer

Personal-email activity followed by file-transfer activity within the configured correlation window.

### Remote Access + File Transfer

Remote-access activity combined with file-transfer activity within the configured session or time relationship.

### After-Hours Multi-Category Activity

After-hours activity combined with multiple configured data-handling or exfiltration categories.

The purpose of chain analysis is to provide additional context around individual browser-history events.

---

# Confidence Classification

The analyzer distinguishes between the strength of the available evidence.

### CONFIRMED

Direct evidence in the available browser-history data supports the finding.

### PROBABLE

The available evidence provides strong support for the interpretation, but browser history alone does not directly prove the underlying action.

### POSSIBLE

The activity matches a relevant indicator, but the available evidence is insufficient to establish the interpretation with higher confidence.

The analyzer should not represent an inferred action as directly observed evidence.

---

# Risk Classification

Findings are assigned a risk level according to the configured DFIR-IBHA rules.

Supported levels include:

- **CRITICAL**
- **HIGH**
- **MEDIUM**
- **LOW / INFO**

Risk and confidence are separate characteristics.

For example, an event may be considered:

```text
Risk       : HIGH
Confidence : POSSIBLE
```

This means the activity may be important to investigate even though the available browser-history evidence is limited.

---

# Evidence Reporting

For identified findings, the analyzer records the available evidence, including:

- URL
- Page title
- Timestamp
- Row number
- Visit count, when available
- Detection category
- Risk level
- Confidence level
- Related activity
- Correlation information

Findings are tied back to the browser-history evidence so that an investigator can review the underlying event.

---

# Scan Completeness

The analyzer is designed to analyze the complete uploaded dataset when the full CSV is accessible.

There is no fixed 5,000-row limit.

The investigation reports the scan status:

```text
Total rows   : [N]
Rows scanned : [N]
Scan status  : COMPLETE / PARTIAL
```

### COMPLETE

All accessible data rows in the uploaded CSV were analyzed.

### PARTIAL

Only part of the uploaded dataset was available or analyzed.

The analyzer must not claim a complete scan when the complete dataset was not inspected.

If the dataset cannot be fully accessed, the limitation should be disclosed.

---

# File Profile

Before analysis, the analyzer identifies the structure of the uploaded CSV.

The file profile includes:

- File name
- Total rows
- Column names
- URL column
- Page-title column
- Timestamp column
- Visit-count column, when available
- Earliest timestamp
- Latest timestamp
- Analysis date range, when specified

If the required URL or timestamp information cannot be identified, analysis should not proceed until the relevant columns are clarified.

---

# Date Filtering

The analysis can be performed against:

- The complete available date range
- A relative date range, such as the last 90 days
- A specified absolute date range

Example:

```text
Analyze the attached browser-history CSV using DFIR-IBHA,
time frame: last 90 days from today,
from Data Theft perspective.
```

Example:

```text
Analyze the attached browser-history CSV using DFIR-IBHA,
time frame: 1 January 2026 to 1 March 2026,
from Insider Threat perspective.
```

---

# MITRE ATT&CK Mapping

Where supported by the observed activity and DFIR-IBHA rules, findings can be mapped to relevant MITRE ATT&CK techniques.

The mapping provides investigative context and does not by itself prove that a particular technique was successfully executed.

---

# Reporting

The Internet History Analyzer produces a structured investigation report containing relevant sections such as:

- Investigation scope
- File profile
- Scan completeness
- Findings
- Confidence assessment
- Risk assessment
- Temporal analysis
- Behavioral chains
- Flight-risk analysis
- MITRE ATT&CK mapping
- Evidence appendix
- Investigation limitations
- Restricted-content findings

The current DFIR-IBHA implementation supports Markdown and HTML investigation reports.

---

# Evidence Limitations

Browser history provides evidence of browser-recorded activity.

A browser-history entry does not by itself prove:

- Successful authentication
- Successful upload
- Successful download
- File contents
- User identity
- User intent
- Successful data transfer
- Actual data exfiltration

Where the evidence supports only an inference, the report should identify it as an inference and assign an appropriate confidence level.

---

# Current Implementation

The current Internet History Analyzer is based on the **DFIR-IBHA Cognitive-Chat instruction set**.

The Cognitive-Chat methodology defines:

- Investigation invocation
- File profiling
- Indicator scanning
- Risk classification
- Confidence classification
- Temporal analysis
- Behavioral-chain detection
- Flight-risk analysis
- MITRE ATT&CK mapping
- Evidence reporting
- Scan-completeness reporting

The analysis methodology is documented in the corresponding DFIR-IBHA instruction file included with the skill.

---

# Version

**DFIR-IBHA Internet History Analyzer — v1.3**

The detection rules, indicators, correlation logic, scoring, and reporting templates may change between versions.

Changes should be documented in the skill's changelog.

---

# Responsible Use

This skill is intended for authorized DFIR investigations, security analysis, incident response, and defensive security research.

Investigators should validate significant findings against additional forensic evidence where available.

The Internet History Analyzer should be treated as an **AI-assisted investigation and triage capability**, not as a replacement for forensic validation.

Users are responsible for ensuring that their investigation and handling of browser-history data complies with applicable laws, organizational policies, privacy requirements, and authorization requirements.

---

# Part of AI-In-DFIR

The Internet History Analyzer is part of the **AI-In-DFIR** project.

[← Back to AI-In-DFIR](../README.md)