# Projet de Transformation de Données avec dbt : Analyse de Commandes E-commerce

Ce projet est une démonstration de mes compétences en Data Engineering avec dbt. L'objectif est de prendre des données brutes de commandes d'un magasin en ligne, de les nettoyer, de les transformer et de créer des tables d'analyse propres et fiables, prêtes à être utilisées dans un outil de Data Visualisation comme Tableau ou Power BI.

---

### 🎯 Contexte Business

Une entreprise e-commerce fictive, "Cyclistic", souhaite mieux comprendre ses ventes. Les données brutes sont réparties dans plusieurs fichiers (commandes, clients, produits) et ne sont pas directement exploitables.

**Le problème à résoudre :** Créer un modèle de données unique et fiable pour répondre à des questions business clés, telles que :
* Quel est le revenu total par client ?
* Quels sont les produits les plus vendus ?
* Quelle est la répartition des ventes par mois ?

---

### 🗃️ Source des Données

Les données utilisées sont un jeu de données public simulant des ventes. Il est composé de trois fichiers CSV : `customers.csv`, `orders.csv`, et `payments.csv`.

---

### 🏗️ Architecture et Démarche

Le projet suit les meilleures pratiques de dbt avec une architecture en trois couches :

1.  **Sources** : Déclaration des données brutes.
2.  **Staging (`stg_`)** : Nettoyage simple, renommage des colonnes et tests de qualité de base (ex: pas de commandes sans client).
3.  **Marts (`marts_`)** : Création des tables finales agrégées. Ici, j'ai créé deux tables principales :
    * `dim_customers` : La table de dimension contenant des informations sur chaque client.
    * `fct_orders` : La table de faits contenant les métriques clés de chaque commande (montant, statut, etc.).

---

### ✅ Tests de Qualité des Données

Pour garantir la fiabilité des données, plusieurs tests ont été mis en place sur les colonnes clés via les fichiers `.yml` :
* `unique` : Pour s'assurer qu'il n'y a pas de doublons d'ID.
* `not_null` : Pour vérifier que les identifiants critiques ne sont jamais vides.
* `accepted_values` : Pour s'assurer que le statut d'une commande est bien l'un des statuts attendus.

---

### ⚙️ Comment Lancer le Projet

1.  **Prérequis :** Avoir `dbt-core` et un adaptateur de base de données (ex: `dbt-duckdb`) installés.
2.  **Cloner le repository :**
    `git clone https://github.com/Alisson-K/dbt-challenge.git`
3.  **Installer les dépendances :**
    `dbt deps`
4.  **Lancer les transformations :**
    `dbt run`
5.  **Lancer les tests :**
    `dbt test`
