# MRP-OPT-97: Failover & Quota Management Spec

## 1. Monitoring
Agents MUST periodically poll their usage quotas. In OpenClaw, this is handled via the `session_status` tool.

## 2. Thresholds
To prevent mission interruption (429 errors), define two levels of gating:
- **Alert:** Notify the operator when capacity is < 20%.
- **Failover:** Automatically switch to a secondary provider when capacity is < 10%.

## 3. Provider Mapping
Every primary capability should have a pre-configured backup provider.

| Capability | Primary (Example) | Backup (Example) |
| :--- | :--- | :--- |
| Reasoning | `antigravity/claude-4.5` | `openrouter/claude-3.5` |
| Bulk | `antigravity/gemini-3-flash` | `openrouter/deepseek-chat` |

## 4. Automatic Rerouting
The Task-Router MUST be updated dynamically. This can be achieved by:
1. Updating the agent's default model.
2. Using model overrides in `sessions_spawn` calls.

---
*Stay online. Stay lethal.*
