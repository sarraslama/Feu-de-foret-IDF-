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
| Question | Mode d’occupation du sol (MOS) | BDIFF | Artificialisation des sols | Météo des forêts |
|---|---|---|---|---|
| **Q1. Quelles sont les caractéristiques des zones les plus touchées en Seine-et-Marne ?** |  **Bonne** — permet de caractériser l’occupation du sol et de distinguer les espaces urbains, agricoles, forestiers et naturels. |  **Bonne** — permet de localiser les incendies et d’identifier les secteurs les plus touchés. |  **Partielle** — permet de caractériser le niveau d’artificialisation et la pression urbaine sur les territoires concernés. | **Partielle** — permet de caractériser les niveaux de danger météorologique associés aux territoires et aux périodes étudiées. |
| **Q2. À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents ?** |  **Absente** — ne fournit pas l’historique temporel des incendies. | **Bonne** — permet d’analyser la répartition des incendies dans le temps si les dates et heures des événements sont disponibles. |  **Absente** — ne contient pas les dates et horaires des incendies. |  **Partielle** — permet de comparer les périodes de danger météorologique avec les périodes de survenue des incendies, mais ne permet pas à elle seule d’identifier les heures de départ des feux. |
| **Q3. Quelle est l’ampleur des faux positifs et des faux négatifs sous le seuil actuel de la Météo des forêts ?** |  **Absente** — ne fournit ni prévisions météorologiques ni historique des incendies. | **Bonne** — fournit les incendies réellement observés nécessaires pour comparer les prévisions aux événements réels. |  **Absente** — ne fournit pas les niveaux de danger météorologique ni les incendies observés. |  **Bonne** — fournit les niveaux de danger permettant de comparer les prévisions avec les incendies réellement observés dans la BDIFF. |
| **Q4. Comment répartir au mieux le budget limité pour protéger en priorité les zones et les moments les plus risqués ?** | **Bonne** — permet d’identifier les types d’occupation du sol présents dans les zones exposées et de cibler les secteurs prioritaires. |  **Bonne** — permet d’identifier les secteurs ayant connu des incendies et d’évaluer leur récurrence. |  **Partielle** — permet d’identifier les secteurs soumis à une forte pression urbaine, mais ne permet pas de déterminer directement la répartition du budget. |  **Bonne** — permet d’identifier les périodes et les niveaux de danger afin de cibler les moments nécessitant davantage de moyens. |



## 6. Décisions face aux données manquantes


L’analyse des sources disponibles montre que certaines questions ne peuvent pas être traitées complètement avec les données actuelles. Il est donc nécessaire de préciser quelles données doivent être recherchées en priorité et quelles hypothèses peuvent être retenues lorsque certaines informations restent indisponibles.
