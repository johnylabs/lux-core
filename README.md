# lux-core

Local AI control layer for my home lab.

`lux-core` defines how my **personal AI system** behaves across:

- The **LLM engine** on the RTX 3090 (`home-llm-gateway-3090`)
- My SOC / cloud / networking labs
- My language and quant tools

It is the **policy + orchestration layer**, not the model weights.

> Previously: SARAH-ANN Core.  
> Now renamed and aligned with my on-prem server identity.

---

## 🔎 Purpose

- Run powerful models **locally** with strict control.
- Define **what the AI is allowed to do** and **how it talks**.
- Standardize how apps in my lab call the LLM gateway:
  - SOC runbook assistant
  - Spanish tutor
  - Market deviation tools
  - Future apps

Lux does not care which exact model is loaded; it cares about:

- Policies
- Tools
- Workflows

---

## 🧱 Repository Structure

```text
lux-core/
├── README.md
├── policies/
│   ├── alignment-policy.md         # what the AI is and is NOT for
│   ├── privacy-policy.md           # data handling, logging, retention
│   ├── safety-policy.md            # refusal rules, harmful content, boundaries
│   └── autonomy-policy.md          # what it can trigger or change in the lab
├── prompts/
│   ├── system-prompts.md           # core system prompts (general / dev / soc / spanish)
│   ├── style-guidelines.md         # tone, format, how responses should look
│   └── tool-directives.md          # how the model should request tools (search, RAG, etc.)
├── tools/
│   ├── tool-catalog.md             # list of tools lux is allowed to call
│   ├── tool-profiles/
│   │   ├── web-search.md
│   │   ├── rag-docs.md
│   │   ├── soc-lab-tools.md
│   │   └── quant-tools.md
│   └── access-rules.md             # which app can use which tools
├── flows/
│   ├── overview.md                 # how requests flow through lux → gateway → tools
│   ├── soc-runbook-flow.md         # ai-soc-runbook-qa interaction pattern
│   ├── spanish-tutor-flow.md       # es-ai-immersion-lab interaction pattern
│   ├── market-deviation-flow.md    # market deviation assistant pattern
│   └── generic-chat-flow.md        # default “personal assistant” chat pipeline
├── gateway-integration/
│   ├── models-policy.md            # which models are allowed (sizes, families, licenses)
│   ├── home-llm-gateway-3090.md    # how lux talks to the gateway API
│   └── rate-limits.md              # per-app and per-user limits
├── logs-spec/
│   ├── logging-policy.md           # what can be logged, what must NOT be logged
│   ├── redaction-rules.md          # how to scrub sensitive data before storage
│   └── review-process.md           # how I review logs for tuning without leaking data
└── roadmap/
    ├── 2025-roadmap.md             # concrete features and milestones
    └── ideas.md                    # future experiments / stretch goals
