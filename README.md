# AI-In-DFIR

> **Reusable AI skills, investigation workflows, and reporting frameworks for DFIR.**

**AI-In-DFIR** is an open-source collection of AI-assisted skills designed for **Digital Forensics and Incident Response (DFIR)**.

The goal is simple:

> **Turn repeatable DFIR investigation methodologies into reusable AI skills that can be used across different AI platforms and investigation scenarios.**

Instead of building one large AI prompt for everything, this project organizes DFIR capabilities into focused, reusable skills.

---

## Why AI-In-DFIR?

DFIR investigations often involve large amounts of structured and unstructured evidence:

- Browser history
- Endpoint artifacts
- Windows event logs
- Email
- Cloud activity
- Network data
- File systems
- Memory artifacts
- Malware
- User activity
- Application artifacts
- Security alerts

AI can help investigators with tasks such as:

- Evidence triage
- Pattern identification
- Timeline analysis
- Behavioral correlation
- Threat hunting
- Suspicious activity detection
- Investigation summarization
- MITRE ATT&CK mapping
- Risk assessment
- Report generation

However, a generic AI chatbot is not a DFIR methodology.

**AI-In-DFIR aims to bridge that gap.**

Each skill is designed around a defined investigation objective, evidence model, detection logic, correlation methodology, confidence model, and reporting structure.

---

## Project Goals

AI-In-DFIR aims to provide:

- 🧠 **AI-assisted DFIR investigation skills**
- 🔎 **Evidence-driven analysis**
- 🧩 **Modular investigation workflows**
- 📊 **Structured risk and confidence assessment**
- 🔗 **Cross-artifact correlation**
- 🛡️ **DFIR-focused threat detection**
- 📝 **Consistent investigation reporting**
- 🔄 **Reusable prompts and instructions**
- 🌐 **Platform-independent AI workflows where possible**

The project is intended to be useful for both individual investigators and teams experimenting with AI-assisted DFIR.

---

# Skills

Each investigation domain is maintained as an independent skill.

Initial and planned skills include:

| Skill | Description | Status |
|---|---|---|
| Internet Browser History Analyzer | Analyze browser history for suspicious browsing, data transfer, cloud storage, AI usage, remote access, insider-threat indicators, and behavioral chains. | 🚧 In Development |
| Endpoint Analyzer | Analyze endpoint artifacts and identify suspicious activity, persistence, execution, and user behavior. | 🔬 Planned |
| Email Analyzer | Analyze email artifacts for phishing, exfiltration, suspicious communication, and account activity. | 🔬 Planned |
| Cloud Activity Analyzer | Analyze cloud-service activity and identify suspicious access, sharing, downloads, and exfiltration patterns. | 🔬 Planned |
| Windows Event Analyzer | Analyze Windows event logs for suspicious authentication, execution, persistence, and lateral-movement activity. | 🔬 Planned |
| Malware Analysis | Assist with structured malware triage and behavioral analysis. | 🔬 Planned |
| Memory Forensics Assistant | Assist investigators with memory-forensics interpretation and artifact triage. | 🔬 Planned |
| Timeline Analyzer | Correlate artifacts across time to identify suspicious activity chains. | 🔬 Planned |

The list will evolve as new skills are developed.

---

# Design Philosophy

AI-In-DFIR follows several principles.

## 1. Evidence First

AI should not invent evidence.

A finding should be traceable to an observable artifact whenever possible.

The project favors:

> **Evidence → Interpretation → Confidence → Risk**

rather than:

> **Assumption → Conclusion**

---

## 2. Observation ≠ Inference

A browser artifact may demonstrate that a URL was accessed.

It does not necessarily prove:

- successful authentication
- successful upload
- successful download
- file contents
- user intent
- data exfiltration
- account ownership

Skills should distinguish observed artifacts from analytical inference.

---

## 3. Confidence and Risk Are Different

A suspicious event can have high investigative risk while still having limited evidentiary confidence.

Skills should therefore distinguish concepts such as:

- **Observed**
- **Possible**
- **Probable**
- **Corroborated**
- **Confirmed**

from:

- **Critical**
- **High**
- **Medium**
- **Low**

This prevents severity from being confused with evidentiary certainty.

---

## 4. Correlation Over Isolated Indicators

A single event may be benign.

Multiple related events occurring within a meaningful time window can provide much stronger investigative context.

For example:

```text
Document Processing
        ↓
Personal Email
        ↓
Cloud Storage
        ↓
File Transfer
```

can be substantially more significant than any individual event alone.

Where appropriate, skills should therefore include temporal and behavioral correlation.

---

## 5. Complete-Scan Awareness

Skills should explicitly report whether the available evidence was completely analyzed.

A skill should distinguish:

```text
SCAN STATUS: COMPLETE
```

from:

```text
SCAN STATUS: PARTIAL
```

AI should never claim complete analysis when only a subset of the evidence was accessible.

There is no arbitrary universal row-count limit. The relevant question is whether the AI platform can access and analyze the complete evidence set.

---

## 6. Reproducibility

Investigation logic should be documented clearly enough that another investigator can understand:

- What was searched
- Which indicators were used
- How severity was assigned
- How confidence was assigned
- Which correlation rules were applied
- Which evidence supported a finding
- What limitations existed

The goal is to make AI-assisted DFIR **auditable rather than opaque**.

---

# Platform Compatibility

The skills are intended to be adaptable to multiple AI environments, including:

- ChatGPT
- Claude
- Gemini
- Other LLM platforms
- Local/private AI deployments
- Agentic investigation environments

Some platforms provide additional capabilities such as:

- Python execution
- File-system access
- Code execution
- Large-context processing
- Tool use
- Agentic workflows

Where platform capabilities differ, skills may provide multiple execution variants.

For example:

```text
Cognitive Chat
Code Interpreter
Agentic
```

The investigation methodology should remain consistent even when the execution mechanism changes.

---

# Example Architecture

A skill may contain:

```text
skill/
├── README.md
├── instructions/
│   ├── cognitive-chat.md
│   ├── code-interpreter.md
│   └── agentic.md
│
├── indicators/
│   ├── domains.txt
│   ├── keywords.txt
│   └── services.yaml
│
├── detection/
│   ├── rules.md
│   ├── correlation.md
│   └── scoring.md
│
├── templates/
│   ├── report.md
│   └── report.html
│
└── examples/
    └── ...
```

Not every skill needs every directory. The structure should match the investigation domain.

---

# Current Skill: Internet Browser History Analyzer

The first major skill in this repository is the **Internet Browser History Analyzer**.

It is designed to analyze browser-history exports and identify potential indicators including:

- Personal and disposable email
- File-transfer services
- Cloud storage
- Paste and code-sharing services
- Remote-access software
- Social and communication platforms
- AI/LLM services
- Document processing and conversion
- NSFW/restricted-content indicators
- Potential insider-threat activity
- Potential data-exfiltration chains
- Job-search / flight-risk indicators
- Temporal activity patterns

The skill combines individual indicators with temporal and behavioral correlation to reduce reliance on isolated domain matches.

---

# Investigation Output

Depending on the skill, an investigation may produce:

- File profile
- Evidence summary
- Detection findings
- Risk classification
- Confidence classification
- Temporal analysis
- Correlated activity chains
- MITRE ATT&CK mapping
- Flight-risk assessment
- Investigation limitations
- Evidence appendix
- Markdown report
- HTML report

The exact output is defined by each individual skill.

---

# Important Disclaimer

AI-In-DFIR is intended to **assist** DFIR professionals and security investigators.

AI-generated findings should not automatically be treated as definitive forensic conclusions.

Investigators should validate significant findings against appropriate evidence sources such as:

- Endpoint artifacts
- File-system evidence
- Authentication logs
- Network telemetry
- Proxy logs
- EDR telemetry
- Cloud audit logs
- Email systems
- Identity-provider logs
- Memory artifacts
- Other relevant forensic sources

AI-In-DFIR does not replace professional forensic examination, organizational procedures, legal requirements, or applicable chain-of-custody practices.

---

# Contributing

Contributions are welcome.

Potential contributions include:

- New DFIR skills
- Detection rules
- Indicator lists
- Correlation techniques
- Reporting templates
- MITRE ATT&CK mappings
- Test datasets
- False-positive research
- Platform-specific execution variants
- Documentation

When contributing a new skill, please document:

1. Investigation objective
2. Required evidence
3. Detection methodology
4. Indicator sources
5. Confidence model
6. Risk model
7. Correlation rules
8. Known limitations
9. Example usage
10. Expected output

---

# Roadmap

### Phase 1 — Foundation

- [x] Repository architecture
- [x] Browser History Analyzer
- [ ] Standard skill specification
- [ ] Common confidence model
- [ ] Common reporting model

### Phase 2 — Endpoint

- [ ] Windows Endpoint Analyzer
- [ ] Windows Event Analyzer
- [ ] Persistence Analyzer
- [ ] User Activity Analyzer
- [ ] Timeline Correlation

### Phase 3 — Communication & Cloud

- [ ] Email Analyzer
- [ ] Cloud Activity Analyzer
- [ ] SaaS Activity Analyzer
- [ ] Identity Activity Analyzer

### Phase 4 — Advanced DFIR

- [ ] Malware Analysis Assistant
- [ ] Memory Forensics Assistant
- [ ] Network Investigation Assistant
- [ ] Threat Hunting Assistant
- [ ] Cross-artifact Investigation Engine

### Phase 5 — AI/Agentic DFIR

- [ ] Agentic investigation workflows
- [ ] Tool-enabled analysis
- [ ] Automated evidence correlation
- [ ] Multi-source investigation workflows
- [ ] Investigation quality evaluation

---

# Versioning

Each skill should maintain its own version.

Example:

```text
Internet Browser History Analyzer v1.3
Endpoint Analyzer v1.0
Email Analyzer v0.5
```

Changes to detection logic, indicators, scoring, or reporting requirements should be documented in the skill's changelog.

---

## Project Status

AI-In-DFIR is an evolving open-source project.

The objective is not to create a single "DFIR prompt", but to build a **collection of structured, reusable AI investigation capabilities for DFIR**.

> **One investigation domain. One focused skill. Evidence-driven AI assistance.**
