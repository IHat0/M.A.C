# M.A.C. (Multi-Agent Cognition) Framework
**The Real-Time, Neuro-Symbolic Operating System for Embodied AI Agents.**  
*Created by [Pulsate Labs](https://pulsatelabs.co.za)*

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Website: Live](https://img.shields.io/badge/Website-Pulsate_Labs-ff6b00.svg)](https://pulsatelabs.co.za)
[![Architecture: Neuro-Symbolic](https://img.shields.io/badge/Architecture-Neuro--Symbolic-purple.svg)]()

---

## 🌐 Overview

**M.A.C.** is an end-to-end, open-source cognitive architecture designed to solve the three fatal bottlenecks of embodied AI in dynamic 3D environments: **Latency, Context Bloat, and Execution Hallucinations.**

While traditional AI agents rely on slow, probabilistic natural language generation, M.A.C. utilizes a neuro-symbolic framework. It decouples high-level LLM reasoning from low-level physical reflexes, allowing agents to navigate complex 3D worlds, maintain infinite memory persistence, and react to physical threats in under 10 milliseconds using consumer-grade hardware.

This repository serves as the central hub and research archive for the M.A.C. ecosystem. 

---

## 🏗️ The Ecosystem (The Three Pillars)

The M.A.C. framework is highly modular. The core engine is divided into three specialized, open-source infrastructure pillars. 

**Explore the individual repositories below:**

### [Pillar 1: M.A.C. Control Language (MAC-L) & Spinal Cord](https://github.com/IHat0/macl-codec)
*The Translator & Reflex Engine.*
Replaces verbose natural language with a strict, token-efficient Domain-Specific Language (DSL). Features an asynchronous "Spinal Cord" interrupt loop that intercepts environmental threats and executes deterministic survival reflexes in `~0.01ms`—bypassing the LLM entirely for safety-critical actions.

### [Pillar 2: Spatial GraphRAG & "Déjà Vu" Seed System](https://github.com/IHat0/spacial-graghrag)
*The Topological Navigation Engine.*
Bypasses heavy computer vision models by translating 3D worlds into lightweight hierarchical graph databases. Allows agents to query massive maps in `<1.2ms`, mutate broken paths in `11µs`, and inject navigation context into the LLM payload using fewer than 20 tokens.

### [Pillar 3: Tri-Partite Memory & Asynchronous Sleep](https://github.com/IHat0/tri-partite-memory)
*The Infinite-Persistence Database.*
Splits memory into Episodic, Semantic, and Spatial stores. Features an automated "Sleep Consolidation" compiler that compresses daily raw sensory logs by `>96%`. Guarantees 100% retention of critical survival facts while maintaining a perfectly flat active context window of `~183 tokens` over thousands of operational days.

### [The Brain: `macl-codec-8b-instruct`](https://github.com/IHat0/macl-codec-8b-instruct)
*The Native Speaker.*
Our proprietary, fine-tuned `Llama-3.1-8B` model. Quantized to 4-bit GGUF (4.6GB) for fast local inference. It natively translates dense, space-delimited state observations into valid MAC-L opcodes with zero syntax hallucinations.

---

## 📄 Research & Documentation

This repository archives the foundational research, technical validation reports, and architecture blueprints for the M.A.C. Framework. 

*   [**Positioning & Synthesis Paper (PDF)**](https://github.com/IHat0/M.A.C/blob/main/MAC_Research_Paper.pdf) - Architectural framing, comparison against flat-context/RAG systems, and the epistemic discipline behind the M.A.C. design.
*   [**Technical Evaluation Report (PDF)**](https://github.com/IHat0/M.A.C/blob/main/MAC_Technical_Report.pdf) - Proof-of-concept validation of the JARVIS cognitive loop, RCON polling stability, and end-to-end WebSocket integration.

---

## 🎯 The Universal Environment Adapter

M.A.C. is environment-agnostic. While our current simulation benchmarks are run inside Minecraft (serving as an ideal, rigorous 3D physics sandbox), the framework is designed around an **Environment Adapter** abstraction. 

By simply replacing the translation adapter, the M.A.C. cognitive loop and MAC-L opcodes can be plugged directly into physical robotics, digital twin city simulations, or alternative game engines (Unreal/Unity) without retraining the core logic.

---
### 🗺️ System Architecture Diagram

```mermaid
flowchart TD
    %% Define Styles
    classDef env fill:#1c1c1c,stroke:#555,stroke-width:1px,color:#fff
    classDef adapter fill:#2c3e50,stroke:#2980b9,stroke-width:2px,color:#fff
    classDef memory fill:#0e2f1d,stroke:#27ae60,stroke-width:2px,color:#fff
    classDef brain fill:#3a1c42,stroke:#8e44ad,stroke-width:2px,color:#fff
    classDef reflex fill:#641e16,stroke:#e74c3c,stroke-width:2px,color:#fff

    subgraph Environment ["🎮 3D Environment (Minecraft / Node.js)"]
        World["Minecraft Server"] <--> Bot["Mineflayer Bridge"]
    end

    subgraph Orchestrator ["⚙️ M.A.C. Orchestrator (Python)"]
        State["State Processor (8-Slot Codec)"]
        SpinalCord{"Pillar 1: L0/L1 Spinal Cord"}
        Interpreter["MAC-L Interpreter & Parser"]
        Sleep["Asynchronous Sleep Compiler"]
    end

    subgraph Memory ["💾 Persistent Stores (Pillars 2 & 3)"]
        P2["Spatial GraphRAG (Map)"]
        P3_E["Episodic Cache (Diary)"]
        P3_S["Semantic Store (Rules)"]
    end

    subgraph Brain ["🧠 Inference Engine"]
        LLM["Pulsate-8B-Instruct (Local GGUF)"]
    end

    %% Real-Time Loop Flow
    Bot -->|Raw Stream 50ms| State
    State --> SpinalCord
    
    %% The Reflex Path
    SpinalCord -->|🚨 L0 THREAT! <10ms| Interpreter
    
    %% The Cognitive Path
    SpinalCord -->|Safe Context| P3_E
    P2 -.->|Spatial Payload| LLM
    P3_S -.->|Semantic Payload| LLM
    P3_E -.->|Episodic Payload| LLM
    
    LLM -->|Outputs MAC-L Codec| Interpreter
    Interpreter -->|Physical Action| Bot

    %% Nightly Sleep Loop Flow
    Sleep -.->|Reads & Purges| P3_E
    Sleep -.->|Writes New Facts| P3_S
    Sleep -.->|Mutates Topology| P2
    
    %% Apply Classes
    class World,Bot env;
    class State,Interpreter,Sleep adapter;
    class P2,P3_E,P3_S memory;
    class LLM brain;
    class SpinalCord reflex;
```
---

## 🏢 About Pulsate Labs

M.A.C. is developed and maintained by **Pulsate Labs Pty Ltd**. We are building the infrastructure for long-horizon autonomous agency. 

For enterprise integration, grant reviews, or academic research partnerships, visit [pulsatelabs.co.za](https://pulsatelabs.co.za) or contact us at `info@pulsatelabs.co.za`.

---
*M.A.C. Framework is released under the Apache License 2.0.*
