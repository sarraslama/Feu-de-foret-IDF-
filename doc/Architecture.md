# Architecture Data et Stack à utiliser

Ce document décrit l'architecture technique, l'organisation du projet ainsi que la stack retenue :

## 1. Architecture des couches de données

| Couche | Rôle | Contenu envisagé | Outil | Questions servies | Fréquence de mise à jour |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Sources** | Ce que vous recevez, tel quel | • `artif-departement.csv` & `artif-commune.csv` (artificialisation 2017/2018–2021)<br>• `mos-occupation-du-sol-2025-and-2021...csv` (polygones forestiers IDF 2021–2025)<br>• `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv` (vigilance été 2024–2026)<br>• `Incendies.csv` (347 sinistres IDF dont 293 dans le 77, 2006–2025) | Exports open data (`data.gouv.fr`, IPR, Météo-France / BDIFF) | Périmètre, variables disponibles et recouvrement temporel | Ponctuelle / saisonnière |
| **Données brutes** | Conservées sans modification | Copie intacte des 7 CSV dans `data/raw/` | Dossier local + GitHub | Traçabilité et reproductibilité | À chaque réception de fichier |
| **Données nettoyées** | Types, formats, doublons, valeurs manquantes traitées | • Séparateurs unifiés (`,` / `;`) et dates ISO (`Date de première alerte` en `Incendies.csv` + `date` en `mdf_*`)<br>• Alignement MDF (`dep_nom` → `nom_dep`, zéro initial `01`–`09`)<br>• Standardisation codes INSEE (`5` car.) / dép. (`2` car.) et filtrage IDF (`75–95`) | Python (`pandas`) | Fiabilité des filtres IDF vs 77, propreté des clés et qualité des données | À chaque mise à jour brute |
| **Données consolidées** | Sources croisées au même grain | • **Grain Département × Jour** : fusion `mdf_2024–2026` croisée avec `Incendies` (sur `num_dep` + `date`) pour analyser la vigilance météo les jours de feu (2024–2025)<br>• **Grain Commune** : agrégation MOS (`st_area_sh`, évolution 2021–2025) + jointure avec `artif-commune` et `Incendies` (sur `insee` / `commune_code`) | Python (`pandas`) | Croisement sinistres, vigilance météo, surfaces brûlées, boisement et artificialisation | À chaque exécution du pipeline |
| **Données prêtes pour l'analyse** | Ce que lisent les indicateurs | Tables finales dans `data/mart/` :<br>• **Dimensions** : `dim_commune`, `dim_departement`, `dim_temps`<br>• **Faits** : `fait_incendies` (sinistres & surfaces), `fait_vigilance_mdf` (niveaux J1/J2 par dép. et jour) | Python + Power BI (modèle & DAX) | Calcul des KPI (nb d'incendies, surfaces parcourues/forêt, jours vigilance $\ge 3$, comparaison 77 vs IDF) | Hebdomadaire / à la demande |
| **Restitution** | Ce que lit le commanditaire | Tableaux de bord Power BI pour le SDIS 77 (zones et communes touchées dans le 77, saisonnalité, croisement météo/sinistres, vulnérabilité MOS/artificialisation) | Power BI Desktop + GitHub (`README.md`) | Aide à la décision et prévention opérationnelle | Synchronisée avec `data/mart/` |

---

## 2. Stack technique retenue

Une architecture simple:

- **Traitement & préparation (ETL léger)** : Python (`pandas`, `numpy`)
- **Stockage intermédiaire & analytique** : Fichiers normalisés (CSV) organisés en arborescence claire :
  - `data/raw/` : données brutes immuables
  - `data/clean/` : données nettoyées et consolidées
  - `data/mart/` : tables dimensionnelles et de faits prêtes pour la BI
- **Restitution & visualisation (BI)** : Power BI Desktop (modèle relationnel, mesures DAX, cartographie et tableaux de bord décisionnels pour le SDIS 77)
- **Versioning, collaboration & documentation** : GitHub (code source Python, suivi des évolutions et documentation dans `docs/architecture.md`)

---

## 3. Étapes de réalisation

1. **Collecte (`data/raw/`)** : Dépôt des 7 fichiers CSV bruts (`artif-departement.csv`, `artif-commune.csv`, `mos-...csv`, `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv`, `Incendies.csv`) sans aucune altération.
2. **Nettoyage & Consolidation (Python)** :
   - Harmonisation des séparateurs, parsing des dates (`Date de première alerte` et `date` MDF) et formatage des codes géographiques (`Code INSEE` / `commune_code` sur 5 caractères, `Département` / `num_dep` sur 2 caractères).
   - Fusion des fichiers Météo des Forêts (`mdf_2024` à `mdf_2026`) et croisement avec `Incendies.csv` sur le couple `(département, date)`.
   - Agrégation des surfaces forestières du MOS (2021 et 2025) par commune (`insee`) et jointure avec `artif-commune` et `Incendies.csv` à la maille communale.
3. **Modélisation (`data/mart/`)** : Export des tables finales séparées par grain :
   - **Dimensions** : `dim_commune` (reliée à `dim_departement`), `dim_departement`, `dim_temps`
   - **Faits** : `fait_incendies`, `fait_vigilance_mdf`
4. **Restitution (Power BI)** : Connexion aux tables de `data/mart/`, configuration des relations `1 → *`, création des mesures DAX et conception des tableaux de bord opérationnels pour le SDIS 77.
