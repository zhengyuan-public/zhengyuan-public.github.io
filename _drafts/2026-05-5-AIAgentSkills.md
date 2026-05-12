---
comments: true
title: AI Agent Skills
date: 2026-05-05 12:00:00
image:
    path: /assets/img/images_preview_default/Cat5.jpeg
math: true
categories: [Artificial Intelligence, AI Agents]
tags: [ai-agents, skill-learning, llm-agents, autonomous-systems]
---

> **Motivation**: LLMs already know lots of *facts*, but lack **procedural knowledge**, which can be added with skills.
{: .prompt-tip }

### Specification for Agent Skills
- [Agent Skills Specification](https://agentskills.io/specification)

#### Directory Structure

```bash
skill-name/
├── SKILL.md          # Required: metadata + instructions
├── scripts/          # Optional: executable code
├── references/       # Optional: documentation
├── assets/           # Optional: templates, resources
└── ...               # Any additional files or directories
```

#### `SKILL.md` Format

1. Metadata (Front Matter)
   - `name`
   - `description`
2. Body
3. Optional
   - `scripts/`
   - `references/`
   - `assets/`

#### Progressive Disclosure

Progressive disclosure works at three levels:

1. Metadata only.
2. Include body.
3. Include optional directories.

### Types of Knowledge

- MCP (Model Context Protocol): Tool access.

- RAG (Retrieval-augmented Generation): Factual Knowledge.

- Fine-tuning: Knowledge baked into model weights.

- **Skills**: Procedural knowledge.

### Memory

|       Human       |  AI Agent  |
| :---------------: | :--------: |
|  Semantic Memory  |    RAGs    |
|  Episodic Memory  |    Logs    |
| Procedural Memory | **Skills** |

### Trust

- Prompt Injection

- Tool Poisoning

- Malware
