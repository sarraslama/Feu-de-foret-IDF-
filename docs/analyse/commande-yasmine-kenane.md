---
updated: 2026-11-13T12:32:19.918+01:00
edited_seconds: 6
---
# Analyse de la commande - Yasmine KENANE

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

> [!test] Test
> Le test : si la réponse est X, la direction fait A ; si elle est Y, elle fait B. Si A et B sont identiques, ce n'est pas une question analytique pertinente.
https://github.com/sarraslama/Feu-de-foret-IDF-/blob/Yasmine/docs/analyse/commande-yasmine-kenane.md
1. Dans quels départements d’Île-de-France les départs de feu se concentrent ils d’une saison à l’autre ?
2. Dans les secteurs prioritaires, quels jours de la semaine et quels créneaux horaires concentrent le plus de départs de feu ?
3. Pour chaque seuil de la Météo des forêts, combien de journées de renfort seraient déclenchées par département francilien, combien seraient sans départ de feu observé et combien de journées avec départ resteraient sous le seuil ?
4. Dans les départements d’Île-de-France, les feux qui démarrent les jours où le niveau de danger annoncé est inférieur au seuil de renfort atteignent-ils des surfaces brûlées comparables à celles observées dans le reste de la France, pour les mêmes niveaux de danger ?

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

## 5. Confrontation aux sources

### Matrice

| Question individuelle | Lien avec le groupe | BDIFF | Météo des forêts | Artificialisation des sols | MOS Île-de-France (complément) |
|---|---|---|---|---|---|
| 1. Dans quels départements franciliens les départs de feu se concentrent-ils d’une saison à l’autre ? | A — Zones les plus touchées | **Partiel.** `Département`, `Année` et la date de première alerte permettent de compter les feux recensés par département et par saison. L’extraction s’arrête en 2025 et son exhaustivité n’est pas garantie. | **Absent.** La rubrique « Grain » décrit un niveau de danger annoncé, sans comptage des feux. | **Absent.** Les rubriques « Grain » et « Période » décrivent l’artificialisation par commune ou département entre deux millésimes. Cette source peut caractériser les zones pour la question A du groupe, mais elle ne permet pas de repérer où les feux se concentrent. | **Partiel.** `Poste 2025`, `insee` et `st_area_sh` peuvent servir à estimer la surface boisée par département et à contextualiser les comptages BDIFF. L’unité de `st_area_sh` reste à vérifier. |
| 2. Quels jours et créneaux horaires concentrent les départs de feu dans les secteurs prioritaires ? | D — Périodes où les incendies sont les plus fréquents | **Partiel.** La rubrique « Grain » confirme la date de première alerte et la commune. La présence d’une heure exploitable dans le CSV et sa complétude restent à vérifier. | **Absent.** Les rubriques « Grain » et « Clés et variables » décrivent des prévisions quotidiennes, sans heure de départ des feux. | **Absent.** La rubrique « Période » décrit deux millésimes d’occupation du sol, sans dates ni heures de feu. | **Absent.** `Poste 2021` et `Poste 2025` décrivent des zones d’occupation du sol, sans horaires de feu. |
| 3. Pour chaque seuil, combien de journées de renfort seraient déclenchées, combien seraient sans départ observé et combien de journées avec départ resteraient sous le seuil ? | B — Faux positifs et faux négatifs | **Partiel.** `Département` et la date de première alerte permettent de compter les journées avec feu recensé. La rubrique « Limites » signale que l’extraction peut manquer d’exhaustivité. | **Partiel.** La rubrique « Clés et variables » décrit le code département, la date de prévision, le niveau de danger et l’échéance. Ces champs permettent de simuler les jours où un seuil aurait été atteint, sous réserve de vérifier les dates présentes dans les CSV. | **Absent.** Les rubriques « Grain » et « Période » ne fournissent ni danger quotidien ni départ recensé. | **Absent.** Les champs `Poste 2021` et `Poste 2025` ne renseignent ni le danger quotidien ni les moyens de renfort. |
| 4. Les feux qui démarrent sous le seuil atteignent-ils des surfaces comparables en Île-de-France et dans le reste de la France, à niveau de danger identique ? | C — Lien entre incendies et Météo des forêts | **Partiel.** La fiche indique une surface parcourue par feu en m². Certaines valeurs manquent et l’extraction étudiée couvre uniquement l’Île-de-France. | **Partiel.** La rubrique « Clés et variables » décrit le niveau annoncé par département et par date cible. La rubrique « Emprise » indique une couverture métropolitaine. La surface parcourue vient de la BDIFF. | **Absent.** La rubrique « Période » décrit l’évolution des sols, sans surface parcourue par feu. | **Absent.** `st_area_sh` correspond à une surface cartographiée dans le MOS. La surface parcourue par chaque incendie est une variable distincte. |

### Écarts avec la section 4

| Question | Meilleure source | Grain | Période | Fraîcheur | Emprise |
|---|---|---|---|---|---|
| 1 | BDIFF | Un départ localisé et un découpage des secteurs → un incendie recensé, rattaché à une commune et à un département. | Plusieurs saisons jusqu’en 2026 → extraction 2006–2025. | Historique consolidé jusqu’à la saison 2026 → diffusion après validation annuelle, dernier millésime observé 2025. | Île-de-France avec détail par secteur → Île-de-France avec détail par commune et département. |
| 2 | BDIFF | Un départ avec heure de début et un relevé des moyens par créneau → un feu avec date de première alerte. Heure à vérifier dans le CSV. Moyens de patrouille non documentés. | Historique des feux jusqu’en 2026 et disponibilités pour 2027 → feux observés de 2006 à 2025. Disponibilités 2027 manquantes. | Historique consolidé et disponibilités 2027 à jour → historique diffusé après validation annuelle. | Secteurs prioritaires franciliens → communes et départements franciliens. Le rattachement aux secteurs reste à établir. |
| 3 | Météo des forêts + BDIFF | Une ligne par département et par jour avec danger, décompte des feux et moyens de renfort → bulletins quotidiens à deux échéances et une ligne par feu BDIFF. Le décompte quotidien est à construire. Les coûts ou heures de renfort manquent. | Saisons communes jusqu’en 2026 → recouvrement potentiel en 2024 et 2025. Les jours communs sont à vérifier dans les fichiers. | Historique consolidé et bulletin disponible avant le renfort → publication météo quotidienne à 17 h pendant la période de diffusion, BDIFF diffusée après validation annuelle. | = pour le périmètre francilien visé. Vérifier la présence des départements et des dates dans les CSV météo. |
| 4 | BDIFF + Météo des forêts | Une ligne par feu avec surface finale en hectares et une ligne de danger par département et jour → surface parcourue en m² avec valeurs manquantes et prévisions à deux échéances. Convertir les surfaces et retenir une échéance commune. | Mêmes saisons et dates sur les territoires comparés, idéalement jusqu’en 2026 → recouvrement potentiel en 2024–2025 pour l’extraction francilienne. La période commune au comparateur reste à vérifier. | Surfaces et bulletins consolidés avant l’arbitrage → export BDIFF issu de campagnes annuelles et archives de bulletins quotidiens. | Île-de-France et reste du territoire national → extraction BDIFF francilienne et météo à couverture métropolitaine. Une extraction d’incendies hors Île-de-France est nécessaire pour la comparaison. |

### Décisions

| Question | Ce qui manque | Décision | Pourquoi | Ce que la décision coûte |
|---|---|---|---|---|
| 1 | Saison 2026 et confirmation de la couverture par département et saison. | **Collecter.** Vérifier la couverture du CSV et récupérer le millésime 2026 lorsqu’il sera disponible. | Comparer les départements sur les mêmes saisons et distinguer les feux recensés des lacunes de couverture. | Temps de contrôle et délai de publication. L’analyse initiale porte sur l’extraction 2006–2025. |
| 2 | Heure exacte de départ et données sur les moyens disponibles par créneau. | **Approximer.** Vérifier la présence de l’heure de première alerte dans le CSV et l’utiliser comme proxy si elle est exploitable. Si elle manque, limiter l’analyse au jour ou au mois. | L’heure d’alerte permet d’étudier les créneaux observés lorsqu’elle est renseignée. | Le délai entre le départ et l’alerte peut déplacer un feu d’un créneau à l’autre. Les résultats ne permettent pas de chiffrer les heures de patrouille à prévoir. |
| 3 | Seuil actuel, coûts ou heures de renfort et règle pour interpréter les jours sans événement BDIFF. | **Collecter.** Demander les règles de renfort et les moyens associés. Vérifier les dates communes et retenir une seule échéance météo par département et jour. | Simuler des journées de renfort comparables et éviter de confondre une journée sans feu recensé avec une journée sans donnée exploitable. | Temps de rapprochement et délai d’accès aux données opérationnelles. Sans ces données, le résultat reste une simulation du nombre de journées. |
| 4 | Extraction BDIFF hors Île-de-France sur les mêmes dates, avec surfaces exploitables. | **Collecter.** Télécharger une extraction couvrant le territoire de comparaison et vérifier la complétude des surfaces. | Comparer des feux observés aux mêmes niveaux de danger sur des périodes communes. | Temps de téléchargement et de contrôle. La comparaison sera limitée aux territoires et aux jours couverts par les deux sources, avec une surface renseignée. |
