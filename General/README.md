# /general/

**General IOC and attack documentation — everything not tied to a single tracked actor.**

Master blocklists, unattributed activity, cross-actor campaigns, defender tooling, and analysis. The catch-all that keeps the archive honest.

---

**Repository:** WIC-IOC
**Folder:** /general/
**Maintained by:** WinterGate Intelligence Collective (WIC)
**Established:** 2026-10-10
**Last Updated:** 2026-10-10
**Version:** 1.0
**Status:** Active — continuously maintained
**Classification:** Public — Defender Use Authorized

---

## What This Folder Is

Not every attack belongs to a tracked actor. Not every IOC fits inside a single campaign. Not every piece of intelligence has a name attached to it yet.

This folder holds everything that falls outside the `/actors/` directory:

- **Unattributed activity** — attacks with no confirmed actor behind them
- **Cross-actor campaigns** — operations involving multiple groups
- **Master blocklists** — combined IOCs for defenders who just want to block everything
- **Defender tooling** — detection rules, scripts, and pipelines
- **Analysis and methodology** — how attribution is done, how evidence is verified, and what lessons were learned

It exists so the archive never has to force activity into an actor folder just to keep the tree clean.

---

## What Goes Where

| **Folder** | **Contents** |
|---|---|
| **`/iocs/`** | Master IOC lists — all IPs, domains, hashes, SSH keys, and filenames in one place |
| **`/attacks/`** | Individual attack reports not tied to a tracked actor — one-off events, unresolved incidents, unclassified activity |
| **`/campaigns/`** | Multi-actor campaigns, coordinated events, or activity spanning more than one group |
| **`/tools/`** | Defender tooling — Sigma rules, YARA rules, ipset scripts, Suricata rules, detection pipelines |
| **`/research/`** | Analysis, methodology, and background material — attribution frameworks, documentation standards, and lessons learned |

---

## The Standard

Everything in this folder meets the same standard as the rest of the archive:

- **Verifiable claims only** — every assertion is backed by observed telemetry or independent OSINT
- **Timestamps** — attack dates, detection times, and first-seen dates are recorded
- **Separation of confirmed and suspected** — clear distinction between what is proven and what is inferred
- **Attribution confidence** — any attribution includes a confidence level
- **Defender-first formatting** — IOCs are presented in copy-paste ready formats
- **Continuous updates** — the folder grows as new activity is observed

If a claim cannot meet these standards, it does not belong here.

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
| **Blocking** | Pull the master blocklists from `/iocs/` into firewalls, DNS sinkholes, and ipset |
| **Detection** | Deploy the Sigma and YARA rules from `/tools/` |
| **Hunting** | Search historical logs for unattributed patterns in `/attacks/` |
| **Briefing** | Use `/campaigns/` to understand multi-actor coordination |
| **Learning** | Read `/research/` for methodology, attribution standards, and lessons learned |

The IOCs here are designed to work with common tooling: iptables, ipset, nftables, pfSense, Suricata, Zeek, Sigma, YARA, Splunk, Elastic, and AbuseIPDB reporting pipelines.

---

## Relationship to /actors/

The `/actors/` folder is for **identified groups** — named, attributed, and profiled.

This `/general/` folder is for **everything else** — activity that is unattributed, spans multiple groups, or doesn't fit the actor model.

When an actor in `/general/attacks/` is later identified and attributed, the entry is moved to the appropriate folder under `/actors/`, and the general entry is updated with a cross-reference.

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
