# Diagnostic et objectif SMART — Localisation et vulnérabilité spatiale des zones à risque

- **Autrice :** Fatiha Bouhadad
- **Version individuelle de travail :** 19 novembre 2026
- **Commanditaire :** Direction du SDIS 77
- **Périmètre d'étude :** Ensemble de l'Île-de-France, avec restitution départementale et lecture particulière du 77.

---

## 1. Diagnostic stratégique

| Niveau | Formulation | Statut et justification |
| :--- | :--- | :--- |
| **Stratégie** | Concentrer les moyens humains, matériels et financiers de prévention et de surveillance sur les zones d'interface les plus exposées en Île-de-France (et particulièrement dans le 77) pour préparer la saison estivale 2027. | Établi par la commande adaptée au SDIS 77, sous contrainte de moyens. |
| **Enjeu** | Une surveillance ou une prévention uniforme sur l'ensemble du territoire consommerait des ressources limitées sans cibler les secteurs les plus vulnérables. Le croisement occupation du sol / sécheresse aide à hiérarchiser les zones. | Contrainte de moyens établie dans la commande. Priorisation terrain et affectation exacte des patrouilles à confirmer avec le SDIS. |
| **Objectif** | Augmenter la part des départs de feux situés dans des secteurs couverts par une prévention ou une surveillance ciblée selon la vulnérabilité spatiale, à enveloppe de ressources maîtrisée. | Proposition à valider. Couverture spatiale actuelle, budget et cibles opérationnelles à mesurer ou demander. |
| **Action** | Croiser les données de départs de feux avec l'occupation du sol, l'artificialisation et l'humidité des sols sur l'Île-de-France (avec restitution départementale et lecture 77), puis identifier les zones critiques pour orienter la prévention et le dimensionnement des patrouilles. | Action proposée. Mise en œuvre soumise à la validation opérationnelle du commanditaire. |

---

## 2. Hypothèse et verdict

- **Hypothèse initiale :** Les incendies se déclenchent principalement là où il y a une forte concentration de forêts, de champs, de zones de loisirs et d'habitations, en particulier là où le sol est le plus sec.
- **Pièce de départ :** Hypothèse spatiale (liée à la localisation des feux et des milieux sur le territoire) formulée dans l'analyse individuelle sur les caractéristiques des zones les plus touchées en Île-de-France. La localisation des feux (`Incendies.csv`), l'occupation forestière (`MOS Île-de-France`) et l'artificialisation communale (`artif-commune.csv`) apportent un premier cadrage chiffré ; l'articulation fine avec la sécheresse des sols (`SIM`) et la géométrie exacte des interfaces bâti/forêt/loisirs reste à consolider.
- **Confirmation attendue :** Une concentration nette et statistiquement marquée des départs de feux en Île-de-France dans certaines typologies d'interfaces (ex. : interface habitat-forêt, massifs boisés bordés de terres agricoles, secteurs à fort assèchement des sols), stable et exploitable pour le SDIS 77.
- **Infirmation attendue :** Une dispersion homogène des départs de feux en Île-de-France ou l'absence de lien net entre ces configurations spatiales/hydriques et la densité d'incendies.
- **Résultats dans l'extraction (2021–2025 et historique complet 2006–2025) :** Sur **182 feux** recensés en Île-de-France sur 2021–2025 (147 dans le 77, 30 dans le 91, 4 dans le 78, 1 dans le 95) et **347 feux** sur 2006–2025 (293 dans le 77, 39 dans le 91, 9 dans le 95, 5 dans le 78, 1 dans le 94), les départs se concentrent majoritairement dans les communes de **massifs boisés et espaces peu artificialisés** ($49,45\ \%$ des feux IDF sur 2021–2025, densité de $0,0349\ \text{feu/km}^2$) et d'**interface habitat-forêt** ($38,46\ \%$ des feux IDF, densité de $0,0102\ \text{feu/km}^2$). Les données SIM d'humidité des sols sont absentes des fichiers traités, et les niveaux Météo des Forêts (MDF 2024–2025 en IDF) montrent que de nombreux feux surviennent dès niveau 1 ou hors période estivale MDF.
- **Verdict :** L'hypothèse d'une concentration spatiale en Île-de-France est **partiellement confirmée** par le premier croisement communal (forêt + artificialisation + historique des feux) : **$87,91\ \%$** des feux IDF sur 2021–2025 (160/182) se produisent dans les communes à massifs boisés peu artificialisés ou en interface habitat-forêt (dont $92,52\ \%$ sur les 147 feux du 77). En revanche, le rôle spécifique des zones de loisirs et de la sécheresse des sols (SIM) n'est pas encore démontré faute de données SIM et de postes MOS complets hors forêt.

### Synthèse des résultats par typologie de zone — Île-de-France (avec lecture 77)

| Typologie de zone / critère *(proxy communal)* | Densité ou part observée en IDF *(et lecture 77)* | Sol / sécheresse (MDF 2024–2025 / SIM) | Lecture pour le SDIS 77 et l'IDF |
| :--- | :--- | :--- | :--- |
| **Interface habitat-forêt** | **IDF :** 70 feux ($38,46\ \%$) sur 2021–2025, $0,0102\ \text{feu/km}^2$ *(131 feux / $0,0191$ sur 2006–2025)*.<br>**77 :** 47 feux ($31,97\ \%$), $0,0148\ \text{feu/km}^2$ *(99 feux / $0,0311$ sur 2006–2025)*. | **MDF IDF :** 15/26 feux en période MDF (9 niv. 1, 6 niv. 2) ; dont 14/23 dans le 77.<br>**SIM :** absent. | Deuxième pôle de départs en IDF et dans le 77 : cibler la prévention aux lisières urbanisées/boisées et surveiller les pics de niveau MDF 2. |
| **Massifs boisés + terres agricoles** | **IDF :** 90 feux ($49,45\ \%$) sur 2021–2025, $0,0349\ \text{feu/km}^2$ *(181 feux / $0,0702$ sur 2006–2025)*.<br>**77 :** 89 feux ($60,54\ \%$), $0,0460\ \text{feu/km}^2$ *(179 feux / $0,0926$ sur 2006–2025)*. | **MDF IDF :** 19/35 feux en période MDF (15 niv. 1, 4 niv. 2) ; dont 18/34 dans le 77.<br>**SIM :** absent. | Densité la plus forte et près de la moitié des feux IDF ($\sim 61\ \%$ dans le 77) : priorité forte pour les patrouilles et la surveillance, même en niveau MDF 1 ou hors été. |
| **Zones de loisirs / fréquentation** | **IDF :** 4 feux ($2,20\ \%$) sur 2021–2025, $0,0073\ \text{feu/km}^2$ *(5 feux / $0,0092$ sur 2006–2025)*.<br>**77 :** 3 feux ($2,04\ \%$), $0,0084\ \text{feu/km}^2$ *(4 feux / $0,0112$ sur 2006–2025)*. | **MDF IDF :** 1/3 feu en période MDF (1 niv. 1) ; dont 1/3 dans le 77.<br>**SIM :** absent. | Proxy limité aux communes à fort flux d'artificialisation : à croiser avec la fréquentation réelle et les sites de loisirs en IDF. |
| **Autres zones / hors interface** | **IDF :** 18 feux ($9,89\ \%$) sur 2021–2025, $0,0086\ \text{feu/km}^2$ *(30 feux / $0,0143$ sur 2006–2025)*.<br>**77 :** 8 feux ($5,44\ \%$), $0,0178\ \text{feu/km}^2$ *(11 feux / $0,0244$ sur 2006–2025)*. | **MDF IDF :** 5/7 feux en période MDF (3 niv. 1, 2 niv. 2) ; dont 4/5 dans le 77.<br>**SIM :** absent. | Part minoritaire des départs recensés en IDF : éviter d'y mobiliser excessivement des moyens dédiés aux feux de forêt/végétation. |

> **Note méthodologique :** Les résultats devront être affinés selon un référentiel géographique unifié (projection **Lambert 93**) et une jointure géométrique directe dès réception des postes MOS complets et des données SIM avant toute intégration définitive dans le plan de prévention.

---

## 3. De l'action à l'objectif SMART

1. **Action :** Réaliser des jointures spatiales et analyses de densité des départs de feux selon l'occupation du sol, l'artificialisation et l'humidité des sols sur l'Île-de-France (avec restitution départementale et lecture 77).
2. **Objectif :** Cibler la prévention active et le dimensionnement des patrouilles sur les zones d'interfaces les plus vulnérables.
3. **Objectif SMART proposé :** D'ici au **30 septembre 2027**, concentrer la prévention active et le dimensionnement des patrouilles du SDIS 77 sur les zones d'interface prioritaires identifiées en Seine-et-Marne afin de faire passer de **$a\ \%$ à $b\ \%$** la part des départs de feux estivaux survenant dans des secteurs couverts par un dispositif adapté, sans dépasser une enveloppe **$B$** de moyens alloués. L'analyse sera éclairée par l'étude de l'Île-de-France sur une fenêtre rétrospective de 5 ans et les indicateurs seront suivis à périmètre constant.

| Critère | Spécification |
| :--- | :--- |
| **Spécifique** | Concentration spatiale et densité des départs de feux selon le type d'occupation du sol (MOS Île-de-France), le degré d'artificialisation et l'indice d'humidité des sols. Analyse sur l'ensemble de l'Île-de-France avec restitution départementale et traduction opérationnelle sur les zones critiques du SDIS 77 (ex. : massif de Fontainebleau, crêtes et plateaux agricoles de la Brie). |
| **Mesurable** | Densité d'incendies par $\text{km}^2$ et par typologie d'interface en IDF et par département, accompagnée de la part de départs couverts ($a$ vers $b\ \%$) et des moyens mobilisés ($B$). $a$ et $b$ restent à définir/valider avec le SDIS. |
| **Atteignable** | Faisabilité technique élevée : un premier appariement communal (MOS forêt + artificialisation + Incendies + MDF) est déjà réalisé sur l'IDF ; la jointure spatiale fine et le *Kernel Density Estimation* sous Python (`geopandas`, `shapely`) ou QGIS nécessitent encore les polygones MOS complets, les données SIM et les périmètres d'intervention du SDIS 77. |
| **Réaliste** | Respecter l'enveloppe $B$, les contraintes opérationnelles du SDIS 77 et la cohérence avec les autres missions de sécurité civile. |
| **Temporel** | Évaluation rétrospective sur 5 ans (2021–2025) et application cartographique prédictive pour la saison estivale 2027 (1er juin au 30 septembre 2027). Remise des livrables selon le calendrier du projet (**11 décembre 2026**). |

**État de validation :** Objectif SMART paramétré avec une première base chiffrée par typologie de zone sur l'Île-de-France et le 77 (2021–2025 et 2006–2025), à finaliser avec le commanditaire. Les valeurs chiffrées cibles ($a$, $b$, $B$) ainsi que le croisement SIM et MOS complet restent à renseigner.

---

## 4. Situation de référence et faisabilité

- **Couverture spatiale / dispositif actuel ($a$) :** À mesurer à partir des données d'intervention et de déploiement disponibles du SDIS 77.
- **Cible de couverture / priorisation ($b$) :** À fixer avec le SDIS 77 après analyse rétrospective sur l'IDF / le 77 et simulation des zones prioritaires.
- **Enveloppe de moyens ($B$) :** À demander au SDIS 77.
- **Référence descriptive disponible :** Sur 2021–2025 en Île-de-France (182 feux), 90 feux ($49,45\ \%$, $0,0349\ \text{feu/km}^2$) surviennent dans les communes de massifs boisés/espaces peu artificialisés et 70 feux ($38,46\ \%$, $0,0102\ \text{feu/km}^2$) dans les communes d'interface habitat-forêt (dont respectivement 89 et 47 feux dans le 77 sur 147 feux).
- **Méthode analytique retenue :** Appariement communal et jointures spatiales / *Kernel Density Estimation* sous Python (`geopandas`, `shapely`) ou QGIS en croisant les localisations/centroïdes des feux passés avec les polygones du MOS.
- **Sources :** `Incendies.csv` (BDIFF, 347 feux IDF dont 293 dans le 77) + `MOS Île-de-France` (extraction forêt 2021–2025) + `artif-commune.csv` / `artif-departement.csv` (data.gouv.fr) + `Météo des Forêts` (`mdf_2024.csv` à `mdf_2026.csv`) ; données SIM Météo-France et interventions/plannings SDIS 77 à intégrer.
- **Périmètre géographique :** Ensemble de l'Île-de-France pour l'analyse comparative et la restitution départementale, avec lecture particulière sur la Seine-et-Marne (ex. : massif de Fontainebleau, crêtes et plateaux agricoles de la Brie).
- **Fenêtre temporelle :** Rétrospective sur 5 ans (2021–2025, complétée de l'historique 2006–2025 pour la robustesse) et projection/application pour la saison estivale 2027.

> **Règle de constance :** La fenêtre rétrospective de 5 ans et les règles de classification des interfaces et de l'humidité des sols doivent être fixées avant les comparaisons et maintenues constantes.

---

## 5. Test de cohérence stratégique

- **Comment améliorer la métrique sans améliorer la pertinence terrain ?** Élargir artificiellement le périmètre des zones classées « à risque » en Île-de-France ou dans le 77 ferait monter mécaniquement la part des feux situés en zone prioritaire sans aider le SDIS 77 à cibler ses moyens. Choisir un maillage trop grossier ou modifier les seuils d'humidité ou de densité en cours d'analyse biaiserait également la lecture. Les critères de zonage, les unités spatiales et les périodes doivent être définis avant l'évaluation.
- **Risque résiduel :** Une forte densité historique ou une sécheresse marquée des sols indique une vulnérabilité ou une prédisposition, mais ne garantit pas à elle seule l'occurrence exacte d'un départ de feu ni l'efficacité d'une patrouille sans prise en compte des facteurs humains et opérationnels sur le terrain.

---

## 6. Articulation avec le livrable de séance 2

La fiche des indicateurs figure dans `02_fiches_indicateurs_KPI1.md`. Ce document représente l'objectif individuel à mettre en commun avec ceux du groupe. Le jeu collectif v0 et les objectifs retenus restent à valider en groupe.
