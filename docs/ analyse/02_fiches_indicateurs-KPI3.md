# Fiches d'indicateurs — Organisation temporelle de la surveillance

Autrice — Hassina Yasmine Kenane  
Version individuelle de travail — 19 novembre 2026  
Commanditaire — SDIS 77. Étude de l'ensemble de l'Île-de-France.  
Diagnostic et objectif associés — 01_diagnostic_objectif_yasmine.md

## 1. KPI principal — Couverture temporelle des alertes

| Rubrique | Spécification |
|---|---|
| Question et objectif | Quels créneaux de surveillance permettent de couvrir davantage d'alertes dans les secteurs concernés, à moyens maîtrisés ? Améliorer la couverture pour la saison 2027, de a % à b %, sous un plafond B d'heures-équipe. a, b et B restent à mesurer ou à valider avec le SDIS. |
| Numérateur | Nombre d'événements BDIFF éligibles dont la première alerte tombe dans une mission de surveillance renforcée planifiée et effectivement assurée, couvrant le secteur de l'événement. Une alerte compte une seule fois même si plusieurs équipes couvrent le créneau. |
| Dénominateur | Tous les événements BDIFF éligibles de la période et du périmètre évalués, avec horodatage exploitable. Les plannings doivent être complets sur ce périmètre. Un état de planning inconnu empêche de publier une couverture complète. |
| Formule | 100 × alertes couvertes / alertes éligibles. Dénominateur nul → valeur non calculable. |
| Unité | Pourcentage, accompagné du numérateur et du dénominateur. |
| Paramètres | Période, départements ou secteurs, critères d'incendie, planning, convention horaire et créneaux semi-ouverts [début, fin[. |
| Grain | Rapprochement au niveau de l'alerte et des missions qui couvrent son secteur. Restitution par département, saison et région seulement si les plannings correspondants sont disponibles. |
| Période et fréquence | Suivi pendant la saison du 1er juin au 30 septembre 2027 selon la disponibilité des remontées. Résultat définitif après validation de l'extraction. Actualisation à chaque import validé. |
| Sources et champs | BDIFF — Année, Numéro, Département, Code INSEE, Date de première alerte. Planning à obtenir — identifiant mission, secteur ou communes couvertes, début, fin, équipes mobilisées et réalisation effective. |
| Lignes utilisables | Pour la référence descriptive 2023–2025, 66/66 alertes estivales ont les champs BDIFF utiles renseignés. Aucun planning n'est fourni, donc aucune couverture opérationnelle ne peut encore être calculée. |
| Situation de référence | Couverture actuelle à mesurer. Le taux de 36,36 % sur 12 h–16 h est une simulation descriptive distincte. |
| Proxy et biais | Première alerte utilisée comme approximation du moment du départ. Le délai de détection peut déplacer un événement entre créneaux. Le sens du biais sur le taux de couverture est indéterminé. La seule simultanéité ne prouve pas l'efficacité de la mission. |
| Décision | Comparer les scénarios de planning et leurs heures-équipe pour proposer une réaffectation. Une baisse de couverture appelle une revue des créneaux, des territoires et de la qualité des remontées. |
| Propriétaire proposé | Yasmine calcule et documente. Responsable qualité du groupe relit. SDIS 77 valide l'objectif, les plannings et l'interprétation opérationnelle. |

### Test d'un paramètre

Scénario descriptif uniforme sur l'historique 2023–2025, en Île-de-France, pour les mois de juin à septembre.

| Paramètre horaire | Alertes dans le créneau | Total | Part | Durée du créneau par jour |
|---|---:|---:|---:|---:|
| [12 h, 16 h[ | 24 | 66 | 36,36 % | 4 h |
| [12 h, 20 h[ | 47 | 66 | 71,21 % | 8 h |

L'élargissement augmente la part couverte et double la durée quotidienne du créneau. Il appelle une vérification des heures-équipe avant toute recommandation. Les alertes incluses dans le dénominateur, la période, la source et la définition de l'événement restent les mêmes dans cette comparaison. Le scénario ne représente pas les patrouilles réellement assurées.

### Jugement RACER

| Critère | Jugement |
|---|---|
| Relevant | La couverture renseigne le positionnement temporel des missions pour l'objectif d'organisation retenu. Son effet sur la détection ou les dégâts doit être évalué avec d'autres données. |
| Accepted | À confirmer avec le SDIS pour les définitions de mission, secteur couvert, réalisation et alerte éligible. |
| Credible | Le calcul est reproductible si la source, les règles de temps, le planning et les exclusions sont explicités. |
| Easy | Simulation horaire accessible avec la BDIFF. Calcul opérationnel conditionné par l'accès aux plannings et aux comptes rendus. |
| Robust | Le plafond d'heures-équipe, les volumes et la comparaison par saison protègent une partie de l'interprétation. Les biais de recensement restent à vérifier. |

## 2. Garde-fou — Charge de surveillance en heures-équipe

| Rubrique | Spécification |
|---|---|
| Risque visé | Augmenter mécaniquement la couverture en étendant la surveillance à toute la journée et à tous les secteurs. |
| Mesure | H = somme, sur les missions distinctes effectivement assurées, de la durée de surveillance en heures × nombre d'équipes. Déduire les pauses et périodes non réalisées selon une convention à fixer. Éviter le double comptage des mêmes équipes sur des missions simultanées. |
| Formule de suivi | 100 × H / B, avec B > 0, plafond d'heures-équipe validé par le SDIS. Afficher H en valeur absolue. |
| Paramètres et périmètre | Même saison et mêmes moyens du SDIS que le KPI principal. La couverture géographique d'une mission doit être explicite. |
| Sources et faisabilité | Planning et réalisation des missions à obtenir. Aucun champ ne permet actuellement de mesurer H ou B. |
| Seuil et décision | Dépassement de 100 % du budget validé → réexaminer le scénario ou justifier une décision opérationnelle. Le montant B reste à obtenir. |
| Limite | Une heure-équipe peut mobiliser des effectifs et des équipements différents. Si nécessaire, compléter par les heures-agent et les coûts lorsque ces données deviennent disponibles. |
| Propriétaire proposé | Référent opérationnel du SDIS pour les moyens, Yasmine pour le calcul, responsable qualité pour la relecture. |

Détournement possible — Le planificateur étend tous les créneaux pour augmenter la couverture apparente. H/B rend visible la consommation supplémentaire. Les règles de décompte doivent être fixées avant le choix des scénarios.

Risque résiduel — Une surveillance dans le bon secteur et au bon horaire ne garantit pas la détection précoce ou une réduction des dommages. La prévention peut réduire les départs et modifier le dénominateur des événements observés.

## 3. Indicateur descriptif calculable — Part des alertes entre 12 h et 16 h

| Rubrique | Spécification |
|---|---|
| Rôle | KPI secondaire pour préparer les scénarios horaires. |
| Formule | 100 × alertes estivales dont l'heure appartient à [12 h, 16 h[ / toutes les alertes estivales avec horodatage exploitable. |
| Périmètre et période | Île-de-France, juin à septembre 2023–2025, puis restitution par année et département avec effectifs. |
| Source exacte | Incendies.csv — Année, Numéro, Département, Date de première alerte. Filtre d'export sur le type de feu F à documenter. |
| Lignes utilisables | 66/66 alertes estivales disposent des champs requis. Convention horaire à confirmer. Les contrôles de validation et les vérifications de doublons restent à conserver dans la chaîne de qualité. |
| Référence | 24/66 = 36,36 %. La tranche [16 h, 20 h[ contient 23/66 = 34,85 %. |
| Décision | Examiner ensemble les créneaux voisins avant de proposer une répartition horaire. |
| Proxy et biais | Heure de première alerte utilisée pour approcher le départ. Biais de délai et de remontée, dont le sens sur une tranche est indéterminé. |
| Propriétaire | Yasmine ; relecture par le responsable qualité du groupe. |

| Tranche horaire | Alertes | Part |
|---|---:|---:|
| [00 h, 04 h[ | 2 | 3,03 % |
| [04 h, 08 h[ | 4 | 6,06 % |
| [08 h, 12 h[ | 7 | 10,61 % |
| [12 h, 16 h[ | 24 | 36,36 % |
| [16 h, 20 h[ | 23 | 34,85 % |
| [20 h, 24 h[ | 6 | 9,09 % |

Protection complémentaire — Afficher les parts de [12 h, 16 h[ par saison (48,00 %, 42,86 %, 26,47 %) et les dénominateurs (25, 7, 34). L'écart maximal est de 21,53 points. Aucun seuil d'acceptabilité n'est imposé à ce stade ; il reste à discuter avec le groupe. Ces effectifs limitent la précision des comparaisons.

## 4. Pré-mortem

Classement qualitatif proposé, sans estimation statistique des probabilités.

| Rang | Cause plausible d'échec | Probabilité appréciée | Gravité | Protection |
|---|---|---|---|---|
| 1 | Le SDIS mobilise davantage d'équipes sur toute la journée pour faire monter la couverture. | Plausible | Élevée | Suivre H/B et faire valider les moyens avant le scénario. |
| 2 | Une saison favorable ou un sous-ensemble de départements est sélectionné pour justifier un créneau. | Plausible, compte tenu des petits effectifs | Élevée | Fixer la période et les critères avant calcul, afficher volumes et parts par saison et département, vérifier les remontées. |
| 3 | L'heure d'alerte est utilisée comme heure exacte de départ, ou sa convention horaire est erronée. | À documenter | Élevée | Confirmer la convention avec le producteur et relire un échantillon de fiches avant application opérationnelle. |

## 5. Jeu individuel proposé pour la mise en commun v0

| Rôle | Indicateur | Situation et raison |
|---|---|---|
| KPI principal | Part des alertes couvertes par une mission planifiée et assurée dans le secteur | Mesure de l'objectif proposé. À calculer après réception des plannings. |
| Garde-fou | Heures-équipe consommées / enveloppe B | À calculer après validation des moyens. Limite l'extension systématique des créneaux. |
| KPI secondaire | Part des alertes estivales entre 12 h et 16 h et comparaison des six tranches égales | Calculable, 36,36 % sur le scénario de référence. Prépare les choix horaires. |
| Contexte | Part des alertes recensées de juin à septembre parmi les alertes annuelles 2023–2025 | 66/106 = 62,26 %. Informe sur la saisonnalité du recensement. |
| Écarté à ce stade | Corrélation horaire avec température et humidité | Variables horaires absentes des fichiers reçus. La Météo des forêts fournit un niveau synthétique quotidien. |

Ce jeu reste une proposition individuelle. Les autres objectifs du groupe et leurs indicateurs doivent être mis en commun avant validation du jeu collectif v0.

## 6. Limites et éléments à obtenir

- Couverture des déclarations BDIFF à confirmer. Sur les 66 alertes estivales, 49 concernent le 77, 15 le 91 et 2 le 78. L'absence d'événement pour les autres départements ne suffit pas à établir l'absence réelle de feu.
- Le filtre type F doit être défini. Tous les événements reçus sont conservés dans le calcul descriptif. Le doublon potentiel repéré en 2015 est hors de la fenêtre de référence 2023–2025.
- La formule de couverture exige des plannings complets, des secteurs identifiables, la réalisation des missions et des conventions temporelles harmonisées.
- La part historique des alertes dans une tranche constitue une aide à la planification. Elle ne mesure pas un effet causal de la surveillance.
- Pour l'étude du seuil météo, le groupe doit disposer d'une autre fiche avec la période commune BDIFF–météo et un choix explicite entre J+1 et J+2.

## 7. Sources de travail

- Supports de cours « De la question analytique aux objectifs » et « Définir des KPIs », fournis dans le cadre de l'UE01.B.
- Extraction Incendies.csv fournie par le groupe, 347 événements et 24 colonnes après les trois lignes de métadonnées.
- Profil qualité BDIFF établi dans le projet.


