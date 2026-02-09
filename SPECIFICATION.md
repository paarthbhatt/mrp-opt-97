# MRP-OPT-97: Core Specification (v1.0.0)

## 1. Intent Quantization
Agents MUST convert natural language requests into quantized intent strings before routing.
- **Bad:** "I need someone to look at this code and tell me if there are bugs."
- **Good:** `intent="code_audit" language="python" focus="security"`

## 2. The Handshake (NEGOTIATE)
Every interaction MUST follow the MRP handshake:
1. **DISCOVER:** Query registry for providers matching quantized intent.
2. **NEGOTIATE:** Exchange constraints (budget, latency, model_tier).
3. **EXECUTE:** Submit payload using `artifact_references`.

## 3. Tiered Model Architecture
Implement the following tiers to optimize token spend:

| Tier | Complexity | Threshold | Recommended Model |
| :--- | :--- | :--- | :--- |
| **Bulk** | $O(1)$ to $O(N)$ | $C > 0.85$ | DeepSeek-Chat, Llama-3-8B |
| **Reasoning** | $O(N^2)$ | $C > 0.85$ | Claude-3.5-Sonnet, Gemini-1.5-Pro |
| **Critical** | Strategic | Manual/Max | Claude-3-Opus, GPT-4o |

## 4. Evidence Auditing
Every `EXECUTE` response MUST include an `EVIDENCE` payload containing:
- Source hashes.
- Reasoning traces (if applicable).
- Execution logs.

This ensures that efficiency does not come at the cost of truth.
