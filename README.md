# SentriKey – Hardware-Enforced Zero-Trust Write Architecture

AMD Slingshot Hackathon Submission  
AI + Cybersecurity and Privacy

## Overview

SentriKey is a ransomware risk-reduction architecture that redefines how write access is granted and monitored. 

Traditional systems allow persistent write permissions once authentication succeeds. SentriKey introduces hardware-gated, time-bound, and behavior-monitored write sessions to significantly reduce the feasibility of mass encryption attacks.

---

## Problem Statement

Ransomware primarily exploits persistent write access. 
Once attackers obtain valid credentials, they can execute uncontrolled file encryption.

Software-only defenses detect attacks after they begin. 
SentriKey focuses on controlling the write primitive itself.

---

## Core Concept

- Read-only mode by default
- Hardware-validated write activation
- Time-bound session tokens
- Behavioral anomaly detection (entropy spikes, bulk rename detection)
- Automatic write revocation
- Snapshot-based recovery
- Zero-trust VPN session binding

---

## Architecture

The system consists of:

1. Hardware Layer (Security Key)
2. Access Control Layer
3. Monitoring Engine
4. Snapshot & Recovery Layer
5. Network Validation Layer

---

## Technology Stack

- Python (behavioral monitoring prototype)
- File system activity monitoring
- Entropy-based anomaly detection
- Time-limited session control
- Snapshot recovery modeling
- Designed for scalable deployment on AMD Ryzen / EPYC processors

---

## AMD Alignment

The architecture is designed to align with:
- AMD Ryzen / EPYC compute scalability
- AMD Secure Processor (future root-of-trust integration)
- AMD AI acceleration stack for low-latency inference

---

## Status

This repository demonstrates architectural modeling and prototype logic for hackathon submission under AMD Slingshot – AI + Cybersecurity and Privacy.

---

## Tagline

Write Nothing. Trust Everything.


## Security Considerations
If ransomware gains admin privileges on the OS, what prevents it from bypassing your write gate or disabling your monitoring engine?”

SentriKey is designed with layered enforcement. Even if the OS is compromised, write activation requires hardware validation and time-bound session control. The monitoring engine operates alongside write-session logic rather than as a separate optional service. While no system can claim absolute immunity, the architecture significantly reduces attack feasibility by removing persistent write access as a default state.

Behavioral anomaly detection can cause false positives. What happens if your system wrongly revokes write access during legitimate high-volume operations?”

The anomaly detection layer is threshold-based and tuned for abnormal entropy spikes and rapid bulk renaming patterns typical of encryption behavior. In enterprise deployments, thresholds can be calibrated per environment. In case of false positives, the system only revokes the time-bound write session not system access and allows re-authentication. The design prioritizes containment while minimizing operational disruption.

Why can’t this be implemented purely in software without hardware?”

Software-only systems enforce policies within the same execution layer that ransomware can compromise. By introducing hardware-gated activation, we create a physical dependency for write privilege escalation. This increases the attack cost significantly and reduces reliance on credential-based trust alone. Hardware acts as an additional root of verification rather than a replacement for software controls.
