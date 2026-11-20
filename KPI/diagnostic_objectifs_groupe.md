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
