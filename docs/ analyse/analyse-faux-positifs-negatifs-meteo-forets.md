# Analyse des faux positifs et faux négatifs de la Météo des forêts en Île-de-France

## 1. Contexte et problématique

Les incendies de forêt représentent un risque important pour les espaces naturels, les populations et les infrastructures. Leur apparition dépend de plusieurs facteurs, notamment les conditions météorologiques, l'état de sécheresse de la végétation, l'occupation du sol et les activités humaines.

La Météo des forêts a été mise en place par Météo-France afin d'informer la population sur le niveau de danger de feu de forêt. Elle fournit des niveaux de danger météorologique à l'échelle départementale.

Cependant, un niveau de danger élevé ne signifie pas nécessairement qu'un incendie va se produire. À l'inverse, des incendies peuvent survenir même lorsque le niveau de danger annoncé est faible ou modéré.

Dans le cadre de notre projet, nous souhaitons donc étudier la pertinence des niveaux de danger annoncés en Île-de-France, en les comparant aux incendies réellement recensés.

L'objectif est d'identifier les éventuels écarts entre le danger annoncé et les événements observés, puis de proposer des pistes d'amélioration de l'évaluation du risque.

## 2. Question de recherche et hypothèse

**Question de recherche :**

Quelle est l'ampleur des faux positifs et des faux négatifs associés au seuil actuel de la Météo des forêts ?

**Hypothèse :**

En combinant les niveaux de danger de la Météo des forêts avec l'historique des incendies recensés et des données complémentaires, comme les conditions météorologiques, l'humidité des sols, l'occupation du sol et la proximité des infrastructures, il serait possible d'améliorer l'évaluation du risque d'incendie.

Cette approche pourrait permettre de mieux identifier les situations où le niveau de danger annoncé ne correspond pas aux événements observés et de proposer des ajustements des seuils d'alerte.

## 3. Objectif SMART

L'objectif de cette analyse est d'évaluer la pertinence des niveaux de danger de la Météo des forêts en Île-de-France en les comparant aux incendies recensés dans la BDIFF, afin d'identifier les limites des seuils d'alerte et de proposer des améliorations.

| Critère | Définition |
|---|---|
| **S – Spécifique** | Évaluer les niveaux de danger de la Météo des forêts dans les huit départements d'Île-de-France en les comparant aux incendies recensés. |
| **M – Mesurable** | Calculer les taux de faux positifs et de faux négatifs, la sensibilité, la précision et la spécificité, puis comparer plusieurs seuils d'alerte. |
| **A – Atteignable** | Exploiter les archives de la Météo des forêts et les données de la BDIFF, puis rechercher des données météorologiques et environnementales complémentaires. |
| **R – Pertinent** | Améliorer la compréhension du danger d'incendie afin d'aider à mieux cibler les périodes et les territoires nécessitant une vigilance renforcée. |
| **T – Temporel** | Réaliser l'analyse sur les années communes disponibles entre les sources et finaliser les résultats avant la restitution finale du projet. |

**Objectif SMART formulé :**

Évaluer la pertinence des niveaux de danger de la Météo des forêts dans les huit départements d'Île-de-France, sur les périodes communes disponibles avec la BDIFF, en calculant les principaux indicateurs de classification et en comparant plusieurs seuils d'alerte, afin de proposer des pistes d'amélioration de l'évaluation du risque incendie.

## 4. Périmètre géographique et temporel

### 4.1. Périmètre géographique

L'étude porte sur l'ensemble de la région Île-de-France, composée des huit départements suivants :

| Code département | Département |
|---|---|
| 75 | Paris |
| 77 | Seine-et-Marne |
| 78 | Yvelines |
| 91 | Essonne |
| 92 | Hauts-de-Seine |
| 93 | Seine-Saint-Denis |
| 94 | Val-de-Marne |
| 95 | Val-d'Oise |

Les niveaux de danger de la Météo des forêts étant disponibles à l'échelle départementale, l'analyse principale sera réalisée à cette même échelle.

### 4.2. Périmètre temporel

Les périodes disponibles ne sont pas identiques pour les deux sources.

- **BDIFF :** notre extraction couvre les années 2006 à 2025.
- **Météo des forêts :** les archives étudiées concernent les années 2024, 2025 et 2026.

L'analyse devra donc porter uniquement sur les périodes communes et effectivement disponibles dans les deux sources.

La première période à examiner sera 2024-2025. L'année 2026 pourra être ajoutée si les données BDIFF correspondantes sont disponibles.

Il faudra également vérifier les dates exactes de publication et les périodes de diffusion des niveaux de danger.

## 5. Sources de données

### 5.1. Météo des forêts

La Météo des forêts, produite par Météo-France, fournit une information quotidienne sur le niveau de danger de feu de forêt.

Les niveaux sont répartis en quatre catégories :

| Niveau | Couleur | Signification |
|---|---|---|
| 1 | Vert | Danger faible |
| 2 | Jaune | Danger modéré |
| 3 | Orange | Danger élevé |
| 4 | Rouge | Danger très élevé |

Les archives comprennent notamment des niveaux de danger prévus à J+1 et J+2.

**Utilité pour l'analyse :**

- Identifier le niveau de danger annoncé pour chaque département et chaque journée.
- Comparer les niveaux de danger aux incendies recensés.
- Tester plusieurs seuils d'alerte.
- Repérer les journées où le niveau de danger semble sous-estimer ou surestimer les conditions associées aux incendies observés.

**Limite :**

La Météo des forêts évalue un niveau de danger météorologique. Elle ne prédit pas avec certitude qu'un incendie va se produire.

### 5.2. BDIFF

La BDIFF (Base de Données sur les Incendies de Forêts en France) permet d'étudier les incendies recensés sur le territoire français.

Notre extraction concerne l'Île-de-France et contient 347 événements recensés sur la période 2006-2025.

Les informations disponibles comprennent notamment :

- Le numéro de l'incendie.
- L'année.
- Le département.
- Le code INSEE.
- Le nom de la commune.
- La date de première alerte.
- Les surfaces parcourues par le feu.
- Certaines informations sur les conséquences de l'incendie.

**Utilité pour l'analyse :**

- Identifier les incendies réellement recensés.
- Déterminer les jours et les départements concernés.
- Comparer les événements recensés avec les niveaux de danger annoncés.
- Étudier la fréquence des incendies selon les périodes et les départements.

**Limite :**

La disponibilité d'une heure suffisamment précise dans la date de première alerte doit être vérifiée. De plus, l'absence d'un incendie dans la base ne garantit pas qu'aucun départ de feu n'a eu lieu.

### 5.3. Données complémentaires envisagées

Pour améliorer l'analyse, plusieurs données supplémentaires pourraient être intégrées :

| Donnée recherchée | Utilité |
|---|---|
| Température | Identifier les journées présentant des températures élevées. |
| Humidité de l'air | Étudier les conditions favorisant le dessèchement de la végétation. |
| Vent | Évaluer les conditions favorables à la propagation des incendies. |
| Précipitations | Étudier les périodes de sécheresse et de retour des précipitations. |
| Humidité des sols | Ajouter un indicateur de sécheresse des sols. |
| Occupation du sol (MOS) | Identifier les types d'espaces concernés par les incendies. |
| Artificialisation des sols | Étudier le contexte territorial et les interfaces entre espaces naturels et espaces urbanisés. |

Ces données constituent des pistes complémentaires. Leur disponibilité, leur période et leur précision devront être vérifiées avant leur intégration.

## 6. Méthodologie de traitement et de croisement des données

### 6.1. Préparation des données

La préparation des données se déroulera en plusieurs étapes :

1. Charger les fichiers CSV de la Météo des forêts et de la BDIFF.
2. Vérifier les noms et les formats des colonnes.
3. Filtrer les données sur les huit départements d'Île-de-France.
4. Vérifier les valeurs manquantes et les éventuelles incohérences.
5. Harmoniser les codes départementaux et les formats de dates.
6. Identifier les périodes communes aux deux sources.
7. Construire une table de correspondance entre les niveaux de danger et les incendies recensés.

### 6.2. Définition de l'unité d'analyse

L'unité d'analyse retenue sera une journée pour un département.

Pour chaque couple département-jour, nous associerons :

- Le niveau de danger annoncé par la Météo des forêts.
- La présence ou l'absence d'au moins un incendie recensé dans la BDIFF.

Une journée sera considérée comme ayant connu un incendie lorsqu'au moins un événement correspondant sera recensé dans la BDIFF pour le département concerné.

Cette méthode permettra de comparer les niveaux de danger et les événements observés à une échelle géographique cohérente.

### 6.3. Prise en compte des prévisions J+1 et J+2

Les prévisions J+1 et J+2 devront être analysées séparément.

Par exemple, si un niveau de danger est publié le lundi pour le mardi (J+1), il devra être comparé aux incendies recensés le mardi.

Il ne faudra pas comparer la date de publication de la prévision à la date de l'incendie, mais bien la date à laquelle le niveau de danger s'applique.

Cette distinction permettra d'éviter les erreurs lors du croisement des données.

### 6.4. Définition des seuils d'alerte à tester

Afin d'évaluer la sensibilité des résultats au seuil choisi, plusieurs scénarios pourront être comparés.

| Scénario | Niveaux considérés comme une alerte positive |
|---|---|
| Scénario A | Jaune, orange et rouge (2, 3, 4) |
| Scénario B | Orange et rouge (3, 4) |
| Scénario C | Rouge uniquement (4) |

Ces scénarios sont des hypothèses de travail. Ils ne représentent pas nécessairement les seuils opérationnels actuellement utilisés par les services de secours.

Le seuil réel utilisé pour déclencher une action de surveillance ou de mobilisation devra être vérifié.

## 7. Classification des résultats : matrice de confusion

Le croisement entre le niveau de danger et les incendies observés permettra de construire une matrice de confusion.

| | Incendie observé | Aucun incendie observé |
|---|---|---|
| **Alerte positive** | Vrai positif (VP) | Faux positif (FP) |
| **Alerte négative** | Faux négatif (FN) | Vrai négatif (VN) |

### 7.1. Vrai positif (VP)

Une journée est classée en vrai positif lorsque le niveau de danger dépasse le seuil choisi et qu'au moins un incendie est recensé dans le département.

### 7.2. Faux positif (FP)

Une journée est classée en faux positif lorsque le niveau de danger dépasse le seuil choisi, mais qu'aucun incendie n'est recensé.

Cela ne signifie pas nécessairement que l'évaluation météorologique est erronée. Le danger indique des conditions favorables aux incendies, mais un départ de feu n'est pas systématique.

### 7.3. Faux négatif (FN)

Une journée est classée en faux négatif lorsqu'un incendie est recensé alors que le niveau de danger est inférieur au seuil choisi.

Ces situations devront être étudiées afin d'identifier les éventuels facteurs qui ne sont pas suffisamment pris en compte dans l'évaluation du danger.

### 7.4. Vrai négatif (VN)

Une journée est classée en vrai négatif lorsque le niveau de danger est inférieur au seuil choisi et qu'aucun incendie n'est recensé.

## 8. Métriques et indicateurs de performance (KPI)

Plusieurs indicateurs seront utilisés pour évaluer la pertinence des niveaux de danger.

### 8.1. Indicateurs principaux

| KPI | Formule | Objectif |
|---|---|---|
| Taux de faux positifs (FPR) | FP / (FP + VN) × 100 | Mesurer la proportion de journées sans incendie classées en alerte. |
| Taux de faux négatifs (FNR) | FN / (FN + VP) × 100 | Mesurer la proportion de journées avec incendie non identifiées comme journées d'alerte. |
| Sensibilité (Recall) | VP / (VP + FN) × 100 | Mesurer la capacité du seuil à détecter les journées avec incendie. |
| Précision (Precision) | VP / (VP + FP) × 100 | Mesurer la proportion de journées alertées ayant connu un incendie. |
| Spécificité | VN / (VN + FP) × 100 | Mesurer la capacité du seuil à identifier les journées sans incendie. |

Les indicateurs seront calculés uniquement lorsque les dénominateurs sont non nuls.

### 8.2. Interprétation des indicateurs

- Un taux de faux positifs élevé indique qu'une part importante des journées sans incendie est classée en alerte.
- Un taux de faux négatifs élevé indique que de nombreuses journées avec incendie ne sont pas identifiées par le seuil retenu.
- Une sensibilité élevée signifie que le système identifie une grande partie des journées où un incendie est observé.
- Une précision élevée signifie qu'une part importante des journées alertées correspond à des journées avec incendie observé.
- Une spécificité élevée indique que le système identifie correctement une grande partie des journées sans incendie.

Il faudra accorder une attention particulière au taux de faux négatifs, car les journées avec incendie sont relativement rares par rapport à l'ensemble des journées étudiées.

### 8.3. KPI complémentaires

| KPI complémentaire | Utilité |
|---|---|
| Nombre de jours en alerte par département | Identifier les départements les plus souvent concernés par des niveaux de danger élevés. |
| Nombre d'incendies par niveau de danger | Étudier la répartition des incendies selon le niveau annoncé. |
| Nombre de journées avec incendie par mois | Identifier les périodes saisonnières les plus concernées. |
| Nombre de journées d'alerte sans incendie | Estimer la fréquence des alertes sans événement recensé. |
| Nombre d'incendies par département | Identifier les départements présentant le plus d'événements recensés. |

Ces indicateurs permettront d'aller au-delà d'une simple comparaison globale et d'étudier les différences entre les départements et les périodes.

## 9. Comparaison des seuils et pistes d'amélioration

Une fois les indicateurs calculés, les trois scénarios de seuils seront comparés.

L'objectif sera d'identifier le meilleur compromis entre la détection des journées avec incendie et la limitation des journées alertées sans incendie observé.

| Scénario | Avantage recherché | Risque associé |
|---|---|---|
| A – Jaune, orange et rouge | Détecter davantage de journées avec incendie. | Augmenter le nombre de journées alertées sans incendie observé. |
| B – Orange et rouge | Rechercher un compromis entre détection et nombre d'alertes. | Certains incendies peuvent survenir lors de journées jaunes ou vertes. |
| C – Rouge uniquement | Réduire le nombre de journées considérées comme alertes. | Risquer de manquer davantage de journées avec incendie. |

Les résultats pourront également être étudiés département par département afin de repérer les différences territoriales.

### 9.1. Intégration de données météorologiques complémentaires

L'ajout de données sur la température, le vent, l'humidité et les précipitations pourrait permettre de mieux caractériser les conditions météorologiques associées aux incendies.

### 9.2. Intégration de données environnementales

L'humidité des sols, l'état de sécheresse de la végétation et l'occupation du sol pourraient apporter des informations complémentaires sur la vulnérabilité des espaces naturels.

### 9.3. Prise en compte des caractéristiques territoriales

La présence de forêts, de zones agricoles, de zones de loisirs, d'habitations et d'infrastructures pourrait aider à mieux comprendre les différences de risque entre les départements et les communes.

### 9.4. Comparaison des performances

Les différents scénarios seront évalués à partir des KPI calculés. Le choix d'un seuil ne devra pas reposer uniquement sur la réduction des faux positifs : il faudra également prendre en compte les conséquences d'un faux négatif et les besoins opérationnels des services de secours.

## 10. Limites de l'analyse

Plusieurs limites devront être prises en compte.

### 10.1. Différence d'échelle géographique

La Météo des forêts fournit des niveaux de danger à l'échelle départementale, alors que les incendies sont localisés à l'échelle de la commune ou de l'événement.

Un niveau de danger élevé dans un département ne signifie pas que les conditions sont identiques sur tout son territoire.

### 10.2. Différence de couverture temporelle

La BDIFF contient un historique plus long que les archives de la Météo des forêts.

La comparaison devra donc se limiter aux années communes et aux périodes pour lesquelles les deux sources disposent de données exploitables.

### 10.3. Absence d'incendie recensé

L'absence d'incendie dans la BDIFF ne signifie pas nécessairement qu'aucun départ de feu n'a eu lieu. La qualité et l'exhaustivité des données devront être prises en compte.

### 10.4. Nature du niveau de danger

La Météo des forêts évalue un danger météorologique et non la probabilité certaine qu'un incendie se déclenche.

Les faux positifs et faux négatifs calculés dans cette étude seront donc des classifications opérationnelles construites à partir d'un seuil choisi, et non une mesure directe d'erreurs de prévision d'incendies.

### 10.5. Déséquilibre entre les classes

Les journées sans incendie sont beaucoup plus nombreuses que les journées avec incendie.

Un taux global de bonnes classifications pourrait donc être élevé même si le système détecte mal les journées avec incendie.

Il sera nécessaire d'interpréter les KPI séparément, notamment la sensibilité et le taux de faux négatifs.

## 11. Conclusion provisoire

Le croisement des données de la Météo des forêts et de la BDIFF constitue une première méthode pour évaluer la pertinence des niveaux de danger annoncés en Île-de-France.

Cette analyse permettra d'identifier les journées où un incendie a été recensé malgré un niveau de danger inférieur au seuil choisi, ainsi que les journées présentant un niveau de danger élevé sans incendie recensé.

La comparaison de plusieurs seuils permettra d'étudier les compromis entre la détection des journées avec incendie et la limitation des alertes sans événement observé.

L'intégration de données météorologiques, environnementales et territoriales complémentaires pourrait ensuite améliorer la compréhension des situations à risque.

Les résultats chiffrés seront ajoutés après le croisement effectif des fichiers CSV. Aucun taux de faux positifs ou de faux négatifs ne sera avancé sans calcul sur les données réelles.

Cette analyse permettra de proposer des pistes d'amélioration de l'évaluation du danger et de contribuer à une meilleure orientation des moyens de surveillance et de prévention des incendies en Île-de-France.

## 12. Références des sources

- Météo des forêts – Météo-France : https://meteofrance.com/meteo-des-forets
- Archives de la Météo des forêts – data.gouv.fr : https://www.data.gouv.fr/datasets/archives-de-la-meteo-des-forets
- BDIFF – Base de données sur les incendies de forêts : https://bdiff.agriculture.gouv.fr/incendies
- Inventaire des sources du projet : `docs/sources/inventaire.md`
- Fiche BDIFF du groupe : `docs/sources/fiche-bdiff.md`
