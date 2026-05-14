<div align="center">

<img src="https://raw.githubusercontent.com/AutomataNexus/assets/main/logos/automatanexus/AutomataNexus_Logo.png" alt="AutomataNexus" width="420" onerror="this.style.display='none'" />

# AutomataNexus

**The $468 AI-powered HVAC controller that replaces $5,000 Trane/Siemens systems.**
**60+ deployed. 16 facilities. Hailo NPU acceleration. Pure Rust, edge to cloud.**

[![Rust](https://img.shields.io/badge/built%20with-Rust-orange.svg?logo=rust)](https://www.rust-lang.org)
[![Projects](https://img.shields.io/badge/projects-50%2B-14b8a6.svg)](#product-families)
[![Edge](https://img.shields.io/badge/target-edge%20%26%20on--prem-14b8a6.svg)](#)
[![Controllers](https://img.shields.io/badge/fleet-60%2B%20controllers-2d2a26.svg)](#nexusedge--on-prem-hvac-controllers)
[![Sites](https://img.shields.io/badge/sites-16%20production-2d2a26.svg)](#nexusedge--on-prem-hvac-controllers)
[![SLSA Level 3](https://img.shields.io/badge/SLSA-Level%203-3f51b5.svg)](https://slsa.dev/spec/v1.0/levels#build-l3)
[![ORCID](https://img.shields.io/badge/ORCID-0009--0005--2158--7060-A6CE39.svg?logo=orcid)](https://orcid.org/0009-0005-2158-7060)
[![Website](https://img.shields.io/badge/web-automatanexus.com-14b8a6.svg)](https://automatanexus.com)
[![NexusEdge](https://img.shields.io/badge/NexusEdge-Hailo%20Community-00A8A8.svg)](https://nexusedgehailo.automatanexus.com)

</div>

---

### Featured In

<table>
<tr>
<td align="center" width="33%">
<a href="https://www.influxdata.com/resources/influxdb-3-hackathon-winner-behind-the-scenes-of-nexus-bms-for-smart/"><strong>InfluxDB Hackathon Winner</strong></a><br><em>Behind the Scenes of Nexus BMS for Smart Buildings</em>
</td>
<td align="center" width="33%">
<a href="https://hailo.ai/success-stories/automata-nexus/"><strong>Hailo AI Case Study</strong></a><br><em>AI-Enhanced Building Management with Hailo-8 NPU</em>
</td>
<td align="center" width="33%">
<a href="https://dev.to/automatanexus/axonml-a-pytorch-equivalent-ml-framework-written-in-rust-328a"><strong>DEV Community</strong></a><br><em>AxonML: PyTorch-equivalent ML framework in Rust</em>
</td>
</tr>
</table>

---

## What we build

AutomataNexus designs and ships pure-Rust infrastructure for **HVAC controls, industrial monitoring, and edge AI**. We replace heterogeneous legacy stacks (Node-RED, Python micro-services, off-the-shelf BMS appliances, vendor-locked NPU toolchains) with a coherent, auditable, performance-first Rust ecosystem that runs on a Raspberry Pi at the edge or scales to a multi-tenant SaaS.

We've shipped **50+ projects** across eight product families, deployed across our own production HVAC controller fleet at **16 customer sites** with **60+ controllers** under management, with thousands of telemetry points flowing into our database every second.

---

## Product Families

### NexusEdge — On-prem HVAC controllers

[![NexusEdge](https://img.shields.io/badge/NexusEdge-HailoCommunity-14b8a6.svg?logo=github)](https://github.com/AutomataNexus/NexusEdge-HailoCommunity)
[![Talos](https://img.shields.io/badge/Talos-hardware%20daemon-475569.svg?logo=github)](https://github.com/AutomataNexus/Talos)
[![Controllers](https://img.shields.io/badge/fleet-60%2B%20controllers-success.svg)](#)
[![Sites](https://img.shields.io/badge/sites-16%20production-success.svg)](#)
[![Hailo](https://img.shields.io/badge/NPU-Hailo--8%20%7C%20Hailo--10H-blue.svg)](#)

Rust controller firmware running on Raspberry Pi 5 with NVMe + Hailo-8/10H NPU acceleration. Talks to Sequent Microsystems I/O HAT stacks (MegaBAS, MegaIND, Univin16, Uout16, Relind16, Relind8) over I2C. Drives building-system equipment -- AHUs, RTUs, chillers, boilers, DOAS units, mixing valves, lead/lag pumps -- across 16 production sites. Runtime-gated AN26 HMAC-SHA256 licensing.

- **Talos** -- Rust I2C hardware daemon, the ground-truth bridge between the controller and physical I/O. 22 concrete control algorithms (TMC, PID, cascade, lead/lag, and 18 more).
- **NexusConfigurator** -- Tauri 2 desktop app that commissions, configures, deploys, and monitors the controller fleet.
- **NexusBMS** -- Fleet command bus + customer-facing dashboards for setpoints, schedules, and incident updates.

### Aegis-DB -- Multi-paradigm distributed database

[![Aegis-DB](https://img.shields.io/github/stars/AutomataNexus/Aegis-DB?style=flat&logo=github&label=stars)](https://github.com/AutomataNexus/Aegis-DB)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](https://github.com/AutomataNexus/Aegis-DB/blob/main/LICENSE)
[![Rust](https://img.shields.io/badge/lang-Rust-orange.svg?logo=rust)](#)
[![Paradigms](https://img.shields.io/badge/paradigms-6-14b8a6.svg)](#)

A single Rust binary that speaks **SQL, Document, Graph, Key-Value, Time-Series, and Streaming** workloads. Powers our HVAC telemetry storage at the edge and our SaaS at the core. ACID, horizontal scale, zero-dependency.

### AxonML -- PyTorch-equivalent ML framework, pure Rust

[![AxonML](https://img.shields.io/github/stars/AutomataNexus/AxonML?style=flat&logo=github&label=stars)](https://github.com/AutomataNexus/AxonML)
[![License](https://img.shields.io/badge/license-MIT%20%7C%20Apache--2.0-blue.svg)](https://github.com/AutomataNexus/AxonML/blob/main/LICENSE)
[![Crates](https://img.shields.io/badge/crates-22-orange.svg?logo=rust)](#)
[![Tests](https://img.shields.io/badge/tests-2%2C285%20passing-success.svg)](#)
[![LoC](https://img.shields.io/badge/LoC-226%2C373-informational.svg)](#)
[![CUDA](https://img.shields.io/badge/CUDA-15%20PTX%20kernels-76b900.svg?logo=nvidia)](#)
[![LLMs](https://img.shields.io/badge/LLM%20archs-9-purple.svg)](#)
[![NN Layers](https://img.shields.io/badge/NN%20layers-41-purple.svg)](#)

22 crates, **226K+ lines of Rust**, ~92-95% PyTorch parity with several novel features that go *beyond* PyTorch. Trains on CUDA with 15 custom PTX kernel modules. 9 LLM architectures (GPT-2, LLaMA, Mistral, Phi, BERT, SSM/Mamba, Hydra, Trident, Chimera). 41 NN layer types. 6 quantization formats including 1.58-bit ternary. Distributed training (DDP, FSDP, pipeline parallelism). ONNX import/export with 39 operators.

- **NexusSentinel** [![NexusSentinel](https://img.shields.io/badge/NexusSentinel-edge%20ML-14b8a6.svg?logo=github)](https://github.com/AutomataNexus/NexusSentinel) -- Facility health assessment. ~15K-param MLP autoencoder + severity classifier, SLSA Level 3.
- **NexusWatch** [![NexusWatch](https://img.shields.io/badge/NexusWatch-vision-14b8a6.svg?logo=github)](https://github.com/AutomataNexus/NexusWatch) -- Edge computer vision. YOLOv8 + custom architectures on Hailo NPU.

### NexusOracle -- AI-powered HVAC diagnostics

[![NexusOracle](https://img.shields.io/badge/NexusOracle-AI%20assistant-purple.svg?logo=github)](https://github.com/AutomataNexus/NexusOracle)
[![Backends](https://img.shields.io/badge/backends-nexus--serve%20%7C%20Gemini%20%7C%20Claude-purple.svg)](#)

AI diagnostic assistant for the NexusEdge controller fleet. Terminal chat TUI, daemon API, mobile app, tech field guide. Connects to controllers via SSH, reads live sensor data, diagnoses faults, suggests fixes. Powered by nexus-serve (local) with cloud fallback.

### Ferrum -- Transactional email platform

[![FerrumEmail](https://img.shields.io/github/stars/AutomataNexus/FerrumEmail?style=flat&logo=github&label=stars)](https://github.com/AutomataNexus/FerrumEmail)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](https://github.com/AutomataNexus/FerrumEmail/blob/main/LICENSE)
[![Live](https://img.shields.io/badge/SaaS-ferrum--mail.com-e07a5f.svg)](https://ferrum-mail.com)
[![Crates](https://img.shields.io/badge/crates.io-9%20crates-orange.svg?logo=rust)](#)

The full email stack in Rust. **FerrumEmail** is the React-Email equivalent for Rust -- type-safe component templates, cross-client rendering, unified sending API. **FerrumMailSaaS** is the hosted transactional email platform (live at ferrum-mail.com). **FerrumMailbox** is the self-hosted SMTP server + mailbox + REST API. **FerrumMailMobile** is the cross-platform email client.

### NexusShield + NexusProbe + NexusGauntlet + NexusCure -- Security platform

[![NexusShield](https://img.shields.io/badge/NexusShield-zero%20trust-c0582b.svg?logo=github)](https://github.com/AutomataNexus/NexusShield)
[![Modules](https://img.shields.io/badge/modules-24-c0582b.svg)](#)
[![Tests](https://img.shields.io/badge/tests-275-success.svg)](#)
[![Footprint](https://img.shields.io/badge/footprint-%3C5%20MB-informational.svg)](#)

- **NexusShield** -- Adaptive zero-trust gateway + real-time endpoint protection. 24 modules, 275 tests, <5 MB footprint.
- **NexusVault** -- Zero-dependency secrets management. Built into Aegis-DB.
- **NexusProbe + NexusGauntlet** -- Application security testing. Authenticated sessions, smart contracts, business logic, race conditions, crypto attacks, mobile RE.
- **NexusCure** -- Automated remediation. Consumes findings from Shield/Probe, plans and executes targeted fixes. Surgical, auditable, reversible.

### NexusStratum -- UI component system for Rust

[![NexusStratum](https://img.shields.io/github/stars/AutomataNexus/NexusStratum?style=flat&logo=github&label=stars)](https://github.com/AutomataNexus/NexusStratum)
[![Rust](https://img.shields.io/badge/lang-Rust-orange.svg?logo=rust)](#)
[![Frameworks](https://img.shields.io/badge/adapters-Leptos%20%7C%20Dioxus-14b8a6.svg)](#)

Complete UI component system for Rust. Headless primitives, styled components, and framework adapters for Leptos and Dioxus. Powers the NexusBMS and NexusConfigurator dashboards.

### Penumbra -- 3D rendering SDK

[![Penumbra](https://img.shields.io/badge/Penumbra-3D%20rendering-475569.svg?logo=github)](https://github.com/AutomataNexus/Penumbra)
[![Rust](https://img.shields.io/badge/lang-Rust-orange.svg?logo=rust)](#)
[![WASM](https://img.shields.io/badge/target-native%20%7C%20WASM-blue.svg)](#)

General-purpose 3D rendering SDK for Rust. PBR, instanced entities, satellite tile streaming, atmosphere, post-processing, WASM target.

### NexusFlight -- Open-source FPV drone stack

[![NexusFlight](https://img.shields.io/badge/NexusFlight-flight%20controller-475569.svg?logo=github)](https://github.com/AutomataNexus/NexusFlight)
[![NexusCoreDrive](https://img.shields.io/badge/NexusCoreDrive-ESC%20firmware-475569.svg?logo=github)](https://github.com/AutomataNexus/NexusCoreDrive)
[![MCUs](https://img.shields.io/badge/MCU%20families-4-informational.svg)](#)
[![Boards](https://img.shields.io/badge/board%20targets-220-informational.svg)](#)

- **NexusFlight** -- Rust flight controller firmware + ground station.
- **NexusCoreDrive** -- Rust `no_std` ESC firmware with Field Oriented Control. 4 MCU families, 220 board targets, AM32-compatible bootloader.
- **NexusFlight-Suite** -- Desktop configurator for the firmware family.

### NexusPulse -- SMS / messaging / tactical SA

[![NexusPulse](https://img.shields.io/badge/NexusPulse-messaging-475569.svg?logo=github)](https://github.com/AutomataNexus/NexusPulse)
[![Carriers](https://img.shields.io/badge/carriers-7%20backends-informational.svg)](#)
[![E2E](https://img.shields.io/badge/encryption-Signal%20protocol-success.svg)](#)

- **NexusPulse** -- Self-hosted, provider-agnostic SMS notification service. Pure Rust, 7 carrier backends, Aegis-DB persistence.
- **NexusPulse-Mobile** -- E2E encrypted messaging app, Signal-protocol security, SMS fallback.
- **NexusPulse-Tactical** -- Tactical situational awareness -- satellite maps, E2E encrypted comms, Meshtastic mesh, SMS fallback.
- **NexusPulse-Tactical-Mobile** -- Cross-platform tactical SA app, LoRa mesh, offline-first.

### NexusCompress -- Structured-data compression

[![NexusCompress](https://img.shields.io/badge/NexusCompress-compression-475569.svg?logo=github)](https://github.com/AutomataNexus/NexusCompress)
[![Rust](https://img.shields.io/badge/lang-Rust-orange.svg?logo=rust)](#)

Pure Rust compression framework. Format-aware lossless compression with derive macros, online adaptive training, purpose-built pipelines for time-series, tensors, records, logs, and text. Beats zstd and OpenZL on structured data.

### Other infrastructure

- **ISO 10816 Vibration Sensor** [![ISO](https://img.shields.io/badge/ISO%2010816-vibration-475569.svg?logo=github)](https://github.com/AutomataNexus/IS0-10816-Vibration-Sensor) -- Enterprise vibration monitoring. Up to 32 sensors, real-time analysis, multi-zone severity classification.
- **NexusScribe** -- AI transcription platform.
- **firebase-client-sdk** [![firebase](https://img.shields.io/badge/firebase--client--sdk-Rust-orange.svg?logo=github)](https://github.com/AutomataNexus/firebase-client-sdk) -- Pure Rust Firebase client SDK (no service account keys on edge devices).

---

## Engineering principles

1. **One language, end to end.** Rust from the I2C bus up through the controller, the database, the ML framework, the email stack, the desktop app, and the SaaS. We treat language sprawl as a liability.
2. **Pure-Rust dependencies wherever possible.** No OpenSSH dependency in our SSH client (russh). No CPython runtime on edge controllers. No vendor SDKs we can replace with native Rust (NexusFoundry replaces Hailo DFC). When we can write it in Rust, we do.
3. **Edge-first, internet-optional.** Controllers operate fully offline. SaaS is supplemental, not the source of truth. The on-prem `fleet.toml` is canonical.
4. **No telemetry by default.** Operator-side software does not phone home. Outbound calls are operator-initiated and target operator-configured endpoints.
5. **Auditable supply chain.** Every release ships with SLSA Level 3 provenance, SHA-256 manifests, and reproducible builds. Authenticode-signed installers for Windows.
6. **Owner-operator deployable.** Every product runs end-to-end on commodity hardware (Raspberry Pi, NVIDIA workstation, Windows laptop). No cloud lock-in. Customer-deployable as readily as SaaS.

---

## Current focus

- Hardening the **NexusEdge** controller fleet across 16 production sites and 60+ controllers.
- **RustyMythos** -- training a Recurrent-Depth Transformer (RDT) from scratch in AxonML. Adaptive test-time compute, MoE routing, edge NPU deployment via NexusFoundry.
- **nexus-serve** -- pure-Rust LLM inference. 9 architectures, 35+ tok/s on RTX 5070, CUDA + Hailo NPU backends.
- **NexusFoundry** -- reproducible HEF compilation for Hailo NPU. Silicon-proven on H8 + H10.
- **NexusGauntlet** -- authenticated app-sec testing platform.
- Shipping **NexusFlight** open-source FPV stack.

---

## Get in touch

**Andrew Jewell, Sr.** -- Founder / AI Systems Engineer
**ORCID** [`0009-0005-2158-7060`](https://orcid.org/0009-0005-2158-7060)
Email: [`andrew.jewellsr@automatanexus.com`](mailto:andrew.jewellsr@automatanexus.com) | DevOps: [`devops@automatanexus.com`](mailto:devops@automatanexus.com)

We collaborate with HVAC technicians, controls engineers, Rust systems programmers, and ML researchers who like working at the intersection of physical systems and software. If that's you, send an email.

For commercial licensing of any of our proprietary products, see the project's `COMMERCIAL.md`.

For the **NexusEdge Community Edition** (open-source, Apache 2.0), see [NexusEdge-HailoCommunity](https://github.com/AutomataNexus/NexusEdge-HailoCommunity).

---

<div align="center">

*Some of our work is open source. Some is not. We document the difference clearly in every repo's `LICENSE.md`.*

**© 2026 AutomataNexus, LLC.** Indiana, USA.

</div>
