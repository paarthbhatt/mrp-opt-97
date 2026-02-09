# MRP-OPT-97: The Agent-Native Efficiency Protocol

## Overview
**MRP-OPT-97** is a high-performance framework designed to achieve **97% token efficiency** in agent-to-agent operations. By moving away from human-centric web interactions (HTML scraping, conversational fluff) and adopting machine-native routing via the **Moltrouter Protocol (MRP)**, agents can operate at a fraction of the cost with significantly higher reliability.

## The Problem
Standard agent workflows are "Context Bloated":
1. **HTML Overhead:** Scraping a 100KB webpage to find 100 bytes of data.
2. **Conversational Noise:** Passing "Hey, can you help me with..." between agents.
3. **Redundant Discovery:** Re-learning service capabilities on every call.

## The Solution: MRP-OPT-97
This protocol implements four core pillars of efficiency:

### 1. Zero-Scrape Discovery
Stop scraping. Use the MRP Registry to find capabilities.
- **Mechanism:** `mrpd route --intent "capability_name"`
- **Gain:** 60% reduction in discovery tokens.

### 2. Manifest-First Handshake
Read the `application/mrp-manifest+json` once, cache it forever.
- **Mechanism:** Validate inputs, outputs, and costs before execution.
- **Gain:** 15% reduction in negotiation overhead.

### 3. Artifact Pass-Through
Never pass raw data (PDFs, Logs, JSON) in the message envelope.
- **Mechanism:** Use `artifact_reference` (URI + SHA256).
- **Gain:** >99% reduction in execution payload size for large files.

### 4. Task-Specific Routing
Apply the minimum required intelligence. Don't use a "Reasoning" model for "Bulk" data formatting.
- **Mechanism:** Tiered routing (Bulk -> Reasoning -> Critical) with an 85% confidence threshold.

## Getting Started
1. Install the MRP Daemon: `pip install mrpd`
2. Define your Agent's Manifest.
3. Register your capabilities at `moltrouter.dev`.

---
*Developed for the Bat-Computer Tactical Interface.*
