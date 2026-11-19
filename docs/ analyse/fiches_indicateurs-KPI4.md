# Fiches d'indicateurs — Répartition budgétaire et allocation optimisée des ressources


---

## 1. KPI principal — Taux de réduction des feux de forêt majeurs (≥ 1 ha) en zones prioritaires

| Rubrique | Spécification |
| :--- | :--- |
| **Question et objectif** | Comment répartir au mieux un budget et des ressources limitées afin de protéger en priorité les zones les plus à risque ? Réduire de **10 %** le nombre de feux de forêt majeurs ($\ge 1\text{ ha}$) dans les **10 communes/massifs les plus vulnérables** de Seine-et-Marne d'ici la fin de la saison estivale **2027** (30 septembre 2027), sous contrainte d'enveloppe budgétaire $B$. |
| **Numérateur** | Nombre d'événements BDIFF éligibles survenus dans le périmètre des 10 communes prioritaires ($Z_{10}$) dont la surface parcourue est supérieure ou égale à $10\,000\text{ m}^2$ ($1\text{ hectare}$). Chaque événement compte une seule fois. |
| **Dénominateur** | Nombre de référence de feux majeurs ($\ge 1\text{ ha}$) sur $Z_{10}$ sur la période historique de référence (ou, pour le suivi de gravité interne, ensemble des feux éligibles sur $Z_{10}$). Dénominateur nul $\rightarrow$ taux d'évolution non calculable (afficher le volume brut). |
| **Formule** | $\Delta \text{KPI-1 (\%)} = 100 \times \frac{N_{\ge 1\text{ ha},\,2027}(Z_{10}) - N_{\ge 1\text{ ha},\,\text{réf}}(Z_{10})}{N_{\ge 1\text{ ha},\,\text{réf}}(Z_{10})}$, accompagné du volume brut $N_{\ge 1\text{ ha}}(Z_{10})$. |
| **Unité** | Pourcentage d'évolution (%), toujours accompagné du nombre absolu de feux majeurs et de la surface totale parcourue (en hectares). |
| **Paramètres** | Périmètre spatial $Z_{10}$ (10 communes prioritaires du 77), seuil de gravité ($10\,000\text{ m}^2$), période de référence (moyenne pluriannuelle 2012–2025 ou 2015–2025), fenêtre d'évaluation (suivi mensuel jusqu'au 30 septembre 2027). |
| **Grain** | Événement d'incendie rattaché à sa commune (`Code INSEE`), agrégé sur les 10 zones prioritaires par mois et par saison. |
| **Période et fréquence** | Suivi mensuel des indicateurs avec bilan final au terme de la saison estivale 2027 (**30 septembre 2027**). Actualisation à chaque import validé. |
| **Sources et champs** | `Incendies.csv` (BDIFF) — `Année`, `Numéro`, `Département`, `Code INSEE`, `Nom de la commune`, `Date de première alerte`, `Surface parcourue (m2)`, `Surface forêt (m2)`, `Précision des surfaces`, `Précision de la donnée`. Référentiels spatiaux : `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv` (`insee`, `mos2025`, `st_area_sh`) et `artif-commune.csv` (`commune_code`, `pourcent_artif_2`). Données SDIS 77 à obtenir : délais de première présentation et coûts engagés. |
| **Lignes utilisables** | Sur l'historique 2012–2025 en Seine-et-Marne, **293/293 événements** ont un code INSEE et une surface renseignés (**215/215** dans $Z_{10}$, dont **5 lignes** signalées `Données partielles ou non valides` à documenter). En revanche, **aucune donnée de délai de présentation ni de budget SDIS 77** n'est présente dans les fichiers fournis. |
| **Situation de référence** | Sur la période 2012–2025 en Seine-et-Marne, on recense **29 feux $\ge 1\text{ ha}$** dans les 10 communes prioritaires (sur **37 feux $\ge 1\text{ ha}$** dans tout le département `77`, soit **78,38 %**), avec une moyenne de **2,07 feux majeurs/an** sur 14 ans (et **4 feux $\ge 1\text{ ha}$** sur 2023–2025, tous situés dans $Z_{10}$). |
| **Proxy et biais** | 1) `Incendies.csv` (export BDIFF filtré sur `Type de feu : F`) sert de proxy aux bilans opérationnels du SDIS 77. 2) **Biais d'estimation :** **25 des 29 feux $\ge 1\text{ ha}$** de $Z_{10}$ (**86,21 %**) ont une surface `Estimées` (souvent arrondie à exactement `10 000 m²`), pouvant créer un effet de seuil artificiel. 3) **Petits effectifs annuels :** sur une seule année (ex. 0 à 4 feux $\ge 1\text{ ha}$), un seul événement fait varier fortement le taux. |
| **Décision** | Allouer en priorité les colonnes mobiles, patrouilles et crédits de prévention sur les 10 communes de $Z_{10}$ (pôle massif de Fontainebleau et sud-ouest du 77). Une stagnation ou hausse des feux majeurs déclenche une révision du maillage spatial ou des créneaux d'engagement. |
| **Propriétaire proposé** | [Prénom Nom] calcule et documente. Responsable qualité du groupe relit. SDIS 77 valide le périmètre $Z_{10}$, les données de délais et l'enveloppe budgétaire. |

### Test d'un paramètre (périmètre spatial et seuil de gravité sur l'historique 2012–2025 en Seine-et-Marne)

| Périmètre spatial testé (Département 77) | Total feux | Part des feux du 77 | Feux $\ge 0,5\text{ ha}$ | Feux $\ge 1\text{ ha}$ | Part des feux $\ge 1\text{ ha}$ du 77 | Surface parcourue cumulée |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Top 5 communes du 77** (`77186`, `77333`, `77339`, `77006`, `77244`) | 191 | 65,19 % | 36 | 22 | 59,46 % | 724 306 m² (72,43 ha) |
| **Top 10 communes du 77 ($Z_{10}$, retenu)** | **215** | **73,38 %** | **43** | **29** | **78,38 %** | **870 423 m² (87,04 ha)** |
| **Ensemble du département 77 (507 communes)** | 293 | 100,00 % | 55 | 37 | 100,00 % | 1 084 204 m² (108,42 ha) |

* **Enseignement du test :** Passer du Top 5 au **Top 10 communes ($Z_{10}$)** permet de capter **78,38 %** des feux majeurs ($\ge 1\text{ ha}$) du département (29 sur 37) et **73,38 %** de l'ensemble des départs de feu, tout en ciblant seulement **17,22 %** des surfaces boisées du 77 (`21 836,86 ha` sur `126 837,98 ha` dans le MOS 2025). Élargir au-delà disperserait les moyens pour seulement 8 feux majeurs supplémentaires répartis sur près de 500 communes.

### Jugement RACER

| Critère | Jugement |
| :--- | :--- |
| **Relevant** | L'indicateur mesure directement la réduction des sinistres forestiers graves dans les secteurs où se concentrent près de 80 % des feux majeurs de Seine-et-Marne. |
| **Accepted** | Le seuil de $1\text{ hectare}$ ($10\,000\text{ m}^2$) et le ciblage sur 10 communes prioritaires sont lisibles et directement actionnables par le commandement du SDIS 77. |
| **Credible** | Le calcul est reproductible à partir des codes INSEE et des surfaces de `Incendies.csv`, sous réserve d'encadrer les surfaces estimées et les petits effectifs annuels. |
| **Easy** | Calculable immédiatement sur l'historique BDIFF, mais le suivi du second volet (délai de première présentation à -15 %) dépend de la transmission des extractions internes du SDIS 77. |
| **Robust** | La comparaison à une moyenne pluriannuelle et l'association avec un garde-fou budgétaire et territorial évitent les conclusions trompeuses liées à une seule saison atypique. |

---

## 2. Garde-fou — Taux de mobilisation à vide (faux positifs budgétaires) et déport territorial hors $Z_{10}$

| Rubrique | Spécification |
| :--- | :--- |
| **Risque visé** | Faire baisser artificiellement les feux majeurs en dépensant sans limite sur toutes les alertes (sur-mobilisation à vide) ou en dégarnissant le reste de la Seine-et-Marne au profit exclusif des 10 communes cibles. |
| **Mesure** | 1) **Efficience budgétaire :** part des jours-zones prépositionnés (ou jours d'alerte Météo des forêts activés) qui ne donnent lieu à aucun départ de feu dans $Z_{10}$. 2) **Équilibre territorial :** part des feux majeurs ($\ge 1\text{ ha}$) survenant hors des 10 communes cibles dans le département `77`. |
| **Formule de suivi** | $\text{GF-1a (\%)} = 100 \times \frac{\text{Jours activés sans feu recensé sur } Z_{10}}{\text{Total jours activés sur } Z_{10}}$ et $\text{GF-1b (\%)} = 100 \times \frac{N_{\ge 1\text{ ha}}(\text{77 hors } Z_{10})}{N_{\ge 1\text{ ha}}(\text{77 total})}$, accompagnés du ratio budgétaire $\text{Coût engagé} / \text{Enveloppe } B$. |
| **Paramètres et périmètre** | Même période d'évaluation (saison 2027) et périmètre départemental `77` (comparaison $Z_{10}$ vs 497 autres communes). |
| **Sources et faisabilité** | **Partiellement vérifiée (proxy disponible) :** sur les **371 journées** Météo des forêts du `77` (`mdf_2024.csv` à `mdf_2026.csv`), déclencher une mobilisation sur tout le département dès `niveau_j1 >= 2` génère **105 jours sans feu sur 111 jours d'alerte (94,59 %)**, et historiquement **8 des 37 feux $\ge 1\text{ ha}$ (21,62 %)** ont lieu hors $Z_{10}$. Les données financières exactes du SDIS 77 restent à obtenir pour remplacer le proxy. |
| **Seuil et décision** | Dépassement de **100 %** de l'enveloppe $B$ ou hausse de la part des feux majeurs hors $Z_{10}$ au-dessus de **25 %** $\rightarrow$ recalibrer les seuils de déclenchement (croisement MDF + créneau horaire) et redéployer une réserve mobile. |
| **Limite** | Le proxy basé sur les fichiers MDF ne distingue pas le coût d'une simple astreinte en caserne de celui d'une colonne mobile prépositionnée sur le terrain. |
| **Propriétaire proposé** | Référent administratif/financier du SDIS 77 pour les coûts engagés, [Prénom Nom] pour le calcul, responsable qualité pour la relecture. |

* **Détournement possible —** Le gestionnaire mobilise les moyens en continu sur $Z_{10}$ dès le moindre niveau d'alerte pour afficher une baisse des grands feux, ce qui fait exploser les coûts de fonctionnement ou laisse les communes rurales du nord/est du 77 sans couverture rapide.
* **Risque résiduel —** Même avec une allocation optimale sur $Z_{10}$, un incendie majeur déclenché par malveillance ou travaux en dehors des créneaux renforcés peut survenir.

---

## 3. Indicateur descriptif calculable — Concentration spatio-temporelle des feux majeurs ($\ge 1\text{ ha}$)

| Rubrique | Spécification |
| :--- | :--- |
| **Rôle** | **KPI secondaire** pour calibrer l'allocation des moyens dans l'espace (choix des 10 communes) et dans le temps (créneaux d'engagement prioritaires). |
| **Formule** | $100 \times \frac{\text{Feux } \ge 1\text{ ha dans la tranche horaire (ou saison)}}{\text{Total des feux } \ge 1\text{ ha du 77 avec horodatage exploitable}}$. |
| **Périmètre et période** | Seine-et-Marne (`Département = 77`), historique complet 2012–2025 (**293 feux**, dont **37 feux $\ge 1\text{ ha}$**). |
| **Source exacte** | `Incendies.csv` — `Année`, `Numéro`, `Département`, `Code INSEE`, `Date de première alerte`, `Surface parcourue (m2)`. |
| **Lignes utilisables** | **293/293 événements** en Seine-et-Marne (et **37/37 feux $\ge 1\text{ ha}$**) disposent d'un horodatage et d'une surface exploitables. |
| **Référence** | Sur les **37 feux majeurs ($\ge 1\text{ ha}$)** du 77, **21 feux (56,76 %)** démarrent entre **12 h et 16 h** (`[12 h, 16 h[`) et **29 feux (78,38 %)** entre **12 h et 20 h** (`[12 h, 20 h[`). Par ailleurs, **10 feux $\ge 1\text{ ha}$ (27,03 %)** surviennent au printemps (mars–mai) contre **20 (54,05 %)** en été (juin–août). |
| **Décision** | Concentrer le prépositionnement des colonnes mobiles sur le créneau **12 h – 20 h** (avec pic **12 h – 16 h**) et activer une veille budgétaire anticipée dès le **printemps (avril–mai)** plutôt que sur le seul été. |
| **Proxy et biais** | L'heure de première alerte approxime l'heure réelle d'éclosion ; le délai de détection en forêt peut décaler légèrement l'horodatage d'une tranche à la suivante. |
| **Propriétaire** | [Prénom Nom] ; relecture par le responsable qualité du groupe. |

| Tranche horaire (Seine-et-Marne, 2012–2025) | Tous feux (77) | Part tous feux | Feux majeurs ($\ge 1\text{ ha}$) | Part feux majeurs |
| :--- | :---: | :---: | :---: | :---: |
| `[00 h, 04 h[` | 3 | 1,02 % | 0 | 0,00 % |
| `[04 h, 08 h[` | 12 | 4,10 % | 2 | 5,41 % |
| `[08 h, 12 h[` | 65 | 22,18 % | 6 | 16,22 % |
| **`[12 h, 16 h[` (pic majeur)** | **111** | **37,88 %** | **21** | **56,76 %** |
| **`[16 h, 20 h[`** | **86** | **29,35 %** | **8** | **21,62 %** |
| `[20 h, 24 h[` | 16 | 5,46 % | 0 | 0,00 % |

* **Protection complémentaire —** Toujours afficher les volumes absolus ($n = 37$ feux majeurs au total dans le 77) à côté des pourcentages afin d'éviter toute sur-interprétation sur les tranches à faible effectif.

---

## 4. Pré-mortem

Classement qualitatif des risques d'échec de l'allocation budgétaire et opérationnelle, sans estimation statistique des probabilités.

| Rang | Cause plausible d'échec | Probabilité appréciée | Gravité | Protection (garde-fou) |
| :---: | :--- | :---: | :---: | :--- |
| **1** | **Mauvais calibrage météo/saisonnier des engagements :** déclencher les moyens sur le seul indice Météo des forêts entraîne **94,59 %** de jours d'alerte sans feu en été tout en manquant les feux majeurs printaniers (27,03 % des feux $\ge 1\text{ ha}$ ont lieu au printemps, hors fenêtre MDF). | Plausible | Élevée | Suivre **GF-1a** (taux de mobilisation à vide) et déclencher les ressources par un **score combiné** (commune $Z_{10}$ + créneau `12 h–20 h` + indice MDF + alerte printanière dès mars-avril). |
| **2** | **Volatilité des petits effectifs et biais des surfaces estimées :** **86,21 %** des feux majeurs de $Z_{10}$ ont une surface `Estimées` (souvent arrondie à `10 000 m²`) et le nombre annuel de feux $\ge 1\text{ ha}$ est faible (0 à 7 par an), rendant un taux annuel très instable. | Plausible | Élevée | Comparer `KPI-1` à une **moyenne pluriannuelle glissante**, exiger une mesure GPS pour tout feu $> 5\,000\text{ m}^2$ et suivre en parallèle le taux d'attaque naissante ($< 1\,000\text{ m}^2$). |
| **3** | **Effet tunnel sur les 10 communes prioritaires :** concentrer tout le budget sur $Z_{10}$ laisse les autres secteurs boisés/agricoles du 77 (qui comptent **21,62 %** des feux $\ge 1\text{ ha}$) sans renfort rapide. | À documenter | Moyenne à élevée | Suivre **GF-1b** (part des feux majeurs hors $Z_{10}$) et conserver une réserve mobile repositionnable à l'échelle départementale. |

---

## 5. Jeu individuel proposé pour la mise en commun v0

| Rôle | Indicateur | Situation et raison |
| :--- | :--- | :--- |
| **KPI principal** | **Nombre et taux d'évolution des feux majeurs ($\ge 1\text{ ha}$) dans les 10 communes prioritaires ($Z_{10}$)** | Mesure directement l'objectif SMART de réduction de **-10 %** des incendies majeurs grâce au ciblage des ressources (**29 feux $\ge 1\text{ ha}$** sur 2012–2025). |
| **Garde-fou** | **Taux de jours activés sans feu sur $Z_{10}$ (et part des feux majeurs hors $Z_{10}$ / ratio coût $B$)** | Limite le gaspillage budgétaire sur alertes à vide (**94,59 %** de jours sans feu si seuil MDF $\ge 2$ brut) et empêche l'abandon du reste du département (**21,62 %** des feux majeurs). |
| **KPI secondaire 1** | **Concentration spatio-temporelle des feux majeurs (par commune $Z_{10}$ et tranche horaire `12 h–20 h`)** | Calculable immédiatement (**78,38 %** des feux $\ge 1\text{ ha}$ dans $Z_{10}$ et **78,38 %** entre `12 h` et `20 h`). Guide concrètement où et quand engager les crédits. |
| **KPI secondaire 2** | **Délai médian de première présentation des secours sur $Z_{10}$** | Suit le second volet de l'objectif SMART (**-15 %** de délai). À calculer après réception des données opérationnelles du SDIS 77. |
| **Contexte** | **Nombre de jours à indice Météo des forêts élevé (`niveau_j1 >= 2` ou `3`) sur la saison** | Calculable sur 2024–2026 (`0` jour en 2024, `22` en 2025, `89` en 2026 dans le 77). Permet d'interpréter l'évolution des sinistres selon la sévérité météo sans la piloter. |
| **Écarté à ce stade** | **Corrélation brute température maximale / nombre de feux** | Ne change aucune décision d'allocation budgétaire : l'effet météo est déjà synthétisé dans les niveaux `niveau_j1` / `niveau_j2` de la Météo des forêts. |

---

## 6. Limites et éléments à obtenir

* **Données internes SDIS 77 à obtenir :** les fichiers fournis ne contiennent ni les **délais de première présentation des secours** (nécessaires pour mesurer l'objectif de **-15 %**), ni les **coûts horaires / effectifs par caserne**, ni les plannings des colonnes mobiles.
* **Complétude de l'occupation du sol (MOS) :** dans le fichier `mos-occupation-du-sol-...csv` fourni, les enregistrements extraits pour le département `77` ne couvrent que le poste `Bois ou forêts` (`mos2025 = 1`, `126 837,98 ha`) ; l'obtention de la couche complète (champs, zones de loisirs, habitats) affinera la cartographie d'interface forêt-habitat.
* **Fenêtre saisonnière de la Météo des forêts :** les fichiers `mdf_2024.csv` à `mdf_2026.csv` ne couvrent que la période estivale élargie (fin mai à début octobre), alors que **27,03 %** des feux majeurs ($\ge 1\text{ ha}$) du 77 se produisent au printemps (mars–mai).
* **Qualité des surfaces BDIFF :** **86,21 %** des feux $\ge 1\text{ ha}$ de $Z_{10}$ ont une surface estimée ; l'intégration des comptes rendus géolocalisés du SDIS 77 améliorera la précision de l'évaluation en 2027.

---

## 7. Sources de travail

* Supports de cours « De la question analytique aux objectifs » et « Définir des KPIs » (UE01.B).
* `Incendies.csv` (extraction BDIFF Île-de-France, 347 événements dont **293 en Seine-et-Marne** sur 2012–2025).
* `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv` (indices quotidiens Météo des forêts, **371 journées** analysées pour le département `77`).
* `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv`, `artif-commune.csv` et `artif-departement.csv` (occupation et artificialisation des sols en Seine-et-Marne).

---

## 8. Dépôt et revue

Déposer cette contribution dans `kpi/02_fiches_indicateurs.md` dans une section nominative dédiée (en conservant les fiches des autres membres du groupe comme celle de Yasmine), effectuer un commit individuel, puis soumettre la contribution à la relecture du groupe pour valider le jeu collectif v0.
