# 📚 v7 Documentation Reorganization Kit

**2 prompts pour analyser et réorganiser la doc v7 → v8**

---

## 📁 Fichiers

### 🔍 Prompts (Instructions)

| Fichier | Description | Output |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d'ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analyse détaillée d'UN folder avec % match | `[folder]-detailed-analysis.md` |

---

## 🚀 Utilisation

### 1️⃣ Vue d'Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère** :
- 📊 Executive summary (stats globales)
- 📁 Analyse des 21 folders
- 🎯 Matrice de priorisation
- ✅ Action items
- ⚠️ Risques
- 📈 Métriques

**Taille** : ~50-60 pages Markdown

---

### 2️⃣ Analyse Détaillée d'un Folder

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère** :
- 📊 Stats du folder
- 📋 Tableau détaillé organisé comme Experience League
- 🔗 Liens cliquables (v7 + Experience League)
- 📈 Jusqu'à 3 matchs v8 par fichier avec %
- 📄 Recap file par file
- 🎯 Plan de réorganisation
- ✅ Checkboxes pour tracking

**Taille** : ~30-40 pages Markdown

---

## 📊 Exemple d'Output

### Prompt 1 (Overview)
```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Prompt 2 (Detailed Folder)
```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯 Workflow Recommandé

### Semaine 1 : Vue d'ensemble
1. Exécuter **Prompt 1** → Obtenir `v7-reorganization-overview.md`
2. Identifier les folders prioritaires
3. Partager avec stakeholders

### Semaine 2-4 : Analyse détaillée
1. Pour chaque folder prioritaire :
   - Exécuter **Prompt 2** 
   - Obtenir `[folder]-detailed-analysis.md`
   - Valider les décisions
   - Commencer les actions

### Semaine 5+ : Exécution
1. Supprimer les fichiers identifiés (DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Migrer le contenu manquant (MOVE)
4. Reviewer les cas ambigus (REVIEW)

---

## 💡 Tips

### Pour les prompts
- ✅ Copier/coller l'intégralité du prompt
- ✅ Ne pas modifier le format
- ✅ Adapter seulement le chemin du folder (Prompt 2)

### Pour les outputs
- 📝 Output en Markdown (pas HTML)
- 🔗 Liens cliquables automatiques
- ✅ Checkboxes pour tracking
- 📊 Stats et pourcentages
- 🎨 Emojis et icônes

### Pour l'analyse
- 🎯 Commencer par les gros folders (delivery, workflow)
- ⚡ Prioriser les quick wins (95-100% match)
- 🔍 Reviewer manuellement les cas ambigus (<70% match)
- ✅ Valider avec SME avant suppression massive

---

## ⚠️ Important

### Avant de supprimer
1. ✅ Vérifier l'équivalent v8
2. ✅ Vérifier qu'il n'y a pas de contenu v7-specific
3. ✅ Mettre à jour `redirects.csv`
4. ✅ Valider avec un expert (pour les premiers)

### Pour les fichiers v7-only
1. ✅ Ajouter un badge au début du fichier
2. ✅ Expliquer pourquoi c'est v7-only
3. ✅ Lien vers les limitations v8

---

## 🆘 Support

**Questions** ?  
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Output trop long → Demander un résumé
- Besoin d'aide → Ping l'équipe doc

---

**Dernière mise à jour** : 2026-01-13

