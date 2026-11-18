# Analyse de la commande 

## 1. Questions d’analyse

Quatre questions permettent d’éclairer la décision de la direction :

1. **Quelles sont les caractéristiques des zones les plus touchées en Seine-et-Marne ?**
2. **À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents en Seine-et-Marne ?**
3. **Quelle est l’ampleur des faux positifs et des faux négatifs associés au seuil actuel de la Météo des forêts ?**
4. **Comment répartir au mieux un budget limité afin de protéger en priorité les zones et les périodes les plus à risque ?**

---

## 2. Termes à clarifier

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
| **SDIS** | Organisation chargée de gérer les feux | Service départemental d'incendie et de secours |
| **Météo des forêts** | Information sur les conditions météorologiques des forêts | Indicateur permettant d'évaluer le niveau de danger lié aux feux de forêt |
| **Guet** | Personne chargée de surveiller les forêts | Dispositif de surveillance permettant d'anticiper et de détecter les départs de feux |
| **Indice** | Seuil de déclenchement des feux | Indicateur permettant d'évaluer le niveau de danger météorologique |

---

## 3. Besoin décisionnel

### Décision à éclairer

> Choisir comment répartir les ressources humaines et financières du SDIS 77 et, si nécessaire, redéfinir le seuil d'alerte de la Météo des forêts pour l'été 2027 afin de réduire les faux positifs tout en maintenant une bonne détection des situations à risque.

### Informations manquantes

- Le budget exact disponible pour les renforcements ;
- Le nombre d'agents mobilisables ;
- La définition précise du seuil actuel de la Météo des forêts ;
- Les modalités opérationnelles de déclenchement des dispositifs de surveillance.

---

## 4. Besoins en données

| Question | Donnée idéale | Grain | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| **Q1** | Historique des interventions pour feux de forêt avec localisation géographique | 1 ligne = 1 intervention | 5 dernières années | Annuelle | Seine-et-Marne, découpage communal |
| **Q2** | Date et heure précises des départs de feux | 1 ligne = 1 intervention | 5 dernières années | Journalière / mensuelle | Seine-et-Marne et Île-de-France |
| **Q3** | Historique journalier croisant l'indice Météo des forêts et les interventions réelles | 1 ligne = 1 jour / commune ou secteur | Étés des 3 dernières années | Journalière | Seine-et-Marne |
| **Q4** | Données relatives aux coûts des déploiements et aux ressources mobilisées | 1 ligne = 1 secteur opérationnel / coût journalier | 2 dernières années | Récente / annuelle | Seine-et-Marne et Île-de-France |

---

## 5. Matrice de couverture

# Matrice de confrontation des questions et des sources

Cette matrice permet de confronter les questions d’analyse retenues par le groupe aux sources étudiées afin d’identifier les sources réellement utiles, les couvertures partielles et les données manquantes.

## Matrice de couverture

| Question | Artificialisation des sols | Recherche et identification des incendies | BD Forêt |
|---|---|---|---|
| **Q1. Quelles sont les caractéristiques des zones les plus touchées en Seine-et-Marne ?** |  **Partielle** — permet de caractériser le niveau d’artificialisation des communes et d’identifier les secteurs fortement urbanisés. |  **Bonne** — permet de localiser les incendies recensés et d’identifier les secteurs les plus touchés. |  **Bonne** — permet de localiser et de caractériser les espaces forestiers concernés. |
| **Q2. À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents ?** | **Absente** — ne contient pas d’informations sur les dates ou les horaires des incendies. |  **Partielle** — permet d’étudier la fréquence des incendies, à condition que les données contiennent des informations temporelles suffisamment précises, notamment les dates et, si possible, les heures. | **Absente** — décrit principalement les espaces forestiers et ne fournit pas l’historique temporel des incendies. |
| **Q3. Quelle est l’ampleur des faux positifs et des faux négatifs sous le seuil actuel de la Météo des forêts ?** |  **Absente** — ne contient ni niveaux de danger météorologique ni historique des prévisions. |  **Partielle** — permet d’identifier les incendies réellement observés, mais ne fournit pas à elle seule les niveaux de danger annoncés par la Météo des forêts. |  **Absente** — ne contient pas les prévisions de la Météo des forêts nécessaires à l’évaluation du seuil. |
| **Q4. Comment répartir au mieux le budget limité pour protéger en priorité les zones et les moments les plus risqués ?** |  **Partielle** — permet de caractériser la pression urbaine et l’interface entre espaces urbanisés et espaces naturels. |  **Partielle** — permet d’identifier les secteurs ayant connu des incendies et donc de repérer les zones nécessitant potentiellement une attention particulière. |  **Partielle** — permet de localiser et de caractériser les espaces forestiers à protéger, mais ne permet pas à elle seule de déterminer la répartition optimale du budget. |


## 6. Décisions face aux données manquantes

- **Q1 — Zones les plus touchées :** utiliser l'artificialisation des sols comme premier indicateur de caractérisation des territoires.
- **Q2 — Périodes et horaires :** utiliser les données **BDIFF** afin d'extraire les dates et heures des départs de feux.
- **Q3 — Météo des forêts :** revoir les datasets disponibles et extraire les métriques nécessaires pour croiser les niveaux de danger avec les interventions réelles.
- **Q4 — Répartition du budget :** en l'absence de données financières détaillées, utiliser l'artificialisation des sols comme **indicateur proxy** pour orienter les actions de prévention.
