# APT Cheat Sheet
Tracking modern cyber threat actors for fun, work, and study.
---

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
| **Source / Link** | US-CERT / Dragos — https://www.cisa.gov/uscert/ncas/alerts/IR-ALERT-H-16-056-01 |

**2.2 "NotPetya" Global Ransomware Attack**

| Field | Details |
|---|---|
| **Date** | 2017-06 |
| **Campaign / Vulnerability Name** | NotPetya |
| **Victims / Targets** | Maersk, Merck, FedEx/TNT, Mondelez, Rosneft; >60 countries; estimated $10B+ in damages |
| **Description** | Disguised as ransomware but functioned as a destructive wiper, NotPetya spread via the M.E.Doc Ukrainian accounting software supply chain and EternalBlue/Mimikatz for lateral movement. Widely considered the most destructive cyberattack on record at that time. |
| **Source / Link** | US DoJ Indictment — https://www.justice.gov/opa/press-release/file/1328521/dl |

**2.3 Winter Olympics Disruption**

| Field | Details |
|---|---|
| **Date** | 2018-02 |
| **Campaign / Vulnerability Name** | Olympic Destroyer |
| **Victims / Targets** | Pyeongchang Winter Olympics IT infrastructure; South Korean government and sports organizations |
| **Description** | Sandworm deployed Olympic Destroyer to disrupt the opening ceremony, disrupting Wi-Fi, TVs, and the official website. The malware used obfuscation to mimic Lazarus Group TTPs as a false flag, complicating attribution. |
| **Source / Link** | Cisco Talos / Kaspersky — https://securelist.com/olympic-destroyer-is-here-to-trick-the-industry/84295/ |

**2.4 Ukraine OT/ICS Disruption**

| Field | Details |
|---|---|
| **Date** | 2023-11 |
| **Campaign / Vulnerability Name** | Industroyer2 / SwiftSlicer / CaddyWiper operations |
| **Victims / Targets** | Ukrainian energy sector organizations |
| **Description** | Sandworm combined a custom OT-targeting tool (Industroyer2) with data wipers to simultaneously destroy data on IT systems while disrupting industrial control systems. Mandiant/Google labeled this campaign as APT44 and described it as Russia's primary cyber sabotage unit. |
| **Source / Link** | Mandiant — https://cloud.google.com/blog/topics/threat-intelligence/apt44-unearthing-sandworm |

**2.5 Global Signal Messenger Targeting**

| Field | Details |
|---|---|
| **Date** | 2025-02 |
| **Campaign / Vulnerability Name** | Signal Messenger Compromise Campaign |
| **Victims / Targets** | Ukrainian military personnel, government officials, journalists using Signal |
| **Description** | Sandworm and other Russia-aligned actors exploited Signal's linked device feature and QR code phishing to silently mirror targets' Signal communications. Part of a broad effort to intercept encrypted communications on the battlefield. |
| **Source / Link** | Google TAG — https://blog.google/threat-analysis-group/government-backed-actors-exploiting-winrar-vulnerability/ |

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
---

# Threat Actor Profile: Dragonfly
>🪰 The threat actor name Dragonfly was coined by Symantec (part of the insect-driven naming convenction).
---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Dragonfly |
| **Aliases** | Energetic Bear, Berserk Bear, IRON LIBERTY, Crouching Yeti, TEMP.Isotope, DYMALLOY, Ghost Blizzard, BROMINE, TG-4192, ALLANITE, Koala Team, Havex |
| **Actor Type** | APT |
| **Suspected Origin** | Russia — FSB Center 16 |
| **Active Since** | 2010 (earliest attributed activity) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Western Energy Sector Campaign**

| Field | Details |
|---|---|
| **Date** | 2013-2014 |
| **Campaign / Vulnerability Name** | Havex / Dragonfly Campaign |
| **Victims / Targets** | Energy companies across US, Spain, France, Italy, Germany, Turkey, Poland; ICS/SCADA vendors |
| **Description** | Dragonfly used spearphishing, watering hole attacks, and trojanized ICS software to target energy sector companies. The Havex RAT was deployed, including via poisoned software updates from legitimate ICS vendors, enabling reconnaissance of OT environments. |
| **Source / Link** | Symantec — https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/dragonfly-western-energy-cyberattacks |

**2.2 US Energy Grid Penetration**

| Field | Details |
|---|---|
| **Date** | 2015-2017 |
| **Campaign / Vulnerability Name** | Dragonfly 2.0 |
| **Victims / Targets** | US electric utilities; UK and Irish energy companies; grid operators in Europe |
| **Description** | The resurgent Dragonfly 2.0 phase used more targeted spearphishing against senior energy executives, watering hole attacks on sector websites, and credential harvesting. The group obtained access to operational systems including HMI screenshots of grid control panels — access that could enable destructive attacks. |
| **Source / Link** | Symantec / US-CERT AA-17-352A — https://www.cisa.gov/news-events/alerts/2018/03/15/russian-government-cyber-activity-targeting-energy-and-other-critical |

**2.3 US State and Local Government Targeting**

| Field | Details |
|---|---|
| **Date** | 2020-09 |
| **Campaign / Vulnerability Name** | AA20-296A (CISA/FBI Advisory) |
| **Victims / Targets** | US state, local, territorial and tribal (SLTT) government networks; US aviation networks; election infrastructure |
| **Description** | A CISA/FBI advisory attributed a broad campaign against SLTT governments and aviation networks to Dragonfly (Berserk Bear). The group exploited vulnerabilities including CVE-2019-19781 (Citrix), CVE-2020-0688 (Exchange), CVE-2020-1472 (Zerologon), and CVE-2018-13379 (Fortinet VPN). |
| **Source / Link** | CISA Advisory AA20-296A — https://www.cisa.gov/news-events/cybersecurity-advisories/aa20-296a |

**2.4 German Critical Infrastructure Supply Chain Attack**

| Field | Details |
|---|---|
| **Date** | 2020 |
| **Campaign / Vulnerability Name** | German Energy Sector Supply Chain Compromise |
| **Victims / Targets** | German energy and water sector companies |
| **Description** | Berserk Bear penetrated German industrial suppliers to access downstream critical infrastructure targets. The group used supplier relationships as a trusted path into energy networks, consistent with its long-running supply chain focus. |
| **Source / Link** | Cyware / BSI (Germany) reporting — https://cyware.com/news/berserk-bear-apt-penetrates-german-infrastructure-via-supply-chain-attacks-f790a4d5 |

---

## 3. Primary Targets

### Industries / Sectors
- Energy (electricity generation and distribution, oil and gas)
- Industrial Control Systems (ICS) / SCADA
- Aviation and transportation
- Government (federal, state, local)
- Defense and aerospace
- Water and utilities

### Notable Victim Organizations
- US electric utilities (multiple unnamed)
- UK and Irish energy grid operators
- German energy and industrial suppliers
- US SLTT government entities (2020)

### Technologies & CVEs Exploited
- CVE-2019-19781 (Citrix ADC/Gateway)
- CVE-2020-0688 (Microsoft Exchange)
- CVE-2020-1472 (Zerologon/Netlogon)
- CVE-2018-13379 (Fortinet FortiOS VPN)
- CVE-2019-10149 (Exim MTA)
- Havex RAT (custom ICS targeting tool)
- Trojanized ICS vendor software

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Spearphishing Attachment [T1566.001] |
| Initial Access | Drive-by Compromise [T1189] |
| Initial Access | Supply Chain Compromise: Compromise Software Supply Chain [T1195.002] |
| Initial Access | Valid Accounts [T1078] |
| Initial Access | Trusted Relationship [T1199] |
| Execution | User Execution [T1204] |
| Persistence | Valid Accounts [T1078] |
| Credential Access | Brute Force [T1110] |
| Credential Access | Input Capture [T1056] |
| Discovery | Network Sniffing [T1040] |
| Discovery | Remote System Discovery [T1018] |
| Collection | Screen Capture [T1113] |
| Collection | Data from Information Repositories [T1213] |
| Defense Evasion | Indicator Removal on Host [T1070] |
| Command and Control | Commonly Used Port [T1043] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
>[Source: MITRE ATT&CK](https://attack.mitre.org/groups/G0035/)
---
# Threat Actor Profile: UAC-0099
>⚠️ LIMITED INTELLIGENCE WARNING 
Naming Authority: CERT-UA (Computer Emergency Response Team of Ukraine).
Origin Timeframe: The group was first formally documented and named by CERT-UA in May 2023 (specifically in Advisory #6710).
Designation Meaning: The "UAC" prefix stands for Ukraine Activity Croup, a convention used by CERT-UA to track malicious cyber activity specifically targeting Ukrainian entities.
---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | UAC-0099 |
| **Aliases** | None publicly documented |
| **Actor Type** | APT |
| **Suspected Origin** | Russia (assessed with moderate confidence; state-nexus probable based on targeting and supporting role in Sandworm operations) |
| **Active Since** | 2022 |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Initial Espionage Campaign Against Ukrainian Media and Government**

| Field | Details |
|---|---|
| **Date** | 2023-06 |
| **Campaign / Vulnerability Name** | LONEPAGE Campaign — CERT-UA#6569 |
| **Victims / Targets** | Ukrainian state organizations, media representatives |
| **Description** | CERT-UA documented UAC-0099's first known major campaign using phishing emails with HTA, RAR, and LNK file attachments to deliver LONEPAGE, a VBS-based malware that beacons to a C2 server for command execution. The group gained unauthorized remote access to dozens of Ukrainian computers and focused on intelligence collection. |
| **Source / Link** | CERT-UA / Deep Instinct — https://www.deepinstinct.com/blog/threat-actor-uac-0099-continues-to-target-ukraine |

**2.2 WinRAR Zero-Day Exploitation**

| Field | Details |
|---|---|
| **Date** | 2023-08 |
| **Campaign / Vulnerability Name** | CVE-2023-38831 Exploitation |
| **Victims / Targets** | Ukrainian corporate employees working remotely for non-Ukrainian companies |
| **Description** | UAC-0099 rapidly exploited CVE-2023-38831 in WinRAR just three days after the patch was released, using court summons-themed lures to deliver LONEPAGE. The group impersonated the Lviv city court, demonstrating familiarity with Ukrainian administrative structures and awareness of the vulnerability before public disclosure. |
| **Source / Link** | Deep Instinct — https://www.deepinstinct.com/blog/threat-actor-uac-0099-continues-to-target-ukraine |

**2.3 Expanded Government and Defense Targeting**

| Field | Details |
|---|---|
| **Date** | 2024-12 / 2025-08 |
| **Campaign / Vulnerability Name** | MATCHBOIL/MATCHWOK/DRAGSTARE Campaign — CERT-UA#12463 |
| **Victims / Targets** | Ukrainian state bodies (forestry, forensic, manufacturing), defense forces, defense-industrial complex |
| **Description** | UAC-0099 transitioned to a new C# toolset (MATCHBOIL loader, MATCHWOK backdoor, DRAGSTARE stealer). ESET confirmed the group acts as an initial access broker for Sandworm, breaching networks and handing off validated targets for destructive follow-on operations including data wipers. |
| **Source / Link** | CERT-UA / ESET / Security Affairs — https://securityaffairs.com/180896/apt/cert-ua-warns-of-uac-0099-phishing-attacks-targeting-ukraines-defense-sector.html |

---

## 3. Primary Targets

### Industries / Sectors
- Government (Ukrainian state bodies)
- Defense and defense-industrial complex
- Media and journalism
- Forestry and agriculture (2025)
- Forensic and manufacturing institutions

### Notable Victim Organizations
- Multiple Ukrainian state agencies (unnamed)
- Ukrainian defense enterprises
- Ukrainian media organizations

### Technologies & CVEs Exploited
- CVE-2023-38831 (WinRAR archive processing)
- Cloudflare services (C2 infrastructure hosting)
- UKR.NET email service (phishing delivery)

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Spearphishing Attachment [T1566.001] |
| Initial Access | Spearphishing Link [T1566.002] |
| Execution | Command and Scripting Interpreter: PowerShell [T1059.001] |
| Execution | Command and Scripting Interpreter: Visual Basic [T1059.005] |
| Execution | User Execution: Malicious File [T1204.002] |
| Persistence | Scheduled Task/Job: Scheduled Task [T1053.005] |
| Persistence | Boot or Logon Autostart Execution: Registry Run Keys [T1547.001] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Deobfuscate/Decode Files or Information [T1140] |
| Defense Evasion | Abuse Elevation Control Mechanism [T1548] |
| Credential Access | Credentials from Web Browsers [T1555.003] |
| Collection | Data Staged [T1074] |
| Collection | Screen Capture [T1113] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Command and Control | Ingress Tool Transfer [T1105] |
>[Source: CERT-UA advisories](https://medium.com/h7w/analyzing-uac-0099-tactics-techniques-and-procedures-2023-2025-296f6ad672fc)
---
# Threat Actor Profile: PHALT#BLYX
>⚠️ LIMITED INTELLIGENCE WARNING  
PHALT#BLYX is a campaign-level designation assigned by Securonix in January 2026, not a named persistent threat actor group. The name comes directly from technical artifacts found within the malicious code during the infection process, specifically within an MSBuild project file. Attribution to a specific Russian-aligned threat group is assessed with low confidence.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | PHALT#BLYX |
| **Aliases** | None publicly documented; linked to UAC-0200 cluster patterns |
| **Actor Type** | APT (assessed; Russian-speaking threat actor with state-nexus indicators) |
| **Suspected Origin** | Russia / Russian-speaking threat actors (assessed with low-moderate confidence based on DCRat provenance and Russian debug strings) |
| **Active Since** | 2025 (campaign active as of January 2026 reporting) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 European Hospitality Sector Campaign**

| Field | Details |
|---|---|
| **Date** | 2025-2026 |
| **Campaign / Vulnerability Name** | PHALT#BLYX |
| **Victims / Targets** | European hospitality organizations (hotels, booking platforms); estimated 7,099+ unique victim IPs contacted C2 infrastructure |
| **Description** | Attackers sent phishing emails impersonating Booking.com reservation cancellations to hospitality staff. The chain directed victims to a high-fidelity Booking.com clone (low-house[.]com) presenting a fake CAPTCHA and then a fake Windows BSOD screen — a ClickFix lure that tricked users into running PowerShell commands. The PowerShell downloaded a malicious MSBuild .proj file, which compiled and executed a customized DCRat payload injected into aspnet_compiler.exe. Windows Defender exclusions were added for persistence. |
| **Source / Link** | Securonix Threat Research — https://www.securonix.com/blog/analyzing-phaltblyx-how-fake-bsods-and-trusted-build-tools-are-used-to-construct-a-malware-infection/ |

---

## 3. Primary Targets

### Industries / Sectors
- Hospitality (hotels, booking platforms)
- Tourism and travel (assessed expansion likely)

### Notable Victim Organizations
- European hospitality organizations (unnamed)
- Targets identified primarily via Euro-denominated lures, indicating European focus

### Technologies & CVEs Exploited
- No CVEs exploited; attack is entirely social engineering and Living-off-the-Land (LotL) based
- MSBuild.exe (trusted Windows build tool abused for payload execution)
- aspnet_compiler.exe (process injection target)
- DCRat (AsyncRAT variant; Russia-linked commodity RAT)

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Spearphishing Link [T1566.002] |
| Execution | Command and Scripting Interpreter: PowerShell [T1059.001] |
| Execution | Trusted Developer Utilities Proxy Execution: MSBuild [T1127.001] |
| Execution | User Execution: Malicious Link [T1204.001] |
| Defense Evasion | Trusted Developer Utilities Proxy Execution [T1127] |
| Defense Evasion | Process Injection [T1055] |
| Defense Evasion | Impair Defenses: Disable or Modify Tools [T1562.001] |
| Defense Evasion | Masquerading [T1036] |
| Persistence | Boot or Logon Autostart Execution: Startup Folder [T1547.001] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Command and Control | Ingress Tool Transfer [T1105] |
>[Source:Securonix Threat Research](https://www.securonix.com/blog/analyzing-phaltblyx-how-fake-bsods-and-trusted-build-tools-are-used-to-construct-a-malware-infection/)
---
# Threat Actor Profile: Salt Typhoon
>🌀 Microsoft naming conventions generally use weather-related terms.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Salt Typhoon |
| **Aliases** | FamousSparrow, GhostEmperor, Earth Estries, UNC2286, OPERATOR PANDA, RedMike, UNC5807 |
| **Actor Type** | APT |
| **Suspected Origin** | China — Ministry of State Security (MSS); Sichuan Juxinhe Network Technology sanctioned by US Treasury in January 2025 |
| **Active Since** | 2021 (earliest attributed activity; likely earlier) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 US Telecommunications Compromise**

| Field | Details |
|---|---|
| **Date** | 2023-2024 |
| **Campaign / Vulnerability Name** | US Telecom Espionage Campaign |
| **Victims / Targets** | AT&T, Verizon, T-Mobile, Lumen, Consolidated Communications, Windstream, Spectrum; nine US telecoms total; CALEA wiretap systems |
| **Description** | Salt Typhoon infiltrated core routing infrastructure across major US broadband providers, accessing subscriber metadata (call records, timestamps, IP addresses) for over one million users in the Washington DC metro area. Critically, the group accessed CALEA lawful intercept systems, enabling surveillance of law enforcement wiretap targets. Audio recordings of Trump and Harris campaign staff were obtained. The intrusion was estimated to have been underway for one to two years prior to discovery. |
| **Source / Link** | CISA Advisory AA25-239A — https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-239a |

**2.2 US Army National Guard Compromise**

| Field | Details |
|---|---|
| **Date** | 2024 |
| **Campaign / Vulnerability Name** | US Military Network Compromise |
| **Victims / Targets** | A US state's Army National Guard |
| **Description** | Salt Typhoon gained entry through a weakly configured remote access service and spread across the environment, obtaining administrator credentials, network diagrams, and traffic logs describing Guard system interconnections across states. |
| **Source / Link** | NJCCIC Salt Typhoon Profile — https://www.cyber.nj.gov/threat-landscape/nation-state-threat-analysis-reports/china-linked-cyber-operations-targeting-us-critical-infrastructure/salt-typhoon | TECHCRUNCH — https://techcrunch.com/2024/12/04/senators-say-u-s-military-is-failing-to-secure-its-phones-from-foreign-spies/ |

**2.3 Canadian Telecom Breach**

| Field | Details |
|---|---|
| **Date** | 2025-02 |
| **Campaign / Vulnerability Name** | Canadian Telecom Espionage |
| **Victims / Targets** | Unnamed Canadian telecommunications company |
| **Description** | Salt Typhoon extended its telecom espionage campaign to Canada, consistent with a confirmed pattern of targeting Five Eyes allies. Australian ASIO director-general separately confirmed Salt Typhoon probed Australian telecommunications networks in November 2025. |
| **Source / Link** | CBC News / Australian ASIO statements — https://en.wikipedia.org/wiki/Salt_Typhoon |

**2.4 Viasat Compromise**

| Field | Details |
|---|---|
| **Date** | 2025-06 |
| **Campaign / Vulnerability Name** | Satellite Communications Targeting |
| **Victims / Targets** | Viasat (US satellite communications company) |
| **Description** | Salt Typhoon was attributed to the compromise of Viasat, a US satellite internet provider. Satellite communications represent a strategic expansion of Salt Typhoon's targeting from terrestrial telecoms. |
| **Source / Link** | Industry reporting cited in Wikipedia — https://en.wikipedia.org/wiki/Salt_Typhoon |

---

## 3. Primary Targets

### Industries / Sectors
- Telecommunications (primary focus)
- Government and defense
- Satellite communications
- Hotels and lodging (historical)
- Law enforcement and intelligence infrastructure (CALEA systems)

### Notable Victim Organizations
- AT&T, Verizon, T-Mobile, Lumen Technologies, Windstream, Consolidated Communications, Spectrum
- Viasat
- Unnamed Canadian and Australian telecoms

### Technologies & CVEs Exploited
- CVE-2023-20198 (Cisco IOS XE authentication bypass)
- CVE-2023-20273 (Cisco IOS XE command injection — post-auth)
- CVE-2023-46805 (Ivanti Connect Secure authentication bypass)
- CVE-2024-21887 (Ivanti Connect Secure command injection)
- CVE-2024-3400 (Palo Alto PAN-OS GlobalProtect RCE)
- CVE-2021-26855 (Microsoft Exchange ProxyLogon)
- CVE-2018-0171 (Cisco Smart Install)
- SNMP community string cracking from exfiltrated config files
- Custom tools: GhostSpider backdoor, JumbledPath, SnappyBee, Masol RAT, Demodex rootkit

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Exploit Public-Facing Application [T1190] |
| Initial Access | Valid Accounts: Local Accounts [T1078.003] |
| Execution | Command and Scripting Interpreter: PowerShell [T1059.001] |
| Persistence | Server Software Component: Web Shell [T1505.003] |
| Persistence | Scheduled Task/Job [T1053] |
| Defense Evasion | Indicator Removal: Clear Linux or Mac System Logs [T1070.002] |
| Defense Evasion | Masquerading [T1036] |
| Credential Access | Brute Force: Password Cracking [T1110.002] |
| Discovery | Gather Victim Network Information: Network Topology [T1590.004] |
| Discovery | Network Service Discovery [T1046] |
| Lateral Movement | Remote Services [T1021] |
| Collection | Data from Configuration Repository: Network Device Configuration Dump [T1602.002] |
| Exfiltration | Exfiltration Over Alternative Protocol [T1048] |
| Command and Control | Protocol Tunneling [T1572] |
>[Source: MITRE ATT&CK](https://attack.mitre.org/groups/G1020)
---
