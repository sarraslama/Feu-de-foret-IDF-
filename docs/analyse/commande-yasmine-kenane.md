---
updated: 2026-11-13T12:32:19.918+01:00
edited_seconds: 6
---
# Analyse de la commande - Yasmine KENANE

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

> [!test] Test
> Le test : si la réponse est X, la direction fait A ; si elle est Y, elle fait B. Si A et B sont identiques, ce n'est pas une question analytique pertinente.

1. Dans quels départements d’Île-de-France les départs de feu se concentrent ils d’une saison à l’autre ?
2. Dans les secteurs prioritaires, quels jours de la semaine et quels créneaux horaires concentrent le plus de départs de feu ?
3. Pour chaque seuil de la Météo des forêts, combien de journées de renfort seraient déclenchées par département francilien, combien seraient sans départ de feu observé et combien de journées avec départ resteraient sous le seuil ?
4.Dans les départements d’Île-de-France, les feux qui démarrent les jours où le niveau de danger annoncé est inférieur au seuil de renfort atteignent-ils des surfaces brûlées comparables à celles observées dans le reste de la France, pour les mêmes niveaux de danger ?

## 2. Les termes inconnus

Les mots de la commande que vous ne savez pas définir précisément, ou qui peuvent se comprendre de plusieurs façons.

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
| Départ de feu | Début d’un incendie de végétation en un lieu et à un moment donnés. | Quels types de végétation sont inclus ? Comment compter un feu qui donne lieu à plusieurs alertes ou interventions ? |
| Secteur d’intervention | Zone géographique sur laquelle des équipes peuvent être affectées. | Quel découpage la direction utilise-t-elle pour répartir les moyens ? |
| Saison des feux | Période de l’année pendant laquelle la surveillance des feux est organisée. | Quelles dates retenir, et faut-il appliquer les mêmes dates aux territoires comparés ? |
| Niveau de danger de la Météo des forêts | Niveau de danger annoncé pour une date et un territoire donnés. | Quels sont les niveaux, leur ordre, la date visée par le bulletin et son échelle géographique ? |
| Seuil de déclenchement | Niveau à partir duquel le dispositif renforcé est activé. | Quel seuil est actuellement appliqué ? Est-il commun à tous les départements ? |
| Dispositif renforcé | Moyens de surveillance supplémentaires, comme des patrouilles ou du guet. | Quelles actions sont déclenchées et combien d’heures, d’équipes ou de dépenses mobilisent-elles ? |

## 3. Les besoins

La décision à éclairer, en une phrase : Pour la saison des feux 2027, la direction doit décider où et quand concentrer les moyens de surveillance en Île-de-France et à partir de quel niveau de danger déclencher le dispositif renforcé, compte tenu des moyens disponibles.

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) :


- Le périmètre exact de la décision, à l’échelle de toute l’Île-de-France ou d’un département pilote, ainsi que le découpage utilisé pour affecter les équipes.
- Les dates de début et de fin de la saison à étudier et les types de feux à inclure.
- Le seuil actuellement appliqué et les actions déclenchées lorsque ce seuil est atteint.
- Le budget, les équipes et les heures mobilisables, et le coût d’une journée de renfort.
- La priorité donnée à la couverture des journées avec départ de feu par rapport au coût des journées de renfort.


## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| 1 | Historique des départs de feu avec un identifiant unique, la date et la localisation du départ. Découpage des secteurs pour rattacher chaque départ à une zone d’intervention. | Une ligne par départ de feu. Une ligne par secteur dans le découpage géographique. | Plusieurs saisons comparables jusqu’à 2026. | Historique consolidé jusqu’à la saison 2026 avant la répartition des moyens. | Île-de-France, avec un détail par secteur d’intervention. |
| 2 | Date, heure de départ et secteur de chaque feu. Heures de patrouille et de guet mobilisables par secteur et par créneau. | Une ligne par départ de feu. Une ligne par secteur, date et créneau pour les moyens disponibles. | Plusieurs saisons jusqu’à 2026 pour les feux. Saison 2027 pour les moyens. | Historique consolidé et disponibilités à jour lors de la planification des patrouilles. | Secteurs prioritaires d’Île-de-France. |
| 3 | Niveau de danger annoncé pour la journée, nombre de départs, coût estimé et heures nécessaires pour une journée de renfort. Les journées sans départ confirmé et les journées où l’information manque doivent être identifiables. | Une ligne par département et par jour. | Toutes les saisons communes aux historiques des bulletins et des départs, idéalement jusqu’à 2026. | Historique consolidé avant le choix du seuil. En 2027, bulletin disponible avant la décision quotidienne de renfort. | Départements d’Île-de-France. |
| 4 | Surface finale brûlée en hectares, date et département du départ de chaque feu, niveau de danger annoncé pour ce département et ce jour. | Une ligne par feu pour la surface brûlée. Une ligne par département et par jour pour le niveau de danger. | Mêmes saisons et mêmes dates pour tous les départements comparés, idéalement jusqu’en 2026. | Surfaces brûlées et bulletins consolidés avant le choix du seuil pour 2027. | Départements d’Île-de-France et reste du territoire national, selon le périmètre à confirmer. |