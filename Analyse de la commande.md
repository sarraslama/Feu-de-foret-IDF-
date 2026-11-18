# Analyse de la commande collective

## 1. Les questions

Les quatre questions auxquelles l'analyse devra apporter des réponses sont :

* **Quelles sont les caractéristiques des zones les plus touchées par les incendies en Seine-et-Marne ?**
* **À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents en Seine-et-Marne ?**
* **Quelle est l'ampleur des faux positifs et des faux négatifs associés au seuil actuel de la Météo des forêts ?**
* **Comment répartir au mieux un budget et des ressources limitées afin de protéger en priorité les zones et les périodes les plus à risque ?**

---

## 2. Les termes inconnus

| **Terme** | **Ce que je pensais que cela voulait dire** | **Définition à retenir / à vérifier** |
| :--- | :--- | :--- |
| **SDIS** | Une entreprise qui prédit le déclenchement des feux. | Service départemental d'incendie et de secours. Il assure notamment la prévention, la préparation et la lutte contre les incendies et les secours aux personnes. |
| **Météo des forêts** | La température des forêts est différente de celle des villes. | Dispositif d'information de Météo-France qui indique quotidiennement le niveau de danger de feu de végétation à l'échelle départementale. |
| **Guet** | Une personne qui surveille les forêts. | Surveillance d'un territoire pour détecter rapidement un départ de feu. Le terme peut désigner une activité ou un dispositif de surveillance. |
| **Indice** | Un seuil qui déclenche automatiquement les feux. | Indicateur permettant d'évaluer un niveau de danger météorologique ou de risque. Il ne signifie pas qu'un incendie va nécessairement se produire. |

---

## 3. Les besoins

### La décision à éclairer en une phrase

> Identifier les territoires et les périodes les plus exposés aux incendies, évaluer la pertinence et redéfinir les seuils d'alerte de la Météo des forêts pour l'été 2027 afin de réduire les faux positifs, et déterminer la répartition optimale des ressources humaines et financières du SDIS 77 consacrées à la prévention, à la surveillance et aux renforcements.

### Ce qui manque dans la commande pour y répondre

* Le budget disponible pour les actions de prévention et de surveillance.
* Le nombre d’agents et les moyens matériels du SDIS 77.
* Les critères et seuils de la Météo des forêts.
* Les données historiques détaillées des interventions.
* Les données météorologiques sur la température, le vent, l’humidité et les précipitations.

---

## 4. Les données

Pour chaque question, voici les données qui seraient idéalement nécessaires pour y répondre :

| **Question** | **Donnée idéale** | **Grain (une ligne = ?)** | **Période** | **Fraîcheur** | **Emprise géographique** |
| :---: | :--- | :--- | :--- | :--- | :--- |
| **1** | Historique des incendies avec leur localisation, les surfaces brûlées et des informations sur l'environnement des zones touchées : végétation, couverture forestière, relief et occupation des sols. | 1 ligne = 1 incendie, associé à une commune et à sa localisation. | Plusieurs saisons comparables jusqu'en 2026. | Historique consolidé jusqu'à la saison 2026 avant la répartition des moyens. | Seine-et-Marne (77), avec un découpage communal. |
| **2** | Historique des niveaux de danger de la Météo des forêts croisé avec les incendies réellement observés, afin de comparer les alertes aux événements réels et de calculer les faux positifs et les faux négatifs. | 1 ligne = 1 jour et 1 département, avec le niveau de danger et la présence ou l'absence d'incendie. | Historique consolidé avant le choix du seuil. En 2027, bulletin disponible avant la décision quotidienne de renfort. | Journalière, pendant la période de diffusion des alertes. | Seine-et-Marne (77). |
| **3** | Données météorologiques comprenant la température, le vent, l'humidité, les précipitations et le niveau de danger de la Météo des forêts, croisées avec l'historique des incendies. | 1 ligne = 1 jour et 1 département pour les données météo, avec les incendies associés à leur date et à leur commune. | Les 5 dernières années. | Journalière. | Seine-et-Marne (77) et Île-de-France. |
| **4** | Historique détaillé des départs de feu avec les dates, les heures, les communes et les surfaces brûlées, afin d'identifier les périodes où les incendies sont les plus fréquents. | 1 ligne = 1 incendie, avec une date et une heure précises. | Historique consolidé et disponibilités à jour lors de la planification des patrouilles. | Données actualisées régulièrement, avec horodatage précis. | Seine-et-Marne (77) et Île-de-France. |
