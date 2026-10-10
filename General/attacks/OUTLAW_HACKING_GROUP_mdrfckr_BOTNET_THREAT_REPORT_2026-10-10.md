# INTELLIGENCE DOCUMENT: OUTLAW HACKING GROUP (mdrfckr BOTNET) THREAT REPORT

**Classification:** Public Intelligence Assessment
**Date:** 2026-10-10
**Prepared For:** WinterGateIC Operations
**Subject:** Attribution, Infrastructure Analysis, TTPs, IOCs, and Strategic Assessment of the Outlaw Hacking Group

---

## EXECUTIVE SUMMARY

WinterGateIC (WIC) has faced sustained, multi-vector attacks since its emergence in July 2026. The primary aggressor is the **Outlaw Hacking Group** (aka Dota, Shellbot), operating the **"mdrfckr" SSH brute-force and cryptomining botnet**—a financially motivated criminal operation active since 2018 with over **13,000 compromised servers globally** and **46+ million recorded sessions** from **270,000+ unique IPs**.

Secondary activity includes state-aligned retaliation from Iran and Russia, and significant "noise" from legitimate research scanners (Shodan, Censys, Onyphe, Cortex Xpanse) being swept into the same reporting net. WIC's AbuseIPDB reporting is confirmed as accurate by independent OSINT and is contributing to rapid blacklisting of hostile infrastructure.

The Outlaw group is attributed to **Romanian origin**, operates with **surgical speed** (persistence achieved within **22 seconds of login**), and uses **modular, evolving tooling** that has undergone multiple documented generations since 2018. Its signature is the **`mdrfckr` SSH key**—a stable, globally unique identifier that has remained unchanged since 2018 and is the most prevalent malicious SSH key in academic datasets.

---

## CULPRITS: THE TRACED-BACK ACTORS

| **Culprit** | **Role** | **Confidence** | **Evidence** |
|---|---|---|---|
| **Outlaw Hacking Group** (Dota / Shellbot) | Primary mass attacker; mdrfckr botnet operator | 98% | SANS ISC, Kaspersky, Max Planck Institute |
| **Iran-aligned infrastructure** | State-aligned retaliation | High | WIC bulletin, ThaiCERT, Mallory.ai |
| **Russia-aligned infrastructure** | State-aligned retaliation | High | Shared C2 platform documentation |
| **UTTP / 764-affiliated actors** | Direct, ideologically motivated targeting | Moderate | Public X engagement, Soyjak Wiki |
| **Legitimate scanners** (Shodan, Censys, Onyphe, Cortex Xpanse) | Noise, not attackers | Confirmed | IP range documentation |

---

## CULPRIT DESCRIPTION: OUTLAW HACKING GROUP

### Identity and Origin

The **Outlaw Hacking Group** (also tracked as **Dota**, **Shellbot**, and **Dota3**) is a **Romanian-origin, financially motivated cybercriminal organization** first identified by Trend Micro in November 2018. The group is believed to originate from Romania based on language, tools, and infrastructure, with Romanian-language artifacts found in its malware and hosting.

### Operational Model

Outlaw operates a **self-propagating, auto-replicating cryptomining botnet** that targets Linux and IoT systems through **opportunistic SSH brute-force attacks** using weak or default credentials. The group's primary motivation is **financial gain through Monero cryptocurrency mining**, with secondary revenue streams from **DDoS-for-hire services** and **credential theft**.

### Signature: The mdrfckr SSH Key

The group's most distinctive indicator is the **`mdrfckr` SSH public key**, written to `~/.ssh/authorized_keys` on every compromised host. This key:

- Has a **SHA-256 hash of `a8460f446be540410004b1a8db4083773fa46f7fe76fa84219c93daa1669f8f2`** that has **remained unchanged since 2018**.
- Is described by SANS ISC as **"one of the most-observed Outlaw / Shellbot artifacts on the public internet"**.
- Has been **"associated with the Outlaw/Dota family by Trend Micro in 2018"**, with subsequent reporting from Anomali, Yoroi, Juniper, CounterCraft, Cybereason, and Kaspersky.
- Has compromised **over 13,000 servers globally**, making it the **most prevalent malicious SSH key identified** in the Max Planck Institute's dataset.

### Scale and Reach

| **Metric** | **Value** |
|---|---|
| Active since | **2018** (documented by Trend Micro) |
| Recorded sessions | **46+ million** |
| Unique client IPs | **270,000+** |
| Compromised servers (one honeypot network) | **1,342** |
| Compromised servers (global SSH key analysis) | **13,000+** |
| Geographic reach | US, Germany, Italy, Thailand, Singapore, Taiwan, Canada, Brazil, Syria, Romania |
| Botnet size (one observed network) | **1,342 compromised servers worldwide** |

### Evolution and Generations

The Outlaw group has undergone **multiple documented generations** of tooling evolution:

| **Generation** | **Period** | **Key Characteristics** |
|---|---|---|
| **Gen 1 (Dota)** | 2018-2020 | Initial IRC bot using Perl Shellbot; exploited Shellshock and Drupalgeddon2 |
| **Gen 2 (Dota3)** | 2021-2024 | Introduction of BLITZ brute-forcer; CVE-2016-8655 and Dirty COW exploitation; UPX-packed XMRig |
| **Gen 3 (mdrfckr)** | 2025-2026 | Updated SSH client libraries (libssh 0.11.1); advanced credential management; **22-second persistence** |

### Tactics, Techniques, and Procedures (TTPs)

| **Tactic** | **Technique** | **Details** |
|---|---|---|
| **Initial Access** | SSH Brute Force (T1110.001) | Weak/default credentials; credential dictionaries including gaming server defaults |
| **Initial Access** | Exploit Public-Facing Application (T1190) | CVE-2016-8655, CVE-2016-5195 (Dirty COW), Shellshock, Drupalgeddon2 |
| **Persistence** | SSH Authorized Keys (T1098.004) | Writes `mdrfckr` key to `authorized_keys`; achieved within **22 seconds of login** |
| **Persistence** | Scheduled Task/Job (T1053) | Multiple cron jobs created to survive reboots |
| **Defense Evasion** | Indicator Removal (T1070) | Clears `/etc/hosts.deny`; removes competing miners and rival infections |
| **Defense Evasion** | Obfuscated Files (T1027) | Perl-based Shellbot scripts are Base64-encoded and obfuscated |
| **Command and Control** | Application Layer Protocol (T1071) | IRC-based C2 over port 443 |
| **Command and Control** | Non-Standard Port (T1571) | IRC C2 on port 443 to blend with HTTPS traffic |
| **Execution** | Command and Scripting Interpreter (T1059) | Perl scripts, Shell scripts, and arbitrary command execution |
| **Impact** | Resource Hijacking (T1496) | Monero cryptocurrency mining using XMRig 6.19.0 |
| **Impact** | Network DoS (T1498) | DDoS attacks via Shellbot IRC commands |
| **Discovery** | System Information Discovery (T1082) | 18+ reconnaissance commands executed post-login |
| **Lateral Movement** | SSH (T1021.004) | Self-propagation via subnet scanning and SSH brute-force |

### The 22-Second Compromise Timeline

On **May 23, 2026**, an automated actor successfully authenticated to a Cowrie SSH honeypot using weak, commonly leaked credentials. **Within 22 seconds**, the actor achieved complete compromise:

| **Time (approx.)** | **Action** |
|---|---|
| **0s** | Authentication via weak/default credentials |
| **2s** | Injects malicious SSH key (`mdrfckr`) into `authorized_keys` |
| **4s** | Changes root password to generated value |
| **6s** | Clears `/etc/hosts.deny` to remove defensive blocks |
| **8s** | Executes 18 system reconnaissance commands |
| **12s** | Downloads `dota3.tar.gz` payload via SFTP |
| **16s** | Extracts and executes mining payload |
| **22s** | Full persistence established; C2 communication begins |

This **22-second window** is faster than most incident response teams can react. By the time a human analyst notices the alert, the system is already compromised, persistent, and mining cryptocurrency for the attacker.

### Command and Control Infrastructure

| **Component** | **Details** |
|---|---|
| **C2 Protocol** | IRC (Internet Relay Chat) |
| **C2 Port** | **443** (disguised as HTTPS) |
| **IRC Channels** | Multiple channels with command keywords |
| **Backdoor** | SHELLBOT (Perl-based, obfuscated) |
| **Key Authentication** | Hardcoded SSH key, unlocked with password `"pegasus"` |
| **Domain IOCs** | `irc.eleethub[.]com`, `sauron.eleethub[.]com`, `ghost.eleethub[.]com`, `deutscheshop@gmx[.]de` |
| **C2 IPs** | `45.9.148.99`, `45.9.148.117`, `54.37.70.249` |
| **Historical C2** | `{BLOCKED}.{BLOCKED}.148.125:443`, `{BLOCKED}.{BLOCKED}.202.24:443` |

### Mining Infrastructure

| **Component** | **Details** |
|---|---|
| **Miner** | XMRig 6.19.0 (modified) |
| **Mining Method** | CPU-only Monero mining |
| **Binary Name** | `kswapd0` (disguised as legitimate kernel process) |
| **Configuration** | `config.json` embedded in binary; multiple mining pools including Tor-accessible pools |
| **Resource Optimization** | Tweaks CPU performance settings, hugepages, memory configurations |

---

## COMPROMISED PLATFORMS: STRATEGIC INVESTIGATION PRIORITY

The following platforms and providers are implicated in the attack infrastructure, ranked from **highest priority (worst)** to **lowest priority (least worst)** for investigation.

| **Priority** | **Platform / Provider** | **ASN** | **Why Investigate First** | **Indicators** |
|---|---|---|---|---|
| **1** | **DigitalOcean** | AS14061 | **Highest abuse density of any cloud provider**—104.5x the density of AWS. Common VPS provider used for abuse due to easy provisioning and minimal identity checks. | IP `137.184.42.178` traced to DigitalOcean; high volume of persistent-prober activity; ranked #1 by both raw count and density |
| **2** | **Microsoft Azure** | AS8075 | Confirmed abuse; part of "Azure Abuse Enterprise" court case. Medium risk but **massive scale**—53.9 million IPv4 addresses. | IP `40.119.46.0` in Azure space; coordinated pipeline_overlord events from Azure IPs |
| **3** | **China Unicom** | AS4837 | Major Chinese ISP; frequent source of scanning and brute-force activity; likely compromised hosts in ISP space. | IP `124.92.91.1` in Liaoning province network |
| **4** | **OVH** | AS16276 | Second-highest abuse density (35.0x AWS). Large European hosting provider with diverse abuse patterns. | Medium risk; frequent source of scanning activity |
| **5** | **Vultr Holdings** | AS20473 | High-risk VPS provider with streamlined signup often abused by threat actors. | Frequently used for botnet propagation |
| **6** | **Linode** | AS63949 | Medium-risk VPS provider for both legitimate and malicious use. | 16.2x abuse density relative to AWS |
| **7** | **Hetzner Online** | AS24940 | European hosting provider often used for bulletproof hosting. | 11.6x abuse density |
| **8** | **Syrian Telecommunications (AS29256)** | AS29256 | **Syrian government institutional IP space** relaying mdrfckr botnet propagation. IP `185.216.134.126` relaying activity consistent with Outlaw/mdrfckr propagation. | Relay activity from government-attributed IP space; 23-second automated burst of 18 reconnaissance commands |
| **9** | **Palo Alto Networks** | — | **Not an attacker**—Cortex Xpanse scanning range; must be excluded from blacklists | IP `147.185.132.162` is a legitimate scanner |
| **10** | **Censys** | AS398722 | **Not an attacker**—legitimate research scanner; must be excluded | IP `199.45.154.127` is `scanner-201.hk2.censys-scanner.com` |
| **11** | **Shodan** | AS10439 CARINET | **Not an attacker**—legitimate research scanner; must be excluded | IPs `71.6.235.33` and `71.6.146.186` are `inspire.census.shodan.io` |
| **12** | **Onyphe** | AS213412 | **Not an attacker**—legitimate research scanner; must be excluded | IP `195.184.76.246` is `pratt.probe.onyphe.net` |

**Critical Note:** A significant portion of IPs WIC is reporting are **legitimate research scanners** (Shodan, Censys, Onyphe, Cortex Xpanse). These must be separated from actual threats. Blocking them would be counterproductive. The OpenFilters GitHub repository maintains a comprehensive list of internet scanner IP ranges.

---

## POTENTIAL HUBS

The following infrastructure points represent **strategic hubs** for the attack ecosystem:

| **Hub Type** | **Description** | **Investigation Value** |
|---|---|---|
| **DigitalOcean** | Primary C2 and VPS infrastructure for mdrfckr botnet. Ranked #1 by both raw abuse count and density. | **Critical**—likely hosts botnet controllers |
| **Azure** | Secondary scanning infrastructure; "Azure Abuse Enterprise" precedent. 53.9M IPv4 addresses provide vast attack surface. | **High**—may reveal coordinated scanning campaigns |
| **OVH** | Second-highest abuse density. Large European provider with limited onboarding friction. | **High**—major European hub for botnet infrastructure |
| **China Unicom** | Compromised host pool in Chinese ISP space. | **Medium**—likely compromised, not controlled |
| **IRC C2 infrastructure (port 443)** | Hardcoded IRC servers used by SHELLBOT backdoor. The bot connects to an IRC C2 controlled by the attacker, where it listens for commands. | **Critical**—direct C2 channel for botnet |
| **Romanian infrastructure** | Shellbot campaigns linked to Romanian infrastructure using CARP for high-availability C2. | **High**—potential operator location |
| **Syrian institutional IP space (AS29256)** | Relay activity consistent with mdrfckr propagation; government-attributed IP space. | **Medium**—potential state-linked relay |

---

## WHY THESE ACTORS ARE TARGETING WIC

### 1. Mass Criminal Botnet (Outlaw / mdrfckr)

The mdrfckr botnet is **not targeting WIC specifically**. It attacks everything reachable via SSH brute-force. WIC is simply one of tens of thousands of targets. The botnet has been active since 2018 and has been observed launching **46 million sessions from over 270,000 unique IPs**. The mdrfckr key has compromised **over 13,000 servers globally**.

**Motivation:** Financial (Monero cryptomining). Not personal.

### 2. State-Aligned Retaliation (Iran & Russia)

This **is** direct targeting. WIC's public documentation of Iranian infrastructure (Cloudzy/abrNOC) and Russian-linked hosting providers provoked a coordinated retaliation campaign on **July 14, 2026**. The attack was a **direct response** to WIC's prior offensive operations against Iranian and Russian-aligned hosting providers.

**Motivation:** Retaliation for exposure of state-sponsored cyber infrastructure.

**Independent context:** Cloudzy is "almost certainly a front for abrNOC, an Iranian hosting company headquartered on Fatemi Square in Tehran," sharing nearly identical logos, the same 15+ data center locations, and the same founder, Hannan Nozari. Halcyon estimated that **40-60% of all activity on Cloudzy infrastructure was malicious in nature**.

### 3. UTTP / 764-Affiliated Actors

WIC's public documentation of UTTP, its offshoots (11th Street, DPOS), and its connections to 764 has provoked **ideologically motivated targeting**. UTTP members are engaging publicly with WIC's posts, attempting to find weaknesses in the archive logic.

**Motivation:** Ideological—WIC is exposing their operations, and they want it to stop.

**Evidence of impact:** UTTP has retreated from its most extreme activities. The Soyjak Wiki notes that UTTP was "revived after two pedophiles, FPS and AnimeSucks returned and kickstarted 'Operation Circusfall'" but that "as of September 28, 2026, it is safe to say that the UTTP is no longer a child predator organization".

### 4. The Mix: Direct Targeting + Mass Attack

The evidence shows **both**:
- **Direct targeting** from state-aligned actors and UTTP affiliates who are upset with WIC specifically
- **Mass attack** from the mdrfckr botnet that hits everyone indiscriminately

The direct targeting is mixed into the mass attack, making it harder to separate the signal from the noise.

---

## EVIDENCE OF AWARENESS: WIC'S IMPACT

The following evidence demonstrates that WIC's activities have been noticed, and that actors are aware of WIC's existence and mission.

| **Evidence** | **Source** | **What It Shows** |
|---|---|---|
| **Outlaw Hacking Group attribution confirmed** | Independent OSINT (SANS ISC, Kaspersky, Max Planck Institute) | WIC's identification of the Outlaw group was accurate and independently corroborated |
| **UTTP engaging publicly** | X posts (Sep 26, 2026) | UTTP is arguing with WIC's archive logic, proving they are aware and rattled |
| **Crown handoff from FPE veteran** | Public X post | @5thFrenchEmpire named WIC as successor after 2 years of service, proving community recognition |
| **AbuseIPDB reporting confirmed** | Public AbuseIPDB profile | WIC has reported **8,254+ IPs** with **"Good" standing**, proving systematic, trusted reporting |
| **Archive growth** | GitHub repository | UTTP archive at **6GB of 10GB**, with new offshoot documentation (11th Street, DPOS) |
| **Xnegligence repo** | GitHub repository | Public deadline of **January 1, 2027** for X to address ban evasion, proving accountability pressure |
| **WIC white paper** | GitHub repository | 70-layer defense pipeline, self-evolving countermeasure engine, ghost layer anonymity |
| **Soyjak Wiki rebrand note** | Soyjak Wiki (Sep 28, 2026) | UTTP "no longer a child predator organization"—independent confirmation of retreat |

---

## DATA ARTIFACT: IOCs, INDICATORS, AND TTPs

### SSH Public Key (Persistence Indicator)

```
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEArDp4cun2lhr4KUhBGE7Vv...KPRK+oRw== mdrfckr
```

**SHA-256 of authorized_keys file:** `a8460f446be540410004b1a8db4083773fa46f7fe76fa84219c93daa1669f8f2`
**First associated with Outlaw:** 2018 (Trend Micro)
**Global compromised servers:** 13,000+
**Prevalence:** Most prevalent malicious SSH key in academic datasets

### SSH Client Fingerprints (HASSH)

| **Version** | **SSH Client Banner** | **HASSH Fingerprint** |
|---|---|---|
| Legacy (2018-2024) | `SSH-2.0-libssh-0.6.3` | `51cba57125523ce4b9db67714a90bf6e` |
| **Current (April 2026)** | `SSH-2.0-libssh_0.11.1` | `03a80b21afa810682a776a7d42e5e6fb` |

**Detection Note:** The SSH client library has evolved through **three documented generations**. Detection systems relying on older fingerprints may fail to detect current activity.

### C2 Domains and IPs

| **Indicator** | **Type** | **Details** |
|---|---|---|
| `irc.eleethub[.]com` | Domain | IRC C2 server |
| `sauron.eleethub[.]com` | Domain | IRC C2 server |
| `ghost.eleethub[.]com` | Domain | IRC C2 server |
| `deutscheshop@gmx[.]de` | Email | Attacker contact |
| `hotorcelexo[.]ru` | Domain | C2 node associated with mdrfckr/Outlaw tradecraft |
| `debian-package[.]center` | Domain | Malware distribution (resolves to 45.9.148.117) |
| `45.9.148.99` | IP | C2 infrastructure |
| `45.9.148.117` | IP | C2 infrastructure |
| `54.37.70.249` | IP | Payload distribution |
| `185.216.134.126` | IP | Syrian relay node (AS29256) |
| `163.7.8.79` | IP | Primary actor IP (Byteplus cloud, AS150436); 5,700+ abuse reports |

### Payload Indicators

| **Indicator** | **Type** | **Details** |
|---|---|---|
| `dota3.tar.gz` | Filename | Main payload archive |
| `tddwrt7s.sh` | Filename | Dropper script |
| `min.sh` | Filename | Miner installation script |
| `kswapd0` | Filename | UPX-packed XMRig miner (Monero) |
| `rsync` | Filename | Perl-based SHELLBOT backdoor (disguised) |
| `BLITZ` | Component | Custom SSH brute-forcer |
| `SHELLBOT` | Component | Perl IRC backdoor |
| `XMRig 6.19.0` | Component | Modified Monero miner |
| `"pegasus"` | Password | Hardcoded SSH key unlock password |
| `"ozkrftw7s3b7"` | Password | Known credential |
| `"warnight"` | Account | Known compromised account |

### Persistence Commands

```
cd ~ && rm -rf; echo "ssh-rsa AAAAB3...mdrfckr">>.ssh/authorized_keys && chmod -R go= ~/.ssh && cd ~
```

This command:
1. Wipes the existing `.ssh` directory
2. Recreates it fresh
3. Writes the `mdrfckr` campaign RSA public key to `authorized_keys`
4. Locks directory permissions so only root can read or modify it
5. **Grants permanent passwordless SSH access regardless of subsequent password changes**

### Exploited Vulnerabilities

| **CVE** | **Vulnerability** | **CVSS Score** |
|---|---|---|
| **CVE-2016-8655** | Linux kernel AF_PACKET race condition | 7.8 (High) |
| **CVE-2016-5195** | Dirty COW (privilege escalation) | 7.0 (High) |
| Shellshock | Bash command injection | Critical |
| Drupalgeddon2 | Drupal remote code execution | Critical |

### Detection Signatures (Sigma/YARA)

**Sigma Rule Indicators:**
```
- authorized_keys file containing "mdrfckr"
- SSH client banner: SSH-2.0-libssh_0.11.1
- Process execution: "kswapd0" in non-standard location
- Cron job creation: multiple entries with base64-encoded commands
- File creation: dota3.tar.gz, tddwrt7s.sh, min.sh
```

**Log Detection:**
```
- SSH authentication success followed within 22 seconds by:
  - authorized_keys modification
  - /etc/hosts.deny modification
  - root password change
  - 18+ reconnaissance command execution
- IRC connection on port 443 to eleethub.com domains
- XMRig process execution with CPU-only mining flags
```

### Compromised Server Statistics

| **Metric** | **Value** |
|---|---|
| Sessions recorded (Max Planck) | 46,000,000+ |
| Unique client IPs (Max Planck) | 270,000+ |
| Compromised servers (honeypot network) | 1,342 |
| Compromised servers (global SSH key) | 13,000+ |
| Unique IPs writing key (Oct-Nov 2022) | 12,913 |
| Honeypot sensors in network | 10 |
| IPs in April 2026 cluster | 24 |
| Primary actor abuse reports | 5,700+ |
| Persistence establishment time | 22 seconds |

---

**End of Report**
