# Angular Migration Planner

> **Perform your Angular migrations stress-free with full guidance!**
>
> **Professional Angular migration companion tool for version upgrades, Nx monorepo refactoring, and technical debt assessment**
>
> **AI-powered migration auto-fix + Angular schematics (experimental)**

[![npm downloads](https://img.shields.io/npm/dm/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/typescript-5.9-blue)](https://www.typescriptlang.org/)
[![Tests](https://img.shields.io/badge/tests-748%20passing-success)](tests)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)[![Status](https://img.shields.io/badge/status-alpha-orange)](https://www.npmjs.com/package/@silvestv/migration-planificator)

**[🇬🇧 English](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.md) | [🇫🇷 Français](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.fr.md)**

---

## 🎯 What Is This?

A complete **Angular migration analysis (AST)** AND **AI-assisted migration** tool for:

- 🔄 **Angular Migrations** — Plan migrations 17→18, 18→19, 19→20, 20→21 with precise estimates
- 🏢 **Nx Monorepo** — Analyze multi-app/lib workspaces with per-target breakdown
- 📊 **Technical Debt** — Identify deprecated APIs, anti-patterns, modernization opportunities
- 💰 **Workload Estimation** — Calculate time (days/hours/minutes) by priority and risk level
- 🎨 **Code Modernization** — Detect Signals, Control Flow, Standalone Components opportunities

Perfect for **technical teams** and **tech leads** planning Angular upgrades or refactoring.

📸 [See the result](#workload-page-overview-workload-page) | 🤖 [AI Auto-Fix](#-ai-auto-fix-experimental)

---

## 🏆 Why Choose This Tool?

Unlike simple regex scanners or manual audits:

- ✅ **88% AST Coverage** — Context-aware detection eliminates false positives (ignores comments, strings, migrated code)
- ✅ **Cross-File Intelligence** — Connects TypeScript ↔ HTML templates (detects `@Component` + `<router-outlet>` patterns)
- ✅ **Production-Ready** — 748 tests passing, TypeScript strict mode, optimized batch processing
- ✅ **Time Savings** — Auto workload calculation + Gantt timeline = instant migration roadmap
- ✅ **Zero Dependencies** — Pure AST analysis with ts-morph + @angular/compiler (no external APIs)

---

## 🚀 Quick Start

```bash
# Navigate to your project
cd path-to-my-project # (if local install)

# Install
npm install -D @silvestv/migration-planificator
npm install -g @silvestv/migration-planificator

# Run directly
npx @silvestv/migration-planificator
npx @silvestv/migration-planificator --project-path=path-to-my-project
```

### CLI Options

```bash
--scanner=<mode>        ast | regex | both              [default: ast]
--project-path=<path>   Path to Angular project         [default: .]
--rules=<versions>      18 | [18,19] | all              [default: all]
```

### Examples

```bash
# Scan current directory (AST, all rules)
npx @silvestv/migration-planificator

# Comparative scan on Nx workspace
npx @silvestv/migration-planificator --scanner=both --project-path=/workspace/my-app

# Only Angular 17→18 rules
npx @silvestv/migration-planificator --rules=18

# Multiple versions
npx @silvestv/migration-planificator --rules=[18,19,20]
```

### Open Report

```bash
open output/index.html   # macOS/Linux
start output/index.html  # Windows
```

---

## 📊 Report Contents

5 HTML files generated in `output/` :

- **Overview** — Project summary, global stats, apps/libs cards
- **Workload** — Charts (pie, bar, doughnut), Gantt timeline, hierarchy tree, real-time editing, filters
- **Migration Guide** — Step-by-step checklist per rule
- **Rules Overview** — All 119 rules with detection status
- **Delta** *(both mode)* — AST vs Regex comparison, divergence analysis

---

## Workload page overview (workload page)

<p align="center">
  <img src="https://raw.githubusercontent.com/silvestv/migration-planificator-documentation/master/public/img/migration-page-en-light.jpg" alt="Workload page" width="600"/>
</p>

---

## 🤖 AI Auto-Fix (Experimental)

Generate structured prompts for AI agents (Claude CLI / Gemini CLI -> not recommended) to automatically migrate your code.

> **Recommended**: **Claude Code Opus 4 (CLI)** with a **small-to-medium repository** (< 500 files impacted). Experimental — review all agent changes before merging.

### Prerequisites

- An IDE (VSCode / WebStorm)
- Claude Code (recommended) OR Gemini CLI
- Note: migrating a rule costs a certain number of tokens!

### Command

1. project > ./output/workload-planner.html
2. Open the page in your browser
3. On a migration rule, click the AI FIX button: it copies to clipboard
4. Open a terminal in the project to migrate
5. Paste the clipboard command such as:
```bash
   npx @silvestv/migration-planificator fix --rule=RULE_KEY
```
OR from another repo with
```bash
npx @silvestv/migration-planificator fix --rule=RULE_KEY --project-path=/path/to/project
```
6. Execute: prompt generation

**Note**: "RULE_KEY" values are visible at the bottom of rule "details" modals.

| Option | Description | Default |
|--------|-------------|---------|
| `--rule=RULE_KEY` | Migration rule to fix **(required)** | — |
| `--project-path=PATH` | Path to Angular project | `.` |
| `--branch=BRANCH` | Base branch | `master` |
| `-y` | Skip precondition confirmation | `false` |
| `--skip-validation` | Skip build & tests in prompt | `false` |

### Output

4 files in `output/ai/migration/{version}/{rule}-prompts/` :

| File | Purpose |
|------|---------|
| `constitution.md` | Absolute agent rules (safety, quality, imports) |
| `context.md` | Rule description + all occurrences (file:line) |
| `ledger.json` | Migration tracking (schematic, iterations, blame) |
| `file-prompt.md` | Complete 7-phase instructions for the agent |

### Usage

```bash
cd /path/to/project && claude       # or gemini
> Execute output/ai/migration/19/signal_inputs-prompts/file-prompt.md (example)
```

The agent will: check preconditions → create branch → propose plan → implement → validate (AST + build + tests) → commit & push.

### Agent Pipeline

<p align="center">
  <img src="https://raw.githubusercontent.com/silvestv/migration-planificator-documentation/master/public/img/autofix-pipeline-en.jpg" alt="AI Auto-Fix Agent Pipeline" width="600"/>
</p>

---

## 📋 Migration Rules

**119 rules** across 4 versions:

| Migration | Mandatory | Recommended | Optional | Total |
|-----------|-----------|-------------|----------|-------|
| **17→18** | 8         | 17          | 0        | 25    |
| **18→19** | 15        | 13          | 9        | 37    |
| **19→20** | 6         | 7           | 5        | 18    |
| **20→21** | 21        | 6           | 12       | 39    |

**Categories**: `environment` • `imports` • `api` • `routing` • `template` • `test` • `ssr` • `reactive` • `signals` • `config`

**Risk Levels**: 🔴 Critical • 🟠 High • 🟡 Medium • 🟢 Low

---

## 🔒 Security

**100% local processing.** No telemetry, no external APIs, no data leaves your machine. See [SECURITY.md](https://github.com/silvestv/migration-planificator-documentation/blob/master/SECURITY.md)

---

## 🤝 Support

- 🐛 [Report a Bug](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=bug_report.md)
- ✨ [Request a Feature](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=feature_request.md)
- ❓ [Ask a Question](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=question.md)
- 📧 victor.silvestre.dev@gmail.com

---

## 📝 License

© 2025 Victor SILVESTRE — [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0). Free for commercial use. See [LICENSE](LICENSE).

Built with **ts-morph**, **@angular/compiler**, **TailwindCSS**, **Chart.js**

---

📧 [Contact](mailto:victor.silvestre.dev@gmail.com) • 📦 [NPM Package](https://www.npmjs.com/package/@silvestv/migration-planificator)
