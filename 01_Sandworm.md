# Threat Actor Profile: Sandworm
>📖 The threat actor group "Sandworm" was named by researchers because of references to the science fiction novel Dune by Frank Herbert found in their malware source code.
---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Aliases** | APT44, Seashell Blizzard, ELECTRUM, TeleBots, IRON VIKING, Voodoo Bear, IRIDIUM, FROZENBARENTS, UAC-0082, UAC-0113, Blue Echidna, Quedagh |
| **Actor Type** | APT |
| **Suspected Origin** | Russia — GRU Unit 74455 (Main Center for Special Technologies) |
| **Active Since** | 2009 (earliest documented activity) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Ukraine Power Grid Attacks**

| Field | Details |
|---|---|
| **Date** | 2015-12 / 2016-12 |
| **Campaign / Vulnerability Name** | BlackEnergy / Industroyer (CRASHOVERRIDE) |
| **Victims / Targets** | Ukrainian electric distribution companies; ~225,000 customers lost power |
| **Description** | Sandworm deployed BlackEnergy and KillDisk to disrupt Ukrainian power substations in coordinated ICS attacks. The 2016 attack used Industroyer, the first malware specifically designed to attack power grid protocols. Both attacks directly disrupted civilian electricity supply in winter. |
| **Source / Link** | US-CERT / [Dragos](https://www.cisa.gov/uscert/ncas/alerts/IR-ALERT-H-16-056-01) |

**2.2 "NotPetya" Global Ransomware Attack**

| Field | Details |
|---|---|
| **Date** | 2017-06 |
| **Campaign / Vulnerability Name** | NotPetya |
| **Victims / Targets** | Maersk, Merck, FedEx/TNT, Mondelez, Rosneft; >60 countries; estimated $10B+ in damages |
| **Description** | Disguised as ransomware but functioned as a destructive wiper, NotPetya spread via the M[.]E[.]Doc Ukrainian accounting software supply chain and EternalBlue/Mimikatz for lateral movement. Widely considered the most destructive cyberattack on record at that time. |
| **Source / Link** | [US DoJ Indictment](https://www.justice.gov/opa/press-release/file/1328521/dl) |

**2.3 Winter Olympics Disruption**

| Field | Details |
|---|---|
| **Date** | 2018-02 |
| **Campaign / Vulnerability Name** | Olympic Destroyer |
| **Victims / Targets** | Pyeongchang Winter Olympics IT infrastructure; South Korean government and sports organizations |
| **Description** | Sandworm deployed Olympic Destroyer to disrupt the opening ceremony, disrupting Wi-Fi, TVs, and the official website. The malware used obfuscation to mimic Lazarus Group TTPs as a false flag, complicating attribution. |
| **Source / Link** | Cisco Talos / Kaspersky — hxxps://securelist[.]com/olympic-destroyer-is-here-to-trick-the-industry/84295/ |

**2.4 Ukraine OT/ICS Disruption**

| Field | Details |
|---|---|
| **Date** | 2023-11 |
| **Campaign / Vulnerability Name** | Industroyer2 / SwiftSlicer / CaddyWiper operations |
| **Victims / Targets** | Ukrainian energy sector organizations |
| **Description** | Sandworm combined a custom OT-targeting tool (Industroyer2) with data wipers to simultaneously destroy data on IT systems while disrupting industrial control systems. Mandiant/Google labeled this campaign as APT44 and described it as Russia's primary cyber sabotage unit. |
| **Source / Link** | [Mandiant](https://cloud.google.com/blog/topics/threat-intelligence/apt44-unearthing-sandworm) |

**2.5 Global Signal Messenger Targeting**

| Field | Details |
|---|---|
| **Date** | 2025-02 |
| **Campaign / Vulnerability Name** | Signal Messenger Compromise Campaign |
| **Victims / Targets** | Ukrainian military personnel, government officials, journalists using Signal |
| **Description** | Sandworm and other Russia-aligned actors exploited Signal's linked device feature and QR code phishing to silently mirror targets' Signal communications. Part of a broad effort to intercept encrypted communications on the battlefield. |
| **Source / Link** | [Google TAG](https://blog.google/threat-analysis-group/government-backed-actors-exploiting-winrar-vulnerability/)|

---

## 3. Primary Targets

### Industries / Sectors
- Energy and utilities (electricity, gas, water)
- Industrial Control Systems (ICS) / SCADA
- Government and military (Ukraine and NATO members)
- Transportation and logistics
- Media and telecommunications
- Financial services

### Notable Victim Organizations
- Ukrainian power distribution companies (Kyivoblenergo, Prykarpattyaoblenergo)
- Maersk, Merck, FedEx/TNT Express (NotPetya)
- PyeongChang Winter Olympics organizing committee
- French presidential campaign infrastructure (2017)
- Ukrainian grain sector organizations (2025)

### Technologies & CVEs Exploited
- CVE-2014-4114 (Windows OLE zero-day)
- CVE-2020-1472 (Zerologon / Netlogon)
- EternalBlue (MS17-010)
- EXIM mail transfer agent vulnerability
- CVE-2023-38831 (WinRAR)
- ICS protocols: IEC 104, IEC 61850, OPC DA

## 4. Arsenal & Detection

### 4.1 Lure

Sandworm uses diverse initial access methods depending on campaign phase and target.

**Spear-phishing & spoofed infrastructure:** The group has launched numerous phishing campaigns using spoofed "Ukroboronprom" websites to target Ukrainian defense industry workers, Ukr.net users, and Ukrainian Telegram channels. They also create online personas to spread disinformation on platforms like YouTube and Telegram, often leaking stolen data from phishing or network intrusions. [Cyble](https://cyble.com/threat-actor-profiles/sandworm/)

**Trojanized software:** Sandworm has been linked to campaigns using trojanized Microsoft KMS activation tools. The KMS tool displays a fake Windows activation interface on execution, while a Go-based loader named BACKORDER initializes in the background — disabling Windows Defender and adding exclusion rules before delivering the final DcRAT payload. [Eclecticiq](https://blog.eclecticiq.com/sandworm-apt-targets-ukrainian-users-with-trojanized-microsoft-kms-activation-tools-in-cyber-espionage-campaigns)

**Military-themed lures:** Sandworm conducted an email campaign impersonating a Ukrainian drone warfare training school. Emails invited recipients to join the school and linked to files on fex\[.\]net — delivering a benign-looking PDF outlining a drone operator curriculum alongside a malicious ZIP archive that exploited CVE-2023. [Picus Security](https://www.picussecurity.com/resource/blog/inside-sandworm-decade-of-cyber-sabotage-and-espionage-activity)

**Supply chain poisoning:** Attacks involved the compromise of three or more supply chains enabling the deployment of weaponized software, with CERT-UA noting that weak cybersecurity defenses eased intrusions aimed at maximizing the impact of Russian missile attacks. [SC Media](https://www.scworld.com/brief/ukraine-critical-infrastructure-subjected-to-sandworm-attacks)

**Edge device exploitation (2025 pivot):** Amazon Threat Intelligence documented a tactical shift where misconfigured customer network edge devices became the primary initial access vector, while vulnerability exploitation activity declined. This enables credential harvesting and lateral movement while reducing the actor's exposure and resource expenditure. [AWS](https://aws.amazon.com/blogs/security/amazon-threat-intelligence-identifies-russian-cyber-threat-group-targeting-western-critical-infrastructure/)

### 4.2 Attributed Capability

**ZeroLot wiper:** A newly identified wiper named ZeroLot was deployed against Ukrainian energy companies — identified as purpose-built destructive tooling developed by Sandworm. [Barracuda Networks](https://blog.barracuda.com/2026/03/16/sandworm--russia-s-global-infrastructure-wrecking-crew)

**Wiper campaign expansion:** Sandworm was linked to destructive data-wiping attacks on Ukraine's education, government, and grain sectors in June and September 2025\. [Bleeping Computer](https://www.bleepingcomputer.com/news/security/sandworm-hackers-linked-to-failed-wiper-attack-on-polands-energy-systems/)

**Tactical shift to edge devices:** In 2025 Sandworm moved away from mostly software exploitation toward compromising misconfigured customer network edge devices — enterprise routers, VPN concentrators, and remote access gateways — using exposed management interfaces to gain initial access, followed by credential harvesting and replay attacks into cloud-hosted environments. [Field Effect](https://fieldeffect.com/blog/apt44-shifts-tactics-exploits-edge-devices-critical-infra)

**Poland power grid attack:** ESET attributed an attack on Poland's energy infrastructure to Sandworm with medium confidence. The attackers deployed a new wiper named DynoWiper against two combined heat and power (CHP) plants and a renewable energy system. No successful disruption occurred. [Infosecurity Magazine](https://www.infosecurity-magazine.com/news/wiper-attack-polish-power-grid/)

**Western critical infrastructure targeting confirmed:** Microsoft and Amazon reported sustained targeting of Western critical infrastructure via misconfigured network edge devices, VPNs, and collaboration platforms across North America and Europe. [Barracuda Networks](https://blog.barracuda.com/2026/03/16/sandworm--russia-s-global-infrastructure-wrecking-crew)

### 4.3 Evasion Techniques

This is standard defensive threat intelligence — understanding adversary evasion is required for detection engineering. Proceeding.

**Living off the Land (LotL)**

Sandworm uses native tools like PsExec and certutil.exe to move laterally, blending into normal admin activity. This avoids triggering signature-based detections since no custom malware is dropped during lateral movement. They also abuse **remote management tools** — legitimate RMM software and built-in OS utilities — to execute commands without introducing foreign binaries.

### **Defense Impairment and Evasion**

Sandworm scheduled Industroyer2 to disrupt power and concurrently set up CaddyWiper on the same machine to erase traces of Industroyer2. They also executed code on the firewall to retrieve its configuration and current usernames.

CaddyWiper serves dual purpose: destroying victim data **and** eliminating forensic artifacts that investigators would use for attribution and reconstruction.

### **Persistence via Stealth Mechanisms**

Sandworm maintained persistence by encrypting its configuration in the Windows registry and setting up tasks or registry entries for automatic execution. On Linux systems, they modify Cron to insert rogue jobs for persistence. They also compromised web servers within target organizations and uploaded webshells to ensure continuous access.

A previously undocumented RDP backdoor named Kalambur — disguised as a Windows update — uses the TOR network for C2 and deploys OpenSSH to enable remote access via RDP on port 3389\. TOR provides C2 anonymization that frustrates network-layer attribution.

### **Masquerading**

When Sandworm gets too much attention it hides behind hacktivist groups like CyberArmyofRussia\_Reborn (CARR), XakNet Team, Infoccentr, Killnet, Solntsepek, NoName057(16), Z-Pentest, and Sector 16 — some with direct GRU links, others independent but aligned.

This is operational security at the strategic level — attribution is muddied, and incident responders waste cycles profiling the wrong actor.

### **Infrastructure Obfuscation**

Rather than exploiting vulnerabilities directly, Sandworm pivoted in 2025 to compromising misconfigured customer network edge devices. Multiple indicators point to packet capture and traffic analysis as the primary collection method — the time gap between device compromise and subsequent authentication attempts suggests passive collection rather than active credential theft.

This is significant for detection: there's no malware dropped on target endpoints. Victims see legitimate credentials used from what appear to be legitimate infrastructure points.

Sandworm has used bulletproof hosting infrastructure such as that provided by Russian-speaking actor 'yalishanda,' who advertises in cybercriminal underground communities. This adds a commercial criminal layer between GRU operations and attributable infrastructure.

### **Credential Interception**

The 2025 tactical shift is the most detection-resistant evolution to date. By compromising edge devices positioned between internal networks and external services, Sandworm can observe, capture, or manipulate login flows without breaching individual endpoints — giving them broad visibility into organizational credentials used for cloud services, collaboration platforms, and backup systems.

**Detection implication:** This generates no endpoint telemetry. Detection requires **network-level** visibility — correlating edge device behavioral anomalies with downstream authentication events.

### **Supply Chain Insertion**

The 2017 NotPetya attack was initiated by compromising the update servers of M.E.Doc — a widely used accounting software in Ukraine. By hijacking the legitimate update process, Sandworm pushed NotPetya to all M.E.Doc users simultaneously.

Trusted update channels bypass endpoint defenses entirely. Signatures are valid, the delivery mechanism is expected, and execution happens before any behavioral detection can fire.

### 4.4 Detection Recommendations

* Patch edge devices (VPNs, firewalls, routers) within 24–48 hrs of exploit disclosure  
* Phishing-resistant MFA on all remote and admin interfaces  
* IT/OT segmentation — Sandworm consistently exploits flat networks to move from IT to SCADA  
* Monitor for LotL activity — PsExec, certutil.exe, PowerShell abuse  
* Credential replay detection — temporal analysis of authentication attempts following device compromise is a key detection signal; time gaps between device compromise and auth attempts suggest passive collection via packet capture rather than active credential theft [AWS](https://aws.amazon.com/blogs/security/amazon-threat-intelligence-identifies-russian-cyber-threat-group-targeting-western-critical-infrastructure/)




---

## 5. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Spearphishing Attachment [T1566.001] |
| Initial Access | Supply Chain Compromise [T1195] |
| Initial Access | Drive-by Compromise [T1189] |
| Execution | Command and Scripting Interpreter: PowerShell [T1059.001] |
| Execution | User Execution: Malicious File [T1204.002] |
| Persistence | Scheduled Task/Job [T1053] |
| Persistence | Boot or Logon Autostart Execution [T1547] |
| Defense Evasion | Masquerading [T1036] |
| Defense Evasion | Indicator Removal: Clear Windows Event Logs [T1070.001] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Credential Access | OS Credential Dumping: LSASS Memory [T1003.001] |
| Discovery | Network Service Scanning [T1046] |
| Lateral Movement | Lateral Tool Transfer [T1570] |
| Lateral Movement | Remote Services: SMB/Windows Admin Shares [T1021.002] |
| Collection | Data from Local System [T1005] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Impact | Data Destruction [T1485] |
| Impact | Disk Wipe [T1561] |
| Impact | Inhibit System Recovery [T1490] |
>[Source: MITRE ATT&CK](https://attack.mitre.org/groups/G0034/)
