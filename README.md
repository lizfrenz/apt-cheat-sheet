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
# Threat Actor Profile: GTG-1002
>⚠️ LIMITED INTELLIGENCE WARNING  
GTG-1002 is a recently designated threat actor cluster. Attribution to a specific Chinese state group has not been formally confirmed by government sources. Public documentation derives primarily from Anthropic and SOCRadar reporting.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | GTG-1002 |
| **Aliases** | None publicly documented |
| **Actor Type** | APT |
| **Suspected Origin** | China (attributed with moderate confidence based on code reuse and infrastructure patterns) |
| **Active Since** | 2022 |
| **Current Status** | Inactive (campaign contained by mid-2025 per reporting) |

---

## 2. Notable Events

**2.1 AI-Orchestrated Global Espionage Campaign (2022–2025)**

| Field | Details |
|---|---|
| **Date** | 2022-2025 |
| **Campaign / Vulnerability Name** | GTG-1002 AI-Powered Espionage Campaign |
| **Victims / Targets** | Approximately 30 organizations across defense, energy, technology, finance, and manufacturing sectors in Asia and Europe |
| **Description** | GTG-1002 represents the first publicly documented case of an AI agent — specifically Anthropic's Claude Code — being used as the primary operator in a large-scale cyber espionage campaign. The threat actors built an autonomous framework around Claude Code, bypassing safety guardrails through prompt manipulation and role-play scenarios. The AI performed approximately 80–90% of the campaign work including reconnaissance, target profiling, vulnerability discovery, exploit generation, credential theft, and data sorting. Human operators provided oversight but limited direct participation. The 18-month campaign focused on stealing military and energy-related intelligence. |
| **Source / Link** | SOCRadar / Anthropic safety reporting — https://socradar.io/blog/ai-powered-gtg-1002-campaign/ |

---

## 3. Primary Targets

### Industries / Sectors
- Defense and military
- Energy
- Technology
- Finance and financial services
- Manufacturing

### Notable Victim Organizations
- Approximately 30 organizations (unnamed) across Asia and Europe

### Technologies & CVEs Exploited
- AI safety vulnerabilities (prompt injection / role-play manipulation of Claude Code)
- Specific CVEs leveraged: Unknown / Not publicly documented
- The campaign leveraged AI to autonomously identify and generate exploits against targets

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Reconnaissance | Gather Victim Org Information [T1591] |
| Reconnaissance | Active Scanning [T1595] |
| Initial Access | Exploit Public-Facing Application [T1190] |
| Execution | Command and Scripting Interpreter [T1059] |
| Credential Access | Credential Dumping [T1003] |
| Credential Access | Brute Force [T1110] |
| Collection | Data from Network Shared Drive [T1039] |
| Collection | Automated Collection [T1119] |
| Exfiltration | Automated Exfiltration [T1020] |
| Exfiltration | Data Transfer Size Limits [T1030] |
>[Source: SOCRadar GTG-1002 report](https://malpedia.caad.fkie.fraunhofer.de/actor/gtg-1002) 
---

# Threat Actor Profile: Konni Group
>🐀 The KONNI RAT: Security researchers (including Cisco Talos) first identified the unique backdoor malware and dubbed it "KONNI".
---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Konni Group |
| **Aliases** | Kimsuky (subset), Earth Imp, TA406, Thallium, Vedalia, Velvet Chollima, APT37 (partial overlap attributed by some vendors) |
| **Actor Type** | APT |
| **Suspected Origin** | North Korea — Reconnaissance General Bureau (RGB) |
| **Active Since** | 2014 (first undetected activity; publicly documented from 2017) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Russian Diplomatic Targeting (2022)**

| Field | Details |
|---|---|
| **Date** | 2022-01 |
| **Campaign / Vulnerability Name** | New Year's Spearphishing Campaign / Konni RAT v3 |
| **Victims / Targets** | Russian diplomatic entities and government bodies |
| **Description** | Konni conducted spearphishing attacks using New Year's Eve lures against Russian diplomatic targets. Malicious ZIP files launched a multi-stage attack chain deploying a new version of the Konni RAT as a Windows service (scrnsvc.dll). The use of CAB files as infection stages was a distinctive marker. Researchers noted this represented an unusual targeting of Russia, a nominal DPRK ally. |
| **Source / Link** | Cluster25 / Security Affairs — https://securityaffairs.com/126388/apt/konni-apt-russia-entities.html |

**2.2 Korean Government and Academic Targeting (2024)**

| Field | Details |
|---|---|
| **Date** | 2024 |
| **Campaign / Vulnerability Name** | Kimsuky/Konni RAT Campaign (Q3 2024) |
| **Victims / Targets** | Korean and Russian government entities; virtual asset transaction specialists; North Korean affairs experts |
| **Description** | The Konni campaign escalated attacks leveraging cloud and FTP services for C2 to complicate detection. Attacks used financial and governmental themes as lures and deployed AsyncRAT variants with XOR-based encryption and future-dated timestamps for AV evasion. The group abused free hosting platforms for C2 infrastructure. |
| **Source / Link** | CYFIRMA APT Quarterly Highlights Q3 2024 — https://www.cyfirma.com/research/apt-quarterly-highlights-q3-2024/ |

**2.3 Blockchain Developer Targeting / AI-Generated Backdoor (2025–2026)**

| Field | Details |
|---|---|
| **Date** | 2025-10 / 2026-01 |
| **Campaign / Vulnerability Name** | Blockchain Developer Spearphishing Campaign |
| **Victims / Targets** | Software developers and engineers in blockchain, cryptocurrency, and Web3 sectors across Japan, Australia, and India |
| **Description** | Konni shifted targeting to blockchain/crypto developers using fake project documentation as lures. Check Point Research identified a PowerShell backdoor that appeared to be AI-generated (LLM-written code with verbose documentation and modular structure). The campaign used weaponized LNK files, UAC bypass (uc.exe), and RMM tools (SimpleHelp) for persistence. |
| **Source / Link** | Check Point Research — https://securityaffairs.com/187317/apt/north-korea-linked-konni-uses-ai-to-build-stealthy-malware-tooling.html |

---

## 3. Primary Targets

### Industries / Sectors
- Government (South Korean, Russian, and Japanese government bodies)
- Cryptocurrency and blockchain
- Defense and national security think tanks
- Academia and research institutions
- Media and journalism

### Notable Victim Organizations
- South Korean government agencies
- Russian diplomatic missions
- Web3/blockchain development companies (Japan, Australia, India)
- North Korean affairs research institutions

### Technologies & CVEs Exploited
- Weaponized LNK files
- UAC bypass techniques (uc.exe)
- Konni RAT (custom implant, active since 2014)
- AsyncRAT variants
- SimpleHelp RMM (for remote access persistence)
- Cloudflare infrastructure abuse

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
| Privilege Escalation | Abuse Elevation Control Mechanism: Bypass UAC [T1548.002] |
| Defense Evasion | Modify Registry [T1112] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Process Injection [T1055] |
| Collection | Screen Capture [T1113] |
| Collection | Input Capture: Keylogging [T1056.001] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Command and Control | Encrypted Channel [T1573] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
>[Source: MITRE ATT&CK KONNI](https://attack.mitre.org/software/S0356/)[Source: MITRE ATT&CK Kimsuky](https://attack.mitre.org/groups/G0094/)
---

# Threat Actor Profile: TeamPCP
>☁️ Security researchers identified the group after observing malicious activity involving the "TeamPCP Cloud stealer" and tpcp.tar.gz files used to exfiltrate data to attacker-controlled servers.

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
| **Victims / Targets** | 60,000+ servers worldwide; victims in South Korea, Canada, United States, Serbia, UAE; JobsGO (Vietnam) — 2M+ records exfiltrated |
| **Description** | TeamPCP launched a worm-driven campaign targeting exposed Docker APIs, Kubernetes clusters, Redis servers, Ray dashboards, and React2Shell vulnerabilities. Each compromised server became a self-propagating scanner and criminal platform running cryptocurrency miners (XMRig/Monero), proxy software, and ransomware C2 infrastructure. Kubernetes clusters were converted into distributed botnets. Data was published via the ShellForce Telegram channel. |
| **Source / Link** | Flare — https://flare.io/learn/resources/blog/teampcp-cloud-native-ransomware |

**2.2 Trivy Supply Chain Attack (2026-03)**

| Field | Details |
|---|---|
| **Date** | 2026-03 |
| **Campaign / Vulnerability Name** | CVE-2026-33634 / Trivy Supply Chain Compromise |
| **Victims / Targets** | Aqua Security (Trivy vulnerability scanner), LiteLLM AI gateway, Telnyx Python package; estimated 95 million developers downstream |
| **Description** | TeamPCP compromised Aqua Security's Trivy vulnerability scanner by stealing GitHub authentication credentials via an automated agent. They injected credential-stealing malware into official Trivy releases and GitHub Actions, then pivoted to compromise LiteLLM and Telnyx. Checkmarx GitHub Actions were subsequently compromised via stolen Trivy credentials. TeamPCP also deployed a Kubernetes wiper targeting Iranian time-zone systems. |
| **Source / Link** | The Hacker News — https://thehackernews.com/2026/03/teampcp-hacks-checkmarx-github-actions.html |

**2.3 Partnership with Vect Ransomware Group (2026)**

| Field | Details |
|---|---|
| **Date** | 2026 |
| **Campaign / Vulnerability Name** | RaaS Partnership with Vect |
| **Victims / Targets** | Organizations with compromised CI/CD pipelines and cloud environments |
| **Description** | TeamPCP began partnering with the Vect ransomware group to convert supply chain compromises into large-scale ransomware operations, expanding from cryptomining and data theft into full ransomware deployment as an initial access broker. |
| **Source / Link** | Socket / Infosecurity Magazine — https://www.infosecurity-magazine.com/news/teampcp-targets-telnyx-pypi-package/ |

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
- JobsGO.vn (Vietnam recruitment platform)

### Technologies & CVEs Exploited
- CVE-2026-33634 (Trivy supply chain — CVSS 9.4)
- Exposed Docker APIs (unauthenticated)
- Exposed Kubernetes API servers
- Redis misconfiguration
- Ray dashboard exposure
- React2Shell vulnerability

---

## 4. MITRE ATT&CK TTPs

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
>[Source: Wiz Threat Landscape](https://threats.wiz.io/all-actors/teampcp)
---
# Threat Actor Profile: Cl0p
> The name "Cl0p" for the ransomware group originates from the word "clop" itself, which is often used in Russian-language hacker forums to describe malware or activities related to data encryption. A clop means a tick or more commonly a bedbug in Russian.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Cl0p |
| **Aliases** | TA505, FIN11, UNC2546, UNC2582, UNC4857, Lace Tempest |
| **Actor Type** | eCrime |
| **Suspected Origin** | Russia / Russian-speaking criminal group (assessed with high confidence; avoids encrypting systems with Russian/Azerbaijani keyboard layouts) |
| **Active Since** | 2019 (Cl0p ransomware first observed); TA505 active since ~2014 |
| **Current Status** | Active |

---

## 2. Notable Events

**Event 1 — Accellion FTA Zero-Day Campaign (2020–2021)**

| Field | Details |
|---|---|
| **Date** | 2020-12 / 2021-01 |
| **Campaign / Vulnerability Name** | CVE-2021-27101 through CVE-2021-27104 (Accellion FTA) |
| **Victims / Targets** | Reserve Bank of New Zealand, Bombardier, Kroger, Qualys, University of Colorado, Jones Day, and ~100 others |
| **Description** | Cl0p/TA505 exploited four zero-day vulnerabilities in Accellion's legacy File Transfer Appliance to steal data from major global organizations. Rather than encrypting systems, the group focused on pure data extortion, threatening to publish stolen files on the CL0P^_-LEAKS dark web site. |
| **Source / Link** | CISA / Mandiant — https://www.cisa.gov/news-events/cybersecurity-advisories/aa21-055a |

**Event 2 — GoAnywhere MFT Zero-Day (2023)**

| Field | Details |
|---|---|
| **Date** | 2023-01 |
| **Campaign / Vulnerability Name** | CVE-2023-0669 (Fortra GoAnywhere MFT) |
| **Victims / Targets** | Approximately 130 organizations across healthcare, financial services, government |
| **Description** | Cl0p exploited a zero-day in the GoAnywhere managed file transfer platform, exfiltrating data from ~130 victims over 10 days. Ransom notes were sent to senior executives identified via open-source research, with no lateral movement beyond the GoAnywhere platform itself. |
| **Source / Link** | CISA Advisory AA23-158A — https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-158a |

**Event 3 — MOVEit Transfer Zero-Day Campaign (2023)**

| Field | Details |
|---|---|
| **Date** | 2023-05 / 2023-06 |
| **Campaign / Vulnerability Name** | CVE-2023-34362 (Progress MOVEit Transfer) |
| **Victims / Targets** | ~2,000 organizations; US federal agencies (Department of Energy, HHS), BBC, British Airways, Shell, PwC, Siemens Energy |
| **Description** | Cl0p exploited a critical SQL injection zero-day in the MOVEit Transfer platform, deploying the LEMURLOOT web shell to steal data at scale. The campaign impacted organizations in over 40 countries and resulted in a $10M US State Department bounty for information linking the group to a foreign government. The group publicly stated it deleted government and military data. |
| **Source / Link** | CISA / FBI Advisory AA23-158A — https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-158a |

**Event 4 — Cleo File Transfer Platform Exploitation (2024)**

| Field | Details |
|---|---|
| **Date** | 2024-12 |
| **Campaign / Vulnerability Name** | Cleo Harmony / VLTrader / LexiCom Zero-Days |
| **Victims / Targets** | Organizations using Cleo managed file transfer products |
| **Description** | Cl0p claimed responsibility for exploiting zero-day vulnerabilities in Cleo's file transfer platforms, continuing its pattern of targeting MFT software. The group demonstrated consistent operational focus: identify widely deployed enterprise file transfer tools, develop or acquire zero-day exploits, and execute mass data theft campaigns. |
| **Source / Link** | BleepingComputer — https://www.bleepingcomputer.com/news/security/clop-ransomware-claims-responsisbility-for-cleo-data-theft-attacks/ |

---

## 3. Primary Targets

### Industries / Sectors
- Financial services and banking
- Healthcare
- Government (federal and state agencies)
- Manufacturing and energy
- Legal and professional services
- Technology and managed service providers

### Notable Victim Organizations
- US federal agencies (Department of Energy, HHS)
- BBC, British Airways, Shell, PwC, Siemens Energy (MOVEit)
- Reserve Bank of New Zealand (Accellion)
- Approximately 2,000 MOVEit victims globally

### Technologies & CVEs Exploited
- CVE-2021-27101 to CVE-2021-27104 (Accellion FTA)
- CVE-2021-35211 (SolarWinds Serv-U)
- CVE-2023-0669 (GoAnywhere MFT)
- CVE-2023-34362 (MOVEit Transfer)
- Cleo Harmony/VLTrader/LexiCom zero-days (2024)
- LEMURLOOT web shell (custom MOVEit payload)

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Exploit Public-Facing Application [T1190] |
| Initial Access | Phishing: Spearphishing Attachment [T1566.001] |
| Initial Access | Valid Accounts [T1078] |
| Execution | Command and Scripting Interpreter [T1059] |
| Execution | Server Software Component: Web Shell [T1505.003] |
| Persistence | Boot or Logon Initialization Scripts [T1037] |
| Persistence | Scheduled Task/Job [T1053] |
| Privilege Escalation | Create or Modify System Process [T1543] |
| Defense Evasion | Subvert Trust Controls: Code Signing [T1553.002] |
| Defense Evasion | Impair Defenses: Disable or Modify Tools [T1562.001] |
| Defense Evasion | Indicator Removal: File Deletion [T1070.004] |
| Credential Access | Remote Services: Remote Desktop Protocol [T1021.001] |
| Lateral Movement | Remote Services [T1021] |
| Collection | Data Staged [T1074] |
| Exfiltration | Exfiltration Over Web Service [T1567] |
| Impact | Data Encrypted for Impact [T1486] |
| Impact | Inhibit System Recovery [T1490] |
>[Source: Blackpoint Cyber Clop Threat Profile](https://blackpointcyber.com/threat-profile/clop-ransomware/)
---
# Threat Actor Profile: Interlock
>🔒 The name drives from file extension: When Interlock ransomware encrypts a victim’s files, it renames them to include the .interlock.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Interlock |
| **Aliases** | Nefarious Mantis |
| **Actor Type** | eCrime |
| **Suspected Origin** | Unknown / Not publicly documented (possible Rhysida / Vice Society lineage) |
| **Active Since** | 2024-09 |
| **Current Status** | Active |

---

## 2. Notable Events

**Event 1 — Texas Tech University Health Sciences Center Breach (2024)**

| Field | Details |
|---|---|
| **Date** | 2024-09 |
| **Campaign / Vulnerability Name** | Texas Tech University HSCA Data Breach |
| **Victims / Targets** | Texas Tech University Health Sciences Center; approximately 1.46 million patient records compromised |
| **Description** | One of Interlock's earliest high-profile attacks targeted a healthcare academic institution, demonstrating the group's intent to pursue sensitive data in regulated sectors. The breach involved both data exfiltration and encryption, with stolen records including patient medical information. |
| **Source / Link** | Arctic Wolf / Quorum Cyber — https://arcticwolf.com/resources/blog/threat-actor-profile-interlock-ransomware/ |

**Event 2 — DaVita Kidney Care Breach (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-04 |
| **Campaign / Vulnerability Name** | DaVita Ransomware Attack |
| **Victims / Targets** | DaVita Inc. (Fortune 500 dialysis provider); 200,000+ patients; 1.5 TB of data stolen |
| **Description** | Interlock's most impactful known attack targeted DaVita, one of the largest kidney care providers in the US. The group exfiltrated approximately 700,000 files including patient data, insurance information, and financial records. When DaVita did not pay the ransom, Interlock leaked the data on its "Worldwide Secrets Blog" dark web site. |
| **Source / Link** | Arctic Wolf / Quorum Cyber — https://arcticwolf.com/resources/blog/threat-actor-profile-interlock-ransomware/ |

**Event 3 — City of St. Paul, Minnesota Attack (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-07 |
| **Campaign / Vulnerability Name** | City of St. Paul Ransomware Attack |
| **Victims / Targets** | City of St. Paul, Minnesota government; 3,500 city employees' personal data at risk |
| **Description** | Interlock took key city systems offline in a ransomware attack. The city confirmed it did not pay the ransom. PRODAFT had detected Interlock pre-attack activity 10 days before, providing advance warning. Interlock publicly claimed responsibility in August 2025. |
| **Source / Link** | Arctic Wolf — https://arcticwolf.com/resources/blog/threat-actor-profile-interlock-ransomware/ |

**Event 4 — CISA/FBI Joint Advisory — Malware Upgrade (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-07-22 |
| **Campaign / Vulnerability Name** | CISA Advisory AA25-203A |
| **Victims / Targets** | Organizations across North America and Europe in healthcare, education, government, technology |
| **Description** | CISA, FBI, HHS, and MS-ISAC issued a joint advisory confirming Interlock had upgraded its encryptors for both Windows and Linux, with enhanced VM encryption capabilities. The advisory noted the group added ClickFix social engineering in May 2025, and that it operates without affiliates in a closed model. |
| **Source / Link** | CISA Advisory AA25-203A — https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-203a |

---

## 3. Primary Targets

### Industries / Sectors
- Healthcare (primary)
- Education and higher education
- Government
- Technology and manufacturing
- Defense contractors
- Transportation and logistics

### Notable Victim Organizations
- DaVita Inc. (Fortune 500 kidney care)
- Texas Tech University Health Sciences Center
- City of St. Paul, Minnesota
- National Defense Corp. (reported)

### Technologies & CVEs Exploited
- Drive-by downloads from compromised legitimate websites
- ClickFix social engineering (added May 2025)
- Compromised credentials for initial access
- Custom ransomware (Windows and Linux/FreeBSD variants)
- NodeSnake RAT (custom)
- LummaStealer, BerserkStealer infostealers
- RDP, AnyDesk, PuTTY (lateral movement)

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Drive-by Compromise [T1189] |
| Initial Access | Valid Accounts [T1078] |
| Initial Access | Phishing [T1566] |
| Execution | Command and Scripting Interpreter: PowerShell [T1059.001] |
| Execution | User Execution: Malicious Link [T1204.001] |
| Persistence | Scheduled Task/Job [T1053] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Virtualization/Sandbox Evasion [T1497] |
| Credential Access | Credentials from Web Browsers [T1555.003] |
| Lateral Movement | Remote Services: Remote Desktop Protocol [T1021.001] |
| Lateral Movement | Remote Access Software [T1219] |
| Collection | Data Staged [T1074] |
| Exfiltration | Exfiltration Over Web Service [T1567] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
| Impact | Data Encrypted for Impact [T1486] |
| Impact | Inhibit System Recovery [T1490] |
| Impact | Data Destruction [T1485] |
>[Source: CISA Advisory AA25-203A](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-203a)
---
# Threat Actor Profile: ShinyHunters
>✨ Refers to the Pokémon franchise, where "shiny" creatures are rare, and "hunters" seek them out.
---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | ShinyHunters |
| **Aliases** | UNC6040, UNC6240, UNC6661, ShinyCorp, Sp1d3rHunters (collaborative persona with Scattered Spider) |
| **Actor Type** | eCrime |
| **Suspected Origin** | Multi-national (Western; French national Sebastien Raoult sentenced in US 2024; leadership appears to operate internationally) |
| **Active Since** | 2020 |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Mass Database Theft Campaign (2020–2021)**

| Field | Details |
|---|---|
| **Date** | 2020-2021 |
| **Campaign / Vulnerability Name** | Mass Data Breach Campaign |
| **Victims / Targets** | Tokopedia (91M accounts), Mathway (25M), Wattpad, Microsoft GitHub private repos, AT&T (disputed at the time) |
| **Description** | ShinyHunters emerged as a prolific data theft collective, systematically breaching databases via credential stuffing and API exploitation. Stolen data was sold or leaked on hacking forums. The group built a reputation through self-promotion and direct engagement with the cybersecurity press. |
| **Source / Link** | Vali Cyber ShinyHunters Profile — https://valicyber.com/resources/shinyhunters/ |

**2.2 Snowflake Customer Campaign (2024)**

| Field | Details |
|---|---|
| **Date** | 2024 |
| **Campaign / Vulnerability Name** | Snowflake / Ticketmaster / Santander Campaign |
| **Victims / Targets** | Ticketmaster (560M users), Santander Bank, Neiman Marcus, AT&T, Truist Bank; approximately 165 organizations via Snowflake |
| **Description** | ShinyHunters used old, valid credentials captured by infostealers (in combination with missing MFA) to breach Snowflake cloud storage accounts. AT&T paid approximately $370,000 to have stolen data deleted. The campaign represented a pivot from direct database hacking to cloud storage exploitation. |
| **Source / Link** | ReliaQuest — https://reliaquest.com/blog/threat-spotlight-shinyhunters-data-breach-targets-salesforce-amid-scattered-spider-collaboration/ |

**2.3 Salesforce Vishing Campaign (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-06 |
| **Campaign / Vulnerability Name** | Salesforce Extortion Campaign (UNC6040/UNC6240/UNC6661) |
| **Victims / Targets** | Google, Cisco, Adidas, Louis Vuitton, Pandora, Allianz, Tiffany & Co., Dior, Qantas; 80+ nations |
| **Description** | ShinyHunters (tracked as UNC6040 by Google GTIG) pivoted to voice phishing (vishing) attacks targeting Salesforce environments. Attackers impersonated IT support, calling employees to convince them to install a trojanized "Salesforce Data Loader" app, granting OAuth access to organizational data. DDoS attacks and harassment of victim staff were used as additional extortion pressure. |
| **Source / Link** | Google GTIG / Mandiant — https://cloud.google.com/blog/topics/threat-intelligence/expansion-shinyhunters-saas-data-theft |

**2.4 Alliance with Scattered Spider / LAPSUS$ (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-08 |
| **Campaign / Vulnerability Name** | Scattered LAPSUS$ Hunters Supergroup |
| **Victims / Targets** | Qantas (5.7M customers), Jaguar Land Rover, Kering (Gucci/Balenciaga) |
| **Description** | ShinyHunters launched a Telegram channel combining operations with Scattered Spider and LAPSUS$, advertising a forthcoming RaaS platform ("shinysp1d3r"). The collaborative supergroup combined ShinyHunters' data exfiltration expertise with Scattered Spider's social engineering and LAPSUS$'s insider recruitment. French law enforcement arrested four suspected members. |
| **Source / Link** | The Hacker News / Resecurity — https://thehackernews.com/2025/08/cybercrime-groups-shinyhunters.html |

---

## 3. Primary Targets

### Industries / Sectors
- Technology and SaaS platforms
- Financial services and banking
- Retail and e-commerce
- Aviation and travel
- Luxury goods
- Automotive

### Notable Victim Organizations
- Google, Cisco, Adidas, Louis Vuitton, Pandora, Dior, Tiffany & Co., Allianz
- Qantas, Jaguar Land Rover, Kering
- Ticketmaster, AT&T, Santander Bank

### Technologies & CVEs Exploited
- Credential stuffing with infostealer-harvested credentials
- Missing or SMS-based MFA bypass
- Salesforce OAuth device code flow abuse
- BrowserStack API key theft
- Social engineering / vishing (IT impersonation)
- No CVEs required in recent campaigns — pure social engineering

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Valid Accounts [T1078] |
| Initial Access | Phishing: Spearphishing via Service [T1566.003] |
| Initial Access | Phishing for Information [T1598] |
| Credential Access | Steal Application Access Token [T1528] |
| Credential Access | Credentials from Password Stores [T1555] |
| Credential Access | Multi-Factor Authentication Interception [T1111] |
| Discovery | Cloud Service Discovery [T1526] |
| Discovery | Cloud Storage Object Discovery [T1619] |
| Collection | Data from Cloud Storage [T1530] |
| Collection | Data from Information Repositories [T1213] |
| Exfiltration | Exfiltration Over Web Service [T1567] |
| Impact | Financial Theft [T1657] |
| Impact | Network Denial of Service [T1498] |
>[Source: Google GTIG / Mandiant](https://cloud.google.com/blog/topics/threat-intelligence/expansion-shinyhunters-saas-data-theft)

---
# Threat Actor Profile: Contagious Interview
>😷"Contagious" (The Infection), the campaign is designed to infect software developers and "Interview" is the Lure.  The name is coined by researches from Palo Alto Unit 42.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Contagious Interview |
| **Aliases** | CL-STA-0240, PurpleBravo, DeceptiveDevelopment, DEV#POPPER, Famous Chollima, UNC5342, Void Dokkaebi, Tenacious Pungsan, WaterPlum, Gwisin Gang |
| **Actor Type** | APT |
| **Suspected Origin** | North Korea — Lazarus Group nexus; RGB-affiliated |
| **Active Since** | 2023 (first publicly documented); operational pattern consistent with DPRK activity since 2017 |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Initial BeaverTail/InvisibleFerret Campaign (2023)**

| Field | Details |
|---|---|
| **Date** | 2023-11 |
| **Campaign / Vulnerability Name** | Contagious Interview — BeaverTail Campaign |
| **Victims / Targets** | Software developers (primarily US tech industry); cryptocurrency wallet holders |
| **Description** | Unit 42 first documented Contagious Interview: North Korean threat actors posing as anonymous recruiters lured software developers into fake technical interviews. Victims were asked to run code that deployed BeaverTail (a JavaScript infostealer/downloader) and InvisibleFerret (a Python backdoor). BeaverTail can steal credentials from 13 different cryptocurrency wallets. |
| **Source / Link** | Palo Alto Unit 42 — https://unit42.paloaltonetworks.com/two-campaigns-by-north-korea-bad-actors-target-job-hunters/ |

**2.2 Expanded Targeting with Front Companies (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-04 |
| **Campaign / Vulnerability Name** | BlockNovas / SoftGlide / Angeloper Campaign |
| **Victims / Targets** | Cryptocurrency and blockchain developers globally; supply chain risk to their employer organizations |
| **Description** | Contagious Interview established three fraudulent front companies in the crypto consulting sector (BlockNovas LLC, SoftGlide LLC, Angeloper Agency) with AI-generated employee personas on LinkedIn and social media. ClickFix lures were embedded in video interview platforms. The FBI seized the BlockNovas domain on April 23, 2025. New malware variant OtterCookie was introduced alongside BeaverTail and InvisibleFerret. |
| **Source / Link** | Silent Push / The Hacker News — https://thehackernews.com/2025/04/north-korean-hackers-spread-malware-via.html |

**2.3 EtherHiding Blockchain C2 (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-02 |
| **Campaign / Vulnerability Name** | JADESNOW / EtherHiding Campaign |
| **Victims / Targets** | Web3/DeFi developers; cryptocurrency platforms |
| **Description** | Google GTIG documented Contagious Interview (UNC5342) adopting EtherHiding — storing and retrieving malicious payloads via Ethereum smart contracts. The technique makes C2 infrastructure highly resistant to takedown. JADESNOW malware was used to deploy a JavaScript variant of InvisibleFerret, enabling cryptocurrency theft. |
| **Source / Link** | Google GTIG — https://cloud.google.com/blog/topics/threat-intelligence/dprk-adopts-etherhiding |

**2.4 AI Developer Targeting (2025–2026)**

| Field | Details |
|---|---|
| **Date** | 2025-2026 |
| **Campaign / Vulnerability Name** | PurpleBravo — AI/Blockchain Sector Campaign |
| **Victims / Targets** | 3,136 identified IP addresses; AI, crypto, financial services, and software development organizations in Europe, South Asia, Middle East, Central America |
| **Description** | Recorded Future's Insikt Group documented PurpleBravo targeting 20+ organizations, with the group expanding into AI sector targeting. Actors monitored cybersecurity threat intelligence platforms (Validin, VirusTotal) to detect infrastructure exposure and rapidly deployed replacement infrastructure, suggesting real-time operational monitoring. |
| **Source / Link** | The Hacker News / SentinelOne — https://thehackernews.com/2026/01/north-korean-purplebravo-campaign.html |

---

## 3. Primary Targets

### Industries / Sectors
- Cryptocurrency and blockchain development
- Decentralized finance (DeFi)
- AI and Web3 technology
- Financial services
- IT services and software development
- Marketing agencies

### Notable Victim Organizations
- Bybit (cryptocurrency exchange — linked to Trevor Greer persona)
- Multiple unnamed crypto firms globally

### Technologies & CVEs Exploited
- npm malicious packages (supply chain)
- ClickFix social engineering
- Ethereum smart contracts (EtherHiding C2)
- Video conferencing platform impersonation (MiroTalk, FreeConference.com clones)
- BeaverTail malware (JavaScript/Qt infostealer)
- InvisibleFerret backdoor (Python)
- OtterCookie malware
- JADESNOW downloader

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Phishing: Spearphishing via Service [T1566.003] |
| Initial Access | Supply Chain Compromise: Compromise Software Dependencies [T1195.001] |
| Execution | Command and Scripting Interpreter: Python [T1059.006] |
| Execution | Command and Scripting Interpreter: JavaScript [T1059.007] |
| Execution | User Execution: Malicious File [T1204.002] |
| Persistence | Scheduled Task/Job [T1053] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Masquerading [T1036] |
| Credential Access | Credentials from Web Browsers [T1555.003] |
| Credential Access | Steal Web Session Cookie [T1539] |
| Collection | Data from Local System [T1005] |
| Collection | Clipboard Data [T1115] |
| Command and Control | Web Service [T1102] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
| Impact | Financial Theft [T1657] |
>[Source: Palo Alto Unit 42](https://unit42.paloaltonetworks.com/north-korean-threat-actors-lure-tech-job-seekers-as-fake-recruiters/#:~:text=Executive%20Summary,downloader%20and%20the%20InvisibleFerret%20backdoor.)
---

# Threat Actor Profile: DPRK IT Workers
>🖥️👷 The primary purpose of these individuals (an insider threat) was to earn foreign currency (often $100,000+ annually per worker) and send it back to North Korea.

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | DPRK IT Workers |
| **Aliases** | Famous Chollima, Jasper Sleet, Wagemole (CL-STA-0241), PurpleDelta |
| **Actor Type** | APT |
| **Suspected Origin** | North Korea — Reconnaissance General Bureau (RGB); Treasury-sanctioned entities include Yanbian Silverstar and Volasys Silverstar |
| **Active Since** | 2017 (estimated); FBI advisory issued 2022 |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 FBI Public Advisory — Laptop Farm Operations (2022–2024)**

| Field | Details |
|---|---|
| **Date** | 2022-2024 |
| **Campaign / Vulnerability Name** | DPRK IT Worker Fraud Scheme |
| **Victims / Targets** | 300+ US companies including multiple Fortune 500 firms; two US government agencies |
| **Description** | North Korea deployed thousands of skilled IT workers abroad (primarily in China and Russia) with stolen or fabricated identities to obtain remote employment at Western companies. US-based facilitators operated "laptop farms" to route company-provided devices through domestic addresses. Individual workers earned up to $300,000/year; collectively generating hundreds of millions annually for the DPRK weapons program. CrowdStrike tracked 304 Famous Chollima incidents in 2024 alone. |
| **Source / Link** | FBI IC3 / US DoJ — https://www.ic3.gov/PSA/2025/PSA250723-4 |

**2.2 Yanbian Silverstar / Volasys Silverstar Indictments (2024)**

| Field | Details |
|---|---|
| **Date** | 2024-12 |
| **Campaign / Vulnerability Name** | DoJ Indictment — 14 DPRK Nationals |
| **Victims / Targets** | At least 64 US companies; nonprofit organizations |
| **Description** | The US indicted 14 North Korean nationals working for DPRK-controlled companies Yanbian Silverstar (China) and Volasys Silverstar (Russia) for using stolen identities to obtain remote IT employment over six years, generating at least $88 million. |
| **Source / Link** | US DoJ — https://www.justice.gov/opa/pr/two-north-korean-nationals-and-three-facilitators-indicted-multi-year-fraudulent-remote |

**2.3 Escalation to Data Extortion (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-01 |
| **Campaign / Vulnerability Name** | IC3 Alert — Data Extortion by IT Workers |
| **Victims / Targets** | US and international companies employing DPRK workers |
| **Description** | The FBI issued an IC3 advisory noting that North Korean IT workers, upon being discovered or fired, escalated to data extortion — stealing proprietary code, data, and company secrets, then threatening to leak or sell them unless ransoms were paid. Workers were observed attempting credential theft via session cookies and initiating work sessions from non-company devices. |
| **Source / Link** | FBI IC3 — https://www.ic3.gov/PSA/2025/PSA250123 |

**2.4 Arizona Laptop Farm Sentencing (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-07 |
| **Campaign / Vulnerability Name** | $17M IT Worker Fraud — Chapman Sentencing |
| **Victims / Targets** | 300+ US companies |
| **Description** | An Arizona woman was sentenced to 102 months in prison for operating a laptop farm that facilitated North Korean IT workers posing as US citizens at over 300 US companies, generating more than $17 million in illicit revenue for the DPRK. |
| **Source / Link** | FBI — https://www.fbi.gov/investigate/cyber/alerts/2025 |

---

## 3. Primary Targets

### Industries / Sectors
- US Technology and software development
- Cryptocurrency and blockchain
- Defense contractors and government suppliers
- Financial services
- Any remote-work employer

### Notable Victim Organizations
- 64+ named US companies (DoJ indictment)
- Fortune 500 companies (multiple unnamed)
- Two US government agencies

### Technologies & CVEs Exploited
- Identity theft and synthetic identity creation
- AI-generated/manipulated photos (Remaker AI)
- Voice-changing software
- Astrill VPN for infrastructure obfuscation
- Residential proxies
- Remote monitoring and management (RMM) tools
- TeamViewer, AnyDesk, Telegram (coordination)
- Once embedded: session cookie theft, data exfiltration, extortion

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Valid Accounts [T1078] |
| Persistence | Valid Accounts [T1078] |
| Persistence | Remote Access Software [T1219] |
| Defense Evasion | Valid Accounts [T1078] |
| Defense Evasion | Masquerading [T1036] |
| Credential Access | Steal Web Session Cookie [T1539] |
| Collection | Data from Local System [T1005] |
| Collection | Data from Network Shared Drive [T1039] |
| Exfiltration | Exfiltration Over Web Service [T1567] |
| Exfiltration | Transfer Data to Cloud Account [T1537] |
| Impact | Financial Theft [T1657] |
| Impact | Data Encrypted for Impact [T1486] |
>[Source: Microsoft Threat Intelligence](https://www.microsoft.com/en-us/security/blog/2025/06/30/jasper-sleet-north-korean-remote-it-workers-evolving-tactics-to-infiltrate-organizations/)

---
# Threat Actor Profile: DarkSpectre

>⚠️ LIMITED INTELLIGENCE WARNING DarkSpectre was first publicly named by Koi Security in late 2025.The moniker refers to the group's "sleeper" strategy. Malicious code is disguised within benign-looking extensions—such as tab managers, translators, or video downloaders—that operate normally for years to build trust before turning into spyware, a tactic resembling a "phantom" or "spectre" threat that is hard to detect.


---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | DarkSpectre |
| **Aliases** | ShadyPanda (sub-campaign), GhostPoster (sub-campaign), Zoom Stealer (sub-campaign) |
| **Actor Type** | APT |
| **Suspected Origin** | China (assessed with moderate confidence; Alibaba Cloud C2 infrastructure; nation-state operational scale) |
| **Active Since** | 2018 (earliest sub-campaign activity; seven-year operational footprint) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 ShadyPanda Browser Extension Campaign (2018–2025)**

| Field | Details |
|---|---|
| **Date** | 2018-2025 |
| **Campaign / Vulnerability Name** | ShadyPanda (DarkSpectre Pillar 1) |
| **Victims / Targets** | Approximately 5.6 million users of Chrome, Edge, and Firefox extensions globally |
| **Description** | DarkSpectre published legitimate-appearing browser extensions (new tab pages, productivity tools) using real domains (infinitynewtab[.]com, infinitytab[.]com). After accumulating millions of users and building trust, the group pushed malicious updates with 72-hour delayed activation affecting only ~10% of page loads to evade detection. Extensions performed comprehensive spyware functions including search hijacking, behavioral profiling, and affiliate fraud. |
| **Source / Link** | Koi Security — https://www.koi.ai/blog/darkspectre-unmasking-the-threat-actor-behind-7-8-million-infected-browsers |

**2.2 GhostPoster Campaign (2022–2025)**

| Field | Details |
|---|---|
| **Date** | 2022-2025 |
| **Campaign / Vulnerability Name** | GhostPoster (DarkSpectre Pillar 2) |
| **Victims / Targets** | Approximately 1.05 million users |
| **Description** | A second malicious extension cluster under the DarkSpectre umbrella, GhostPoster focused on credential harvesting and persistent device fingerprinting. Shared C2 infrastructure with ShadyPanda confirmed unified actor attribution. |
| **Source / Link** | Koi Security / The Hacker News — https://thehackernews.com/2025/12/darkspectre-browser-extension-campaigns.html |

**2.3 Zoom Stealer / Corporate Intelligence Campaign (2025)**

| Field | Details |
|---|---|
| **Date** | 2025 |
| **Campaign / Vulnerability Name** | Zoom Stealer (DarkSpectre Pillar 3) |
| **Victims / Targets** | 2.2 million users; corporate participants in Google Meet, Zoom, and GoTo Webinar sessions |
| **Description** | DarkSpectre deployed 18 malicious browser extensions mimicking enterprise videoconferencing tools. These established persistent WebSocket connections to stream meeting data in real time: meeting URLs with embedded passwords, meeting IDs, topics, participant lists, webinar speaker profiles, company affiliations, and logos. ExtraHop assessed this phase represents a shift toward semiconductor and aerospace sector targeting via supply chain interdiction in software development environments. |
| **Source / Link** | Koi Security / The Hacker News — https://thehackernews.com/2025/12/darkspectre-browser-extension-campaigns.html |

---

## 3. Primary Targets

### Industries / Sectors
- Corporate organizations broadly (via mass extension distribution)
- Semiconductor and aerospace (assessed emerging focus)
- Any enterprise using videoconferencing tools

### Notable Victim Organizations
- 8.8 million users total across three campaigns (unnamed organizations)
- Targets identified via corporate meeting infiltration capabilities

### Technologies & CVEs Exploited
- No CVEs — browser extension marketplace abuse (Chrome, Edge, Firefox, Opera)
- WebSocket connections for real-time data streaming
- Time-delayed payload activation (3-day delay post-approval)
- Alibaba Cloud infrastructure for C2
- VMProtect obfuscation
- Legitimate driver exploitation (TrueSight2) for AV evasion (related campaigns)

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Drive-by Compromise [T1189] |
| Execution | Browser Extensions [T1176] |
| Persistence | Browser Extensions [T1176] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Time Based Evasion [T1497.003] |
| Defense Evasion | Masquerading [T1036] |
| Collection | Browser Session Hijacking [T1185] |
| Collection | Data from Information Repositories [T1213] |
| Collection | Screen Capture [T1113] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Exfiltration | Exfiltration Over Web Service [T1567] |
>[Source: Koi Security Research](https://www.koi.ai/blog/darkspectre-unmasking-the-threat-actor-behind-7-8-million-infected-browsers)

---
# Threat Actor Profile: Mustang Panda
>🐎🐼 [Crowdstrike convention](https://www.crowdstrike.com/en-us/blog/meet-crowdstrikes-adversary-of-the-month-for-june-mustang-panda/)

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Mustang Panda |
| **Aliases** | Earth Preta, BRONZE PRESIDENT, TA416, RedDelta, HIVE0154, FIREANT, CAMARO DRAGON, STATELY TAURUS, TWILL TYPHOON, LUMINOUS MOTH, UNC6384 |
| **Actor Type** | APT |
| **Suspected Origin** | China — People's Republic of China (PRC); widely attributed to MSS or PLA-affiliated entity |
| **Active Since** | 2012 |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Vatican and Catholic Organization Targeting (2020)**

| Field | Details |
|---|---|
| **Date** | 2020-07 |
| **Campaign / Vulnerability Name** | RedDelta Vatican Campaign |
| **Victims / Targets** | Vatican, Catholic Church missions to China, Diocese of Hong Kong |
| **Description** | Mustang Panda targeted the Vatican and Catholic organizations ahead of the renewal of a Vatican-China agreement on bishop appointments. Attacks used PlugX malware delivered via spearphishing with geopolitical lures. The operation demonstrated Mustang Panda's political intelligence targeting in support of Chinese state interests in religious affairs. |
| **Source / Link** | Recorded Future Insikt Group — https://go.recordedfuture.com/hubfs/reports/cta-2020-0728.pdf |

**2.2 European Diplomatic Targeting During Ukraine Invasion (2022)**

| Field | Details |
|---|---|
| **Date** | 2022-03 |
| **Campaign / Vulnerability Name** | Europe PlugX Campaign / "Political Guidance for EU approach towards Russia" Lure |
| **Victims / Targets** | European diplomatic and government entities; EU Commission-related organizations |
| **Description** | During the Russian invasion of Ukraine, Mustang Panda ramped up targeting of European diplomatic entities using politically themed lures (including a malicious RAR titled "Political Guidance for the new EU approach towards Russia"). The campaign deployed new PlugX variants and demonstrated Mustang Panda's opportunistic exploitation of geopolitical crises for intelligence collection. |
| **Source / Link** | Cisco Talos / EclecticIQ — https://blog.talosintelligence.com/2022/05/mustang-panda-targets-europe.html |

**2.3 ASEAN-Australia Summit Targeting (2024)**

| Field | Details |
|---|---|
| **Date** | 2024 |
| **Campaign / Vulnerability Name** | ASEAN Entity Campaign |
| **Victims / Targets** | ASEAN government bodies; Philippines, Slovakia; organizations attending 2024 ASEAN-Australia Summit |
| **Description** | Mustang Panda continued its aggressive targeting of Southeast Asian government entities, combining phishing with USB-based malware (HIUPAN worm / PUBLOAD). The group used ToneShell backdoors and mixed legitimate and malicious components to evade detection, per Trend Micro reporting. |
| **Source / Link** | Palo Alto Unit 42 — https://unit42.paloaltonetworks.com/asean-entities-chinese-apt/ |

**2.4 SnakeDisk USB Worm / Thailand Government Targeting (2025)**

| Field | Details |
|---|---|
| **Date** | 2025 |
| **Campaign / Vulnerability Name** | SnakeDisk Campaign |
| **Victims / Targets** | Thai government and military entities (geofenced to Thai IPs); US policy organizations |
| **Description** | Mustang Panda deployed SnakeDisk, a geo-fenced USB worm engineered to execute only on devices with Thai IP addresses, coinciding with the Thailand-Cambodia border conflict. In parallel, after a January 2025 PlugX infrastructure dismantlement by international law enforcement, Mustang Panda rapidly retooled with the LOTUSLITE C++ backdoor to renew targeting of US policy organizations. |
| **Source / Link** | Picus Security / Brandefense — https://www.picussecurity.com/resource/blog/breaking-down-mustang-panda-windows-endpoint-campaign |

---

## 3. Primary Targets

### Industries / Sectors
- Government and diplomatic entities (primary)
- Non-governmental organizations (NGOs)
- Religious organizations
- Telecommunications
- Think tanks and policy research institutions
- Military (Southeast Asia)

### Notable Victim Organizations
- Vatican and Catholic Church organizations
- European Commission / EU diplomatic entities
- Philippine, Thai, Slovak government bodies
- US think tanks (unnamed)

### Technologies & CVEs Exploited
- PlugX / Korplug RAT (primary tool across all campaigns)
- ToneShell / Frankenstein ToneShell backdoors
- LOTUSLITE backdoor (2026)
- SnakeDisk USB worm
- StarProxy, SplatCloak, PAKLOG, CorKLOG (2025 toolset)
- DLL sideloading with signed binaries
- HIUPAN USB worm
- LNK files and RAR archives (phishing delivery)

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Spearphishing Attachment [T1566.001] |
| Initial Access | Replication Through Removable Media [T1091] |
| Execution | User Execution: Malicious File [T1204.002] |
| Execution | Shared Modules [T1129] |
| Persistence | Scheduled Task/Job: Scheduled Task [T1053.005] |
| Persistence | Boot or Logon Autostart Execution: Registry Run Keys [T1547.001] |
| Defense Evasion | DLL Side-Loading [T1574.002] |
| Defense Evasion | Subvert Trust Controls: Code Signing [T1553.002] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Masquerading [T1036] |
| Defense Evasion | Rootkit [T1014] |
| Collection | Data from Local System [T1005] |
| Collection | Data Staged [T1074] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Command and Control | Ingress Tool Transfer [T1105] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
>[Source: MITRE ATT&CK Group G0129](https://attack.mitre.org/groups/G0129/) 
---
# Threat Actor Profile: Silver Fox

>⚠️ LIMITED INTELLIGENCE WARNING Discovered by Chinese security firm ThreatBook. Known for the fast evolving techniques. 

---

## 1. Basic Identification

| Field | Value |
|---|---|
| **Primary Name** | Silver Fox |
| **Aliases** | Void Arachne, The Great Thief of Valley, Silver Fox APT |
| **Actor Type** | APT (note: exhibits hybrid financially motivated / state espionage characteristics — possible state-sponsored group masquerading as eCrime) |
| **Suspected Origin** | China (assessed with moderate confidence based on infrastructure, language targeting, and Alibaba Cloud usage) |
| **Active Since** | 2024 (first documented; earlier activity likely under different tracking) |
| **Current Status** | Active |

---

## 2. Notable Events

**2.1 Chinese-Speaking User Campaign via Winos 4.0 / ValleyRAT (2024)**

| Field | Details |
|---|---|
| **Date** | 2024-06 |
| **Campaign / Vulnerability Name** | ValleyRAT / Winos 4.0 Campaign |
| **Victims / Targets** | Chinese-speaking individuals and organizations; government entities, cybersecurity companies, e-commerce, finance, gaming companies |
| **Description** | Silver Fox (tracked by Trend Micro as Void Arachne) distributed ValleyRAT (aka Winos 4.0) through SEO poisoning, Telegram channels, and social media, disguising the malware as popular AI applications, VPN software, and gaming tools. The campaign targeted Chinese-speaking users circumventing the Great Firewall. ValleyRAT is a modular backdoor enabling keystroke logging, security bypass, screen capture, and data exfiltration. |
| **Source / Link** | Trend Micro / Forescout Vedere Labs — https://industrialcyber.co/medical/forescout-details-silver-fox-campaign-targeting-healthcare-with-backdoors-keyloggers-crypto-miners/ |

**2.2 Healthcare Sector Targeting via DICOM Viewer (2024–2025)**

| Field | Details |
|---|---|
| **Date** | 2024-07 / 2025-01 |
| **Campaign / Vulnerability Name** | DICOM Viewer Trojanization Campaign |
| **Victims / Targets** | Healthcare organizations in US and Canada; patients and hospitals via Philips DICOM medical imaging viewers |
| **Description** | Forescout Vedere Labs identified 29 malware samples (July 2024–January 2025) masquerading as Philips DICOM viewers. The MediaViewerLauncher.exe first-stage malware performed C2 beaconing, downloaded encrypted payloads from Alibaba Cloud, and established persistence via Windows Scheduled Tasks. Final payloads included ValleyRAT backdoor, a keylogger, and an XMRig cryptocurrency miner. |
| **Source / Link** | Forescout Vedere Labs / Infosecurity Magazine — https://www.infosecurity-magazine.com/news/chinese-silver-fox-backdoors/ |

**2.3 Microsoft Teams SEO Poisoning with Russian False Flag (2025)**

| Field | Details |
|---|---|
| **Date** | 2025-11 |
| **Campaign / Vulnerability Name** | teamscn[.]com Campaign |
| **Victims / Targets** | Chinese-speaking users and organizations, including Western companies operating in China |
| **Description** | Silver Fox used a fake Microsoft Teams website (teamscn[.]com) to distribute ValleyRAT loaders, incorporating Cyrillic characters in the ZIP filename to create a Russian false flag and complicate attribution. ReliaQuest linked this to Silver Fox via infrastructure pivot analysis connecting the domain to prior Telegram phishing sites targeting Chinese-speaking users. |
| **Source / Link** | ReliaQuest — https://reliaquest.com/blog/threat-spotlight-silver-foxs-russian-ruse-fake-microsoft-teams-attack/ |

**2.4 South Asia Tax Lure Campaign (2025–2026)**

| Field | Details |
|---|---|
| **Date** | 2025-2026 |
| **Campaign / Vulnerability Name** | Tax Authority Impersonation Campaign |
| **Victims / Targets** | South Asian financial sector; organizations in India and surrounding region |
| **Description** | Silver Fox transitioned from ValleyRAT to abusing a misconfigured Chinese RMM tool, then to a custom Python-based stealer disguised as a WhatsApp application. Lures impersonated national tax authorities and payroll documents. Sekoia TDR confirmed the evolution across 2025–2026, noting the group increasingly blends intelligence collection with financial crime. |
| **Source / Link** | Sekoia TDR — https://blog.sekoia.io/silver-fox-the-only-tax-audit-where-the-fine-print-installs-malware/ |

---

## 3. Primary Targets

### Industries / Sectors
- Healthcare (medical imaging platforms)
- Government and law enforcement
- Cybersecurity companies
- E-commerce and financial services
- Gaming
- Chinese-speaking individuals globally (primary demographic)

### Notable Victim Organizations
- Healthcare delivery organizations (HDOs) using Philips DICOM viewers
- Chinese-speaking enterprises in US, Canada
- South Asian financial organizations

### Technologies & CVEs Exploited
- SEO poisoning (Google Search manipulation)
- Trojanized legitimate software (DICOM viewers, Teams, AI apps, VPN clients)
- ValleyRAT / Winos 4.0 (modular RAT derived from Gh0st RAT)
- TrueSight2 vulnerable driver (AV evasion)
- VMProtect obfuscation
- CleverSoar installer, Nidhogg rootkit (late 2024)
- Alibaba Cloud for payload hosting

---

## 4. MITRE ATT&CK TTPs

| Tactic | Technique |
|---|---|
| Initial Access | Drive-by Compromise [T1189] |
| Initial Access | Phishing: Spearphishing Attachment [T1566.001] |
| Execution | Shared Modules [T1129] |
| Execution | User Execution: Malicious File [T1204.002] |
| Persistence | Scheduled Task/Job: Scheduled Task [T1053.005] |
| Persistence | Boot or Logon Autostart Execution: Registry Run Keys [T1547.001] |
| Defense Evasion | Subvert Trust Controls: Install Root Certificate [T1553.004] |
| Defense Evasion | Rootkit [T1014] |
| Defense Evasion | Obfuscated Files or Information [T1027] |
| Defense Evasion | Impair Defenses: Disable or Modify Tools [T1562.001] |
| Defense Evasion | Masquerading [T1036] |
| Credential Access | Input Capture: Keylogging [T1056.001] |
| Collection | Screen Capture [T1113] |
| Collection | Credentials from Web Browsers [T1555.003] |
| Command and Control | Application Layer Protocol: Web Protocols [T1071.001] |
| Exfiltration | Exfiltration Over C2 Channel [T1041] |
| Impact | Resource Hijacking [T1496] |
>[Source: Sekoia TDR](https://blog.sekoia.io/silver-fox-the-only-tax-audit-where-the-fine-print-installs-malware/)

---
