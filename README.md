# Angular Migration Planner

> **Professional Angular migration analysis tool for version upgrades, Nx monorepo refactoring, and technical debt assessment**

Plan Angular migrations (17→18, 18→19, 19→20, 20→21) with precision AST analysis, calculate workload estimates, and generate interactive HTML dashboards.

[![npm version](https://img.shields.io/npm/v/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![npm downloads](https://img.shields.io/npm/dm/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/typescript-5.9-blue)](https://www.typescriptlang.org/)
[![Tests](https://img.shields.io/badge/tests-748%20passing-success)](./tests)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)[![Status](https://img.shields.io/badge/status-alpha-orange)](https://www.npmjs.com/package/@silvestv/migration-planificator)

**[🇬🇧 English](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.md) | [🇫🇷 Français](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.fr.md)**

---

For security concerns or to report vulnerabilities, see [SECURITY.md](https://github.com/silvestv/migration-planificator-documentation/blob/master/SECURITY.md)

---

## 🎯 What Is This?

A comprehensive **Angular migration analysis tool** for:

- 🔄 **Angular Upgrades**: Plan migrations 17→18, 18→19, 19→20, 20→21 with precise workload estimates
- 🏢 **Nx Monorepo**: Analyze multi-app/multi-lib workspaces with per-target breakdown
- 📊 **Technical Debt**: Identify deprecated APIs, anti-patterns, modernization opportunities
- 💰 **Workload Estimation**: Calculate time (days/hours/minutes) by priority and risk level
- 🎨 **Code Modernization**: Detect Signals, Control Flow, Standalone component opportunities

Perfect for **engineering teams** and **tech leads** planning Angular upgrades or refactoring initiatives.

---

## 🏆 Why Choose This Tool?

Unlike simple regex-based scanners or manual audits:

- ✅ **88% AST Coverage**: Context-aware detection eliminates false positives (ignores comments, strings, migrated code)
- ✅ **Cross-File Intelligence**: Connects TypeScript ↔ HTML templates (detects `@Component` + `<router-outlet>` patterns)
- ✅ **Production-Ready**: 748 passing tests, TypeScript strict mode, optimized batch processing
- ✅ **Time Saver**: Automated workload calculation + Gantt timeline = instant migration roadmap
- ✅ **Zero Dependencies**: Pure AST analysis with ts-morph + @angular/compiler (no external APIs)

---

## ✨ Key Features

- **AST Precision**: Context-aware detection via ts-morph + @angular/compiler (88% rule coverage)
- **Interactive Dashboard**: HTML report with charts, Gantt timeline, real-time workload editing
- **3 Scan Modes**: AST (precise), Regex (fast), Both (comparative with delta analysis)
- **119 Migration Rules**: Covering breaking changes, deprecations, best practices (to18, to19, to20, to21)
- **Cross-File Analysis**: TypeScript ↔ HTML template detection
- **Multi-Project**: Nx Monorepo and Angular Standalone support

---

## 🎓 Use Cases

### Angular Version Migration
Upgrade Angular 17→21 with comprehensive change list and time estimates:
```bash
npx @silvestv/migration-planificator --scanner=both --rules=all --project-path=/path/to/angular-app
```
**Output**: All required changes, time breakdown, risk assessment, interactive planner

### Nx Monorepo Refactoring
Modernize large Nx workspace with 10+ apps/libs:
```bash
npx @silvestv/migration-planificator --scanner=both --project-path=/path/to/nx-workspace
```
**Output**: Per-app/lib breakdown, shared dependencies impact, Gantt timeline

### Technical Debt Assessment
Audit codebase for deprecated APIs:
```bash
npx @silvestv/migration-planificator --scanner=ast --rules=[18,19,20]
```
**Output**: Deprecated patterns (*ngIf, @Input()), modernization opportunities, file tracking

---

## 🚀 Quick Start

### Installation

#### Via npm (Recommended)
```bash
npm install -g @silvestv/migration-planificator
# or
npx @silvestv/migration-planificator --project-path=/path/to/your/project
```

#### From Source
```bash
git clone <repository-url>
cd migration-planificator
npm install
npm run build
```

### Generate First Report
```bash
# Analyze current directory
npx @silvestv/migration-planificator

# Analyze specific project with options
npx @silvestv/migration-planificator --scanner=both --project-path=/path/to/your/project

# Filter by migration version
npx @silvestv/migration-planificator --rules=18              # Only Angular 17→18
npx @silvestv/migration-planificator --rules=[18,19]         # Angular 17→19

# Or using global installation
migration-planificator --scanner=both --project-path=/path/to/your/project
```

### Open Report
```bash
open output/index.html  # macOS/Linux
start output/index.html # Windows
```

---

## 💻 Usage

### After npm Installation

```bash
# Basic usage
npx @silvestv/migration-planificator

# With options
npx @silvestv/migration-planificator --scanner=both --project-path=/path/to/project --rules=all

# Global installation
npm install -g @silvestv/migration-planificator
migration-planificator --scanner=ast --project-path=./my-angular-app
```

### CLI Options
```bash
--scanner=<mode>        ast | regex | both [default: ast]
--project-path=<path>   Path to Angular project [default: current directory]
--rules=<versions>      18 | [18,19] | all [default: all]
```

### Examples
```bash
# Scan current directory with AST
npx @silvestv/migration-planificator

# Comparative scan (AST vs Regex) on specific project
npx @silvestv/migration-planificator --scanner=both --project-path=/workspace/my-app

# Only check Angular 17→18 migration rules
npx @silvestv/migration-planificator --rules=18

# Multiple versions with regex scanner
npx @silvestv/migration-planificator --scanner=regex --rules=[18,19]
```

### For Development (from cloned repository)
```bash
# Build and run
npm run build
npm start -- --scanner=both --project-path=/path/to/project

# Quick report scripts
npm run report                          # AST scan + HTML (default)
npm run report -- --scanner=ast         # AST mode only
npm run report -- --scanner=regex       # Regex mode only
npm run report -- --scanner=both        # Comparative AST vs Regex
```

---

## 📊 Report Contents

### Overview Page
- Project summary (type, Angular version, apps/libs count)
- Global statistics (rules detected, total workload)
- Apps/libs cards with individual analysis

### Workload Page
- **Charts**: Pie (migrations), Bar (top rules), Doughnut (priorities)
- **Gantt Timeline**: Sequential migration phases
- **Hierarchy Tree**: Monorepo → Apps/Libs → Migrations → Priorities → Rules
- **Real-time Editing**: Click time estimates to adjust, auto-recalculates
- **Filters**: Risk level, category, rule type, text search

### Delta Page (Both Mode)
- Rule-by-rule comparison (AST vs Regex accuracy)
- Divergence analysis, performance stats, recommendations

---

## 📋 Migration Rules

**119 rules** across 4 versions:

| Migration | Mandatory | Recommended | Optional | Total |
|-----------|-----------|-------------|----------|-------|
| **17→18** | 8         | 17          | 0        | 25    |
| **18→19** | 15        | 13          | 9        | 37    |
| **19→20** | 6         | 7           | 5        | 18    |
| **20→21** | 21        | 6           | 12       | 39    |

### Categories
`environment` (Node/TS versions) • `imports` (modules) • `api` (Angular APIs) • `routing` (Router) • `template` (directives) • `test` (testing) • `ssr` (SSR) • `reactive` (Signals)

### Risk Levels
🔴 **Critical** (breaking changes) • 🟠 **High** (major deprecations) • 🟡 **Medium** (improvements) • 🟢 **Low** (optimizations)

---

## 🐛 Troubleshooting

### Invalid Regular Expression
Ensure JavaScript compatibility:
```bash
# (?s) not supported → use [\s\S]*?
```

### Build Fails
```bash
rm -rf dist/
npm run build
```

### Empty Report
- Verify `--project-path` points to Angular root
- Check `angular.json` or `nx.json` exists
- Supports Angular 17, 18, 19, 20, 21

---

## 🔒 Security Notice

**This CLI runs entirely on your local machine.** It does **not collect, transmit, or store** any data externally. No network requests are made during analysis.

- ✅ **100% Local Processing** - Your code never leaves your machine
- ✅ **No Telemetry** - Zero data collection or tracking
- ✅ **No External APIs** - Pure AST analysis with local libraries
- ✅ **Signed Package** - Automatically signed by npm registry for integrity verification
- ✅ **Auditable** - Inspect published package contents anytime:
  ```bash
  npm pack @silvestv/migration-planificator
  tar -tzf silvestv-migration-planificator-*.tgz
  # Or view files directly
  npm view @silvestv/migration-planificator files
  ```

For security concerns or to report vulnerabilities, see [SECURITY.md](https://github.com/silvestv/migration-planificator-documentation/blob/master/SECURITY.md)

---

## 🤝 Contributing & Support

This project uses a **dual-license model**:
- **AGPL-3.0 License** for community/open-source use
- **Commercial License** available for enterprise support and features

### 🐛 Report a Bug

Found a bug? Please report it via GitHub Issues:

1. **Go to**: [GitHub Issues](https://github.com/silvestv/migration-planificator-documentation/issues/new/choose)
2. **Select**: "Bug Report" template
3. **Fill in**:
   - Bug description
   - Steps to reproduce
   - Expected vs actual behavior
   - Your environment (OS, Node.js version, Angular version)
   - Command used

**Quick link**: [Report a Bug](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=bug_report.md)

### ✨ Request a Feature

Have an idea for improvement?

1. **Go to**: [GitHub Issues](https://github.com/silvestv/migration-planificator-documentation/issues/new/choose)
2. **Select**: "Feature Request" template
3. **Describe**:
   - The problem you're trying to solve
   - Your proposed solution
   - Use case and who benefits
   - Any mockups or examples

**Quick link**: [Request a Feature](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=feature_request.md)

### ❓ Ask a Question

Need help or have questions?

1. **Go to**: [GitHub Issues](https://github.com/silvestv/migration-planificator-documentation/issues/new/choose)
2. **Select**: "Question" template
3. **Check first**:
   - [FAQ](https://github.com/silvestv/migration-planificator-documentation/blob/master/FAQ.md)
   - [Troubleshooting Guide](https://github.com/silvestv/migration-planificator-documentation/blob/master/TROUBLESHOOTING.md)

**Quick link**: [Ask a Question](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=question.md)

### 📧 Direct Contact

For urgent issues, security concerns, or commercial inquiries:

📧 **Email**: victor.silvestre.dev@gmail.com

**Enterprise users**: Contact us for commercial licensing, priority support, and custom features.

---
## 📝 License

© 2025 Victor SILVESTRE

Licensed under the **Apache License, Version 2.0** (the "License").
You may not use this file except in compliance with the License.
You may obtain a copy of the License at:

http://www.apache.org/licenses/LICENSE-2.0

### Key Terms

- ✅ **Commercial Use** - Freely use for any purpose including commercial
- ✅ **Modification** - Modify and distribute your own versions
- ✅ **Distribution** - Redistribute the original or modified versions
- ✅ **Patent Grant** - Includes express grant of patent rights from contributors
- ✅ **Private Use** - Use privately without any obligations

### Requirements

When distributing or modifying:
- 📝 Include the LICENSE file
- 📝 Include the NOTICE file (if present)
- 📝 State any significant changes made to the code

### Disclaimer

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

See [LICENSE](LICENSE) for the full license text.

📧 **Contact**: victor.silvestre.dev@gmail.com



## 🙏 Acknowledgments

Built with **ts-morph** (TypeScript AST), **@angular/compiler** (HTML parsing), **TailwindCSS** (design), **Chart.js** (visualization)

---

**🚀 Start planning your Angular migration today!**

---

📧 [Contact](mailto:victor.silvestre.dev@gmail.com) • 📦 [NPM Package](https://www.npmjs.com/package/@silvestv/migration-planificator)
