# Analyse de la commande – Sarra Slama

## 1. Les questions

L'objectif est de comprendre les facteurs liés aux incendies de forêt en Seine-et-Marne et en Île-de-France afin d'améliorer leur prévention et leur détection.

Les quatre questions auxquelles l'analyse devra apporter des réponses sont :

1. Quelles sont les caractéristiques des zones les plus touchées par les incendies en Seine-et-Marne ?
2. Dans quelle mesure les alertes de la Météo des forêts permettent-elles d'anticiper les incendies réels ? Quelle est l'ampleur des faux positifs et des faux négatifs ?
3. Quel est le lien entre les conditions météorologiques et les incendies de forêt ?
4. Quelles sont les périodes de l'année et les heures de la journée où les incendies sont les plus fréquents ?

Ces questions doivent permettre d'identifier les territoires les plus exposés, de mieux comprendre les conditions favorables aux incendies et d'évaluer l'intérêt des dispositifs actuels de prévention.

## 2. Les termes inconnus

Certains termes de la commande peuvent être difficiles à comprendre ou peuvent avoir plusieurs significations. Il est donc nécessaire de les clarifier avant de commencer l'analyse.

| **Terme** | **Ce que je pensais que cela voulait dire** | **Définition à retenir / à vérifier** |
|---|---|---|
| SDIS | Une entreprise qui prédit le déclenchement des feux. | Service départemental d'incendie et de secours. Il assure notamment la prévention, la préparation et la lutte contre les incendies et les secours aux personnes. |
| Météo des forêts | La température des forêts est différente de celle des villes. | Dispositif d'information de Météo-France qui indique quotidiennement le niveau de danger de feu de végétation à l'échelle départementale. |
| Guet | Une personne qui surveille les forêts. | Surveillance d'un territoire pour détecter rapidement un départ de feu. Le terme peut désigner une activité ou un dispositif de surveillance. |
| Indice | Un seuil qui déclenche automatiquement les feux. | Indicateur permettant d'évaluer un niveau de danger météorologique ou de risque. Il ne signifie pas qu'un incendie va nécessairement se produire. |

## 3. Les besoins

### La décision à éclairer

Identifier les territoires et les périodes les plus exposés aux incendies, évaluer la pertinence des alertes de la Météo des forêts et déterminer comment mieux orienter les moyens humains et financiers consacrés à la prévention et à la surveillance.

### Ce qui manque dans la commande pour y répondre

Plusieurs informations seraient nécessaires pour répondre précisément aux questions :

- Le budget disponible pour les actions de prévention et de surveillance.
- Le nombre d'agents et les moyens matériels disponibles au sein du SDIS 77.
- Les critères et les seuils utilisés pour déterminer les niveaux de danger de la Météo des forêts.
- Les données historiques détaillées des interventions, notamment les dates et heures exactes des départs de feu.
- Les données météorologiques permettant d'étudier le rôle de la température, du vent, de l'humidité et des précipitations.

## 4. Les données

Pour chaque question, voici les données qui seraient idéalement nécessaires pour y répondre.

| **Question** | **Donnée idéale** | **Grain (une ligne = ?)** | **Période** | **Fraîcheur** | **Emprise géographique** |
|---|---|---|---|---|---|
| 1 | Historique des incendies avec leur localisation, les surfaces brûlées et des informations sur l'environnement des zones touchées : végétation, couverture forestière, relief et occupation des sols. | 1 ligne = 1 incendie, associé à une commune et à sa localisation. | Les 5 dernières années | Mise à jour annuelle | Seine-et-Marne (77), avec un découpage communal |
| 2 | Historique des niveaux de danger de la Météo des forêts croisé avec les incendies réellement observés, afin de comparer les alertes aux événements réels et de calculer les faux positifs et les faux négatifs. | 1 ligne = 1 jour et 1 département, avec le niveau de danger et la présence ou l'absence d'incendie. | Les 3 à 5 dernières années | Journalière, pendant la période de diffusion des alertes | Seine-et-Marne (77) |
| 3 | Données météorologiques comprenant la température, le vent, l'humidité, les précipitations et le niveau de danger de la Météo des forêts, croisées avec l'historique des incendies. | 1 ligne = 1 jour et 1 département pour les données météo, avec les incendies associés à leur date et à leur commune. | Les 5 dernières années | Journalière | Seine-et-Marne (77) et Île-de-France |
| 4 | Historique détaillé des départs de feu avec les dates, les heures, les communes et les surfaces brûlées, afin d'identifier les périodes où les incendies sont les plus fréquents. | 1 ligne = 1 incendie, avec une date et une heure précises. | Les 5 dernières années | Données actualisées régulièrement, avec horodatage précis | Seine-et-Marne (77) et Île-de-France |

## 5. Confrontation des questions aux sources

### Matrice de couverture

| **Question** | **Source explorée** | **Degré de couverture** | **Raison et justification (colonnes / rubriques)** |
|---|---|---|---|
| 1. Caractéristiques des zones les plus touchées | BDIFF | partiel | Les colonnes `Département`, `Code INSEE`, `Nom de la commune`, `Année` et les champs relatifs aux surfaces brûlées permettent d'identifier les territoires les plus touchés et de comparer les incendies. Cependant, la colonne `Type de peuplement` est entièrement vide et la source ne décrit pas suffisamment la végétation ou le relief. |
| 1. Caractéristiques des zones les plus touchées | Météo des forêts | partiel | Les niveaux de danger par département permettent d'identifier les territoires exposés à un danger météorologique élevé. Toutefois, la source ne décrit pas les caractéristiques environnementales des communes ou des espaces forestiers touchés. |
| 1. Caractéristiques des zones les plus touchées | Artificialisation des sols | partiel | Les données à l'échelle communale et les pourcentages d'artificialisation permettent de caractériser l'occupation des sols et la pression de l'urbanisation. En revanche, elles ne contiennent pas d'historique des incendies ni de localisation des départs de feu. |
| 2. Évaluation des faux positifs et des faux négatifs | BDIFF | partiel | Les colonnes `Date de première alerte`, `Département`, `Code INSEE` et `Année` permettent d'identifier les incendies réellement enregistrés. Ces événements peuvent être comparés aux niveaux de danger météorologique, mais la BDIFF ne contient pas les prévisions de la Météo des forêts. |
| 2. Évaluation des faux positifs et des faux négatifs | Météo des forêts | partiel | Les archives `mdf-2024`, `mdf-2025` et `mdf-2026` contiennent des niveaux de danger par département et par date. Elles peuvent être croisées avec les incendies de la BDIFF, mais elles ne contiennent pas les interventions réelles. La période disponible est également plus courte que celle de la BDIFF. |
| 2. Évaluation des faux positifs et des faux négatifs | Artificialisation des sols | absent | Les données d'artificialisation ne contiennent ni niveaux de danger météorologique ni interventions réelles des secours. Elles ne permettent donc pas de calculer les faux positifs ou les faux négatifs. |
| 3. Lien entre les conditions météorologiques et les incendies | BDIFF | partiel | Les colonnes `Date de première alerte`, `Département`, `Code INSEE`, `Année` et les surfaces brûlées permettent d'identifier les incendies et de les associer à une période et à un territoire. Cependant, aucune variable météorologique n'est directement renseignée dans cette source. |
| 3. Lien entre les conditions météorologiques et les incendies | Météo des forêts | partiel | Les niveaux de danger journaliers par département permettent d'étudier le lien entre le danger météorologique annoncé et les incendies observés. Cependant, cette source ne fournit pas nécessairement les variables météorologiques détaillées comme la température, le vent, l'humidité et les précipitations. |
| 3. Lien entre les conditions météorologiques et les incendies | Artificialisation des sols | absent | Les fichiers décrivent l'évolution de l'artificialisation des sols selon différents millésimes. Ils ne contiennent pas de données météorologiques ni d'historique des incendies. |
| 4. Périodes de l'année et heures de la journée où les incendies sont les plus fréquents | BDIFF | partiel | La colonne `Date de première alerte` et la colonne `Année` permettent d'étudier la répartition des incendies par année et potentiellement par mois. La présence d'une heure précise dans la date de première alerte reste à vérifier pour distinguer les départs de feu le matin et la nuit. |
| 4. Périodes de l'année et heures de la journée où les incendies sont les plus fréquents | Météo des forêts | partiel | Les archives contiennent une date de prévision et un niveau de danger journalier par département. Elles permettent d'étudier les périodes de danger élevé, mais pas les horaires réels des départs de feu. |
| 4. Périodes de l'année et heures de la journée où les incendies sont les plus fréquents | Artificialisation des sols | absent | Les fichiers mesurent l'artificialisation des sols selon différents millésimes, notamment 2016-2019 et 2019-2022. Ils ne contiennent ni dates ni heures d'intervention ou de départ de feu. |

### Décisions face aux manques

**Pour la Q1 (Caractéristiques des zones les plus touchées) : approximer.**

Croiser les données de la BDIFF avec celles de l'artificialisation des sols afin de repérer les communes qui cumulent des incendies et une forte artificialisation. Cette méthode permet de caractériser une partie du contexte territorial, mais elle ne renseigne pas suffisamment sur la végétation, les types de peuplements forestiers ou la topographie. Des données complémentaires sur les espaces forestiers et l'occupation des sols seraient nécessaires pour approfondir l'analyse.

**For la Q2 (Faux positifs et faux négatifs) : collecter.**

Croiser les archives journalières de la Météo des forêts avec les incendies réellement enregistrés dans la BDIFF. Il faudra harmoniser les dates et les départements et définir précisément le seuil de danger considéré comme une alerte. Les faux positifs et les faux négatifs pourront ensuite être identifiés en comparant les alertes aux incendies observés. Il faudra également rechercher des archives complémentaires si la période 2024-2026 est insuffisante.

**Pour la Q3 (Lien entre météo et incendies) : collecter.**

Utiliser les niveaux de danger de la Météo des forêts et les données d'incendies de la BDIFF pour commencer à étudier leur relation. Pour aller plus loin et analyser le rôle des conditions météorologiques, il faudra collecter des données complémentaires sur la température, le vent, l'humidité et les précipitations.

**Pour la Q4 (Périodes et horaires des incendies) : collecter.**

Utiliser la BDIFF pour analyser la répartition des incendies par année et par mois. Vérifier d'abord si la colonne `Date de première alerte` contient une heure précise. Si ce n'est pas le cas, collecter des données d'intervention plus détaillées auprès du SDIS 77 afin d'obtenir les dates et heures exactes des départs de feu.
