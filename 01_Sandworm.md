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

---

## 4. MITRE ATT&CK TTPs

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
