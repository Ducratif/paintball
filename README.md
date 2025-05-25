# 🎮 Système Paintball – GuerreRP

> Système complet de paintball compétitif développé pour un serveur RP structuré. Intègre gestion d'équipes, compétences, score dynamique, événements spéciaux et un menu admin avancé.

---

## 📦 COMPOSANTS PRINCIPAUX

### 🔫 Gameplay principal
- Détection de zone pour activer les événements paintball
- Gestion complète des kills, respawns, dégâts, et points
- HUD personnalisé avec scores en temps réel
- Système de respawn avec timer et réduction via compétences
- Séparation des armes et règles uniquement en zone
- Support multi-équipe, classement, règles personnalisées

### 👥 Gestion des équipes
- Création dynamique de teams
- Attribution de joueurs, gestion des scores d’équipe
- Sauvegarde en base via `paintball_teams` et `paintball_players`
- Affichage des stats par joueur et par team

### 🧠 Système de compétences
- 7 compétences actuelles, chacune ayant un effet unique
- Types : passive, bonus, permanente
- Stockage SQL dans `paintball_skills` et `paintball_team_skills`
- Application automatique selon les events (kill, domination, respawn…)
- Achat via menu joueur ou attribution via admin

---

## 🛠️ BASE DE DONNÉES

### 📋 Tables requises :
- `paintball_teams`
- `paintball_players`
- `paintball_skills`
- `paintball_team_skills`

> Toutes les compétences sont chargées depuis `skills.lua` et insérées automatiquement au démarrage si manquantes.

---

## 🧩 INTÉGRATION

### Frameworks compatibles :
- ESX Legacy
- ox_lib (menu, UI, notifications)
- oxmysql

### Système de zones :
- Les zones paintball sont activées via `Config.Zones`
- Gestion auto de l'entrée/sortie de zone (`enteredZone`, `onLeaveZone`)

### Interface :
- Ouverture du menu joueur via touche `F9` (en zone)
- Intégration clean dans HUD si activée

---

## 🎯 COMPÉTENCES INCLUSES

| Nom               | Effet                                                                              |
|-------------------|-------------------------------------------------------------------------------------|
| Maître Tireur     | Chaque kill vaut 3 points au lieu de 2                                              |
| Tueur en Série    | +2 points tous les 3 kills consécutifs                                              |
| Renforts Instantanés | Temps de respawn réduit de 5s                                                  |
| Vision Tactique   | Blips sur ennemis toutes les 60s, visible 10s                                       |
| Recrue Brute      | Démarre avec 10 points quand le joueur rejoint une équipe                           |
| Motivation        | Chaque kill de l’équipe donne +1 point à chaque coéquipier dans la zone             |
| Zone Dominée      | Si aucun membre ne meurt pendant 3 min avec 5 ennemis en zone → +5 points à l’équipe |

---

## 🔐 SYSTÈME ADMIN

Le menu admin est séparé dans `/admin/` (voir README_Admin_Paintball.md).  
Commandes sécurisées et fonctionnalités puissantes pour staff/dev.

- `/adminskills` → accès au menu contextuel ox_lib (si ID autorisé)
- Modification des compétences, équipes, stats, debug, logs, etc.

---

## 📁 STRUCTURE GÉNÉRALE

```
paintball/
├── client.lua              -- Gameplay joueur (zone, kills, HUD, respawn...)
├── server.lua              -- Logique serveur principale
├── skills.lua              -- Déclaration, stockage et logique des compétences
├── config.lua              -- Zones, cooldowns, etc.
├── fxmanifest.lua          -- Dépendances et ressources
│
├── admin/                  -- Menu de gestion staff complet (voir README dédié)
│   ├── client.lua, server.lua
│   ├── ui/, modules/, dialogs.lua, etc.
```

---

## ✅ BONNES PRATIQUES

- 💾 Faire une sauvegarde SQL avant d'ajouter une nouvelle compétence
- 🔄 Relancer la ressource `paintball` pour recharger les compétences ou zones
- 🧪 Utiliser les outils de test admin pour vérifier l’équilibrage
- 👥 Garder une team minimale active pour “Zone Dominée” (5 ennemis min requis)

---

## 🧠 TO DO (suggestions)
- Ajout d’un classement permanent via Discord/web
- Mode tournoi avec round / élimination
- Sauvegarde des kills par session et historique long terme
- Export CSV / JSON des stats
- Intégration scoreboard complet via NUI

---

**📌 Créé par : Ducratif**  
Framework : ESX + ox_lib + oxmysql  
Compatible avec tout serveur RP structuré 🧩