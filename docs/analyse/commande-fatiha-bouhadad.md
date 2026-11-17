
# Analyse de la commande - Fatiha Bouhadad

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

> [!test] Test
> Le test : si la réponse est X, la direction fait A ; si elle est Y, elle fait B. Si A et B sont identiques, ce n'est pas une question analytique pertinente.

1.	Quelles sont les caractéristiques des zones les plus touchées à seine et marne ? 
2.  Quelles sont les périodes ou les départs de feux se concentrent le plus en Seine et Marne ? (matin/ nuit ; / mois) ?
3.  Quelle est l'ampleur des fausses alertes (faux positifs) et des faux négatifs sous le seuil actuel de la Météo des forêts ?
4.  Comment répartir au mieux le budget limité pour protéger en priorité les zones et les moments les plus risqués ?

## 2. Les termes inconnus

Les mots de la commande que vous ne savez pas définir précisément, ou qui peuvent se comprendre de plusieurs façons.

| Terme   | Ce que je crois qu'il veut dire                       | Ce qu'il faudrait vérifier |
|SDIS   |Une entreprise qui s'occupe des déclenchement des feux| Service départemental d'incendie et de secours|
|Le niveau de la Météo des forêts |La température des forêts est différente de celle des villes  |Évoluer la gravité et le niveau de danger de foret |
|Guet  |Une personne qui surveille les forets| L’opération à mettre à disposition pour anticiper le danger|
|Indice  |Seuil du déclenchement des feux | évalue un niveau de danger potentiel météorologique |


## 3. Les besoins

La décision à éclairer, en une phrase : Choisir comment répartir les ressources humaines et financières du SDIS 77 et redéfinir le seuil d'alerte de la Météo des forêts pour l'été 2027 afin de réduire les faux positifs. 

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) : Le budget exact alloué aux renforcements, le nombre d'agents disponibles, ou encore la définition précise du seuil actuel qui pose problème.
-

## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| 1 | Historique des interventions de feux de forêt avec les données géographiques | 1 ligne = 1 intervention de feu|5 dernières années | Annuelle|Département de la Seine et Marne avec découpage communal |
| 2 | Horodatage précis (date, heure) des départs de feux| 1 ligne = 1 intervention de feu (avec date/heure)| 5 dernières années| Journalière / Mensuelle|Département de la Seine et Marne et ile de france |
| 3 | Historique journalier croisé entre l'indice Météo des forêts et les interventions réelles sur le terrain| 1 ligne = 1 jour / 1 commune ou secteur| Les étés des 3 dernières années| Journalière|Département de la Seine et Marne|
| 4 | Données comptables du coût des déploiements| 1 ligne = 1 secteur opérationnel / coût journalier| deux dernieres annees|Annuelle recentes | Département de la Seine et Marne et ile de france|



## 5. Confrontation des questions aux sources

# Matrice de couverture

| Question | Source explorée | Degré de couverture | Raison et justification (colonnes / rubriques) |
|---|---|---|---|
| 1. Caractéristiques des zones touchées (77) | Artificialisation des sols (Fichier communal) | partiel | Le grain communal (commune_code, nom) et les pourcentages d'artificialisation permettent de caractériser l'urbanisation des communes forestières du 77 mais la source ne contient pas l'historique direct des départs de feux. |
| 2. Périodes de concentration des feux | Artificialisation des sols | absent | Le fichier mesure l'artificialisation globale des sols par millésime et il ne contient aucun horodatage ni date/heure d'intervention. |
| 3. Ampleur des fausses alertes | Artificialisation des sols | absent | Aucune donnée sur les bulletins météorologiques journaliers, les niveaux de vigilance ou les interventions réelles du SDIS. |
| 4. Répartition optimale du budget et des ressources | Artificialisation des sols | partiel | Permet d'identifier les zones de forte pression urbaine (interface habitat-forêt) mais ne contient pas les données comptables des coûts de déploiement des secours. |

# Décisions face aux manques

Pour la Q2 (Périodes et horaires): un membre du groupe à pris la source BDIFF qui contient les historiques d'interventions du SDIS 77 pour obtenir l'horodatage précis (mois, heure) des départs de feux.
Pour la Q3 (Fausses alertes / Météo des forêts) : collecter :je vais revoir certains datasets et extraire certaines métriques qui vont me permettre de faire le lien et de résoudre la Q3
Pour la Q 4 (Répartition du budget) : approximer — En l'absence de données comptables précises sur les coûts de déploiement nous utilisons l'analyse spatiale de l'artificialisation et de la localisation des zones à risque (couplée au carroyage DFCI) comme proxy pour cibler les secteurs prioritaires.
