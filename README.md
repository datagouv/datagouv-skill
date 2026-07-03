# data.gouv.fr skill

Agent skill for interacting with data.gouv.fr and its three APIs: **Main** ([catalog](https://www.data.gouv.fr/api/1/swagger.json)), **Metrics** ([usage](https://metric-api.data.gouv.fr/api/doc)), **Tabular** ([CSV rows](https://tabular-api.data.gouv.fr/api/doc)). Compatible with any LLM/agent supporting SKILL.md (Claude Code, Cursor, ChatGPT, Codex CLI, Mistral Vibe, etc.).

## 🧩 Skill

Lean **`SKILL.md`** (routing, workflows, examples) plus **`references/`** (endpoint tables, Agent Skills tier 3):

- **Main API** — Datasets, organizations, users, resources, reuses, discussions, harvest, etc. ([references/main-api.md](references/main-api.md))
- **Metrics API** — Usage and download metrics by model ([references/metrics-api.md](references/metrics-api.md))
- **Tabular API** — Query CSV/tabular rows by resource ID ([references/tabular-api.md](references/tabular-api.md))
- **Dataservices** — External APIs catalog and upstream usage ([references/dataservices.md](references/dataservices.md))

## ⚙️ Installation

Clone this repo, then copy the **whole skill directory** (`SKILL.md` + `references/`) into your client's skills folder:

```bash
git clone https://github.com/datagouv/datagouv-skill.git /tmp/datagouv-skill
```

### 🤖 Claude Code

See [Claude Code docs: Skills](https://code.claude.com/docs/en/skills).

- Personal: `mkdir -p ~/.claude/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} ~/.claude/skills/datagouv-apis/`
- Project-only: `mkdir -p .claude/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} .claude/skills/datagouv-apis/`

### 🤖 Cursor

See [Cursor docs: Skills](https://cursor.com/docs/context/skills).

- **From GitHub (recommended):** Cursor Settings → Rules → Project Rules → Add Rule → *Remote Rule (Github)* → enter `https://github.com/datagouv/datagouv-skill`
- **Copy locally:** Personal: `mkdir -p ~/.cursor/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} ~/.cursor/skills/datagouv-apis/` — Project: `mkdir -p .cursor/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} .cursor/skills/datagouv-apis/`

### 🤖 Mistral (Vibe)

See [Mistral docs: Agents & Skills](https://docs.mistral.ai/mistral-vibe/agents-skills).

- Global: `mkdir -p ~/.vibe/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} ~/.vibe/skills/datagouv-apis/`
- Project-only: `mkdir -p .vibe/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} .vibe/skills/datagouv-apis/`

### 🤖 Claude (desktop app)

- Linux: `mkdir -p ~/.config/claude/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} ~/.config/claude/skills/datagouv-apis/`
- MacOS: `mkdir -p ~/Library/Application\ Support/Claude/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} ~/Library/Application\ Support/Claude/skills/datagouv-apis/`

### 🤖 Codex CLI (OpenAI)

See [Codex docs: Skills](https://developers.openai.com/codex/skills).

- User-level install: `mkdir -p ~/.agents/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} ~/.agents/skills/datagouv-apis/`
- Project-level install: `mkdir -p .agents/skills/datagouv-apis && cp -r /tmp/datagouv-skill/{SKILL.md,references} .agents/skills/datagouv-apis/`
- Run: `codex --enable skills -m <model>`

### 🤖 ChatGPT (Code Interpreter)

Paste the content of `SKILL.md` at the start of a chat, or point the model to this repo. Raw URL: `https://raw.githubusercontent.com/datagouv/datagouv-skill/main/SKILL.md`

### 🤖 Other chatbots

Copy the skill directory (`SKILL.md` + `references/`) into a folder your client treats as a skill (e.g. `datagouv-apis/`).

## 🗂️ Repository Structure

```
datagouv_skill/
├── SKILL.md              # Lean core (routing, workflows, examples)
├── references/
│   ├── main-api.md
│   ├── dataservices.md
│   ├── metrics-api.md
│   └── tabular-api.md
├── README.md
└── LICENSE
```

## 🔌 MCP server

data.gouv.fr provides an **[MCP (Model Context Protocol) server](https://github.com/datagouv/datagouv-mcp)** (hosted at `https://mcp.data.gouv.fr/mcp`). Use MCP tools for structured calls; use this skill for richer context and workflows. See [datagouv-mcp](https://github.com/datagouv/datagouv-mcp).

## 🧠 Usage

Restart your LLM/agent after installation. The skill is used automatically when working with data.gouv.fr.

**Cursor:** Type `/` in Agent chat and search for the skill. **Cursor Settings → Rules** shows discovered skills.

**Verify:**
```bash
ls ~/.cursor/skills/datagouv-apis/SKILL.md                    # Cursor
ls ~/.cursor/skills/datagouv-apis/references/main-api.md      # references present
ls ~/.claude/skills/datagouv-apis/SKILL.md                    # Claude Code
```

## 🧯 Troubleshooting

- **Skill not loaded?** Restart your client
- **Wrong path?** Check your client's documentation for the skills directory
- **Missing route tables?** Ensure `references/` was copied alongside `SKILL.md`

## 🤝 Contributing

1. Follow the [SKILL.md standard](https://cursor.com/docs/context/skills) and [Agent Skills progressive disclosure](https://agentskills.io/client-implementation/adding-skills-support)
2. Keep `SKILL.md` concise; add exhaustive detail under `references/`
3. Use Swagger references for exhaustive parameter lists

## 📄 License

MIT License — see [LICENSE](LICENSE).
