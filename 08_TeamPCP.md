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
Trust exploitation by spoofing identities and typosquating domains. Exploitation of compromised accounts.

Their initial access methods have evolved through two distinct phases.
In Phase 1 (December 2025–February 2026), the group launched "Operation PCPcat," a worm-driven campaign that automated scanning for exposed Docker APIs, Kubernetes control planes, Ray dashboards, and Redis servers lacking authentication. They exploited the React2Shell vulnerability (CVE-2025-55182, CVSS 10.0) for pre-authentication remote code execution in React Server Components and Next.js applications. This campaign peaked around December 25, 2025, compromising over 60,000 servers across Azure (61% of victims) and AWS (36%), spanning the UAE, Canada, South Korea, Serbia, the United States, and Vietnam. Industries hit included financial services, consumer goods, professional services, e-commerce, and HR.

Phase 2 (March 2026) represents a dramatic escalation into cascading software supply chain compromise. The chain began when an AI-powered autonomous agent called "hackerbot-claw" exploited a misconfigured pull_request_target GitHub Actions workflow in Aqua Security's Trivy repository on February 27–28, 2026. This bot forked the Trivy repo, opened a legitimate-looking pull request, and injected a malicious script into the GitHub Action runner. By scraping /proc/<pid>/mem, it extracted a Personal Access Token with repository scope across Aqua Security's entire 33+ repository GitHub organization. Critically, Aqua Security's credential rotation was incomplete — the attacker captured refreshed credentials before old access was fully revoked, retaining persistent access that enabled the devastating March 19 attack.

Rather than traditional deception, TeamPCP employs several sophisticated forms of trust exploitation. They spoofed legitimate maintainer identities (including developers DmitriyLewen and Tomochika Hara) in Git commits, cloning original commit metadata to make malicious releases indistinguishable in the GitHub UI. They used typosquatted domains mimicking legitimate vendor infrastructure — for instance, scan.aquasecurtiy[.]org (note the transposed letters). They hid malicious payloads within .WAV audio files using steganography, and deployed ICP blockchain canisters as censorship-resistant C2 dead-drops that cannot be taken down through conventional domain registrar or hosting provider channels.
One particularly aggressive tactic involved incident response disruption: during the Trivy compromise, TeamPCP deployed 88 bot comments from 73 compromised developer accounts in a 102-second window to flood GitHub issue discussions, closed disclosure issues using a compromised maintainer account, and deleted incident coordination threads — deliberately slowing community response.


### 4.2 Attributed Capability
**CanisterWorm**  —  the self-propagating npm/Docker worm with ICP blockchain C2, first observed late 2025\. 

The **TeamPCP Cloud Stealer**  — a multi-stage CI/CD credential harvester. 

The **Kamikaze wiper**  — a geotargeted destructive payload for Iranian-locale systems. 

Python-based scanning modules: `kube.py` for Kubernetes exploitation, `scanner.py`/`teampcp.py` for Docker and Ray dashboard discovery, `react.py` for React2Shell scanning, and `redis-deploy.py` for Redis server exploitation.

The group's dual-use tool stack includes **FRP** (Fast Reverse Proxy) for persistent tunneling, **gost** (GO Simple Tunnel) for SOCKS5 proxying, **Sliver** for C2 over mTLS/WireGuard/HTTPS, **XMRig** for Monero cryptomining, and **TruffleHog** for automated credential validation. Infrastructure analysis revealed use of the **AdaptixC2** framework for some operations.

First documented use of **Internet Computer Protocol (ICP) blockchain canisters** as decentralized, censorship-resistant C2 dead-drops.

### 4.3 Evasion Techniques
#### LotL
Use of **GitHub Releases API as a fallback exfiltration channel**, creating `tpcp-docs` repositories on victim GitHub accounts to stage stolen data.
Use of an **AI-powered autonomous agent** (hackerbot-claw/openclaw) for automated GitHub Actions exploitation — one of the earliest confirmed cases of AI-assisted supply chain attacks.

#### Persistence
Introduction of **.pth file persistence** for Python, ensuring code auto-executes on any Python invocation and survives package removal.

#### Encryption
Exfiltrated data across all campaigns uses a consistent format: encrypted archives named `tpcp[.]tar[.]gz` with **AES-256-CBC \+ RSA-4096 (OAEP) encryption**. The same RSA public key appears across all campaign waves — the strongest technical attribution link tying these operations together. 

#### Obfuscation
Deployment of **WAV audio steganography** for payload delivery, with XOR-obfuscated executables embedded in audio files.

#### Anti-forensic techniques 
Anti-forensic techniques include the October 1985 timestamp Easter egg, "Bad Apple\!\!" anti-sandbox tricks, double-encoded Base64 with zlib compression for miners, and operational signatures like songs embedded in payloads.


### 4.4 Detection Recommendations
* **Enforce MFA on all registry accounts** (npm, PyPI, Docker Hub, GitHub) — compromised publisher accounts were the enabler for OpenVSX and npm compromise.  
* **Implement GitHub org-level required reviewers** for all release workflows.  
* **Alert on unexpected outbound traffic from CI runners** — runners should have a narrow, known egress profile.  
* **Monitor for TLS to unusual infrastructure from build environments** — `.icp0.io` and related ICP domains are not expected in normal CI/CD egress.  
* **Log and alert on `github.com/releases` API calls** from CI environments creating new repos — TeamPCP used `tpcp-docs` repos as exfiltration staging.  
* **Audit exposed Docker APIs** — CanisterWorm propagated via unauthenticated Docker socket access.  
* **Disable unauthenticated Docker daemon exposure** — bind only to `unix:///var/run/docker.sock`, never to `0.0.0.0:2375`.  
* **Apply Kubernetes RBAC strictly** — the Kamikaze payload deployed privileged DaemonSets; restrict DaemonSet creation to narrow service accounts.  
* **Enable Kubernetes admission controllers** (e.g., OPA/Gatekeeper) to block privileged pod specs.  
* **Monitor cloud IMDS endpoints** for unusual access patterns — TeamPCP's stealer targeted EC2 and ECS metadata endpoints.  
* **Store secrets in a vault** (AWS Secrets Manager, HashiCorp Vault) — not in `.npmrc`, `~/.aws/credentials`, `~/.kube/config`, or environment variables accessible to CI runners.  
* **Use short-lived credentials** with OIDC federation where possible — eliminates long-lived tokens as a theft target.  
* **Audit and rotate all publish tokens** for npm, PyPI, Docker Hub, and similar registries — treat any org-wide CI/CD compromise as a full credential rotation event.  
* **Scope tokens to minimum permissions** — a PyPI publish token should not have org-wide access.  
* **Pin all dependencies to specific versions with hash verification** — LiteLLM was compromised partly because Trivy was consumed without version pinning.  
* **Use dependency lock files** and verify integrity on every build.  
* **Monitor PyPI, npm, and other registries** for unexpected new versions of your dependencies — the malicious LiteLLM versions appeared 13 minutes apart and were live for \~5.5 hours before quarantine.  
* **Audit `.pth` files** in Python environments — TeamPCP's LiteLLM payload planted a `.pth` file that executes on any Python invocation and **survives package removal**; detection requires filesystem inspection, not just pip.  
* **Run Trivy and other scanners from verified, immutable container images** rather than pulling from GitHub Actions tags.  
* **Pin all GitHub Actions to commit SHAs**, not tags or branch names — tags are mutable and were the primary hijack vector (75 tags poisoned in the Trivy compromise).  
* **Restrict `pull_request_target`** workflows — never grant write permissions or secret access to code from forks.  
* **Audit GitHub Actions permissions** — apply least privilege; most workflows don't need `contents: write` or `packages: write`.  
* **Enable secret scanning** and push protection on all repos.  
* **Require CODEOWNERS approval** for any workflow file changes.  
* **Rotate all tokens immediately** after any suspected CI/CD compromise — TeamPCP retained access because rotation was incomplete.
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
