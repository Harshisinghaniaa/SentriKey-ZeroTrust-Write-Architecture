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
