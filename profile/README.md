<div align="center">

<img src="https://raw.githubusercontent.com/AutomataNexus/assets/main/logos/automatanexus/AutomataNexus_Logo.png" alt="AutomataNexus" width="420" onerror="this.style.display='none'" />

# AutomataNexus

**Pure-Rust infrastructure for industrial controls, edge ML, and the systems that run them.**

[![Rust](https://img.shields.io/badge/built%20with-Rust-orange.svg?logo=rust)](https://www.rust-lang.org)
[![Edge](https://img.shields.io/badge/target-edge%20%26%20on--prem-14b8a6.svg)](#)
[![SLSA Level 3](https://img.shields.io/badge/SLSA-Level%203-3f51b5.svg)](https://slsa.dev/spec/v1.0/levels#build-l3)
[![Sponsor](https://img.shields.io/badge/sponsor-andrew.jewellsr%40automatanexus.com-pink.svg)](mailto:andrew.jewellsr@automatanexus.com)

</div>

---

## What we build

AutomataNexus designs and ships pure-Rust infrastructure for **HVAC controls, industrial monitoring, and edge AI**. We replace heterogeneous legacy stacks (Node-RED, Python micro-services, off-the-shelf BMS appliances, vendor-locked NPU toolchains) with a coherent, auditable, performance-first Rust ecosystem that runs on a Raspberry Pi at the edge or scales to a multi-tenant SaaS.

We've shipped **30+ projects** across six product families, deployed across our own production HVAC controller fleet at a dozen customer sites, with thousands of telemetry points flowing into our database every second.

---

## Product Families

### NexusEdge — On-prem HVAC controllers

Tauri/Rust controller firmware running on Raspberry Pi 5 with NVMe + Hailo-8 NPU acceleration. Talks to Sequent Microsystems I/O HAT stacks (MegaBAS, MegaIND, Univin16, Uout16, Relind16, Relind8) over I²C. Drives building-system equipment — AHUs, RTUs, chillers, boilers, DOAS units, mixing valves, lead/lag pumps — across over a dozen production sites.

- **Talos** — Rust I²C hardware daemon, the ground-truth bridge between the controller and physical I/O.
- **NexusConfigurator** — Tauri 2 desktop app that commissions, configures, deploys, and monitors the controller fleet from any operator laptop.
- **NexusBMS** — Fleet command bus + customer-facing dashboards for setpoints, schedules, and incident updates.

### Aegis-DB — Multi-paradigm distributed database

[![Aegis-DB stars](https://img.shields.io/github/stars/AutomataNexus/Aegis-DB?style=flat&logo=github)](https://github.com/AutomataNexus/Aegis-DB)

A single Rust binary that speaks **SQL, Document, Graph, Key-Value, Time-Series, and Streaming** workloads. Powers our HVAC telemetry storage at the edge and our SaaS at the core. ACID, horizontal scale, zero-dependency.

### AxonML — PyTorch-equivalent ML framework, pure Rust

[![AxonML stars](https://img.shields.io/github/stars/AutomataNexus/AxonML?style=flat&logo=github)](https://github.com/AutomataNexus/AxonML) [![AxonML downloads](https://img.shields.io/crates/d/axonml?logo=rust)](https://crates.io/crates/axonml)

22 crates, **2,180+ passing tests**, ~92–95% PyTorch parity with several novel features that go *beyond* PyTorch. Trains on CUDA. Targets edge inference on Hailo NPU and CPU fallback. Used internally for biometrics (Aegis Identity), object detection (Nexus / Phantom / NightVision), HVAC anomaly autoencoders (NexusSentinel), and 1.58-bit LLM research (Trident).

- **NexusFoundry** — Pure Rust compiler for Hailo NPU hardware. Compiles ONNX / TFLite / AxonML models to HEF for Hailo-8, 8L, 10H. Replaces the official Hailo DFC toolchain.
- **NexusSentinel** — Facility health assessment for edge deployment. ~15K-param MLP autoencoder + severity classifier, real-time monitoring, SLSA Level 3.
- **Prometheus** — AI-powered edge ML training orchestrator. 13 neural network architectures, DigitalOcean Gradient AI agent, ONNX/HEF conversion, edge deployment.

### Ferrum — Transactional email + mailbox + mobile

The full email stack in Rust. **FerrumEmail** is the React-Email equivalent for Rust — type-safe templates, cross-client rendering. **FerrumMailSaaS** is our hosted SaaS. **FerrumMailbox** is our self-hosted mail server. **FerrumMailMobile** is the cross-platform client.

### NexusShield + NexusProbe + NexusGauntlet + NexusCure — Security platform

- **NexusShield** — Adaptive zero-trust gateway + real-time endpoint protection. 24 modules, 275 tests, <5 MB footprint.
- **NexusVault** — Zero-dependency secrets management. Built into Aegis-DB.
- **NexusProbe + NexusGauntlet** — Application security testing. Authenticated sessions, smart contracts, business logic, race conditions, crypto attacks, mobile RE.
- **NexusCure** — Automated remediation. Consumes findings from Shield/Probe, plans and executes targeted fixes. Surgical, auditable, reversible.

### NexusFlight — Open-source FPV drone stack

- **NexusFlight** — Rust flight controller firmware + ground station.
- **NexusCoreDrive** — Rust `no_std` ESC firmware with Field Oriented Control. 4 MCU families, 220 board targets, AM32-compatible bootloader.
- **NexusFlight-Suite** — Desktop configurator for the firmware family.

### NexusPulse — SMS / messaging / tactical SA

- **NexusPulse** — Self-hosted, provider-agnostic SMS notification service. Pure Rust, 7 carrier backends, Aegis-DB persistence.
- **NexusPulse-Mobile** — E2E encrypted messaging app, Signal-protocol security, SMS fallback.
- **NexusPulse-Tactical** — Tactical situational awareness — satellite maps, E2E encrypted comms, Meshtastic mesh, SMS fallback.
- **NexusPulse-Tactical-Mobile** — Cross-platform tactical SA app, LoRa mesh, offline-first.

### NexusCompress — Structured-data compression

Pure Rust compression framework. Format-aware lossless compression with derive macros, online adaptive training, purpose-built pipelines for time-series, tensors, records, logs, and text. Beats zstd and OpenZL on structured data.

### Other infrastructure

- **ISO 10816 Vibration Sensor platform** — Enterprise vibration monitoring for industrial equipment. Up to 32 WTVB01-485 sensors, real-time analysis, multi-zone severity classification, REST API + Node-RED + dashboard. Built for motors, pumps, fans, rotating machinery.
- **NexusScribe** — AI transcription platform.
- **NexusFlight + ISO sensors** integrate with our HVAC fleet for pump/fan health monitoring.

---

## Engineering principles

1. **One language, end to end.** Rust from the I²C bus up through the controller, the database, the ML framework, the email stack, the desktop app, and the SaaS. We treat language sprawl as a liability.
2. **Pure-Rust dependencies wherever possible.** No OpenSSH dependency in our SSH client (russh). No CPython runtime on edge controllers. No vendor SDKs we can replace with native Rust (NexusFoundry replaces Hailo DFC). When we can write it in Rust, we do.
3. **Edge-first, internet-optional.** Controllers operate fully offline. SaaS is supplemental, not the source of truth. The on-prem `fleet.toml` is canonical.
4. **No telemetry by default.** Operator-side software does not phone home. Outbound calls are operator-initiated and target operator-configured endpoints.
5. **Auditable supply chain.** Every release ships with SLSA Level 3 provenance, SHA-256 manifests, and reproducible builds. Authenticode-signed installers for Windows.
6. **Owner-operator deployable.** Every product runs end-to-end on commodity hardware (Raspberry Pi, NVIDIA workstation, Windows laptop). No cloud lock-in. Customer-deployable as readily as SaaS.

---

## Current focus

- Hardening the NexusEdge controller fleet across 14 production sites and ~50 controllers under management.
- Shipping **NexusFlight** open-source FPV stack.
- Continued AxonML work — training-perf hot path (fused CUDA kernels), 1.58-bit LLM (Trident), edge inference parity.
- NexusFoundry → reproducible HEF compilation pipeline for Hailo NPU.
- NexusGauntlet authenticated app-sec testing.

---

## Get in touch

**Andrew Jewell, Sr.** — Founder / AI Systems Engineer
**ORCID** [`0009-0005-2158-7060`](https://orcid.org/0009-0005-2158-7060)
Email: [`andrew.jewellsr@automatanexus.com`](mailto:andrew.jewellsr@automatanexus.com) · DevOps: [`devops@automatanexus.com`](mailto:devops@automatanexus.com)

We hire HVAC technicians, controls engineers, Rust systems programmers, and ML researchers who like working at the intersection of physical systems and software. If that's you, send an email.

For commercial licensing of any of our proprietary products, see the project's `COMMERCIAL.md`.

---

<div align="center">

*Some of our work is open source. Some is not. We document the difference clearly in every repo's `LICENSE.md`.*

**© 2026 AutomataNexus, LLC.** Indiana, USA.

</div>
