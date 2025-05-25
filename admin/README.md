# 🎯 Menu Admin – Paintball GuerreRP

> 🛠️ Interface de gestion complète des compétences et stats Paintball, réservée aux admins CFX whitelistés.

---

## 📁 STRUCTURE

```
admin/
├── client.lua              -- Point d’entrée client
├── server.lua              -- Vérification des droits & triggers
├── config.lua              -- Liste des CFX ID autorisés
│
├── ui/
│   ├── menu.lua            -- Menu principal (ox_lib)
│   ├── teams.lua           -- Gestion des équipes
│   ├── players.lua         -- Gestion individuelle des joueurs
│   ├── config.lua          -- Modification dynamique des compétences
│   ├── stats.lua           -- Affichage des classements et logs
│   ├── debug.lua           -- Outils de test/dev
│   └── dialogs.lua         -- Popups réutilisables
│
├── modules/
│   ├── team_actions.lua    -- Requêtes/Actions sur les teams
│   ├── player_actions.lua  -- Requêtes/Actions sur les joueurs
│   ├── dynamic_config.lua  -- Modification des compétences (live)
│   ├── stats.lua           -- Classements et logs
│   ├── debug_tools.lua     -- Simulations / outils de test
│   └── permission.lua      -- Vérification des droits admin
```

---

## 🔐 SÉCURITÉ

- CFX license vérifiée dans `config.lua` :
```lua
AdminConfig = {
    AllowedCFX = {
        "license:123...", -- Ajoute ici tes ID autorisés
    },
    EnableLogging = true
}
```

- Toute fonction admin passe par `IsPlayerAdmin(source)`.

---

## 🧭 COMMANDES

- `/adminskills` → Ouvre le menu admin complet si autorisé

---

## 📋 FONCTIONNALITÉS

### 📁 Gestion des Équipes
- Voir compétences d’une team
- Ajouter / retirer une compétence
- Réinitialiser toutes les compétences
- Modifier score manuellement

### 🧍 Gestion des Joueurs
- Rechercher par prénom / ID / license
- Voir team, score, kills, compétences
- Reset score
- Kick d’une team
- Forcer une compétence à sa team

### ⚙️ Config Dynamique
- Modifier à chaud :
  - description
  - effet JSON
  - coût
- Directement dans la base sans restart

### 📊 Statistiques & Logs
- Top teams
- Top joueurs
- Derniers logs admin (optionnel)
- Export JSON de toutes les données (à venir)

### 🧪 Outils Debug
- Ajouter points à sa team
- Simuler une zone dominée
- Forcer une compétence
- Simuler un kill (option future)

---

## 🧠 RECOMMANDATIONS

- 💾 Utilise `admin_logs` (ou fichier `.log`) si tu veux tracer toutes les actions sensibles
- 🧪 Ajoute des compétences de test (`dev_only = true`) si besoin
- 📤 Prévois un bouton "export CSV/JSON" si tu veux intégrer du dashboard externe (Discord bot, WebUI...)