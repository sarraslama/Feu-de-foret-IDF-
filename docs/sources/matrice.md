# Matrice de confrontation des questions et des sources

Cette matrice confronte les questions retenues par le groupe aux sources recensées dans l'inventaire. Elle permet d'identifier les informations disponibles, les limites de chaque source et les données complémentaires à rechercher.

## 1. Sources étudiées

Les sources prises en compte dans cette première version sont :

1. **Mode d'occupation du sol (MOS)** : permet de caractériser l'occupation des territoires.
2. **BDIFF** : Base de données sur les incendies de forêts en France, qui recense les incendies et leurs caractéristiques.
3. **Artificialisation des sols** : fournit des informations sur l'évolution de l'artificialisation à l'échelle des communes et des départements.
4. **Météo des forêts** : fournit des niveaux quotidiens de danger météorologique liés aux feux de forêt.

Les degrés de couverture utilisés sont :
- **Complet** : la source permet de répondre à la question avec la précision géographique, temporelle et le niveau de détail nécessaires.
- **Partiel** : la source apporte des informations utiles, mais certaines données ou précisions manquent.
- **Absent** : la source ne contient pas d'informations utiles pour répondre à la question.
- **Inconnu** : les informations disponibles ne permettent pas encore de vérifier la couverture.

## 2. Matrice de couverture

| Question | MOS | BDIFF | Artificialisation des sols | Météo des forêts |
|---|---|---|---|---|
| **Q1. Quelles sont les caractéristiques des zones les plus touchées en Seine-et-Marne ?** | **Inconnu** — la fiche du MOS doit être vérifiée pour confirmer son niveau géographique, sa période et la possibilité de le croiser avec les lieux d'incendie. | **Partiel** — permet d'identifier les incendies recensés, les communes, les départements et les surfaces brûlées. Cependant, le champ « Type de peuplement » est vide dans notre extrait et les caractéristiques détaillées de la végétation manquent. | **Partiel** — permet de caractériser l'artificialisation des communes, mais ne décrit pas directement les zones incendiées ni leur végétation. | **Partiel** — fournit des niveaux de danger par département et par jour, mais ne permet pas de caractériser précisément les types de zones touchées. |
| **Q2. À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents ?** | **Absent** — décrit l'occupation du sol, mais ne contient pas les dates ou les heures des incendies. | **Partiel** — contient des informations temporelles sur les incendies, notamment la date de première alerte. La disponibilité d'une heure suffisamment précise doit être vérifiée avant de réaliser une analyse matin/nuit. | **Absent** — ne fournit pas de dates ni d'heures de départ de feux. | **Partiel** — permet d'étudier les jours et périodes présentant différents niveaux de danger, mais ne fournit pas les heures réelles de départ des incendies. |
| **Q3. Quelle est l'ampleur des faux positifs et des faux négatifs sous le seuil actuel de la Météo des forêts ?** | **Absent** — ne fournit ni les niveaux de danger météorologique ni les événements d'incendie nécessaires à cette comparaison. | **Partiel** — permet d'identifier les incendies effectivement recensés, mais ne contient pas les niveaux de danger annoncés. | **Absent** — ne contient ni les niveaux de danger ni les événements nécessaires pour calculer ces indicateurs. | **Partiel** — fournit les niveaux quotidiens de danger annoncés, mais ne suffit pas seule à calculer les faux positifs et les faux négatifs. Un rapprochement avec les incendies recensés et une définition du seuil sont nécessaires. |
| **Q4. Comment répartir au mieux le budget limité pour protéger en priorité les zones et les moments les plus risqués ?** | **Inconnu** — la fiche doit être vérifiée pour déterminer si les données permettent de caractériser les territoires à une échelle suffisamment précise pour orienter la surveillance. | **Partiel** — permet d'identifier les secteurs ayant connu des incendies et d'étudier leur fréquence et les surfaces brûlées, mais ne fournit pas les coûts ni les moyens nécessaires aux interventions. | **Partiel** — apporte un contexte sur l'artificialisation des territoires, mais ne permet pas de déterminer directement les besoins opérationnels ou les budgets à attribuer. | **Partiel** — permet de repérer les jours et départements présentant des niveaux de danger élevés, mais ne fournit ni les coûts ni les effectifs disponibles pour organiser les moyens. |

## 3. Analyse des résultats par question

### Q1 — Les caractéristiques des zones les plus touchées

La BDIFF constitue la source principale pour localiser les incendies recensés et repérer les communes les plus touchées en Seine-et-Marne. Elle permet également d'étudier les surfaces brûlées.

Le MOS pourrait compléter cette analyse en apportant des informations sur l'occupation du sol, par exemple les espaces forestiers, agricoles, urbains ou naturels. Toutefois, sa fiche doit être examinée pour vérifier les possibilités de croisement avec les données de la BDIFF.

L'artificialisation des sols apporte un complément sur le contexte territorial, mais ne permet pas à elle seule de caractériser les espaces forestiers.

La Météo des forêts peut aider à étudier les niveaux de danger auxquels les départements ont été exposés, mais son échelle départementale ne permet pas de décrire précisément chaque zone touchée.

**Décision provisoire :** compléter l'analyse avec le MOS après vérification de sa fiche et rechercher des données plus précises sur la végétation et les caractéristiques des espaces naturels.

### Q2 — Les périodes et les horaires des départs de feux

La BDIFF est la source la plus utile pour cette question, car elle contient des informations temporelles sur les incendies recensés.

Il faut néanmoins vérifier si la colonne « Date de première alerte » contient une heure exploitable. Si elle ne contient qu'une date, l'analyse pourra porter sur les années, les mois et les périodes de l'année, mais pas sur les horaires matin/nuit.

La Météo des forêts peut compléter cette analyse en indiquant les périodes pendant lesquelles le danger météorologique était plus élevé. Elle ne donne cependant pas les heures réelles de départ des incendies.

**Décision provisoire :** exploiter les dates de la BDIFF et vérifier la disponibilité des heures. Si elles sont absentes, rechercher des données d'intervention plus précises auprès du SDIS 77.

### Q3 — Les faux positifs et les faux négatifs

Cette question nécessite de rapprocher deux types d'informations :

- La BDIFF, qui recense les incendies effectivement observés.
- La Météo des forêts, qui fournit les niveaux de danger météorologique annoncés.

Il faut cependant faire attention à l'interprétation des résultats. La Météo des forêts évalue un niveau de danger : elle ne prédit pas qu'un incendie va nécessairement se produire.

Pour calculer des faux positifs et des faux négatifs, le groupe devra donc définir précisément :
- le seuil à partir duquel un niveau de danger sera considéré comme une alerte positive ;
- la période et la zone géographique utilisées pour comparer l'alerte aux incendies ;
- la définition d'un événement observé et de l'absence d'événement.

Sans ces définitions, les indicateurs risquent d'être trompeurs. Il faudra également tenir compte du fait que les archives de la Météo des forêts couvrent une période plus courte que l'historique de la BDIFF.

**Décision provisoire :** collecter et rapprocher les données nécessaires, puis définir une méthode de calcul avant de produire les indicateurs.

### Q4 — La répartition du budget et des moyens

Les sources disponibles permettent de construire une première analyse des secteurs et des périodes qui pourraient nécessiter davantage de surveillance.

La BDIFF permet d'identifier les zones ayant déjà connu des incendies. Le MOS pourrait apporter des informations sur les types d'espaces concernés. L'artificialisation des sols permet de mieux comprendre le contexte territorial, tandis que la Météo des forêts permet de repérer les périodes de danger élevé.

En revanche, aucune de ces sources ne permet de déterminer précisément la répartition optimale du budget.

Il manque notamment :
- le budget total disponible ;
- le coût des dispositifs de surveillance ;
- le coût des interventions ;
- le nombre d'agents disponibles ;
- les moyens matériels et leur disponibilité ;
- les coûts associés aux différentes zones et périodes de surveillance.

**Décision provisoire :** réaliser une première priorisation géographique et temporelle à partir des sources existantes, puis rechercher des données budgétaires et opérationnelles pour proposer une répartition réaliste des ressources.

## 4. Bilan de la confrontation

Les sources étudiées sont complémentaires, mais aucune ne permet à elle seule de répondre à toutes les questions.

| Source | Apport principal | Limite principale |
|---|---|---|
| MOS | Caractérisation de l'occupation du sol. | Fiche et niveau de précision à vérifier. |
| BDIFF | Historique des incendies, localisation et surfaces brûlées. | Informations environnementales et horaires à vérifier ou compléter. |
| Artificialisation des sols | Contexte territorial et évolution de l'artificialisation. | Ne décrit pas directement les incendies ni les conditions météorologiques. |
| Météo des forêts | Niveaux quotidiens de danger météorologique. | Ne constitue pas une prédiction certaine d'incendie et ne fournit pas les moyens opérationnels. |

Les principaux besoins complémentaires identifiés sont :

1. Des informations précises sur les heures de départ des incendies.
2. Une vérification des caractéristiques et de la couverture du MOS.
3. Un historique des niveaux de danger de la Météo des forêts permettant une comparaison avec les incendies observés.
4. Des données météorologiques complémentaires si l'analyse doit porter sur la température, le vent, l'humidité et les précipitations.
5. Des données budgétaires, humaines et matérielles pour étudier la répartition des ressources.

## 5. Conclusion

La confrontation des questions aux sources montre que les données disponibles permettent déjà d'étudier l'historique des incendies, leur localisation, les surfaces brûlées et les périodes de danger météorologique.

Cependant, plusieurs analyses nécessitent des informations supplémentaires, notamment pour étudier les horaires des départs de feux, mesurer correctement les faux positifs et les faux négatifs et proposer une répartition concrète des ressources.

Cette matrice constitue une première version collective. Elle devra être actualisée à mesure que les fiches de sources seront vérifiées, que les questions seront validées par le groupe et que de nouvelles données seront identifiées.
