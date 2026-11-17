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

| Question | Source explorée | Couverture | Justification |
|---|---|---|---|
| **Q1 — Caractéristiques des zones touchées** | Artificialisation des sols — fichier communal | **Partielle** | Le grain communal et les pourcentages d'artificialisation permettent de caractériser les communes et d'identifier les zones où l'interface habitat-forêt peut être importante. Cependant, la source ne contient pas l'historique des départs de feux. |
| **Q2 — Périodes de concentration des feux** | BDIFF — historiques des interventions du SDIS 77 |  **Bonne** | Les dates et heures des interventions permettent d'identifier les mois et les plages horaires où les départs de feux sont les plus fréquents. |
| **Q3 — Faux positifs / faux négatifs** | Données Météo des forêts + interventions réelles |  **À compléter** | Les différents jeux de données doivent être croisés afin de comparer le niveau de danger annoncé avec les interventions réellement observées. Les métriques de faux positifs et de faux négatifs pourront ensuite être calculées. |
| **Q4 — Répartition du budget et des ressources** | Artificialisation des sols — fichier communal |  **Partielle** | En l'absence de données précises sur les coûts et les ressources disponibles, l'artificialisation peut servir d'indicateur pour identifier les zones où la pression liée à l'interface habitat-forêt est importante et orienter les actions de prévention. |

---

## 6. Décisions face aux données manquantes

- **Q1 — Zones les plus touchées :** utiliser l'artificialisation des sols comme premier indicateur de caractérisation des territoires.
- **Q2 — Périodes et horaires :** utiliser les données **BDIFF** afin d'extraire les dates et heures des départs de feux.
- **Q3 — Météo des forêts :** revoir les datasets disponibles et extraire les métriques nécessaires pour croiser les niveaux de danger avec les interventions réelles.
- **Q4 — Répartition du budget :** en l'absence de données financières détaillées, utiliser l'artificialisation des sols comme **indicateur proxy** pour orienter les actions de prévention.
