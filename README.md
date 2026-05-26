# OpenBash · Prompt Generator

> **From pentesters, to pentesters.**
> A structured generator for **prompts**, **`CLAUDE.md`** project files, and **`SKILL.md`** agent skills — built for offensive security work.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Made by OpenBash](https://img.shields.io/badge/made%20by-openbash.com-ff2a78)](https://openbash.com)
[![No backend](https://img.shields.io/badge/100%25-client--side-00e5ff)](#privacy)
[![EN / ES](https://img.shields.io/badge/i18n-EN%20%2F%20ES-a855f7)](README.es.md)

[Español](README.es.md) · **English**

---

## What is this

A single-page tool that turns scattered "please do X, but never Y, and respond in this shape" instructions into clean, structured artifacts that LLMs actually follow:

- **`PROMPT`** — one-shot instruction for a single task. Paste it into a chat.
- **`CLAUDE.md`** — project context file that [Claude Code](https://claude.com/claude-code) loads automatically from your repo root.
- **`SKILL.md`** — reusable [agent skill](https://agentskills.io) with YAML frontmatter, loaded dynamically when triggers match.

Faders for **creativity**, **rigor**, **verbosity** and **tone**. Hard **NO·rules** that get injected as meta-instructions and survive any refinement pass. Live preview, token count, validation for `SKILL.md`, and presets curated for pentesters (finding writer, CVSS assessor, evidence validator, OWASP categorizer, engagement workspace, report writing, and more).

### Why pentesters?

Because writing a finding that holds up under client review is not a creative task — it's a structured one, with hard rules ("never paraphrase evidence", "never overstate severity", "never mix remediation into the description"). LLMs are useful for this, but only when constrained. This tool builds those constraints into the prompt.

It works for any structured prompting task, but the defaults, presets, and rules lean toward **offensive security and report writing**.

## Features

- **3 modes**: Prompt · `CLAUDE.md` · `SKILL.md` — each with its own sections, presets, placeholders, and validation rules.
- **EN / ES** — full UI translation. Spanish defaults to Rioplatense.
- **Faders**: creativity (0–1), rigor (0–1), verbosity (concise → exhaustive), tone (casual → formal). Faders alter the rendered output *and* the API temperature when the AI panel is on.
- **NO · Rules** — universal hard rules (no fabrication, no inference beyond input, no filler, no emojis, no markdown if not requested, no language drift, …) plus custom rules per preset.
- **Presets** curated for pentest workflows: `pentest-finding`, `code-review`, `extractor`, `pentest-engagement`, `security-tool-repo`, `report-writing`, `pentest-finding-writer`, `severity-assessor`, `evidence-validator`, `owasp-categorizer`, …
- **Live preview** + token estimate + structural validation (`SKILL.md` checks the YAML frontmatter and warns on weak descriptions, missing triggers, oversized files).
- **Optional AI backend** — bring your own key for Anthropic Claude or OpenAI GPT. `IMPROVE` / `TEST RUN` / `CRITIQUE` actions use your current output + faders.
- **100% client-side** — no backend, no telemetry, no analytics. State is `localStorage`. Your API key never leaves the browser except to go to the provider.

## Use it

**Hosted:** open the GitHub Pages site (enabled on this repo).

**Local:** clone the repo and open `index.html` in any modern browser. That's it — there is no build step, no dependencies, nothing to install.

```bash
git clone https://github.com/openbashok/prompt-generator.git
cd prompt-generator
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

Or serve it with anything:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## How to use

1. Pick a **mode** (Prompt / `CLAUDE.md` / `SKILL.md`).
2. Optionally load a **preset** from the left panel.
3. Toggle which **sections** you want in the output.
4. Fill the **content** fields in the middle column. Live preview updates as you type.
5. Adjust the **faders** to match the task (lower creativity + higher rigor for findings; higher creativity for explainers).
6. Add or remove **NO·rules** — universal ones are on by default; click chips to toggle, add custom ones in the input.
7. **COPY** or **DOWNLOAD** the result.
8. *(Optional)* Open the **AI panel** in the header, drop in an Anthropic or OpenAI key, and use `IMPROVE` / `TEST RUN` / `CRITIQUE` to iterate.

### Output examples

- **Prompt mode** → plain text with `ROLE / CONTEXT / TASK / INPUT / CONSTRAINTS / OUTPUT FORMAT / HARD RULES` sections, ready to paste.
- **`CLAUDE.md` mode** → drop the file at the root of any repo. Claude Code reads it automatically.
- **`SKILL.md` mode** → save as `skills/<name>/SKILL.md`. Includes the YAML frontmatter (`name`, `description`) required by the [agentskills.io](https://agentskills.io) standard.

## Privacy

- Everything runs in your browser. There is no server.
- API keys live in `localStorage` only. They are sent **directly** to the provider you choose (Anthropic / OpenAI), never to a middleman.
- For production or shared environments, run the AI calls through a backend proxy instead of putting keys in a browser.

## Roadmap

This is `v0.5`. Things on the radar:

- More presets (mobile pentest, AD/network, cloud, red team ops, threat modeling).
- CWE categorizer skill, remediation writer skill.
- Export to JSON / import presets across browsers.
- More providers (local models, Ollama).
- Optional dark/light theme toggle (currently dark only — it's a feature).

PRs welcome — see [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Contributing

Found a missing preset, a rule that should be universal, a translation issue, or a bug?

- Open an issue with a concrete example.
- Or send a PR — the whole app is one HTML file with vanilla JS, no build, no framework, no transpilation. Easy to hack on.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for the short version.

## License

[MIT](LICENSE) — do whatever you want, just keep the notice.

## About OpenBash

[OpenBash](https://openbash.com) builds tooling for offensive security teams.
This project is part of that toolbox. Made by pentesters, for pentesters.
