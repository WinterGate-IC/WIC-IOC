# WIC-IOC

**Indicators of Compromise from all attacks against WinterGateIC.**

IPs, domains, hashes, SSH keys, C2 infrastructure, and TTPs from every actor targeting our gate. Defender-ready blocklists, updated continuously.

---

**Repository:** WIC-IOC
**Maintained by:** WinterGate Intelligence Collective (WIC)
**Established:** 2026-10-10
**Last Updated:** 2026-10-10
**Version:** 1.0
**Status:** Active — continuously maintained
**Classification:** Public — Defender Use Authorized

---

## What This Is

This repository is a public, living archive of Indicators of Compromise (IOCs) extracted from attacks against WinterGateIC infrastructure. It documents every threat actor, campaign, and technique that has targeted us — criminal botnets, state-aligned operations, ideologically motivated groups, and everything in between.

The purpose is simple: defenders should not have to be attacked first to know what is coming.

Everything documented here is sourced from observed activity against our infrastructure, cross-referenced with independent threat intelligence, and formatted for immediate defensive use.

---

## Why It Exists

Threat intelligence is usually locked behind paywalls, enterprise contracts, or vendor platforms. By the time it reaches the defenders who need it most — small teams, independent researchers, community operators — the attack has already happened.

This archive removes that barrier. If a threat actor hits our gate, their infrastructure, tooling, and techniques are published here so that anyone can block, detect, and hunt them before they arrive.

An attack on one defender is a lesson for every defender.

---

## What Gets Documented

### IOCs

- **IP addresses** — attacker source IPs and C2 endpoints
- **Domains** — malicious infrastructure, C2 hosts, payload distribution
- **File hashes** — SHA-256 for payloads, keys, and malware samples
- **SSH keys** — persistence indicators and authorized_keys fingerprints
- **Filenames** — droppers, payloads, miners, backdoors
- **URLs** — payload distribution and staging endpoints
- **Email addresses** — attacker contact and registration artifacts
- **Credentials** — known compromised accounts and hardcoded passwords

### TTPs

- **Initial access** — how the actor gets in
- **Persistence** — how they stay in
- **Privilege escalation** — how they move up
- **Defense evasion** — how they hide
- **Command and control** — how they communicate
- **Impact** — what they do once inside
- **Compromise timelines** — observed step-by-step attack sequences

### Attribution

- **Threat actor profiles** — who is behind the activity
- **Confidence levels** — how certain we are
- **Cross-references** — independent corroboration from other firms
- **Campaign tracking** — shared fingerprints across IPs

---

## The Standard

Every entry in this archive meets a documented standard:

- **Verifiable claims only** — every assertion is backed by observed telemetry or independent OSINT
- **Timestamps** — attack dates, detection times, and IOC first-seen dates are recorded
- **Separation of confirmed and suspected** — clear distinction between what is proven and what is inferred
- **Attribution confidence** — every attribution includes a confidence level
- **Defender-first formatting** — IOCs are presented in copy-paste ready formats for firewalls, SIEMs, and detection tools
- **Continuous updates** — the archive grows as new attacks are observed and attributed

If a claim cannot meet these standards, it does not belong in this archive.

---

## What This Is Not

- This is not a target list.
- This is not a call to action.
- This is not a dox.
- This is not a substitute for law enforcement.

This is a record. Nothing more. If you have evidence of criminal activity, report it to the appropriate authorities:

- **FBI IC3** — https://www.ic3.gov
- **NCMEC CyberTipline** — https://www.cybertip.org

---

## How Defenders Can Use This

| **Use Case** | **Action** |
|---|---|
| **Blocking** | Add IPs and domains to firewall blocklists and DNS sinkholes |
| **Detection** | Deploy the documented SSH keys, hashes, and filenames as detection signatures |
| **Hunting** | Search historical logs for the TTPs and compromise timelines documented here |
| **Attribution** | Cross-reference your own incidents against the actor profiles |
| **Briefing** | Use the actor profiles to inform threat models and tabletop exercises |
| **Automation** | Consume the blocklists programmatically into your security stack |

The IOCs here are designed to work with common tooling: iptables, ipset, nftables, pfSense, Suricata, Zeek, Sigma, YARA, Splunk, Elastic, and AbuseIPDB reporting pipelines.

---

## Attribution Ledger

**Confirmed Threat Actors Observed Targeting WIC Infrastructure**

| **Actor** | **Type** | **Confidence** | **First Observed** |
|---|---|---|---|
| Outlaw Hacking Group (Dota / Shellbot) | Criminal botnet — mdrfckr | 98% | 2026-07 |
| Iran-aligned infrastructure | State-aligned | High | 2026-07-14 |
| Russia-aligned infrastructure | State-aligned | High | 2026-07-14 |
| UTTP / 764-affiliated actors | Ideological | Moderate | 2026-09 |
| Legitimate research scanners | Non-hostile noise | Confirmed | Ongoing |

Independent corroboration for the Outlaw attribution was provided by SANS ISC, Kaspersky, and the Max Planck Institute. Cross-references are documented within individual entries.

---

## Recent Activity

The most recent additions to this archive are tied to the ongoing campaign against our infrastructure — including a sustained SSH brute-force and cryptomining operation, state-aligned retaliation activity, and ideologically motivated harassment from groups we have publicly documented.

Specific attribution, IOCs, and TTP breakdowns are in the archive entries.

---

## Related Repositories

- **Xnegligence** — https://github.com/WinterGate-IC/Xnegligence
- **UTTP Investigation** — https://github.com/WinterGate-IC/UTTP
- **Abuse Entities** — https://github.com/WinterGate-IC/ABUSE-ENTITES
- **WIC Artifacts** — https://github.com/WinterGate-IC/wic-artifacts
- **Cloudzy Upstream Filter Vulnerability** — https://github.com/WinterGate-IC/cloudzy-upstream-filter-vulnerability

---

## Document Control

| **Field** | **Value** |
|---|---|
| Repository Established | 2026-10-10 |
| Published | 2026-10-10 |
| Last Verified | 2026-10-10 |
| Maintained By | WinterGate Intelligence Collective |
| Contact | Public via GitHub Issues |

---

**WIC** — WinterGate Intelligence Collective
*Public Release · 2026-10-10*
