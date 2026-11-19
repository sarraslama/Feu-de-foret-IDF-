# Fiches d'indicateurs — Localisation et vulnérabilité spatiale des zones à risque

* **Autrice :** Fatiha Bouhadad
* **Version individuelle de travail :** 19 novembre 2026
* **Commanditaire :** SDIS 77. Étude de l'ensemble de l'Île-de-France, avec restitution départementale et lecture particulière du 77.
* **Diagnostic et objectif associés :** `01_diagnostic_objectif_KPI1.md`

---

## 1. KPI principal — Couverture spatiale des départs par zones prioritaires

| Rubrique | Spécification |
| :--- | :--- |
| **Question et objectif** | Quelles zones d'interface et de vulnérabilité spatiale concentrent le plus de départs de feux dans le 77 et en Île-de-France, à moyens maîtrisés ? Faire passer de $a\ \%$ à $b\ \%$ la part des départs de feux estivaux survenant dans des secteurs couverts par un dispositif adapté d'ici au 30 septembre 2027, sous une enveloppe $B$ de moyens alloués. $a$, $b$ et $B$ restent à mesurer ou à valider avec le SDIS 77. |
| **Numérateur** | Nombre de départs de feux éligibles (`Incendies.csv`) localisés dans les zones d'interface/vulnérabilité classées prioritaires et effectivement couvertes par un dispositif de prévention ou de surveillance adapté sur le secteur. Chaque départ compte une seule fois. |
| **Dénominateur** | Tous les départs de feux éligibles (`Incendies.csv`) de la période et du périmètre évalués, avec localisation exploitable (Code INSEE / géométrie) et périmètre de couverture connu. |
| **Formule** | $100 \times \frac{\text{départs couverts en zone prioritaire}}{\text{départs éligibles}}$. Dénominateur nul $\rightarrow$ valeur non calculable. |
| **Unité** | Pourcentage, accompagné du numérateur et du dénominateur (et de la densité par $\text{km}^2$ par typologie). |
| **Paramètres** | Fenêtre rétrospective (5 ans : 2021–2025, et saison estivale 1er juin–30 septembre), périmètre (Île-de-France / Seine-et-Marne), référentiel géographique (Lambert 93), règles de typologie des interfaces, seuil d'humidité/sécheresse et dispositif couvert. |
| **Grain** | Appariement au niveau communal (Code INSEE) et polygone/zone d'interface ; restitution par typologie de zone, département et saison. |
| **Période et fréquence** | Analyse rétrospective sur 5 ans (2021–2025) et suivi opérationnel sur la saison estivale du 1er juin au 30 septembre 2027. Remise des livrables selon le calendrier du projet (11 décembre 2026). |
| **Sources et champs** | • `Incendies.csv` (347 lignes, 24 colonnes après 3 lignes de métadonnées : `Année`, `Numéro`, `Département`, `Code INSEE`, `Nom de la commune`, `Date de première alerte`, surfaces parcourues/forêt/agricoles)<br>• MOS Île-de-France (`mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv`, 42 115 polygones filtrés sur *Bois ou forêts* : `insee`, `mos2021`, `Poste 2021`, `mos2025`, `Poste 2025`, `st_area_sh`, `st_length_`, `Geo Point`, `Geo Shape`)<br>• `artif-commune.csv` / `artif-departement.csv` (`commune_code`, `departement_code`, `pourcent_artif_1/2`, `surface_artif_1/2`, `flux_surface_1_2`, `commune_surface`)<br>• `mdf_2024.csv` à `mdf_2026.csv` (`date`, `num_dep`, `niveau_j1`, `niveau_j2`)<br>• Données SIM (humidité des sols) et dispositifs SDIS 77 à obtenir. |
| **Lignes utilisables** | Sur 2021–2025 : 182/182 feux en Île-de-France (dont 147 dans le 77) et 116/182 en saison estivale (juin–septembre, dont 87 dans le 77) ont `Année`, `Département`, `Code INSEE` et `Date de première alerte` renseignés. Sur l'historique complet 2006–2025 : 347/347 feux (dont 293 dans le 77). Aucun fichier SIM ni périmètre de patrouille SDIS 77 n'est encore fourni. |
| **Situation de référence** | Couverture actuelle ($a$) à mesurer avec le SDIS 77. Sur 2021–2025 dans le 77 (147 feux), 89 feux ($60,54\ \%$) sont dans la classe *Massifs boisés + terres agricoles* (proxy peu artificialisé) et 47 feux ($31,97\ \%$) dans *Interface habitat-forêt* (proxy mixte avec forêt). |
| **Proxy et biais** | La commune (Code INSEE) et les taux/flux d'artificialisation servent de proxy tant que la jointure point-polygone/distance en Lambert 93 et tous les postes MOS (agriculture, loisirs, habitat) ne sont pas croisés. L'absence de SIM empêche de mesurer directement l'assèchement des sols. |
| **Décision** | Hiérarchiser les secteurs à risque en Seine-et-Marne (ex. : massifs forestiers et interfaces périurbaines) pour cibler la prévention active et le dimensionnement des patrouilles sous enveloppe $B$. |
| **Propriétaire proposé** | Fatiha calcule et documente. Responsable qualité du groupe relit. Direction du SDIS 77 valide les zones prioritaires, $a$, $b$ et $B$. |

### Test d'un paramètre

Comparaison sur la fenêtre rétrospective de 5 ans (2021–2025) en Seine-et-Marne (77) et en Île-de-France selon le périmètre de zones prioritaires retenu (proxy communal forêt MOS + artificialisation `artif-commune.csv`).

| Périmètre prioritaire retenu (2021–2025) | Feux 77 couverts / 147 | Part 77 | Feux IDF couverts / 182 | Part IDF | Surface communale 77 concernée |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Massifs boisés + terres agricoles seuls (proxy)** | 89 | $60,54\ \%$ | 90 | $49,45\ \%$ | $1\ 932,79\ \text{km}^2$ |
| **Massifs boisés + terres agricoles + Interface habitat-forêt** | 136 | $92,52\ \%$ | 160 | $87,91\ \%$ | $5\ 116,31\ \text{km}^2$ |

> **Note analytique :** Ajouter l'interface habitat-forêt élargit fortement la surface couverte dans le 77 (de $1\ 932,79\ \text{km}^2$ à $5\ 116,31\ \text{km}^2$) et porte la part des feux couverts à $92,52\ \%$ (136/147). Il faut donc vérifier l'enveloppe $B$ avant de retenir un périmètre large.

### Jugement RACER

| Critère | Jugement |
| :--- | :--- |
| **Relevant** | Relie directement la localisation historique des départs et la vulnérabilité des milieux à la priorisation des patrouilles et de la prévention du SDIS 77. |
| **Accepted** | À valider avec le SDIS 77 pour la définition opérationnelle des zones prioritaires, des dispositifs couverts et des cibles $a$ et $b$. |
| **Credible** | Reproductible à partir de `Incendies.csv`, du MOS, d'`artif-commune.csv` et de `mdf_*.csv`, à condition de figer les règles de classification et le référentiel Lambert 93. |
| **Easy** | Calcul communal et croisement MDF déjà exécutés en Python ; jointure spatiale fine (*Kernel Density Estimation*) et croisement SIM/SDIS conditionnés par les données complémentaires. |
| **Robust** | La comparaison entre part des feux et densité par $\text{km}^2$, ainsi que la vérification des surfaces et de l'enveloppe $B$, limitent l'effet d'un zonage trop large. |

---

## 2. Garde-fou — Enveloppe de moyens et emprise spatiale ciblée ($B$)

| Rubrique | Spécification |
| :--- | :--- |
| **Risque visé** | Faire monter artificiellement la part de feux couverts en classant une trop grande part du territoire en « zone prioritaire » ou en mobilisant des moyens au-delà du budget/capacité du SDIS 77. |
| **Mesure** | Emprise géographique prioritaire ($S_{\text{prio}}$ en $\text{km}^2$) et moyens mobilisés (patrouilles / heures-équipe / ressources allouées $R$ rapportés à l'enveloppe $B$), suivis à périmètre de définition constant. |
| **Formule de suivi** | $100 \times \frac{R}{B}$ (avec $B > 0$, enveloppe validée par le SDIS 77) et part de surface prioritaire : $100 \times \frac{S_{\text{prio}}}{\text{surface totale du territoire}}$. |
| **Paramètres et périmètre** | Même fenêtre d'analyse et même périmètre géographique (77 et Île-de-France) que le KPI principal. |
| **Sources et faisabilité** | `artif-commune.csv` (`commune_surface`, `surface_artif_2`, `flux_surface_1_2`) et MOS (`st_area_sh`) disponibles pour les surfaces ; enveloppe $B$ et affectation des moyens SDIS 77 à obtenir. |
| **Seuil et décision** | Dépassement de $100\ \%$ de l'enveloppe $B$ ou emprise jugée non soutenable par le SDIS 77 $\rightarrow$ resserrer les seuils de priorité ou réallouer les moyens. |
| **Limite** | Les surfaces communales d'`artif-commune.csv` ne remplacent pas le découpage opérationnel exact des secteurs de patrouille ou des massifs/lisières du SDIS 77. |
| **Propriétaire proposé** | Référent opérationnel du SDIS 77 pour $B$, Fatiha pour le calcul, responsable qualité pour la relecture. |

* **Détournement possible :** Classer presque tout le 77 en zone à risque fait grimper mécaniquement le pourcentage de feux couverts. Le suivi simultané de la surface prioritaire et de $R/B$ rend ce gonflement visible.
* **Risque résiduel :** Une zone vulnérable bien couverte par la prévention ou la surveillance réduit la prédisposition, mais ne garantit pas l'absence de départ de feu ni l'efficacité terrain sans prise en compte des facteurs humains et opérationnels.

---

## 3. Indicateur descriptif calculable — Densité et part des départs par typologie (2021–2025 et 2006–2025)

| Rubrique | Spécification |
| :--- | :--- |
| **Rôle** | KPI secondaire pour quantifier la concentration des départs selon la typologie de zone et l'exposition MDF. |
| **Formule** | $\text{Part (\%)} = 100 \times \frac{\text{feux de la typologie}}{\text{total feux du périmètre}}$ ; $\text{Densité (5 ans)} = \frac{\text{feux de la typologie}}{\text{surface totale de la typologie (km}^2\text{)}}$ (et $\text{densité annuelle} = \frac{\text{densité 5 ans}}{5}$). |
| **Périmètre et période** | Île-de-France (8 départements, 1 267 communes) et Seine-et-Marne (77, 507 communes) ; fenêtre 5 ans 2021–2025 (182 feux IDF / 147 feux 77) et rappel historique 2006–2025 (347 feux IDF / 293 feux 77). |
| **Sources exactes** | `Incendies.csv`, `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv`, `artif-commune.csv`, `mdf_2024.csv` et `mdf_2025.csv` (et `mdf_2026.csv` pour la saison 2026). |
| **Lignes utilisables** | 182/182 feux sur 2021–2025 et 347/347 feux sur 2006–2025 rattachés sans valeur manquante à un code INSEE et une commune d'Île-de-France. Sur 2024–2025 (71 feux IDF, dont 65 dans le 77), 40 feux (dont 37 dans le 77) tombent dans les dates couvertes par les fichiers MDF fournis (juin–septembre). |
| **Référence** | Dans le 77 sur 2021–2025 (147 feux) : 89 feux ($60,54\ \%$, $0,0460\ \text{feu/km}^2$) en *Massifs boisés + terres agricoles* (proxy) et 47 feux ($31,97\ \%$, $0,0148\ \text{feu/km}^2$) en *Interface habitat-forêt* (proxy). |
| **Décision** | Concentrer l'analyse approfondie et les priorités opérationnelles du SDIS 77 sur les massifs boisés/espaces peu artificialisés et les interfaces habitat-forêt. |
| **Proxy et biais** | Le MOS fourni contient uniquement le poste *Bois ou forêts* (`Poste 2025` unique) ; les sous-catégories terres agricoles et zones de loisirs reposent donc sur un proxy communal (`pourcent_artif_2` et `flux_surface_1_2`). Les données SIM sont absentes. |
| **Propriétaire** | Fatiha ; relecture par le responsable qualité du groupe. |

### Résultats 2021–2025 par typologie (proxy communal) — Seine-et-Marne (77)

| Typologie de zone / critère | Feux 2021–2025 | Part 77 (2021–2025) | Densité 5 ans (2021–2025) | Rappel 2006–2025 (77) |
| :--- | :---: | :---: | :---: | :---: |
| **Massifs boisés + terres agricoles (proxy)** | 89 | $60,54\ \%$ | $0,0460\ \text{feu/km}^2$ | 179 feux ($61,09\ \%$, $0,0926\text{/km}^2$) |
| **Interface habitat-forêt (proxy)** | 47 | $31,97\ \%$ | $0,0148\ \text{feu/km}^2$ | 99 feux ($33,79\ \%$, $0,0311\text{/km}^2$) |
| **Autres zones / hors interface (proxy)** | 8 | $5,44\ \%$ | $0,0178\ \text{feu/km}^2$ | 11 feux ($3,75\ \%$, $0,0244\text{/km}^2$) |
| **Zones de loisirs / fréquentation (proxy)** | 3 | $2,04\ \%$ | $0,0084\ \text{feu/km}^2$ | 4 feux ($1,37\ \%$, $0,0112\text{/km}^2$) |

### Résultats 2021–2025 par typologie (proxy communal) — Île-de-France

| Typologie de zone / critère | Feux 2021–2025 | Part IDF (2021–2025) | Densité 5 ans (2021–2025) | Rappel 2006–2025 (IDF) |
| :--- | :---: | :---: | :---: | :---: |
| **Massifs boisés + terres agricoles (proxy)** | 90 | $49,45\ \%$ | $0,0349\ \text{feu/km}^2$ | 181 feux ($52,16\ \%$, $0,0702\text{/km}^2$) |
| **Interface habitat-forêt (proxy)** | 70 | $38,46\ \%$ | $0,0102\ \text{feu/km}^2$ | 131 feux ($37,75\ \%$, $0,0191\text{/km}^2$) |
| **Autres zones / hors interface (proxy)** | 18 | $9,89\ \%$ | $0,0086\ \text{feu/km}^2$ | 30 feux ($8,65\ \%$, $0,0143\text{/km}^2$) |
| **Zones de loisirs / fréquentation (proxy)** | 4 | $2,20\ \%$ | $0,0073\ \text{feu/km}^2$ | 5 feux ($1,44\ \%$, $0,0092\text{/km}^2$) |

> **Protection complémentaire :** Afficher systématiquement le nombre de feux, la surface en $\text{km}^2$ et la distinction entre proxy communal et jointure géométrique exacte.

---

## 4. Pré-mortem

*Classement qualitatif proposé, sans estimation statistique des probabilités.*

| Rang | Cause plausible d'échec | Probabilité appréciée | Gravité | Protection |
| :---: | :--- | :--- | :--- | :--- |
| **1** | Élargissement excessif du zonage « à risque » qui gonfle la part couverte sans cibler les moyens. | Plausible | Élevée | Suivre la surface prioritaire, la densité par $\text{km}^2$ et l'enveloppe $B$ avant validation. |
| **2** | Utilisation de proxies communaux ou d'une extraction MOS partielle comme si c'était une jointure fine multi-postes. | Plausible au vu des fichiers actuels | Élevée | Documenter les limites du MOS fourni (*Bois ou forêts* uniquement) et intégrer les postes complets + Lambert 93. |
| **3** | Absence des données SIM (humidité des sols) et couverture partielle des fichiers MDF (juin–septembre). | Avérée sur les fichiers actuels | Moyenne à élevée | Indiquer explicitement SIM absent et distinguer les feux hors fenêtre MDF (ex. : avril–mai dans le 77 en 2025). |

---

## 5. Jeu individuel proposé pour la mise en commun v0

| Rôle | Indicateur | Situation et raison |
| :--- | :--- | :--- |
| **KPI principal** | Part des départs de feux éligibles situés dans les zones prioritaires couvertes par un dispositif adapté ($a$ vers $b\ \%$) | Paramétré ; calcul opérationnel conditionné par les données de couverture/dispositifs du SDIS 77. |
| **Garde-fou** | Emprise prioritaire ($\text{km}^2$) et part de l'enveloppe $B$ mobilisée ($100 \times R / B$) | Surfaces calculables ; enveloppe $B$ et moyens SDIS 77 à obtenir. |
| **KPI secondaire** | Part et densité des feux ($\text{feu/km}^2$) par typologie de zone sur 2021–2025 | Calculé sur les fichiers disponibles (182 feux IDF / 147 feux 77 ; proxy communal). |
| **Contexte** | Niveaux MDF (`niveau_j1`) observés sur 2024–2026 et part des feux 2024–2025 hors période MDF | Calculé : dans le 77 en 2024, 120/120 jours MDF sont au niveau 1 ; en 2025, 98/120 ($81,67\ \%$) en niveau 1, 21/120 ($17,50\ \%$) en niveau 2, 1/120 ($0,83\ \%$) en niveau 3 ; sur 65 feux du 77 en 2024–2025, 37 tombent dans la période MDF (27 niv. 1, 10 niv. 2) et 28 hors période MDF. |
| **Écarté à ce stade** | Indice d'humidité des sols SIM et analyse géométrique multi-postes (agriculture, loisirs, bâti) | Données SIM absentes et MOS fourni restreint au poste *Bois ou forêts*. |

> Ce jeu reste une proposition individuelle. Les autres objectifs du groupe et leurs indicateurs doivent être mis en commun avant validation du jeu collectif v0.

---

## 6. Limites et éléments à obtenir

* L'extraction MOS fournie ne contient que le poste *Bois ou forêts* (`Poste 2025` unique) ; les catégories terres agricoles et zones de loisirs sont donc approchées par des proxies communaux (`pourcent_artif_2` et `flux_surface_1_2`).
* Les données d'humidité des sols (SIM Météo-France) ne sont pas présentes dans les fichiers reçus.
* Les fichiers MDF (`mdf_2024.csv` à `mdf_2026.csv`) couvrent la période estivale (juin–septembre/début octobre) : 28 des 65 feux du 77 en 2024–2025 (notamment en avril–mai 2025) surviennent hors de cette fenêtre.
* Les périmètres d'intervention, patrouilles et enveloppes ($a$, $b$, $B$) du SDIS 77 restent à collecter pour passer à l'évaluation opérationnelle complète.

---

## 7. Sources de travail

* Supports de cours *« De la question analytique aux objectifs »* et *« Définir des KPIs »*, fournis dans le cadre de l'UE01.B.
* `Incendies.csv` (347 événements en Île-de-France sur 2006–2025, dont 182 sur 2021–2025 et 293 dans le 77).
* `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv` (42 115 polygones, poste *Bois ou forêts*).
* `artif-commune.csv` et `artif-departement.csv` (données d'artificialisation des sols, `data.gouv.fr`).
* `mdf_2024.csv`, `mdf_2025.csv` et `mdf_2026.csv` (niveaux Météo des Forêts `niveau_j1` et `niveau_j2`).
