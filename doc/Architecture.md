# Architecture Data & BI — Prévention des Feux de Forêt (SDIS 77)

Ce document décrit l'architecture technique et l'organisation du projet ainsi que la stuck à utiliser:

## 1. Architecture des couches de données

| Couche | Rôle | Contenu envisagé | Outil | Questions servies | Fréquence de mise à jour |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Sources** | Ce que vous recevez, tel quel | • `artif-departement.csv` & `artif-commune.csv`<br>• `mos-occupation-du-sol-2025-and-2021...csv`<br>• `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv`<br>• `Incendies.csv` (historique des feux) | Exports open data (`data.gouv.fr`, IPR, Météo-France) | Périmètre et périodes disponibles (2021–2026) | Ponctuelle / saisonnière |
| **Données brutes** | Conservées sans modification | Copie intacte des 7 CSV dans `data/raw/` | Dossier local + GitHub | Traçabilité et reproductibilité | À chaque réception de fichier |
| **Données nettoyées** | Types, formats, doublons, valeurs manquantes traitées | Séparateurs unifiés (`,` / `;`), dates ISO, colonnes MDF alignées (`dep_nom` → `nom_dep`), codes INSEE/dép. formatés, filtre IDF (75–95) | Python (`pandas`) | Fiabilité des filtres IDF vs 77 et propreté des clés | À chaque mise à jour brute |
| **Données consolidées** | Sources croisées au même grain | • Fusion `mdf_2024–2026` (grain jour × dép.)<br>• Agrégation MOS par commune (`insee`, surfaces forêts vs artificialisées)<br>• Jointure commune/dép. (`artif` + `MOS` + `Incendies`) | Python (`pandas`, `geopandas`) | Croisement météo, occupation des sols et sinistres | À chaque exécution du pipeline |
| **Données prêtes pour l'analyse** | Ce que lisent les indicateurs | Modèle en étoile dans `data/mart/` :<br>• **Dimensions** : `dim_territoire`, `dim_temps`<br>• **Faits** : `fait_vigilance_mdf`, `fait_incendies` | Python + Power BI (modèle & DAX) | Calcul des KPI (jours vigilance $\ge 3$, taux de forêt, comparaison 77 vs IDF) | Hebdomadaire / à la demande |
| **Restitution** | Ce que lit le commanditaire | Tableaux de bord Power BI pour le SDIS 77 (saisonnalité MDF, vulnérabilité MOS/artificialisation, communes à risque) | Power BI Desktop + GitHub (`README.md`) | Aide à la décision et prévention opérationnelle | Synchronisée avec `data/mart/` |

---

## 2. Stack technique retenue

Une architecture simple, pragmatique et reproductible :

* **Traitement & préparation (ETL léger)** : Python (`pandas`, `numpy``)
* **Stockage intermédiaire & analytique** : Fichiers normalisés (CSV) organisés en arborescence claire :
  * `data/raw/` : données brutes immuables
  * `data/clean/` : données nettoyées et consolidées
  * `data/mart/` : tables dimensionnelles et de faits prêtes pour la BI
* **Restitution & visualisation (BI)** : Power BI Desktop (modèle en étoile, mesures DAX, cartographie et tableaux de bord décisionnels pour le SDIS 77)
* **Versioning, collaboration & documentation** : GitHub (code source Python, suivi des évolutions et documentation dans `docs/architecture.md`)

---

## 3. Étapes de réalisation

1. **Collecte (`data/raw/`)** : Dépôt des fichiers CSV bruts sans aucune altération afin de garantir la traçabilité des sources.
2. **Nettoyage & Consolidation (Python)** :
   * Harmonisation des encodages, séparateurs, formats de dates (ISO) et codes géographiques (INSEE / Départements).
   * Fusion historique des fichiers Météo des Forêts (`mdf_2024` à `mdf_2026`).
   * Agrégation du Mode d'Occupation du Sol (MOS) à la maille communale et croisement avec les données d'artificialisation (`artif`) et l'historique des `Incendies`.
3. **Modélisation (`data/mart/`)** : Structuration et export des tables finales selon un schéma en étoile :
   * **Tables de dimensions** : `dim_territoire`, `dim_temps`
   * **Tables de faits** : `fait_incendies`, `fait_vigilance_mdf`
4. **Restitution (Power BI)** : Connexion aux tables du dossier `data/mart/`, configuration des relations du modèle en étoile, création des indicateurs (DAX) et conception des tableaux de bord opérationnels pour le SDIS 77.
