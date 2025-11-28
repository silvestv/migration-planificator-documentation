# Angular Migration Planner

> **Outil professionnel d'analyse de migrations Angular pour montées de version, refactoring Nx monorepo, et évaluation de dette technique**

Planifiez vos migrations Angular (17→18, 18→19, 19→20, 20→21) avec analyse AST précise, calculez les charges de travail, et générez des dashboards HTML interactifs.

[![npm version](https://img.shields.io/npm/v/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![npm downloads](https://img.shields.io/npm/dm/@silvestv/migration-planificator.svg)](https://www.npmjs.com/package/@silvestv/migration-planificator)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/typescript-5.9-blue)](https://www.typescriptlang.org/)
[![Tests](https://img.shields.io/badge/tests-748%20passing-success)](tests)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)[![Status](https://img.shields.io/badge/statut-alpha-orange)](https://www.npmjs.com/package/@silvestv/migration-planificator)

**[🇬🇧 English](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.md) | [🇫🇷 Français](https://github.com/silvestv/migration-planificator-documentation/blob/master/README.fr.md)**

---

Pour toute préoccupation de sécurité ou signaler une vulnérabilité, voir [SECURITY.md](https://github.com/silvestv/migration-planificator-documentation/blob/master/SECURITY.md)

---

## 🎯 C'est Quoi ?

Un **outil d'analyse de migrations Angular** complet pour :

- 🔄 **Migrations Angular** : Planifiez migrations 17→18, 18→19, 19→20, 20→21 avec estimations précises
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
- ✅ **Production-Ready** : 748 tests réussis, TypeScript strict mode, batch processing optimisé
- ✅ **Gain de Temps** : Calcul charge auto + timeline Gantt = roadmap migration instantanée
- ✅ **Zéro Dépendances** : Analyse AST pure avec ts-morph + @angular/compiler (pas d'APIs externes)

---

## ✨ Fonctionnalités

- **Précision AST** : Détection contextuelle via ts-morph + @angular/compiler (88% règles)
- **Dashboard Interactif** : Rapport HTML avec charts, timeline Gantt, édition temps réel
- **3 Modes Scan** : AST (précis), Regex (rapide), Both (comparatif avec analyse delta)
- **119 Règles Migration** : Couvrant breaking changes, dépréciations, best practices (to18, to19, to20, to21)
- **Analyse Cross-File** : Détection TypeScript ↔ templates HTML
- **Multi-Projets** : Support Nx Monorepo et Angular Standalone

---

## 🎓 Cas d'Usage

### Migration Version Angular
Upgrade Angular 17→21 avec liste complète changements et estimations :
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

**119 règles** sur 4 versions :

| Migration | Obligatoires | Recommandées | Optionnelles | Total |
|-----------|--------------|--------------|--------------|-------|
| **17→18** | 8            | 17           | 0            | 25    |
| **18→19** | 15           | 13           | 9            | 37    |
| **19→20** | 6            | 7            | 5            | 18    |
| **20→21** | 21           | 6            | 12           | 39    |

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
- Support Angular 17, 18, 19, 20, 21

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

Pour toute préoccupation de sécurité ou signaler une vulnérabilité, voir [SECURITY.md](https://github.com/silvestv/migration-planificator-documentation/blob/master/SECURITY.md)

---

## 🤝 Contribuer & Support

Ce projet est sous licence **Apache License 2.0** - libre pour usage commercial et open-source.

### 🐛 Signaler un Bug

Vous avez trouvé un bug ? Signalez-le via GitHub Issues :

1. **Aller sur** : [GitHub Issues](https://github.com/silvestv/migration-planificator-documentation/issues/new/choose)
2. **Sélectionner** : Template "Bug Report"
3. **Remplir** :
   - Description du bug
   - Étapes pour reproduire
   - Comportement attendu vs réel
   - Votre environnement (OS, version Node.js, version Angular)
   - Commande utilisée

**Lien direct** : [Signaler un Bug](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=bug_report.md)

### ✨ Demander une Fonctionnalité

Vous avez une idée d'amélioration ?

1. **Aller sur** : [GitHub Issues](https://github.com/silvestv/migration-planificator-documentation/issues/new/choose)
2. **Sélectionner** : Template "Feature Request"
3. **Décrire** :
   - Le problème que vous essayez de résoudre
   - Votre solution proposée
   - Cas d'usage et qui en bénéficie
   - Maquettes ou exemples éventuels

**Lien direct** : [Demander une Fonctionnalité](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=feature_request.md)

### ❓ Poser une Question

Besoin d'aide ou vous avez des questions ?

1. **Aller sur** : [GitHub Issues](https://github.com/silvestv/migration-planificator-documentation/issues/new/choose)
2. **Sélectionner** : Template "Question"
3. **Vérifier d'abord** :
   - [FAQ](https://github.com/silvestv/migration-planificator-documentation/blob/master/FAQ.md)
   - [Guide de Dépannage](https://github.com/silvestv/migration-planificator-documentation/blob/master/TROUBLESHOOTING.md)

**Lien direct** : [Poser une Question](https://github.com/silvestv/migration-planificator-documentation/issues/new?template=question.md)

### 📧 Contact Direct

Pour les problèmes urgents, préoccupations de sécurité ou demandes commerciales :

📧 **Email** : victor.silvestre.dev@gmail.com

**Utilisateurs entreprise** : Contactez-nous pour licence commerciale, support prioritaire et fonctionnalités personnalisées.

---

## 📝 Licence

© 2025 Victor SILVESTRE

Sous licence **Apache License, Version 2.0** (la "Licence").
Vous ne pouvez utiliser ce fichier qu'en conformité avec la Licence.
Vous pouvez obtenir une copie de la Licence à :

http://www.apache.org/licenses/LICENSE-2.0

### Conditions Principales

- ✅ **Usage Commercial** - Utilisation libre pour tout usage incluant commercial
- ✅ **Modification** - Modifier et distribuer vos propres versions
- ✅ **Distribution** - Redistribuer les versions originales ou modifiées
- ✅ **Droits de Brevets** - Inclut une concession explicite des droits de brevet des contributeurs
- ✅ **Usage Privé** - Utiliser en privé sans aucune obligation

### Obligations

Lors de la distribution ou modification :
- 📝 Inclure le fichier LICENSE
- 📝 Inclure le fichier NOTICE (si présent)
- 📝 Indiquer tout changement significatif apporté au code

### Avertissement

Sauf si requis par la loi applicable ou convenu par écrit, le logiciel
distribué sous la Licence est distribué "TEL QUEL",
SANS GARANTIES OU CONDITIONS D'AUCUNE SORTE, expresses ou implicites.
Consultez la Licence pour les autorisations et limitations
spécifiques régissant la Licence.

Voir [LICENSE](LICENSE) pour le texte complet de la licence.

📧 **Contact** : victor.silvestre.dev@gmail.com

---

## 🙏 Remerciements

Construit avec **ts-morph** (AST TypeScript), **@angular/compiler** (parsing HTML), **TailwindCSS** (design), **Chart.js** (visualisation)

---

**🚀 Commencez à planifier votre migration Angular dès aujourd'hui !**

---

📧 [Contact](mailto:victor.silvestre.dev@gmail.com) • 📦 [Package NPM](https://www.npmjs.com/package/@silvestv/migration-planificator)
