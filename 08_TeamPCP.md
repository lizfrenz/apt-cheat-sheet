# Threat Actor Profile: TeamPCP
>☁️ Security researchers identified the group after observing malicious activity involving the "TeamPCP Cloud stealer" and tpcp[.]tar[.]gz files used to exfiltrate data to attacker-controlled servers. Flare's threat intelligence analysis, published February 5, 2026 by researcher Assaf Morag, noted that Telegram communications reference African and Kenyan politics, suggesting the group may originate from or have ties to East Africa. The Kenyan government reportedly accused TeamPCP of hacking its systems, adding circumstantial weight to this geographic link. However, the attribution is not definitive. Cultural markers in their code complicate the picture: internal timestamps in payloads reference October 26, 1985 (a "Back to the Future" Easter egg), and code comments use English-language internet culture references, indicating operators fluent in Western digital culture. Infrastructure analysis by Trend Micro traced C2 nodes to AS205759, a bulletproof hosting provider operating across a Netherlands-Ukraine jurisdictional gap under Ghosty Networks LLC / DEMENIN B.V. TeamPCP has reported collaborations with LAPSUS$ (the extortion group, allegedly using TeamPCP-sourced credentials) and Vect RaaS (a new ransomware-as-a-service operation distributing affiliate keys via BreachForums). JARM TLS fingerprinting of TeamPCP infrastructure is consistent with the AdaptixC2 framework, whose developer "RalfHacker" has been linked to the Russian criminal underground, though this connection warrants caution.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | TeamPCP |
| **Aliases** | DeadCatx3, PCPcat, ShellForce, CanisterWorm |
| **Actor Type** | eCrime |
| **Suspected Origin** | Unknown / Not publicly documented |
| **Active Since** | 2025-11 (public emergence; self-described rebranding suggests prior activity) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Mass Cloud Infrastructure Compromise via Worm (2025–2026)**

| Field | Details |
|---|---|
| **Date** | 2025-12 / 2026-02 |
| **Campaign / Vulnerability Name** | Operation PCPcat / Cloud Worm Campaign |
| **Victims / Targets** | 60,000+ servers worldwide; victims in South Korea, Canada, United States, Serbia, UAE; JobsGO[.]vn (Vietnam) — 2M+ records exfiltrated |
| **Description** | TeamPCP launched a worm-driven campaign targeting exposed Docker APIs, Kubernetes clusters, Redis servers, Ray dashboards, and React2Shell vulnerabilities. Each compromised server became a self-propagating scanner and criminal platform running cryptocurrency miners (XMRig/Monero), proxy software, and ransomware C2 infrastructure. Kubernetes clusters were converted into distributed botnets. Data was published via the ShellForce Telegram channel. |
| **Source / Link** | Flare — hxxps://flare[.]io/learn/resources/blog/teampcp-cloud-native-ransomware |

**2.2 Trivy Supply Chain Attack (2026-03)**

| Field | Details |
|---|---|
| **Date** | 2026-03 |
| **Campaign / Vulnerability Name** | CVE-2026-33634 / Trivy Supply Chain Compromise |
| **Victims / Targets** | Aqua Security (Trivy vulnerability scanner), LiteLLM AI gateway, Telnyx Python package; estimated 95 million developers downstream |
| **Description** | TeamPCP compromised Aqua Security's Trivy vulnerability scanner by stealing GitHub authentication credentials via an automated agent. They injected credential-stealing malware into official Trivy releases and GitHub Actions, then pivoted to compromise LiteLLM and Telnyx. Checkmarx GitHub Actions were subsequently compromised via stolen Trivy credentials. TeamPCP also deployed a Kubernetes wiper targeting Iranian time-zone systems. |
| **Source / Link** | The Hacker News — hxxps://thehackernews[.]com/2026/03/teampcp-hacks-checkmarx-github-actions.html |

**2.3 Partnership with Vect Ransomware Group (2026)**

| Field | Details |
|---|---|
| **Date** | 2026 |
| **Campaign / Vulnerability Name** | RaaS Partnership with Vect |
| **Victims / Targets** | Organizations with compromised CI/CD pipelines and cloud environments |
| **Description** | TeamPCP began partnering with the Vect ransomware group to convert supply chain compromises into large-scale ransomware operations, expanding from cryptomining and data theft into full ransomware deployment as an initial access broker. |
| **Source / Link** | Socket / Infosecurity Magazine — hxxps://www[.]infosecurity-magazine[.]com/news/teampcp-targets-telnyx-pypi-package/ |

---

## 3. Primary Targets

### Industries / Sectors
- Cloud infrastructure and DevOps
- Software supply chain (open-source ecosystems)
- AI/ML development tooling
- Technology companies
- Financial services
- Any organization with misconfigured cloud infrastructure

### Notable Victim Organizations
- Aqua Security (Trivy scanner)
- LiteLLM (AI gateway)
- Telnyx (Python package)
- Checkmarx (GitHub Actions)
- JobsGO[.]vn (Vietnam recruitment platform)

### Technologies & CVEs Exploited
- CVE-2026-33634 (Trivy supply chain — CVSS 9.4)
- Exposed Docker APIs (unauthenticated)
- Exposed Kubernetes API servers
- Redis misconfiguration
- Ray dashboard exposure
- React2Shell vulnerability

---
## 4. Arsenal & Detection

### 4.1 Lure

### 4.2 Attributed Capability

### 4.3 Evasion Techniques

### 4.4 Detection Recommendations

---

## 5. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Exploit Public-Facing Application [T1190] |
| Initial Access | Supply Chain Compromise: Compromise Software Dependencies [T1195.001] |
| Execution | Command and Scripting Interpreter: Python [T1059.006] |
| Execution | Command and Scripting Interpreter: Unix Shell [T1059.004] |
| Persistence | Scheduled Task/Job: Cron [T1053.003] |
| Persistence | Create or Modify System Process [T1543] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Credential Access | Unsecured Credentials: Credentials in Files [T1552.001] |
| Credential Access | Unsecured Credentials: Container API [T1552.007] |
| Discovery | Cloud Service Discovery [T1526] |
| Discovery | Container and Resource Discovery [T1613] |
| Lateral Movement | Lateral Tool Transfer [T1570] |
| Collection | Data from Cloud Storage [T1530] |
| Exfiltration | Exfiltration Over Web Service [T1567] |
| Impact | Resource Hijacking [T1496] |
| Impact | Data Encrypted for Impact [T1486] |
| Impact | Disk Wipe [T1561] |
>[Source: Wiz Threat Landscape](hxxps://threats[.]wiz[.]io/all-actors/teampcp)
