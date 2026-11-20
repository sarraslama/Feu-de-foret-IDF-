# Diagnostic collectif et objectifs retenus — SDIS 77

**Version** — Jeu collectif v0 actualisé le 20 novembre 2026.  
**Commanditaire** — SDIS 77.  
**Périmètre analytique** — Toute l’Île-de-France, avec restitution par département. Les décisions d’affectation des moyens concernent le SDIS 77 ; une comparaison régionale ne lui attribue pas d’autorité sur les autres SDIS.  
**Statut** — Synthèse des huit fichiers individuels transmis. Arbitrages, responsables et cibles à valider par le groupe et le commanditaire. Les objectifs opérationnels pour 2027 sont des propositions de pilotage, pas des résultats déjà obtenus.

## 1. Mise en commun des contributions

| Contribution | Apport | Arbitrage proposé |
|---|---|---|
| KPI1 — Localisation et vulnérabilité spatiale | Choisir les secteurs prioritaires et mesurer leur couverture | Fusion avec KPI3 dans O1, en conservant les analyses spatiales |
| KPI2 — Seuils Météo des forêts | Comparer les journées signalées aux journées avec feu recensé | Objectif O2, évaluation des seuils et de leur charge potentielle |
| KPI3 — Organisation temporelle | Identifier les saisons et horaires à prendre en compte dans la surveillance | Fusion avec KPI1 dans O1, en conservant les profils temporels |
| KPI4 — Allocation des moyens et feux majeurs | Suivre les conséquences dans des zones prioritaires et les contraintes de ressources | Objectif O3, sous réserve de données opérationnelles et de validation des cibles |

**Trois objectifs sont proposés pour la suite**, conformément à la consigne de retenir trois à cinq objectifs après fusion des doublons. Les contributions individuelles restent conservées. Les deux documents KPI4 sont rapprochés comme une seule contribution ; le document intitulé « diagnostic » contient essentiellement des fiches d’indicateurs.

## Choix du KPI principal collectif

**KPI retenu — Part des journées avec au moins un feu recensé qui restent sous le seuil de déclenchement envisagé pour le dispositif renforcé.** Ce choix fait suite à la mise en commun et à la décision de retenir I1 comme indicateur principal du livrable. Il ne vaut pas validation du seuil opérationnel ou de la cible par le SDIS 77.

**Décision éclairée.** Quel seuil choisir pour préparer les moyens du SDIS 77, en s’appuyant sur une comparaison des départements d’Île-de-France ?

**Formule.** 100 × nombre de jours-départements avec au moins un feu recensé et niveau météo inférieur à N / nombre de jours-départements avec au moins un feu recensé. Un département et une date représentent une observation, même si plusieurs feux sont recensés. Calculer séparément J+1 et J+2.

**Justification.** Ce KPI relie le choix du seuil à un résultat observable avec BDIFF et Météo des forêts sur leurs périodes communes de 2024 et 2025. Il est restitué par département, avec une lecture spécifique du 77. La valeur de référence est à mesurer après validation des dates ; la cible est à fixer avec le SDIS.

**Garde-fous.** Lire systématiquement I1 avec G1, part des journées signalées sans feu recensé, et G2, volume et part des journées signalées. Abaisser N peut améliorer I1 tout en générant une charge potentielle excessive.

**Articulation des sources.** MOS et artificialisation expliquent les caractéristiques territoriales ; les profils spatiaux et horaires préparent le ciblage. I1 mesure la concordance entre un seuil de danger et les feux recensés. L’efficacité réelle des interventions demande des données opérationnelles supplémentaires.

## 2. Diagnostic aux quatre niveaux

| Niveau | Formulation collective | Établi ou supposé ? | Élément de preuve ou validation attendue |
|---|---|---|---|
| Stratégie | Aider le SDIS 77 à préparer la prévention et la surveillance des feux, en éclairant ses choix par une étude francilienne | Établi pour le périmètre ; formulation stratégique à faire valider | Cadrage du projet et périmètre confirmé par le groupe |
| Enjeu | Répartir des moyens limités entre lieux, horaires et niveaux de danger, en maîtrisant les secteurs délaissés et la charge | Supposé quant aux tensions et coûts réels | Budget, effectifs, dispositif actuel et contraintes à demander au SDIS 77 |
| Objectifs | Améliorer la couverture spatio-temporelle, documenter les seuils et suivre l’évolution des feux majeurs | Propositions collectives | O1, O2 et O3 ci-dessous ; valeurs de départ et cibles à compléter |
| Actions | Consolider les sources, contrôler les jointures, calculer les profils et scénarios, puis proposer un dispositif | Actions analytiques proposées | Scripts versionnés, contrôles qualité et restitution ; déploiement soumis au SDIS |

Une action comme « créer une carte » ne constitue pas à elle seule un objectif de résultat. Les objectifs distinguent le livrable analytique de décembre 2026 de l’évaluation opérationnelle envisagée pour 2027.

## 3. Socle factuel et limites

| Source | Ce que permettent les fichiers disponibles | Limite pour le pilotage |
|---|---|---|
| BDIFF — `Incendies.csv` | 347 événements en Île-de-France entre 2006 et 2025, dont 293 dans le 77 ; dates de première alerte, commune et surfaces | Exhaustivité et précision à documenter ; pas de position précise du départ ni de données de patrouilles ou d’arrivée des secours |
| Météo des forêts — `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv` | Niveaux par département, date du fichier et horizons J+1/J+2 | Quatre catégories officielles confirmées ; codage numérique, convention de date et règle SDIS à documenter avant validation des jointures ; aucune donnée d’incendie 2026 dans l’extraction reçue |
| MOS — extraction fournie | Occupation 2021/2025, codes communaux et géométries ; extraction limitée aux bois/forêts en 2025 | Ce filtre ne permet pas de reconstituer toutes les interfaces habitat/forêt/agriculture ; géométries absentes pour certaines lignes ; unité des surfaces exportées à vérifier |
| Artificialisation | Fichier régional fourni ; fichiers communaux et départementaux mentionnés dans les contributions | Les fichiers communaux/départementaux et les règles de typologie doivent être joints pour reproduire les calculs spatiaux |
| Données SDIS / SIM | Besoin identifié | Plannings, coûts, heures réalisées, délais et humidité des sols non disponibles pour cette consolidation |

**Limite temporelle de l’artificialisation.** Selon la documentation transmise, les premiers millésimes vont de 2016 à 2019 et les seconds de 2019 à 2022 selon le territoire. 2022 est la borne maximale annoncée ; les millésimes propres à l’Île-de-France doivent être vérifiés dans les fichiers. Ces données servent de contexte historique et ne mesurent pas directement l’état des sols en 2025 ou 2027. Conserver les deux dates d’observation et documenter le décalage temporel lors des croisements.

L’absence d’événement BDIFF ne prouve pas l’absence de feu. L’absence d’événement dans certains départements ne doit pas produire automatiquement un classement de faible risque. Une surface estimée ne possède pas la même certitude qu’une surface mesurée.

### Niveaux de danger et seuil opérationnel

La documentation officielle de Météo-France distingue **quatre niveaux de danger**, présentés à l’échelle départementale pour le lendemain et le surlendemain.

| Niveau de danger officiel | Couleur |
|---|---|
| Faible | Vert |
| Modéré | Jaune |
| Élevé | Orange |
| Très élevé | Rouge |

Les valeurs **1, 2, 3 et 4** observées dans les fichiers sont des codes. Leur correspondance exacte avec ces catégories doit être confirmée dans le dictionnaire du jeu de données et conservée dans la documentation du pipeline. L’ordre des libellés sur une page grand public ne suffit pas à valider le codage du CSV.

**Le seuil de mobilisation réellement utilisé par le SDIS 77 reste à documenter.** Les quatre catégories ne définissent pas automatiquement sa règle d’activation, les moyens mobilisés ni l’horizon retenu. Pour cette v0, comparer les seuils numériques **N = 2, N = 3 et N = 4** comme des **scénarios exploratoires**, puis interpréter les résultats après validation du codage. Une comparaison sans variation de niveau ou sans effectif suffisant peut être non informative.

La Météo des forêts est un outil de prévention indiquant des conditions favorables aux feux. Elle ne constitue pas une prévision de survenue des incendies et se distingue de la Vigilance météorologique. Les éventuelles restrictions locales sont à rechercher auprès de la préfecture. Un jour signalé sans feu recensé ne prouve pas une prévision erronée ; un feu sous le seuil ne suffit pas à qualifier toute la prévision de défaillante.

## 4. Hypothèses et verdicts

### H1 — Concentration spatiale exploitable pour la surveillance

**Hypothèse.** Certains secteurs concentrent davantage de feux recensés et peuvent justifier une priorité de surveillance.

**Deux éléments de départ.** La BDIFF permet un regroupement communal ; le MOS apporte une information d’occupation du sol. Les contributions proposent également des typologies fondées sur l’artificialisation.

**Confirmation attendue.** Une concentration persiste sur plusieurs années, après contrôle de la couverture des données et, lorsque possible, de la surface exposée. Les zones sont identifiées par une règle reproductible.

**Infirmation attendue.** Le classement change fortement d’une année à l’autre ou provient essentiellement de différences de collecte, de superficie ou de classification.

**Verdict.** Concentrations descriptives observables, mais hypothèse sur les interfaces et la vulnérabilité non conclue. Une commune contenant un feu et une forêt ne localise pas ce feu à une interface. Les résultats par typologie des contributions restent à reproduire avec les fichiers et règles de classement.

### H2 — Concentration saisonnière et horaire

**Hypothèse.** Les feux recensés sont plus fréquents en été et à certaines heures de l’après-midi.

**Deux éléments de départ.** Les dates de première alerte BDIFF sont exploitables ; les regroupements 2023–2025 donnent 66 événements entre juin et septembre sur 106 événements annuels. Sur ces 66 événements estivaux, 24 sont horodatés entre 12 h incluse et 16 h exclue, soit 36,36 %, et 47 entre 12 h incluse et 20 h exclue, soit 71,21 %.

**Confirmation attendue.** Le profil se retrouve sur plusieurs saisons et ne résulte pas d’une heure conventionnelle ou d’un défaut de saisie.

**Infirmation attendue.** Les pics disparaissent après contrôle des horodatages ou ne se reproduisent pas selon les saisons et départements.

**Verdict.** Appui descriptif partiel sur l’extraction. Il ne confirme pas une plage universelle 12 h–15 h ni un lien causal avec température ou humidité. L’heure utilisée est celle de première alerte, proxy de l’heure de départ. L’élargissement d’une plage augmente mécaniquement sa part de feux et sa durée de couverture.

### H3 — Arbitrage entre journées signalées et feux recensés

**Hypothèse.** Le changement de seuil de danger modifie la part des journées avec feu recensé qui restent sous le seuil et le volume des journées signalées.

**Deux éléments de départ.** Les archives météo fournissent deux horizons distincts ; la BDIFF permet de repérer les jours-départements avec au moins un événement recensé.

**Confirmation attendue.** Les scénarios calculés à périmètre constant font apparaître un compromis utile entre détection et volume de jours signalés.

**Infirmation ou limite attendue.** Les effectifs ou la variation des niveaux ne permettent pas de distinguer les scénarios ; la jointure ou la collecte des feux ne permet pas une comparaison fiable.

**Verdict.** À consolider sur 2024 et 2025 après validation des dates. Les résultats exploratoires 2024 du KPI2 ne constituent pas une mesure certifiée du dispositif officiel. Les niveaux météo décrivent un danger, dont la réalisation dépend aussi des mises à feu et des actions de prévention.

## 5. Objectifs collectifs retenus — proposition

### O1 — Améliorer la couverture des feux dans l’espace et le temps

**Action.** Cartographier les secteurs et décrire les horaires des feux recensés.

**Objectif.** Mieux positionner les dispositifs de surveillance selon les lieux et créneaux prioritaires.

**Objectif SMART proposé.** Du 1er juin au 30 septembre 2027, faire passer de **a % à b %** la part des feux recensés en Seine-et-Marne dont le lieu et l’heure de première alerte sont couverts par un dispositif de surveillance conforme à une règle fixée avant la saison, sans dépasser **B heures de surveillance**. Définir les priorités à partir de l’étude de toute l’Île-de-France, avec historique spatial 2021–2025 et profils horaires 2023–2025.

| Critère | Définition |
|---|---|
| Spécifique | Couverture simultanée du secteur et de l’horaire du feu ; définition du dispositif « couvert » à formaliser |
| Mesurable | Nombre de feux couverts / nombre de feux éligibles ; a à mesurer, b à valider après mesure de a |
| Atteignable | Conditionnel à l’accès aux présences réalisées et à une localisation suffisante ; une présence quelque part dans une commune ne suffit pas |
| Réaliste | Heures réelles ≤ B, avec suivi des feux hors des secteurs prioritaires |
| Temporel | Préparation analytique au 11 décembre 2026 ; évaluation opérationnelle fin septembre 2027 si les données sont fournies |

**Référence.** a à mesurer sur une saison antérieure comparable avec dispositif observé. Les 36,36 % de feux entre 12 h et 16 h ne mesurent pas cette couverture.

**Responsabilité proposée.** Contributions KPI1 et KPI3 pour le calcul ; SDIS 77 pour la définition du dispositif, les moyens et la cible.

**Test de cohérence.** Déclarer des secteurs plus grands peut faire monter le taux sans améliorer la surveillance. Fixer une règle de présence vérifiable et suivre les heures réellement engagées.

### O2 — Documenter le choix du seuil de signalement

**Action.** Joindre les prévisions et les événements au grain département-jour.

**Objectif.** Éclairer l’arbitrage entre les journées avec feu non signalées et la charge potentielle des journées signalées.

**Objectif SMART analytique.** D’ici au **11 décembre 2026**, livrer une comparaison reproductible des **trois seuils exploratoires N = 2, 3 et 4**, dont le codage doit être documenté, séparément pour **J+1 et J+2**, sur les journées comparables de **2024 et 2025** des huit départements franciliens, avec matrice de confusion, taux de faux négatifs, part des jours signalés sans feu recensé, volume de jours signalés et rapport des exclusions. Si la convention des dates ne peut être validée, livrer les scénarios comme exploratoires et documenter ce blocage.

**Prolongement opérationnel proposé.** Pour la saison 2027, réduire le taux de faux négatifs de **aFN % à bFN %**, sous une charge maximale **Jmax** de jours-départements signalés. aFN est à mesurer ; bFN et Jmax sont à fixer avec le client. Un seuil météo ne devient une règle de mobilisation qu’après validation opérationnelle.

| Critère | Définition |
|---|---|
| Spécifique | Présence d’au moins un feu recensé par département et date cible ; horizons séparés |
| Mesurable | Trois scénarios N = 2, 3 et 4, matrices VP/FP/FN/VN et indicateurs définis dans le second livrable |
| Atteignable | Fichiers météo 2024/2025 et BDIFF disponibles ; interprétation temporelle et complétude à valider |
| Réaliste | Comparaison sur le même panel et présentation des effectifs ; aucun calcul de coût déduit du seul niveau météo |
| Temporel | Livrable analytique au 11 décembre 2026 ; application éventuelle en 2027 |

**Responsabilité proposée.** Contribution KPI2 pour le calcul ; groupe pour le contrôle ; SDIS 77 pour l’arbitrage du seuil et des moyens.

**Test de cohérence.** Abaisser le seuil au minimum réduit les faux négatifs, mais peut signaler presque tous les jours. Afficher simultanément la charge et les jours signalés sans événement recensé.

### O3 — Suivre les feux majeurs dans les zones prioritaires

**Action.** Construire un historique des feux de surface parcourue ≥ 10 000 m² et figer les zones d’étude.

**Objectif.** Réduire les conséquences des feux en surveillant les zones prioritaires, sans dégrader la situation ailleurs.

**Objectif SMART proposé.** Entre le **1er juin et le 30 septembre 2027**, réduire de **r %** le nombre de feux recensés de surface parcourue ≥ **1 ha** dans un ensemble **Z10 de dix communes du 77**, fixé avant la saison, par rapport à la **moyenne des mêmes mois de 2023, 2024 et 2025**, sous une enveloppe **B** de moyens validée et avec suivi des feux majeurs hors Z10.

| Critère | Définition |
|---|---|
| Spécifique | Feux de surface parcourue totale ≥ 1 ha dans dix communes identifiées par codes INSEE |
| Mesurable | Réduction relative du nombre saisonnier par rapport à la moyenne de trois saisons ; référence à calculer sur Z10 |
| Atteignable | Historique calculable ; résultat 2027 et attribution à une action non disponibles |
| Réaliste | r et B à valider ; effectifs faibles, surfaces estimées et facteurs météo à afficher |
| Temporel | Zones et règles figées avant juin 2027 ; bilan de saison après validation des événements |

**Cible issue du KPI4.** La réduction de **10 %** reste une proposition, pas une cible acceptée. Une évolution observée ne prouve pas l’effet du dispositif. Une moyenne de référence nulle rend le taux non calculable.

**Responsabilité proposée.** Auteur ou autrice du KPI4, à nommer ; validation du périmètre et des moyens par le SDIS 77.

**Test de cohérence.** Une baisse dans Z10 peut masquer une hausse ailleurs ou un changement de déclaration des surfaces. Publier les volumes hors Z10 et la précision des surfaces. Le délai de première présentation est différé jusqu’à réception des données internes ; la cible de −15 % n’est pas retenue comme engagement validé.

## 6. Décisions et compléments avant validation

| Point | Décision ou pièce attendue |
|---|---|
| Priorité du jeu collectif | I1 retenu pour le livrable : part des journées avec feu recensé restant sous le seuil ; cibles et seuil opérationnel à valider avec le SDIS |
| Cibles et contraintes | Mesurer a et aFN ; faire valider b, bFN, Jmax, r et B ; préciser les unités des moyens |
| Zones prioritaires | Fournir une liste versionnée de codes INSEE et une règle de sélection ; distinguer commune, massif et secteur opérationnel |
| Temporalité | Confirmer la signification de `date`, les horizons et le fuseau des horodatages ; conserver la période commune aux sources |
| Données spatiales | Joindre les fichiers communaux d’artificialisation et les règles de typologie ; compléter le MOS si les interfaces sont étudiées |
| Mesure opérationnelle | Obtenir les présences réalisées, les heures, les coûts et, si retenus ultérieurement, les délais d’intervention |
| Gouvernance | Nommer un calculateur et un relecteur par objectif ; tracer les paramètres avant calcul |

## 7. Traçabilité du livrable

Documents consolidés : les diagnostics KPI1, KPI2, KPI3 et `02_diagnostic_objectif_kpi4.md`, ainsi que les quatre fichiers de fiches d’indicateurs transmis. Les chiffres descriptifs 347, 293 et les profils temporels ont été recalculés dans le CSV BDIFF fourni. Les classifications spatiales et les matrices météo ne sont pas présentées comme des résultats collectifs validés.

À déposer dans `kpi/01_diagnostic_objectifs_groupe.md`, avec un commit de groupe. Le jeu d’indicateurs associé figure dans [02_fiches_indicateurs.md](02_fiches_indicateurs.md). Cette v0 doit être relue par les quatre membres avant son adoption collective.

## Références officielles et règle de provenance

- [Météo-France — Météo des forêts](https://meteofrance.com/meteo-des-forets) — quatre niveaux de danger, échelle départementale et limites d’interprétation.
- [Météo-France — La Météo des forêts : s’informer sur le danger de feux](https://meteofrance.com/actualites/la-meteo-des-forets-sinformer-sur-le-danger-de-feux) — horizons, nature du dispositif et distinction avec la Vigilance.

Sources consultées le **20 novembre 2026**. L’article tiers `info-meteo.fr` transmis par le groupe n’est pas retenu pour définir l’échelle ni les règles opérationnelles : il présente notamment une échelle de 1 à 5, qui ne correspond pas aux quatre catégories de la Météo des forêts officielle. Aucune de ces pages publiques n’établit la règle de mobilisation propre au SDIS 77. Une pièce du SDIS ou de la commande reste nécessaire pour cette règle ; le dictionnaire de l’archive reste nécessaire pour le codage exact et la signification de `date`.


# Jeu collectif d’indicateurs v0 — SDIS 77

**Date** — Actualisation du 20 novembre 2026.  
**Périmètre d’étude** — Île-de-France, résultats par département et lecture opérationnelle du 77.  
**Statut** — Proposition de mise en commun des quatre contributions, à valider par le groupe. Les calculs opérationnels restent conditionnés à la réception des données du SDIS.  
**Diagnostic associé** — [01_diagnostic_objectifs_groupe.md](01_diagnostic_objectifs_groupe.md).

## 1. Hiérarchisation du jeu

Le jeu proposé comporte **un KPI principal**, quatre secondaires et trois garde-fous. Les trois indicateurs conditionnels I2, I3 et G3 ne sont pas affichés avec une valeur de performance tant que leurs données et références ne sont pas disponibles. Les décomptes de contexte accompagnent les taux.

| ID | Indicateur | Rôle collectif | Objectif | Faisabilité actuelle | Décision éclairée |
|---|---|---|---|---|---|
| I1 | Taux de jours avec feu recensé restant sous le seuil météo | **KPI principal unique retenu** | O2 | Calcul conditionnel à la validation des jointures | Discuter un seuil plus ou moins sensible avec le SDIS |
| I2 | Part de feux couverts par un dispositif dans l’espace et le temps | Secondaire opérationnel | O1 | Données de présence et localisation à obtenir | Repositionner les dispositifs |
| I3 | Réduction des feux majeurs en zones prioritaires | Secondaire de résultat | O3 | Historique calculable ; Z10, référence et données 2027 à compléter | Réexaminer les priorités de prévention |
| I4 | Part des feux recensés dans les communes sélectionnées | Secondaire préparatoire | O1 | Calculable après fixation de la liste et de la période | Choisir ou réexaminer des zones à étudier |
| I5 | Part des feux estivaux dans une plage horaire fixée | Secondaire préparatoire | O1 | Calculable sur BDIFF | Préparer les horaires de surveillance |
| G1 | Part des jours signalés sans feu recensé | Garde-fou de I1 | O2 | Même condition de jointure que I1 | Rendre visible le coût potentiel d’un seuil trop bas |
| G2 | Part des jours-départements signalés | Garde-fou de charge de I1 | O2 | Météo seule, avec dates et niveaux documentés | Comparer la charge potentielle des scénarios |
| G3 | Heures réalisées / enveloppe d’heures B | Garde-fou de I2 | O1, O3 | Données SDIS et B à obtenir | Adapter les horaires et l’étendue de couverture |
| C1 | Feux majeurs hors Z10, effectifs de feux et jours observables | Contexte et contrôle territorial de I3 | O1, O2, O3 | Historique calculable après fixation de Z10 | Détecter une évolution territoriale masquée ; approfondir avant arbitrage |

**Pourquoi I1 est retenu comme principal.** Il traduit l’arbitrage de seuil commun à la préparation du dispositif et peut être étudié avec les sources météo et incendies existantes. I1 est retenu pour ce livrable à la suite de la demande de consolidation. Le seuil opérationnel et la cible restent à valider avec le SDIS 77. Il mesure une concordance avec les feux recensés et ne mesure pas à lui seul l’efficacité du SDIS.

**Indicateurs écartés de la v0.** Corrélation horaire avec température/humidité, faute de séries horaires dans les archives Météo des forêts fournies ; humidité SIM, faute de fichier ; délai d’arrivée, faute d’horodatage ; coût réel par alerte, faute de mobilisation et de coûts. Sensibilité et précision sont des compléments de lecture de I1/G1, sans indicateur piloté supplémentaire. Le taux FP/(FP+VN) peut être calculé en annexe mais ne doit pas être confondu avec G1.

## 2. Règles communes de calcul

### Périmètres et unités

- Étude régionale : départements 75, 77, 78, 91, 92, 93, 94 et 95. Les décisions de mobilisation concernent le SDIS 77.
- Comparaison météo/feux : 2024 et 2025, seulement aux dates cibles pour lesquelles météo et couverture de collecte des feux sont jugées exploitables. Les fenêtres exactes sont publiées pour chaque horizon.
- Archives météo 2026 : utilisables pour décrire les niveaux, exclues de tout calcul de concordance avec l’extraction BDIFF arrêtée en 2025.
- Profils horaires : juin à septembre 2023–2025. Analyse spatiale préparatoire : 2021–2025. Évaluation opérationnelle proposée : juin à septembre 2027.
- Comparer les horizons sur leur intersection de dates cibles pour une comparaison directe. Ne pas mélanger J+1 et J+2 dans un même taux.

### Limite temporelle des données d’artificialisation

La documentation fournie décrit deux millésimes, le premier entre 2016 et 2019 et le second entre 2019 et 2022 selon le territoire. **2022 est la borne maximale annoncée ; les dates exactes pour l’Île-de-France restent à vérifier dans les fichiers concernés.** Une date de téléchargement ou de mise à jour ne constitue pas une année d’observation. L’artificialisation est utilisée comme contexte territorial historique pour les analyses spatiales. Ne pas la présenter comme une mesure contemporaine de 2025 ou de 2027, ni comme une variable annuelle actualisée. Conserver les millésimes dans les tables et indiquer l’écart temporel lors de l’interprétation. Cette limite n’empêche pas le calcul de I1, qui repose sur météo et BDIFF.

### Niveaux de danger et seuil opérationnel

La documentation officielle de Météo-France distingue **quatre niveaux de danger**, présentés à l’échelle départementale pour le lendemain et le surlendemain.

| Niveau de danger officiel | Couleur |
|---|---|
| Faible | Vert |
| Modéré | Jaune |
| Élevé | Orange |
| Très élevé | Rouge |

Les valeurs **1, 2, 3 et 4** observées dans les fichiers sont des codes. Leur correspondance exacte avec ces catégories doit être confirmée dans le dictionnaire du jeu de données et conservée dans la documentation du pipeline. L’ordre des libellés sur une page grand public ne suffit pas à valider le codage du CSV.

**Le seuil de mobilisation réellement utilisé par le SDIS 77 reste à documenter.** Les quatre catégories ne définissent pas automatiquement sa règle d’activation, les moyens mobilisés ni l’horizon retenu. Pour cette v0, comparer les seuils numériques **N = 2, N = 3 et N = 4** comme des **scénarios exploratoires**, puis interpréter les résultats après validation du codage. Une comparaison sans variation de niveau ou sans effectif suffisant peut être non informative.

La Météo des forêts est un outil de prévention indiquant des conditions favorables aux feux. Elle ne constitue pas une prévision de survenue des incendies et se distingue de la Vigilance météorologique. Les éventuelles restrictions locales sont à rechercher auprès de la préfecture. Un jour signalé sans feu recensé ne prouve pas une prévision erronée ; un feu sous le seuil ne suffit pas à qualifier toute la prévision de défaillante.

### Jointure et population utilisable

1. Conserver un identifiant d’événement composé de `Année` et `Numéro`, et contrôler les doublons potentiels avant décompte. Un numéro seul ne doit pas être supposé unique.
2. Conserver les codes de département et INSEE comme chaînes normalisées. Documenter les communes historiques lors des rapprochements géographiques.
3. Transformer la météo en une table avec une ligne par département, date cible et horizon. `date` est provisoirement traitée comme date d’émission ; la transformation vers la date cible doit être confirmée avant validation.
4. Pour chaque ligne département-date-horizon, définir **Y = 1** s’il existe au moins un événement BDIFF éligible à cette date dans ce département. Plusieurs feux le même jour donnent un seul jour positif. Le nombre de feux est publié séparément.
5. Définir **A = 1** si le niveau du bon horizon est ≥ N. Les seuils exploratoires N = 2, N = 3 et N = 4 sont des scénarios numériques à documenter, pas des seuils opérationnels officiels présumés.
6. Un jour sans ligne météo ou avec niveau absent est exclu et compté. Un événement sans date ou département exploitable est exclu et compté. La construction de Y = 0 demande un calendrier de référence et une couverture de collecte explicitée ; elle ne prouve jamais une absence certaine de feu.
7. Pour tout taux, afficher numérateur, dénominateur, période, filtres et exclusions. Dénominateur nul : **NC**, jamais 0 %. Pour une série à très faible effectif, publier les comptes et éviter le classement de performance ; un effectif minimal d’interprétation reste à fixer avec le client.

### État de la faisabilité vérifiée

Le CSV BDIFF fourni contient **347 événements**, dont **293 dans le 77**, avec dates de première alerte exploitables. Pour le profil estival 2023–2025, **66 lignes** sont utilisables avant revue des doublons et de la qualité des heures. Les effectifs effectivement utilisables pour I1, G1 et G2 sont à publier après validation des dates et de la collecte. Les chiffres des matrices exploratoires individuelles ne sont pas repris comme résultats collectifs certifiés.

La nomenclature MOS et l’artificialisation contextualisent les secteurs ; elles ne sont pas nécessaires à la matrice de confusion. La jointure spatiale fine nécessite des géométries complètes et une position du feu suffisamment précise.

## 3. Fiche I1 — KPI principal

| Rubrique | Définition |
|---|---|
| Question et objectif | Quelles journées avec feu recensé restent sous un seuil donné ? Contribue à O2 et à la préparation du dispositif |
| Formule | **100 × FN / (VP + FN)**, où FN = jours-départements Y=1 et A=0, VP = Y=1 et A=1 |
| Unité | Pourcentage de jours-départements avec au moins un feu recensé ; complément à la sensibilité |
| Paramètres | Seuil N parmi 2, 3 et 4 (scénarios exploratoires), horizon h, fenêtre de dates cibles, départements, définition de l’événement éligible, version des fichiers |
| Périmètre, grain, fréquence | Île-de-France et détail départemental ; département-date cible-horizon ; calcul à chaque import validé et bilan par saison |
| Sources et champs exacts | `mdf_2024.csv`, `mdf_2025.csv` : `date`, `num_dep`, `niveau_j1`, `niveau_j2` ; `Incendies.csv` : `Année`, `Numéro`, `Département`, `Date de première alerte` |
| Lignes utilisables | Jointure contrôlée selon section 2 ; total à calculer après validation des dates ; inconnus exclus et dénombrés |
| Proxy et biais | Première alerte à la place du départ réel ; présence BDIFF à la place de tous les feux. Une collecte incomplète peut biaiser le taux dans les deux sens |
| Référence et cible | Référence 2024–2025 à mesurer après contrôles ; cible bFN à fixer avec le SDIS ; aucun objectif numérique adopté à ce stade |
| Décision | Comparer les seuils conjointement avec G1 et G2 ; proposer un arbitrage, sans automatiser une mobilisation sur ce seul taux |
| Propriétaire proposé | Contribution KPI2 pour calcul et documentation ; relecture par un autre membre ; validation opérationnelle SDIS 77 |

**Lecture de la matrice.** VP : signalé avec feu recensé ; FN : sous le seuil avec feu recensé ; FP : signalé sans feu recensé ; VN : sous le seuil sans feu recensé. Un « faux positif » de cette comparaison n’est pas automatiquement une erreur de prévision du danger.

**Nom à utiliser dans la restitution.** Part des journées avec au moins un feu recensé qui restent sous le seuil de déclenchement envisagé pour le dispositif renforcé.

**Exemple fictif de lecture.** Parmi 20 jours-départements avec feu recensé, 8 présentent un niveau inférieur à N : I1 = 8 / 20 × 100 = 40 %. Cet exemple explique la formule et ne constitue pas un résultat du projet.

**Règle d’arbitrage.** Une valeur élevée invite à examiner les journées non signalées par le seuil. Comparer les scénarios avec G1 et G2 avant toute proposition de modification ; le niveau météo seul n’atteste ni une mobilisation effective ni l’absence de besoin opérationnel.

### Jugement RACER de I1

| Critère | Jugement |
|---|---|
| Relevant — pertinent | Répond à la question de journées avec feu qui ne franchissent pas le seuil choisi |
| Accepted — accepté | Formule explicite et partageable ; I1 est retenu dans ce livrable ; sa cible et son usage opérationnel restent à faire valider par le SDIS |
| Credible — crédible | Défendable après contrôle des dates, de la collecte et des exclusions ; BDIFF reste une observation imparfaite |
| Easy — facile | Calcul reproductible avec pandas après préparation d’une table département-date-horizon |
| Robust — robuste | Fragile à faible effectif ; plusieurs saisons, horizons séparés et analyse de sensibilité sont nécessaires |

## 4. Fiche G1 — Jours signalés sans feu recensé

| Rubrique | Définition |
|---|---|
| Question et objectif | Un meilleur I1 s’accompagne-t-il de très nombreuses journées signalées sans événement recensé ? |
| Formule | **100 × FP / (VP + FP)** |
| Unité | Pourcentage des jours-départements signalés ; complément à la précision |
| Paramètres | Identiques à I1 ; ne pas changer le panel entre les deux indicateurs |
| Périmètre et fréquence | Département-date cible-horizon ; bilan saisonnier et détail départemental |
| Sources et lignes utilisables | Mêmes champs et jointure que I1 ; total à publier après contrôle |
| Proxy et biais | Absence de feu recensé ≠ absence certaine de feu ; un dispositif préventif peut contribuer à éviter un événement |
| Décision | Réexaminer la charge potentielle d’un scénario ; une hausse ne suffit pas à décider de relever N |
| Propriétaire proposé | Contribution KPI2, relecture collective |

G1 ne mesure ni un coût ni une mobilisation effective. Son dénominateur est **VP+FP**, alors que le taux classique de faux positifs utilise **FP+VN**.

## 5. Fiche G2 — Charge potentielle des journées signalées

| Rubrique | Définition |
|---|---|
| Question et objectif | Quelle fraction des journées du panel serait signalée sous le scénario N ? |
| Formule | **100 × (VP+FP) / (VP+FP+FN+VN)** ; publier aussi le volume VP+FP |
| Unité | Pourcentage et nombre de jours-départements signalés |
| Paramètres | N, horizon, calendrier et départements identiques à I1 |
| Sources | Météo : `date`, `num_dep`, `niveau_j1` ou `niveau_j2` ; calcul sur le panel commun pour lecture conjointe avec I1 |
| Lignes utilisables | Une valeur météo valide par département-date cible-horizon ; données manquantes exclues et signalées |
| Proxy et biais | Volume de signalements à la place d’une charge réelle ; les besoins humains et matériels peuvent différer selon le territoire et le jour |
| Fréquence et décision | À chaque scénario puis bilan saisonnier ; comparer à Jmax validé, sans conversion directe en euros |
| Propriétaire proposé | Contribution KPI2 ; SDIS pour l’interprétation de charge |

## 6. Fiche I2 — Couverture spatio-temporelle

| Rubrique | Définition |
|---|---|
| Question et objectif | Le dispositif est-il présent aux lieux et heures des feux recensés ? O1 |
| Formule | **100 × nombre de feux éligibles couverts au lieu et à l’heure / nombre total de feux éligibles** |
| Unité et paramètres | % de feux ; définition du secteur, de la présence minimale, de la plage, des moyens nécessaires et du délai éventuel fixée avant la saison |
| Périmètre, période, grain | Seine-et-Marne, juin–septembre 2027 ; une ligne par feu enrichi par le dispositif observé ; suivi mensuel et bilan saisonnier |
| Sources et champs | BDIFF : identifiants, commune et première alerte ; données SDIS demandées : position du feu, secteur du dispositif, début/fin et moyens effectivement présents. Ces derniers champs sont une demande de données, pas un schéma existant vérifié |
| Lignes utilisables | Aucune mesure opérationnelle calculable avec les seuls fichiers transmis ; publier le nombre de feux appariables lorsque les données arrivent |
| Proxy et biais | Un recouvrement commune-horaire peut surestimer la couverture réelle ; une couverture planifiée peut surestimer une présence réalisée |
| Référence et cible | a à mesurer sur un historique comparable ; b et B à valider |
| Décision et propriétaire | Repositionnement par le SDIS ; calcul proposé aux contributions KPI1 et KPI3 ; lecture avec G3 |

**RACER.** Pertinent pour O1 ; acceptation conditionnée à une définition partagée du dispositif ; crédibilité conditionnée aux présences réalisées ; calcul simple après appariement ; robustesse dépendante de la précision des lieux et horaires.

## 7. Fiche G3 — Respect de l’enveloppe d’heures

| Rubrique | Définition |
|---|---|
| Question et objectif | I2 augmente-t-il au prix d’un dépassement des moyens disponibles ? |
| Formule | **100 × H / B**, H = somme des heures-personnes de surveillance réalisées sur la période, B = enveloppe d’heures-personnes autorisée |
| Paramètres et périmètre | Même saison et périmètre d’intervention que I2 ; définition des missions incluses et règle de décompte écrites |
| Sources et lignes utilisables | Plannings réalisés SDIS et enveloppe validée ; non disponibles ; annulations et doublons à traiter |
| Fréquence, unité | Mensuelle et cumulative saisonnière ; % du budget d’heures, volumes H et B publiés |
| Proxy et biais | Les heures ne couvrent pas tous les coûts matériels ; un suivi financier distinct nécessite des coûts réels |
| Décision et propriétaire | Adapter plages ou secteurs en cas de dépassement prévisionnel ; SDIS fournit et valide, calcul par le binôme KPI1/KPI3 |

## 8. Fiche I3 — Réduction des feux majeurs

| Rubrique | Définition |
|---|---|
| Question et objectif | Comment évolue le nombre de feux de surface parcourue ≥ 1 ha dans Z10 ? O3 |
| Formule | **100 × (Nréf − N2027) / Nréf** ; une valeur positive signifie une réduction. Nréf = moyenne des nombres de feux des étés 2023, 2024 et 2025 dans les mêmes communes |
| Unité et paramètres | %, avec volumes ; seuil 10 000 m², liste Z10 figée avant évaluation, juin–septembre chaque année |
| Périmètre et fréquence | Dix communes du 77 identifiées par codes INSEE ; comptage au feu, bilan saisonnier après validation et état provisoire mensuel |
| Sources et champs | `Incendies.csv` : `Année`, `Numéro`, `Code INSEE`, `Département`, `Date de première alerte`, `Surface parcourue (m2)`, `Précision des surfaces` ; futurs événements 2027 à obtenir |
| Lignes utilisables | Date, commune et surface exploitables ; références à calculer après fixation de Z10 ; Nréf nul → NC |
| Proxy et biais | Surface totale parcourue à la place d’un dommage complet ; seuil sensible aux estimations et arrondis ; météo, mises à feu et collecte influencent l’évolution |
| Référence et cible | Référence saisonnière à calculer ; réduction de 10 % proposée individuellement, non validée collectivement ou par le SDIS |
| Décision et propriétaire | Réexaminer les priorités en lisant aussi C1 et G3 ; responsable KPI4 à nommer |

**RACER.** Pertinent pour les conséquences ; acceptation du seuil, des communes et de la cible à obtenir ; crédibilité limitée par les surfaces estimées ; comptage techniquement simple ; faible robustesse annuelle si quelques feux seulement, imposant une lecture des volumes et des incertitudes.

**Protection territoriale C1.** Publier chaque saison le nombre de feux ≥ 1 ha hors Z10 et son évolution sur une fenêtre comparable, avec les effectifs dans Z10. Une baisse dans Z10 accompagnée d’une hausse ailleurs appelle une analyse, sans prouver un déplacement du risque causé par les moyens. Contrôler également la proportion de surfaces estimées ou de précision inconnue autour de 1 ha. Aucune baisse observée ne permet d’attribuer seule un effet causal à la surveillance.

## 9. Fiches préparatoires I4 et I5

| Rubrique | I4 — Concentration communale | I5 — Concentration horaire |
|---|---|---|
| Question | Où les feux recensés se concentrent-ils ? | Dans quelles plages les premières alertes estivales se concentrent-elles ? |
| Formule | 100 × feux recensés dans une liste Z / feux recensés du périmètre | 100 × feux estivaux dont l’heure appartient à [h1,h2[ / feux estivaux à heure exploitable |
| Paramètres | Liste de codes INSEE, règle de sélection, période, périmètre | Plage fixée avant lecture, mois juin–septembre, années 2023–2025, fuseau à confirmer |
| Sources exactes | BDIFF : identifiants, `Code INSEE`, `Département`, `Date de première alerte` | BDIFF : identifiants, `Date de première alerte`, `Département` |
| Grain et fréquence | Un feu ; actualisation après import validé | Un feu ; bilan annuel et saisonnier |
| Lignes utilisables | Commune/date exploitables ; liste Z et total exclus à publier | 66 lignes estivales 2023–2025 avant revue qualitative des heures |
| Faisabilité / référence | Calculable après fixation de Z ; les typologies d’interface restent à reproduire | [12 h,16 h[ : 24/66 = 36,36 % ; [12 h,20 h[ : 47/66 = 71,21 % |
| Proxy / biais | Nombre de feux recensés ≠ risque rapporté à la surface exposée ; une commune ne localise pas l’interface du feu | Première alerte ≠ départ exact ; petits effectifs, conventions de saisie et plage plus large influencent le taux |
| Décision / propriétaire proposé | Préparer des secteurs à examiner, contribution KPI1 ; ne pas évaluer une couverture réelle avec cette part | Préparer les horaires, contribution KPI3 ; ne pas supprimer la surveillance hors du créneau sur ce seul résultat |

Ces indicateurs expliquent le ciblage. Ils ne mesurent pas une amélioration opérationnelle. Une sélection des communes sur les mêmes données que celles utilisées pour évaluer leur concentration produit un résultat descriptif, pas une validation prédictive ; réserver une période distincte pour tester le ciblage.

## 10. Test de changement de paramètre

| Changement | Ce qui change | Effet sur la décision |
|---|---|---|
| N passe de 2 à 3 à panel et horizon fixes | Les jours signalés ne peuvent qu’être moins nombreux ; G2 ne monte pas ; I1 ne peut que monter ou rester stable. G1 peut varier dans les deux sens | Accepter moins de jours signalés peut laisser davantage de journées avec feu sous le seuil ; comparer les matrices avant de choisir |
| Plage I5 passe de [12 h,16 h[ à [12 h,20 h[ | Sur l’extraction 2023–2025, 24/66 devient 47/66, soit 36,36 % puis 71,21 %. La plage passe aussi de 4 à 8 heures | Ne pas retenir la seconde plage sur sa seule part de feux ; estimer les moyens nécessaires et consulter G3 |
| Z contient 5 communes puis 10 | Le nombre de feux historiques inclus augmente ou reste stable si les listes sont emboîtées ; l’effort de couverture peut augmenter | Fixer la liste et la règle avant l’évaluation ; ajouter des communes n’est pas en soi un gain d’efficacité |

Publier les paramètres et résultats dans la même table de scénarios. Aucune meilleure valeur n’est présumée avant l’arbitrage du client.

## 11. Effets pervers, garde-fous et risques résiduels

| Indicateur | Qui pourrait l’optimiser et comment ? | Effet indésirable | Garde-fou différent | Risque résiduel |
|---|---|---|---|---|
| I1 | Analyste ou pilote abaissant N au minimum pour réduire FN | Presque toutes les journées sont signalées | G1 et G2, publiés à côté de I1 | Des jours sans feu peuvent résulter d’actions efficaces ; coûts réels toujours inconnus |
| I2 | Planificateur élargissant secteurs/plages ou assimilant planification et présence | Hausse artificielle du taux ou couverture excessive | G3, définition figée du dispositif et contrôle des présences sur échantillon | Une présence ne garantit pas une surveillance efficace |
| I3 | Pilote modifiant Z10, la référence ou les estimations de surface après lecture | Baisse apparente et difficultés masquées ailleurs | C1, liste et référence figées, contrôle de précision des surfaces | Variabilité météo et sous-déclaration persistent ; pas d’attribution causale |
| I4/I5 | Analyste choisissant a posteriori communes et plages les plus favorables | Surestimation de la stabilité des concentrations | Validation sur une saison distincte, publication de tous les volumes et durées | Les profils futurs peuvent changer |

## 12. Pré-mortem collectif

Scénario : en 2027, le SDIS prend une mauvaise décision après lecture du jeu.

| Rang | Cause plausible | Probabilité estimée | Gravité estimée | Protection proposée |
|---|---|---|---|---|
| 1 | Dates d’émission et dates cibles confondues, ou météo 2026 croisée avec un historique de feux arrêté en 2025 | Élevée avant contrôle | Très élevée | Valider la convention temporelle, exclure les années non appariables, publier panel et exclusions, relire un échantillon de jointures |
| 2 | Un seuil ou un ciblage est retenu sans mesurer la charge réelle et les feux hors des zones retenues | Élevée avec les données actuelles | Très élevée | Lire I1 avec G1/G2 ; obtenir H et B pour G3 ; suivre C1 ; présenter plusieurs scénarios avant arbitrage |
| 3 | Sous-déclaration, faibles effectifs et surfaces estimées rendent les classements instables | Élevée | Élevée | Afficher les comptes, stratifier par saison/département, contrôler les surfaces et tester les paramètres ; différer les classements fragiles |

Le classement probabilité/gravité est une appréciation de travail du groupe, à discuter, pas un résultat statistique. Les deux premiers risques disposent de protections explicites dès la v0.

## 13. Corrections effectuées lors de la consolidation

- Les quatre catégories officielles sont documentées à partir de Météo-France. Le codage du CSV et le seuil de mobilisation du SDIS restent deux validations distinctes. Les seuils 2, 3 et 4 sont étudiés comme scénarios.

- Spatial et temporel sont fusionnés dans un objectif de couverture ; leurs indicateurs descriptifs sont conservés séparément.
- Les archives 2025 et 2026 sont disponibles dans le dossier collectif, même si la contribution KPI2 avait reçu uniquement 2024. Seules 2024/2025 sont candidates au rapprochement avec la BDIFF actuelle.
- Le résultat individuel « 105 jours sans feu sur 111 alertes » mélangeant 2024–2026 n’est pas retenu : l’extraction ne permet pas d’observer les feux 2026 et les dates doivent être alignées.
- « Mobilisation à vide » devient « jour signalé sans feu recensé » en l’absence de données de mobilisation.
- La réduction de 10 %, le délai de −15 % et tout plafond budgétaire ne sont pas présentés comme acceptés par le commanditaire.
- Les totaux historiques de feux majeurs 2012–2025 ne servent pas de dénominateur direct à une seule saison 2027. Le taux utilise une moyenne de saisons comparables.
- Les interfaces et les densités par typologie sont à reproduire avec fichiers, règles et unités de surfaces contrôlées ; elles ne sont pas des localisations précises de feux déjà établies.

## 14. Validation et passage en v1

Le KPI principal du livrable est I1. Les quatre membres relisent les trois objectifs, les responsabilités et le nombre d’indicateurs avant le commit collectif. Avant calcul certifié, le groupe valide les dates, niveaux, populations et exclusions. Le SDIS valide ensuite les cibles, les moyens et les règles opérationnelles. Les indicateurs conditionnels restent marqués **non calculables avec les données reçues** tant que leurs pièces manquent.

Le fichier attendu par le cours est `kpi/02_fiches_indicateurs.md`. Cette version constitue le **jeu collectif v0**, à reprendre en FOAD pour produire la v1. La spécification technique garde seulement une ligne par indicateur et un lien vers ce fichier. Le diagnostic collectif et les objectifs sont déposés dans `kpi/01_diagnostic_objectifs_groupe.md` avec un commit de groupe distinct des contributions individuelles.

## Références officielles et règle de provenance

- [Météo-France — Météo des forêts](https://meteofrance.com/meteo-des-forets) — quatre niveaux de danger, échelle départementale et limites d’interprétation.
- [Météo-France — La Météo des forêts : s’informer sur le danger de feux](https://meteofrance.com/actualites/la-meteo-des-forets-sinformer-sur-le-danger-de-feux) — horizons, nature du dispositif et distinction avec la Vigilance.

Sources consultées le **20 novembre 2026**. L’article tiers `info-meteo.fr` transmis par le groupe n’est pas retenu pour définir l’échelle ni les règles opérationnelles : il présente notamment une échelle de 1 à 5, qui ne correspond pas aux quatre catégories de la Météo des forêts officielle. Aucune de ces pages publiques n’établit la règle de mobilisation propre au SDIS 77. Une pièce du SDIS ou de la commande reste nécessaire pour cette règle ; le dictionnaire de l’archive reste nécessaire pour le codage exact et la signification de `date`.

