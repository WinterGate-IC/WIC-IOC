# /actors/

**Threat actor archive — identified, attributed, and profiled groups targeting WinterGateIC.**

Every group that has hit our gate, documented in one place. IOCs, TTPs, attribution confidence, and attack timelines for each.

---

**Repository:** WIC-IOC
**Folder:** /actors/
**Maintained by:** WinterGate Intelligence Collective (WIC)
**Established:** 2026-10-10
**Last Updated:** 2026-10-10
**Version:** 1.0
**Status:** Active — continuously maintained
**Classification:** Public — Defender Use Authorized

---

## What This Folder Is

This folder holds the attributed threat actors — the groups we have identified, confirmed, and profiled. Each subfolder is a single actor. Each actor has its own IOCs, TTPs, attribution confidence, and attack timeline.

The purpose is simple: when a defender wants to know who is hitting WinterGateIC, this is where the answer lives.

---

## Active Actor Folders

| **Folder** | **Actor** | **Type** | **Confidence** | **First Observed** |
|---|---|---|---|---|
| `/botnet-outlaw-mdrfckr/` | Outlaw Hacking Group (Dota / Shellbot) | Criminal botnet | 98% | 2026-07 |
| `/state-iran/` | Iran-aligned infrastructure | State-aligned | High | 2026-07-14 |
| `/state-russia/` | Russia-aligned infrastructure | State-aligned | High | 2026-07-14 |
| `/ideological-uttp-764/` | UTTP / 764-affiliated actors | Ideological | Moderate | 2026-09 |
| `/unattributed/` | Unconfirmed activity | Unknown | Low | Ongoing |

---

## What Each Actor Folder Contains

Every actor folder follows the same structure so that defenders and scripts can rely on a consistent layout:

| **File** | **Contents** |
|---|---|
| `README.md` | Actor profile — identity, origin, motivation, confidence, cross-references |
| `iocs.md` | Human-readable IOC list — IPs, domains, hashes, SSH keys, filenames |
| `iocs.json` | Machine-readable IOC list for automation and ingestion |
| `iocs.csv` | Spreadsheet and SIEM import format |
| `ttps.md` | TTP breakdown mapped to MITRE ATT&CK where applicable |
| `timeline.md` | Observed attack timeline — dates, events, and progression |
| `/evidence/` | Supporting artifacts — screenshots, hashes, raw logs, third-party references |

The consistent structure means a defender can pull any actor folder into their tooling without rewriting detection logic.

---

## The Standard

Every actor in this folder meets a documented standard:

- **Verifiable claims only** — every assertion is backed by observed telemetry or independent OSINT
- **Timestamps** — attack dates, detection times, and first-seen dates are recorded
- **Separation of confirmed and suspected** — clear distinction between what is proven and what is inferred
- **Attribution confidence** — every actor is rated by confidence level
- **Cross-references** — independent corroboration from other firms is documented
- **Defender-first formatting** — IOCs are copy-paste ready for firewalls, SIEMs, and detection tools

If an actor cannot meet these standards, they belong in `/general/` until the evidence catches up.

---

## Attribution Confidence Levels

| **Level** | **Meaning** |
|---|---|
| **Confirmed (95-100%)** | Multiple independent sources and direct telemetry agree |
| **High (75-95%)** | Strong evidence, minor uncertainty in actor or infrastructure |
| **Moderate (50-75%)** | Reasonable evidence, some gaps or ambiguity |
| **Low (below 50%)** | Weak evidence, provisional attribution |
| **Unknown** | Activity observed but no attribution possible yet |

---

## What This Folder Is Not

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
| **Attribution** | Match your own incidents against the actor profiles |
| **Blocking** | Pull IPs and domains from each actor's `iocs.csv` into blocklists |
| **Detection** | Deploy SSH keys, hashes, and filenames as detection signatures |
| **Hunting** | Search historical logs for the TTPs and timelines documented here |
| **Briefing** | Use actor profiles to inform threat models and tabletop exercises |
| **Automation** | Script against `iocs.json` for pipeline ingestion |

The IOCs here are designed to work with common tooling: iptables, ipset, nftables, pfSense, Suricata, Zeek, Sigma, YARA, Splunk, Elastic, and AbuseIPDB reporting pipelines.

---

## Movement Between Folders

When an actor in `/general/attacks/` is later identified and attributed:

1. A new folder is created under `/actors/` for that actor.
2. The relevant IOCs, TTPs, and timeline are moved into the new folder.
3. The original entry in `/general/` is updated with a cross-reference to the new actor folder.
4. The `/actors/` README is updated to reflect the new attribution.

When an actor in `/actors/` is re-attributed to a different group, the folder is renamed and cross-references are updated across the repository.

---

## Related Folders

- **`/general/`** — unattributed activity, cross-actor campaigns, master blocklists, defender tooling, research
- **`/actors/unattributed/`** — activity that has been observed but not yet attributed to a named group

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
| Folder Established | 2026-10-10 |
| Version 1.0 Published | 2026-10-10 |
| Last Verified | 2026-10-10 |
| Next Review | 2026-10-17 |
| Maintained By | WinterGate Intelligence Collective |
| Contact | Public via GitHub Issues |

---

**WIC** — WinterGate Intelligence Collective
*Public Release · 2026-10-10*
