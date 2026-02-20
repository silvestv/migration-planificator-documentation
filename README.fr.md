# Angular Migration Planner

> **Effectuez vos migrations Angular sans stress et avec accompagnement !**
> 
> **Outil professionnel d'accompagnement de migrations Angular pour montées de version, refactoring Nx monorepo, et evaluation de dette technique**
> 
> **Auto fix de migration par IA + schematics angular (expérimental)**
> 
[![npm downloads](https://img.shields.io/npm/dm/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/typescript-5.9-blue)](https://www.typescriptlang.org/)
[![Tests](https://img.shields.io/badge/tests-748%20passing-success)](tests)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)[![Status](https://img.shields.io/badge/statut-alpha-orange)](https://www.npmjs.com/package/@silvestv/migration-planificator)

**[🇬🇧 English](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.md) | [🇫🇷 Francais](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.fr.md)**

---

## 🎯 C'est Quoi ?

Un **outil d'analyse (AST) de migrations Angular** ET **de migration assistée par IA** complet pour :

- 🔄 **Migrations Angular** : Planifiez migrations 17→18, 18→19, 19→20, 20→21 avec estimations précises
- 🏢 **Monorepo Nx** : Analysez workspaces multi-apps/libs avec détail par target
- 📊 **Dette Technique** : Identifiez APIs dépréciées, anti-patterns, opportunités de modernisation
- 💰 **Estimation Charge** : Calculez temps (jours/heures/minutes) par priorité et niveau de risque
- 🎨 **Modernisation Code** : Détectez opportunités Signals, Control Flow, Composants Standalone

Parfait pour **équipes techniques** et **tech leads** planifiant des upgrades Angular ou refactoring.

📸 [Voir le résultat](#vue-générale-du-résultat-page-workload) | 🤖 [AI Auto-Fix](#-ai-auto-fix-experimental)

---

## 🏆 Pourquoi Choisir Cet Outil ?

Contrairement aux scanners regex simples ou audits manuels :

- ✅ **88% Couverture AST** : Détection contextuelle élimine faux positifs (ignore commentaires, strings, code migré)
- ✅ **Intelligence Cross-File** : Connecte TypeScript ↔ templates HTML (détecte patterns `@Component` + `<router-outlet>`)
- ✅ **Production-Ready** : 748 tests réussis, TypeScript strict mode, batch processing optimisé
- ✅ **Gain de Temps** : Calcul charge auto + timeline Gantt = roadmap migration instantanée
- ✅ **Zéro Dépendances** : Analyse AST pure avec ts-morph + @angular/compiler (pas d'APIs externes)

---

## 🚀 Demarrage Rapide

```bash
# Se placer sur son projet
cd path-to-my-project # (si install local)

# Installer
npm install -D @silvestv/migration-planificator
npm install -g @silvestv/migration-planificator

# Executer directement
npx @silvestv/migration-planificator
npx @silvestv/migration-planificator --project-path=path-to-my-project
```

### Options CLI

```bash
--scanner=<mode>        ast | regex | both              [defaut: ast]
--project-path=<path>   Chemin vers projet Angular      [defaut: .]
--rules=<versions>      18 | [18,19] | all              [defaut: all]
```

### Exemples

```bash
# Scanner repertoire courant (AST, toutes regles)
npx @silvestv/migration-planificator

# Scan comparatif sur workspace Nx
npx @silvestv/migration-planificator --scanner=both --project-path=/workspace/mon-app

# Uniquement regles Angular 17→18
npx @silvestv/migration-planificator --rules=18

# Plusieurs versions
npx @silvestv/migration-planificator --rules=[18,19,20]
```

### Ouvrir le Rapport

```bash
open output/index.html   # macOS/Linux
start output/index.html  # Windows
```

---

## 📊 Contenu du Rapport

5 fichiers HTML generes dans `output/` :

- **Overview** — Resume projet, stats globales, cards apps/libs
- **Workload** — Charts (pie, bar, doughnut), timeline Gantt, arbre hierarchique, edition temps reel, filtres
- **Migration Guide** — Checklist etape par etape par regle
- **Rules Overview** — Toutes les 119 regles avec statut detection
- **Delta** *(mode both)* — Comparaison AST vs Regex, analyse divergences

---

## Vue générale du résultat (page workload)

<p align="center">
  <img src="https://raw.githubusercontent.com/silvestv/migration-planificator-documentation/master/public/img/migration-page-light.jpg" alt="Workload page" width="600"/>
</p>

---

## 🤖 AI Auto-Fix (Experimental)

Generez des prompts structures pour agents IA (Claude CLI / Gemini CLI -> pas recommandé) afin de migrer automatiquement votre code.

> **Recommande** : **Claude Code Opus 4 (CLI)** avec un **depot de petite a moyenne taille** (< 500 fichiers impactes). Experimental — relisez toutes les modifications de l'agent avant de merger.

### Prérequis

- Un IDE (Vscode / Webstorm)
- Un Claude Code (recommandée) OU Gemini CLI
- Attention : la migration d'une règle coûte un certain nombre de tokens !

### Commande

1. project > ./output/workload-planner.html
2. ouvrer la page dans le navigateur
3. sur une règle de migration, cliquez sur le bouton AI FIX : c'est un clipboard
4. ouvrez un terminal sur le projet à migrer
5. coller la commande du clipboard tel que :
```bash
   npx @silvestv/migration-planificator fix --rule=RULE_KEY
```
OU depuis un autre repo avec
```bash
npx @silvestv/migration-planificator fix --rule=RULE_KEY --project-path=/chemin/vers/projet
```
6. Executez : génération des prompts

**Attention**: les "RULE_KEY" sont visibles en bas des modals de "détails" d'une règle.

| Option | Description | Defaut |
|--------|-------------|--------|
| `--rule=RULE_KEY` | Regle de migration a corriger **(requis)** | — |
| `--project-path=PATH` | Chemin vers le projet Angular | `.` |
| `--branch=BRANCH` | Branche de base | `master` |
| `-y` | Skip confirmation preconditions | `false` |
| `--skip-validation` | Skip build & tests dans le prompt | `false` |

### Sortie

4 fichiers dans `output/ai/migration/{version}/{rule}-prompts/` :

| Fichier | Role |
|---------|------|
| `constitution.md` | Regles absolues de l'agent (securite, qualite, imports) |
| `context.md` | Description regle + toutes les occurrences (fichier:ligne) |
| `ledger.json` | Suivi migration (schematic, iterations, blame) |
| `file-prompt.md` | Instructions completes en 7 phases pour l'agent |

### Utilisation

```bash
cd /chemin/vers/projet && claude       # ou gemini
> Execute output/ai/migration/19/signal_inputs-prompts/file-prompt.md (exemple)
```

L'agent va : verifier preconditions → creer branche → proposer plan → implementer → valider (AST + build + tests) → commit & push.

### Pipeline de l'Agent

<p align="center">
  <img src="https://raw.githubusercontent.com/silvestv/migration-planificator-documentation/master/public/img/autofix-pipeline.jpg" alt="Pipeline Agent AI Auto-Fix" width="600"/>
</p>

---

## 📋 Regles Migration

**119 regles** sur 4 versions :

| Migration | Obligatoires | Recommandees | Optionnelles | Total |
|-----------|--------------|--------------|--------------|-------|
| **17→18** | 8            | 17           | 0            | 25    |
| **18→19** | 15           | 13           | 9            | 37    |
| **19→20** | 6            | 7            | 5            | 18    |
| **20→21** | 21           | 6            | 12           | 39    |

**Categories** : `environment` • `imports` • `api` • `routing` • `template` • `test` • `ssr` • `reactive` • `signals` • `config`

**Niveaux Risque** : 🔴 Critical • 🟠 High • 🟡 Medium • 🟢 Low

---

## 🔒 Securite

**100% traitement local.** Aucune telemetrie, aucune API externe, vos donnees ne quittent jamais votre machine. Voir [SECURITY.md](https://github.com/silvestv/migration-planificator-documentation/blob/master/SECURITY.md)

---

## 🤝 Support

- 🐛 [Signaler un Bug](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=bug_report.md)
- ✨ [Demander une Fonctionnalite](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=feature_request.md)
- ❓ [Poser une Question](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=question.md)
- 📧 victor.silvestre.dev@gmail.com

---

## 📝 Licence

© 2025 Victor SILVESTRE — [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0). Libre pour usage commercial. Voir [LICENSE](LICENSE).

Construit avec **ts-morph**, **@angular/compiler**, **TailwindCSS**, **Chart.js**

---

📧 [Contact](mailto:victor.silvestre.dev@gmail.com) • 📦 [Package NPM](https://www.npmjs.com/package/@silvestv/migration-planificator)
