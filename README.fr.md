# Angular Migration Planner

> **Outil professionnel d'analyse de migrations Angular pour montées de version, refactoring Nx monorepo, et évaluation de dette technique**

Planifiez vos migrations Angular (17→18, 18→19, 19→20) avec analyse AST précise, calculez les charges de travail, et générez des dashboards HTML interactifs.

[![npm version](https://img.shields.io/npm/v/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![npm downloads](https://img.shields.io/npm/dm/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/typescript-5.9-blue)](https://www.typescriptlang.org/)
[![Tests](https://img.shields.io/badge/tests-451%20passing-success)](tests)
[![License](https://img.shields.io/badge/license-AGPL--3.0%20OR%20Commercial-blue)](LICENSE)
[![Status](https://img.shields.io/badge/statut-alpha-orange)](https://www.npmjs.com/package/@silvestv/migration-planificator)

**[🇬🇧 English] | [🇫🇷 Français](https://unpkg.com/@silvestv/migration-planificator/README.fr.md)**

---

## 🎯 C'est Quoi ?

Un **outil d'analyse de migrations Angular** complet pour :

- 🔄 **Migrations Angular** : Planifiez migrations 17→18, 18→19, 19→20 avec estimations précises
- 🏢 **Monorepo Nx** : Analysez workspaces multi-apps/libs avec détail par target
- 📊 **Dette Technique** : Identifiez APIs dépréciées, anti-patterns, opportunités de modernisation
- 💰 **Estimation Charge** : Calculez temps (jours/heures/minutes) par priorité et niveau de risque
- 🎨 **Modernisation Code** : Détectez opportunités Signals, Control Flow, Composants Standalone

Parfait pour **équipes techniques** et **tech leads** planifiant des upgrades Angular ou refactoring.

---

## 🏆 Pourquoi Choisir Cet Outil ?

Contrairement aux scanners regex simples ou audits manuels :

- ✅ **88% Couverture AST** : Détection contextuelle élimine faux positifs (ignore commentaires, strings, code migré)
- ✅ **Intelligence Cross-File** : Connecte TypeScript ↔ templates HTML (détecte patterns `@Component` + `<router-outlet>`)
- ✅ **Production-Ready** : 451 tests réussis, TypeScript strict mode, batch processing optimisé
- ✅ **Gain de Temps** : Calcul charge auto + timeline Gantt = roadmap migration instantanée
- ✅ **Zéro Dépendances** : Analyse AST pure avec ts-morph + @angular/compiler (pas d'APIs externes)

---

## ✨ Fonctionnalités

- **Précision AST** : Détection contextuelle via ts-morph + @angular/compiler (88% règles)
- **Dashboard Interactif** : Rapport HTML avec charts, timeline Gantt, édition temps réel
- **3 Modes Scan** : AST (précis), Regex (rapide), Both (comparatif avec analyse delta)
- **85+ Règles Migration** : Couvrant breaking changes, dépréciations, best practices
- **Analyse Cross-File** : Détection TypeScript ↔ templates HTML
- **Multi-Projets** : Support Nx Monorepo et Angular Standalone

---

## 🎓 Cas d'Usage

### Migration Version Angular
Upgrade Angular 17→20 avec liste complète changements et estimations :
```bash
npx @silvestv/migration-planificator --scanner=both --rules=all --project-path=/path/to/angular-app
```
**Résultat** : Tous changements requis, breakdown temps, évaluation risques, planificateur interactif

### Refactoring Monorepo Nx
Moderniser workspace Nx avec 10+ apps/libs :
```bash
npx @silvestv/migration-planificator --scanner=both --project-path=/path/to/nx-workspace
```
**Résultat** : Breakdown par app/lib, impact dépendances partagées, timeline Gantt

### Évaluation Dette Technique
Auditer codebase pour APIs dépréciées :
```bash
npx @silvestv/migration-planificator --scanner=ast --rules=[18,19,20]
```
**Résultat** : Patterns dépréciés (*ngIf, @Input()), opportunités modernisation, tracking fichiers

---

## 🚀 Démarrage Rapide

### Installation

#### Via npm (Recommandé)
```bash
npm install -g @silvestv/migration-planificator
# ou
npx @silvestv/migration-planificator --project-path=/chemin/vers/projet
```

#### Depuis les Sources
```bash
git clone <repository-url>
cd @silvestv/migration-planificator
npm install
npm run build
```

### Générer Premier Rapport
```bash
# Analyser répertoire courant
npx @silvestv/migration-planificator

# Analyser projet spécifique avec options
npx @silvestv/migration-planificator --scanner=both --project-path=/chemin/vers/projet

# Filtrer par version migration
npx @silvestv/migration-planificator --rules=18              # Seulement Angular 17→18
npx @silvestv/migration-planificator --rules=[18,19]         # Angular 17→19

# Ou avec installation globale
@silvestv/migration-planificator --scanner=both --project-path=/chemin/vers/projet
```

### Ouvrir Rapport
```bash
open output/index.html  # macOS/Linux
start output/index.html # Windows
```

---

## 💻 Utilisation

### Après installation npm

```bash
# Utilisation basique
npx @silvestv/migration-planificator

# Avec options
npx @silvestv/migration-planificator --scanner=both --project-path=/chemin/vers/projet --rules=all

# Installation globale
npm install -g @silvestv/migration-planificator
@silvestv/migration-planificator --scanner=ast --project-path=./mon-app-angular
```

### Options CLI
```bash
--scanner=<mode>        ast | regex | both [défaut: ast]
--project-path=<path>   Chemin vers projet Angular [défaut: répertoire courant]
--rules=<versions>      18 | [18,19] | all [défaut: all]
```

### Exemples
```bash
# Scanner répertoire courant avec AST
npx @silvestv/migration-planificator

# Scan comparatif (AST vs Regex) sur projet spécifique
npx @silvestv/migration-planificator --scanner=both --project-path=/workspace/mon-app

# Vérifier uniquement règles migration Angular 17→18
npx @silvestv/migration-planificator --rules=18

# Plusieurs versions avec scanner regex
npx @silvestv/migration-planificator --scanner=regex --rules=[18,19]
```

### Pour Développement (depuis repository cloné)
```bash
# Build et exécution
npm run build
npm start -- --scanner=both --project-path=/chemin/vers/projet

# Scripts rapports rapides
npm run report                          # AST scan + HTML (default)
npm run report -- --scanner=ast         # AST mode only
npm run report -- --scanner=regex       # Regex mode only
npm run report -- --scanner=both        # Comparative AST vs Regex
```

---

## 📊 Contenu Rapport

### Page Overview
- Résumé projet (type, version Angular, compteur apps/libs)
- Statistiques globales (règles détectées, charge totale)
- Cards apps/libs avec analyse individuelle

### Page Workload
- **Charts** : Pie (migrations), Bar (top règles), Doughnut (priorités)
- **Timeline Gantt** : Phases migration séquentielles
- **Arbre Hiérarchique** : Monorepo → Apps/Libs → Migrations → Priorités → Règles
- **Édition Temps Réel** : Cliquer estimations pour ajuster, recalcul auto
- **Filtres** : Niveau risque, catégorie, type règle, recherche texte

### Page Delta (Mode Both)
- Comparaison règle par règle (précision AST vs Regex)
- Analyse divergences, stats performance, recommandations

---

## 📋 Règles Migration

**85 règles** sur 3 versions :

| Migration | Obligatoires | Recommandées | Optionnelles | Total |
|-----------|--------------|--------------|--------------|-------|
| **17→18** | 8            | 17           | 0            | 25    |
| **18→19** | 15           | 13           | 9            | 37    |
| **19→20** | 6            | 7            | 5            | 18    |

### Catégories
`environment` (versions Node/TS) • `imports` (modules) • `api` (APIs Angular) • `routing` (Router) • `template` (directives) • `test` (tests) • `ssr` (SSR) • `reactive` (Signals)

### Niveaux Risque
🔴 **Critical** (breaking changes) • 🟠 **High** (dépréciations majeures) • 🟡 **Medium** (améliorations) • 🟢 **Low** (optimisations)

---

## 🐛 Dépannage

### Expression Régulière Invalide
Vérifier compatibilité JavaScript :
```bash
# (?s) non supporté → utiliser [\s\S]*?
```

### Build Échoue
```bash
rm -rf dist/
npm run build
```

### Rapport Vide
- Vérifier `--project-path` pointe vers racine Angular
- Vérifier présence `angular.json` ou `nx.json`
- Support Angular 17, 18, 19, 20

---

## 🔒 Sécurité et Confidentialité

**Ce CLI s'exécute entièrement sur votre machine locale.** Il ne **collecte, ne transmet, ni ne stocke** aucune donnée externe. Aucune requête réseau n'est effectuée pendant l'analyse.

- ✅ **100% Traitement Local** - Votre code ne quitte jamais votre machine
- ✅ **Aucune Télémétrie** - Zéro collecte de données ou tracking
- ✅ **Aucune API Externe** - Analyse AST pure avec bibliothèques locales
- ✅ **Package Signé** - Signé automatiquement par le registre npm pour vérification d'intégrité
- ✅ **Auditable** - Inspectez le contenu du package publié à tout moment :
  ```bash
  npm pack @silvestv/migration-planificator
  tar -tzf silvestv-migration-planificator-*.tgz
  # Ou visualisez les fichiers directement
  npm view @silvestv/migration-planificator files
  ```
---

## 🤝 Contribuer

Ce projet utilise un **modèle double-licence** :
- **Licence AGPL-3.0** pour usage communautaire/open-source
- **Licence Commerciale** disponible pour support et fonctionnalités entreprise

### Politique de Contribution

Actuellement, nous nous concentrons principalement sur le maintien et l'évolution du produit principal. Pour signaler bugs, demandes de fonctionnalités ou questions :

📧 **Contact** : victor.silvestre.dev@gmail.com

**Utilisateurs entreprise** : Contactez-nous pour licence commerciale, support prioritaire et fonctionnalités personnalisées.

---

## 📝 Licence

**Double Licence** © 2025 Victor Louis SILVESTRE

Ce projet est disponible sous deux licences :

### 1. AGPL-3.0 (Gratuit pour Usage Non-Commercial)
Pour particuliers, étudiants, chercheurs, organisations à but non lucratif et projets open-source.

**Obligations si vous distribuez ou fournissez comme service** :
- ✅ Rendre votre code source complet disponible sous AGPL-3.0
- ✅ Partager toutes modifications publiquement
- ✅ Inclure mentions de copyright et de licence

### 2. Licence Commerciale (Pour Usage Professionnel)
Pour les entreprises qui doivent utiliser ce logiciel sans les obligations AGPL.

📧 Contact : victor.silvestre.dev@gmail.com

Voir [LICENSE](LICENSE) et [COMMERCIAL-LICENSE.md](COMMERCIAL-LICENSE.md) pour les termes complets.


## 🙏 Remerciements

Construit avec **ts-morph** (AST TypeScript), **@angular/compiler** (parsing HTML), **TailwindCSS** (design), **Chart.js** (visualisation)

---

**🚀 Commencez à planifier votre migration Angular dès aujourd'hui !**

📧 [Contact](mailto:victor.silvestre.dev@gmail.com) • 📦 [Package NPM](https://www.npmjs.com/package/@silvestv/migration-planificator)
