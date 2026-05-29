# 📊 Health-IA-Grafana - Tableaux de bord & Monitoring

**Monitoring et Data Visualization** de la plateforme HealthAI Coach.  
Ce repository centralise les configurations des tableaux de bord **Grafana** permettant d'analyser les données de l'application (utilisateurs, nutrition, sport et santé) en temps réel.

![Grafana](https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-000000?logo=json&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📋 Table des matières

- [Vue d'ensemble](#vue-densemble)
- [Architecture](#architecture)
- [Tableaux de bord inclus](#tableaux-de-bord-inclus)
- [Installation et Importation](#installation-et-importation)
- [Configuration de la source de données](#configuration-de-la-source-de-données)
- [Troubleshooting](#troubleshooting)

---

## Vue d'ensemble

**Health-IA-Grafana** ne contient pas de code source applicatif, mais les exports JSON des dashboards analytiques.

Ces fichiers permettent de recréer instantanément l'environnement de monitoring de la plateforme sur n'importe quelle instance Grafana.

Les données affichées proviennent directement de la base de données **PostgreSQL** gérée par le Backend.

**Point d'entrée recommandé** :  
Le repository [Health-IA-Workspace](https://github.com/GroupMSPR/Health-IA-Workspace) qui orchestre l'ensemble du projet, y compris le conteneur Grafana.

---

## Architecture

### Structure du projet

```text
Health-IA-Grafana/
├── exercisesGrafana.json       # Dashboard des exercices physiques
├── foodsGrafana.json           # Dashboard nutritionnel
├── healthMetricsGrafana.json   # Dashboard des métriques de santé
└── usersGrafana.json           # Dashboard d'analyse des utilisateurs
```

---

## Tableaux de bord inclus

Chaque fichier JSON correspond à un espace de visualisation spécifique.

---

### 👥 Users Dashboard (`usersGrafana.json`)

- Suivi des inscriptions
- Répartition démographique
- Typologie des utilisateurs
- Statistiques d'engagement

---

### 🍎 Foods Dashboard (`foodsGrafana.json`)

- Analyse du catalogue d'aliments
- Statistiques nutritionnelles
- Moyennes des macronutriments :
  - protéines
  - glucides
  - lipides
- Aliments les plus populaires

---

### 💪 Exercises Dashboard (`exercisesGrafana.json`)

- Suivi des activités physiques
- Répartition par difficulté
- Durée moyenne des exercices
- Estimation des calories brûlées

---

### 📊 Health Metrics Dashboard (`healthMetricsGrafana.json`)

- Évolution du poids
- Suivi de l'IMC
- Tendances de fréquence cardiaque
- Suivi de la tension artérielle

> Les données affichées sont anonymisées pour les vues globales.

---

## Installation et Importation

### Prérequis

- Une instance Grafana en cours d'exécution
  - généralement accessible sur :

```txt
http://localhost:3000
```

- Les identifiants administrateur Grafana
  - par défaut :

```txt
admin / admin
```

---

## Étapes d'importation

### 1. Cloner le repository

```bash
git clone https://github.com/GroupMSPR/Health-IA-Grafana.git
cd Health-IA-Grafana
```

---

### 2. Ouvrir Grafana

Exemple :

```txt
http://localhost:3000
```

---

### 3. Importer un dashboard

Dans Grafana :

1. Ouvrir le menu :
   - `+`
   - puis `Import`

2. Cliquer sur :

```text
Upload JSON file
```

3. Sélectionner un fichier :

```text
usersGrafana.json
```

4. Choisir la Data Source PostgreSQL

5. Cliquer sur :

```text
Import
```

Le dashboard devient immédiatement opérationnel.

---

### 4. Répéter l'opération

Importer les autres fichiers JSON :

- `foodsGrafana.json`
- `exercisesGrafana.json`
- `healthMetricsGrafana.json`

---

## Configuration de la source de données

Avant d'importer les dashboards, Grafana doit être connecté à PostgreSQL.

---

### Étapes

Dans Grafana :

1. Aller dans :

```text
Configuration → Data Sources
```

2. Cliquer sur :

```text
Add data source
```

3. Sélectionner :

```text
PostgreSQL
```

---

## Paramètres de connexion

| Champ | Valeur |
|--------|--------|
| Host | `pgsql:5432` |
| Host local | `localhost:55432` |
| Database | `laravel` |
| User | `sail` |
| Password | `password` |
| TLS/SSL Mode | `disable` |

> Utiliser `localhost:55432` uniquement si Grafana tourne hors du réseau Docker.

---

### Validation

Cliquer sur :

```text
Save & Test
```

Un message vert doit confirmer la connexion PostgreSQL.

---

## Troubleshooting

---

### Message : "Datasource not found"

#### Problème

Grafana ne trouve pas la source de données lors de l'import.

#### Solution

Le nom de la Data Source ne correspond pas à celui enregistré dans le JSON exporté.

Lors de l'import :

- utilisez le menu déroulant Grafana
- réassignez la bonne source PostgreSQL

---

### Les panneaux affichent "No data"

#### Problème

Le dashboard s'affiche mais tous les graphiques sont vides.

#### Solution

Vérifiez :

- l'intervalle de temps Grafana (`Time Range`)
- la présence réelle de données PostgreSQL
- que les seeders Laravel ont bien été exécutés

---

## 📚 Documentation supplémentaire

- [Grafana Documentation](https://grafana.com/docs/grafana/latest/)
- [Grafana PostgreSQL Data Source](https://grafana.com/docs/grafana/latest/datasources/postgres/)

---

## 👥 Équipe

Développeurs MSPR :

- Ilan
- Anthony
- Diana

---

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 🔗 Liens

- **Organization** : GroupMSPR
- **Workspace** : Health-IA-Workspace
- **Frontend** : Health-IA-Frontend
- **Backend** : Health-IA-Backend
- **ETL** : Health-IA-ETL
- **FastAPI** : Health-IA-FastAPI

---

Dernière mise à jour : 29 mai 2026

Pour toute question ou contribution, consultez le repository ou ouvrez une issue.
