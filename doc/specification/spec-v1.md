---
updated: 2026-11-20
version: draft-1
---

# Spécification — Île-de-France

Groupe :
 Chef de projet : BOUHADAD FATIHA
 Responsable pipeline et modèle : SLAMA SARRA
 Responsable qualité et conformité : KENANE YASSMINE
 Responsable sources : MARAGHNI TAKWA

 

## 1. La décision

Le commanditaire est la Direction du SDIS 77, dans le cadre d'une étude portant sur l'ensemble de l'Île-de-France. Le projet doit éclairer la préparation de la prévention et de la surveillance des feux de forêt : caractériser les territoires et les périodes concernés, évaluer la concordance du danger Météo des forêts avec les incendies recensés et orienter la réflexion sur les moyens. Une première restitution est attendue pour la soutenance du 11 décembre 2026 ; les conclusions devront distinguer les résultats descriptifs des recommandations opérationnelles qui nécessitent une validation du SDIS.

## 2. Les questions retenues

| N° | Question | Décision qu'elle éclaire | Proposée par |
|---|---|---|---|
| Q1 | Quelles sont les caractéristiques des zones les plus touchées par les incendies en Île-de-France ? | Repérer les territoires à examiner en priorité pour la prévention et la surveillance. | Groupe — attribution à confirmer |
| Q2 | À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents en Île-de-France ? | Décrire la saisonnalité et les créneaux horaires pour préparer l'organisation de la surveillance. | Groupe — attribution à confirmer |
| Q3 | Quelle est l'ampleur des faux positifs et des faux négatifs associés au seuil actuel de la Météo des forêts ? | Évaluer la concordance entre niveaux de danger et incendies recensés ; éclairer l'examen du seuil, sans décider seule d'un seuil opérationnel. | Sarra — à confirmer en groupe |
| Q4 | Comment répartir au mieux les budgets et les moyens opérationnels limités pour protéger les zones et périodes à risque ? | Éclairer des scénarios d'allocation et leur faisabilité, sous validation du commanditaire. | Groupe — attribution à confirmer |

Questions écartées : aucune question écartée n'a été documentée à ce stade. Toute exclusion ou reformulation devra être consignée dans `docs/journal-des-decisions.md` avec sa raison et son coût.

## 3. Les sources retenues

| Source | Fiche | Localisation (URL, API, fichier) | Mode de récupération | Champs utiles | Questions servies |
|---|---|---|---|---|---|
| BDIFF — incendies recensés | `docs/sources/fiche-bdiff.md` | Extraction groupe `Incendies.csv`; source officielle BDIFF à référencer dans la fiche | Export CSV manuel, conserver l'export et ses critères | Année, Numéro, Département, Code INSEE, commune, Date de première alerte, surfaces, nature, impacts et précision | Q1, Q2, Q3, Q4 (base événementielle) |
| Météo des forêts | Fiche source à référencer dans `docs/sources/` | `BD/mdf_2024.csv` dans l'archive reçue; archive Météo-France à documenter | CSV d'archive fourni par le groupe; télécharger les millésimes suivants si disponibles | Date de publication, num_dep, nom_dep, niveau_j1, niveau_j2 | Q3; contexte Q2/Q4 si pertinent |
| MOS Île-de-France | Fiche source à référencer dans `docs/sources/` | `BD/mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv` | CSV fourni dans le ZIP | INSEE, mos2021, Poste 2021, mos2025, Poste 2025, Geo Shape, surfaces/longueurs géométriques | Q1; contexte territorial Q4 |
| Artificialisation — département | Fiche source à référencer dans `docs/sources/` | `BD/artif-departement.csv` | CSV fourni dans le ZIP | code département, nom, région, millésimes, pourcentage et surfaces artificialisées, flux | Q1, contexte Q4 |
| Artificialisation — commune | Fiche source à référencer dans `docs/sources/` | `BD/artif-commune.csv` | CSV fourni dans le ZIP | code commune, nom, département, région, millésimes, pourcentage/surfaces, flux, EPCI, SCOT | Q1, contexte Q4 |

Sources nécessaires mais non reçues / à rechercher : historique de température, humidité et autres variables météo à la granularité utile; document décrivant les codes et le seuil officiel Météo des forêts; archives météo 2025 et 2026 pour l'évaluation multiannuelle; données de budgets, effectifs, moyens engagés, plannings et missions réellement assurées pour Q4. Ces manques sont détaillés en section 5.

Sources écartées à ce stade : aucune source n'est écartée définitivement. Les données météo horaires, les budgets et les plannings ne sont pas intégrés faute de fichiers et d'accès confirmés; ils ne doivent pas être simulés.

## 4. Les sources de référence

| Donnée | Sources concernées | Source de référence | Pourquoi |
|---|---|---|---|
| Incendie recensé, date de première alerte, commune, département, surfaces et impacts | BDIFF; éventuellement autres comptes rendus futurs | BDIFF pour le référentiel historique du projet | Base événementielle retenue et export avec critères documentés. Les autres sources pourront enrichir sans remplacer les événements BDIFF. |
| Niveau de danger Météo des forêts et horizons J+1/J+2 | Archives Météo des forêts | Météo des forêts | Source dédiée à l'indice/niveau de danger. Ne pas la traiter comme un relevé météo horaire ni comme une certitude de départ de feu. |
| Code commune et rattachement départemental | BDIFF, MOS, artificialisation; référentiel INSEE à ajouter si besoin | Code INSEE; référentiel officiel INSEE à documenter | Clé de rapprochement territoriale; conserver les codes comme chaînes pour préserver les zéros initiaux. |
| Occupation du sol et classe MOS | MOS | MOS pour les classes d'occupation du sol, après contrôle de l'anomalie 2025 | Source territoriale détaillée. Les champs 2025 de l'extraction reçue doivent être vérifiés avant comparaison. |
| Artificialisation, millésimes et flux | Artificialisation commune/département | Dataset artificialisation correspondant | Mesure dédiée de l'artificialisation; ne pas confondre avec occupation du sol ou danger incendie. |

## 5. Les manques

Matrice complète : `docs/sources/matrice.md` .

| Question | Ce qui manque | Décision | Ce que la décision coûte | Journal |
|---|---|---|---|---|
| Q1 | Caractéristiques végétation/occupation, autres variables locales et vérification de l'anomalie MOS 2025 | Utiliser MOS et artificialisation comme contexte, pas comme preuve directe de causalité; contrôler MOS 2025 avant d'exploiter les changements | Analyse moins complète; risque de ne pas décrire correctement les évolutions 2021–2025 | À inscrire : décision sur MOS 2025 |
| Q2 | Température/humidité horaires; couverture et convention de l'heure de première alerte; dénominateurs et exhaustivité des déclarations | Analyse descriptive avec date de première alerte comme proxy; limiter les conclusions; obtenir documentation horaire | Ne mesure pas exactement l'heure du départ, ni l'effet météorologique; biais de déclaration possible | À inscrire : proxy horaire |
| Q3 | Archives Météo 2025/2026; définition des niveaux numériques; seuil officiel; convention de validité J+1/J+2; vérification de complétude BDIFF | Premier test sur la période commune 2024; séparer J+1 et J+2; marquer le seuil numérique comme exploratoire tant que la documentation manque | Une année et un seuil exploratoire ne permettent pas d'estimer la performance générale ni de recommander un seuil officiel | À inscrire : périmètre provisoire de Q3 |
| Q4 | Budgets, coûts, effectifs, plannings, secteurs, missions planifiées/réalisées et moyens mobilisés | Construire des scénarios descriptifs à partir des résultats territoriaux et temporels; ne pas calculer une optimisation financière sans données | Impossible de quantifier coût, efficacité ou capacité opérationnelle réelle | À inscrire : absence de données opérationnelles |

## 6. Les incohérences repérées et les transformations nécessaires

| Sources | Nature (format de date, unité, recouvrement, clé) | Exemple tiré du fichier | Transformation nécessaire |
|---|---|---|---|
| BDIFF | Métadonnées avant l'en-tête; CSV séparé par `;`; unités de surface en m² | Les 3 premières lignes sont des informations de sélection; l'en-tête commence ensuite. Les critères indiquent région Île-de-France et type F. | Importer en sautant les 3 lignes de métadonnées; garder ces métadonnées à côté de l'extraction; convertir les dates; conserver surfaces en m² et documenter toute conversion. |
| BDIFF | Identifiant `Numéro` non unique dans l'extraction | Les numéros 1422 et 4399 apparaissent chacun deux fois; 347 lignes et 345 numéros distincts | Ne pas utiliser Numéro seul comme clé. Tester la clé composite (Année, Numéro), vérifier les doublons de lignes et documenter la clé validée. |
| BDIFF | Champs très incomplets | `Type de peuplement` est vide sur 347/347 lignes; `Précision de la donnée` est vide sur 336/347; les champs décès et bâtiments touchés sont vides sur 299/347 | Conserver les champs avec indicateur de complétude; ne pas remplacer les vides par zéro; ne pas exploiter `Type de peuplement` dans cette extraction. |
| Météo des forêts | Timestamp UTC, horizon de prévision; codes de niveaux à documenter | La date commence par `2024-06-04T16:00:00Z` au niveau national; l'extrait Île-de-France couvre 120 dates de publication et 8 départements | Convertir et documenter le fuseau; distinguer date de publication et date de validité; calculer les dates cibles J+1 et J+2 séparément; valider les libellés des codes. |
| Météo des forêts | Recouvrement temporel | Le fichier fourni ne contient que 2024; la période Île-de-France va du 3 juin au 30 septembre 2024 (date de publication UTC) | Limiter le premier croisement à la période commune et demander les archives supplémentaires. |
| MOS | Grain polygonal; géométrie manquante; anomalie potentielle dans le champ 2025 | 42 115 lignes; 1 204 codes INSEE distincts; 305 `Geo Shape` vides (0,72 %). `mos2025` vaut 1 sur les 42 115 lignes, alors que `mos2021` comporte 16 codes | Conserver les polygones; traiter les géométries manquantes comme une limite pour les cartes; vérifier auprès du producteur l'uniformité de `mos2025` avant analyse d'évolution. |
| Artificialisation commune | Champs facultatifs / valeurs manquantes et flux négatifs | Sur le fichier IDF filtré, 1 267 communes; `scot_code` vide sur 613 lignes; 2 valeurs manquantes dans les variables 2021/flux; des flux négatifs existent | Conserver les flux négatifs (ils peuvent représenter une évolution calculée); ne pas imputer; documenter SCOT comme facultatif; vérifier la cause des 2 lignes manquantes. |
| Sources territoriales | Formats et référentiels de codes | BDIFF code INSEE commune et département; MOS a `insee`; artificialisation a `commune_code` et `departement_code` | Uniformiser les codes en chaînes à 5/2 caractères; contrôler la cohérence commune-département; garder le référentiel et le millésime. |

## 7. Conformité

| Champ | Source | Question qui le justifie | Décision (garder, pseudonymiser, écarter) | Technique |
|---|---|---|---|---|
| Numéro de l'événement, année, date | BDIFF | Q1, Q2, Q3, Q4 | Garder | Données d'événements; nécessaires à l'historique, aux agrégations et au rapprochement temporel. |
| Département, code INSEE, commune | BDIFF, MOS, artificialisation | Q1–Q4 selon analyses | Garder | Codes géographiques; utiliser les agrégations départementales/communales pour les restitutions. |
| Surfaces, nature, impacts et précision | BDIFF | Q1, Q4 | Garder si utile; écarter du modèle les champs non pertinents | Minimisation par question; ne pas remplacer les valeurs manquantes par zéro. |
| Niveaux Météo des forêts | Météo des forêts | Q3, éventuellement Q2/Q4 | Garder | Indice public et nécessaire au croisement; documenter l'horizon. |
| Classes MOS, géométrie et artificialisation | MOS, artificialisation | Q1, contexte Q4 | Garder les champs justifiés; limiter la géométrie à l'analyse spatiale | Géométries volumineuses; privilégier agrégats territoriaux pour la restitution. |
| Données nominatives d'agents, plannings individuels ou dossiers personnels | Non reçus; potentiels futurs pour Q4 | Q4 | Écarter les données nominatives; demander des données agrégées par équipe/misson si possible | Minimisation; agrégation et accès restreint si une source opérationnelle devait être obtenue. |

Risque de ré-identification par croisement : les données reçues sont des données publiques territoriales et d'événements, sans nom de personne. Le croisement commune-date et les géométries détaillées peuvent rendre un événement localisable; la restitution doit privilégier les agrégats nécessaires à la décision et ne pas ajouter d'informations personnelles. Aucun fichier individuel d'agent n'est demandé pour le périmètre actuel.

## 8. Historisation

| Source | Ce qui change dans le temps | Exemple | Ce que l'on garde |
|---|---|---|---|
| BDIFF | Nouveaux événements, corrections de fiches, changement de critères d'export et potentiellement de formulaire | Export reçu jusqu'au 31/12/2025; mention de l'ancienne version de formulaire; 347 événements | Chaque export original, date de réception, critères, nom, empreinte/version, puis données transformées séparément. |
| Météo des forêts | Nouveaux millésimes, publications quotidiennes et horizons J+1/J+2; corrections éventuelles | Archive 2024 fournie, dates de publication et deux horizons | Fichiers annuels immuables, date de récupération, version/source, timestamp original et dates de validité dérivées. |
| MOS | Nouveaux millésimes et changements de classe/géométrie | Fichier intitulé MOS 2021 et 2025; champ `mos2025` uniforme à contrôler | Chaque millésime et fichier original; conserver classe et géométrie sans écraser le millésime précédent. |
| Artificialisation | Millésimes de mesure et évolution des flux | Comparaison millésimes 2018 et 2021 dans les fichiers reçus | Fichier original par millésime, dates de récupération, version, variables calculées et valeurs précédentes. |

Principe : les données brutes ne sont jamais écrasées. Une nouvelle version est ajoutée, et le pipeline doit pouvoir être relancé à partir des fichiers archivés sans rappeler une source externe.

## 9. Entrées attendues et qualité

Pour chaque source retenue, ce que l'on exige :

| Source | Champs requis | Champs pouvant être vides (raison) | Clé et grain | Référentiel attendu | Période attendue |
|---|---|---|---|---|---|
| BDIFF | Année, Numéro, département, code INSEE, date première alerte; surfaces si analyse de surface | Précision, type de peuplement, nature, impacts et certaines surfaces selon les formulaires/événements; vides à distinguer de zéro | Événement; clé composite à valider, candidat `Année + Numéro` | Codes départements et communes INSEE; type de feu du filtre d'export à documenter | Extraction 2006–2025; fenêtre commune à préciser selon chaque source |
| Météo des forêts | Timestamp/date, num_dep, niveaux J+1 et J+2, nom département si contrôle | Aucun champ clé attendu vide | Département × date de publication; une ligne par couple | Codes département INSEE à 2 caractères; libellés des niveaux à documenter | Archive 2024 reçue; 2025/2026 à demander |
| MOS | INSEE, classes 2021/2025, géométrie si spatial | Geo Shape peut être vide (305 observés); valeurs non spatiales restent exploitables selon besoin | Polygone d'occupation du sol; plusieurs lignes par commune possibles | Code INSEE commune; nomenclature MOS 79 postes annoncée dans le nom du fichier, à vérifier | Millésimes 2021 et 2025 |
| Artificialisation département | Code département, millésimes, pourcentage et surface | Aucune valeur manquante observée dans le fichier départemental | Département × millésime / comparaison | Codes département; région | Millésimes 2018 et 2021 dans le fichier |
| Artificialisation commune | Code commune, département, millésimes et mesures | SCOT facultatif (613 vides en IDF); 2 lignes ont des valeurs 2021/flux manquantes; autres champs facultatifs selon source | Commune × millésime / comparaison | Codes INSEE commune/département, EPCI/SCOT si disponibles | Millésimes 2018 et 2021 dans le fichier |

### Profil de chaque source (extraction régionale)

| Source / filtre | Profil calculé | Fichier ou requête |
|---|---|---|
| BDIFF — extraction IDF type F, 2006–2025 | 347 lignes; 8 départements ciblés mais événements présents dans 5 départements (77: 293, 91: 39, 95: 9, 78: 5, 94: 1); 345 Numéro distincts; 0 doublon de ligne; 0 valeur manquante sur Année, Numéro, Département, Code INSEE et Date de première alerte; Type de peuplement vide 347/347; précision donnée vide 336/347; champs décès/bâtiments touchés vides 299/347 | `Incendies.csv`; import `read_csv(sep=";", skiprows=3)` |
| Météo des forêts — départements IDF | 960 lignes = 8 départements × 120 dates; du 2024-06-03 16:00 UTC au 2024-09-30 16:00 UTC; 0 doublon; aucun champ vide; J+1 : code 1 sur 958 lignes, code 2 sur 2; J+2 : code 1 sur 959, code 2 sur 1 | `BD/mdf_2024.csv`; import CSV séparateur virgule, filtre num_dep sur 75/77/78/91/92/93/94/95 |
| MOS — source régionale | 42 115 lignes; 1 204 codes INSEE distincts; `Geo Shape` vide 305/42 115 (0,72 %); `mos2021` 16 codes; `mos2025` code 1 sur 42 115 lignes | `BD/mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv`; import `sep=";"` |
| Artificialisation département — IDF | 8 lignes (8 départements); 0 champ vide | `BD/artif-departement.csv`; filtre département IDF |
| Artificialisation commune — IDF | 1 267 communes; `scot_code` vide 613/1 267 (48,38 %); 2 lignes ont des valeurs 2021/flux manquantes; valeurs de flux négatives observées et à conserver/contrôler | `BD/artif-commune.csv`; filtre département IDF |

Le profil a été produit à partir des fichiers joints à la conversation (BD.zip et Incendies.csv), en filtrant l'Île-de-France. Le script de profilage reproductible doit être ajouté au dépôt (chemin à décider, par exemple `scripts/profil_sources.py`) et exécuté sur les copies brutes archivées.

### Règles de qualité

| N° | Source | Niveau ou dimension | Sélecteur | Prédicat | Seuil (et sa justification) | Décision (bloquer, alerter, tolérer) |
|---|---|---|---|---|---|
| RQ1 | BDIFF | Complétude clé et dates | Toutes les lignes de l'extraction | Année, Numéro, Département, Code INSEE et Date de première alerte non nuls; date parseable; code département cohérent avec les 2 premiers chiffres du code INSEE | 100 % attendu pour les champs de jointure; observé 100 % dans le profil reçu | Bloquer le chargement analytique si une clé/date invalide; sinon passer |
| RQ2 | Météo des forêts | Complétude / couverture | Fichier filtré sur les 8 départements IDF | Tous les 8 départements × dates attendues présents; niveaux J+1/J+2 non nuls; pas de doublon département-date | 100 % attendu sur la grille couverte; observé 960/960, sans vide ni doublon | Bloquer une période incomplète ou un doublon non résolu; sinon passer |
| RQ3 | BDIFF | Unicité | Toutes les lignes | La clé candidate `Année + Numéro` est unique; aucun doublon exact | 100 % d'unicité attendu; Numéro seul n'est pas unique (345 valeurs distinctes pour 347 lignes) | Alerter et bloquer la validation de clé jusqu'à test de la clé composite |
| RQ4 | BDIFF | Complétude de champs descriptifs | Type de peuplement, précision, impacts | Mesurer le taux de vide; conserver un indicateur de complétude; ne pas imputer zéro | Seuil de référence tiré du profil : Type de peuplement 0 % rempli et précision 3,17 % remplie; champs impacts 13,83 % remplis. Ces champs ne peuvent pas être requis pour l'analyse générale | Tolérer comme champs facultatifs; écarter Type de peuplement de l'analyse tant que vide |
| RQ5 | MOS | Complétude géométrie | `Geo Shape` sur toutes les lignes | Géométrie absente quantifiée et isolée; classes et INSEE disponibles | 305/42 115 = 0,72 % observé; seuil d'alerte proposé 1 % (arrondi au-dessus du profil de référence, à réviser si la source change) | Alerter si >1 %; tolérer les lignes sans géométrie pour les analyses non spatiales; exclure du calcul spatial |
| RQ6 | MOS | Cohérence / variation de classe | `mos2025` et `Poste 2025` | Vérifier diversité des codes et correspondance code-libellé; investiguer si une classe unique est présente | Profil reçu : code 1 et libellé « Bois ou forêts » pour 100 % des 42 115 lignes alors que 2021 comporte 16 codes. Pas de seuil normal, anomalie bloquante pour toute analyse d'évolution avant validation du producteur | Bloquer l'analyse de changement 2021–2025; alerter et demander validation du fichier |
| RQ7 | Artificialisation commune | Complétude facultative | `scot_code` et mesures 2021/flux | Vides de SCOT signalés; contrôler les deux lignes avec métriques 2021/flux manquantes | SCOT 48,38 % vide dans l'extrait IDF; champ facultatif selon la disponibilité. 2 valeurs manquantes sur mesures : à corriger ou documenter avant KPI de flux | Tolérer SCOT manquant; alerter sur les 2 valeurs manquantes; ne pas imputer automatiquement |
| RQ8 | Sources territoriales | Validité des valeurs / unité | Surfaces, pourcentages et flux | Surfaces ≥0; pourcentages dans [0,100]; flux peuvent être négatifs et doivent être conservés | Bornes physiques; flux négatifs ne sont pas invalides en soi (variation entre millésimes) | Bloquer valeur hors borne; tolérer flux négatifs après validation de leur sens |

Ce que ces indicateurs de qualité ne permettent pas d'affirmer : une complétude élevée ne prouve ni l'exhaustivité des incendies déclarés, ni l'exactitude du danger météo, ni la précision des géométries ou classes. Les contrôles identifient des anomalies de structure et de cohérence, pas la vérité terrain.

## 10. Architecture

Schéma : `docs/architecture.md` (diagramme Mermaid).

| Couche | Rôle | Contenu envisagé | Outil | Questions servies |
|---|---|---|---|---|
| Sources | Données reçues de producteurs / exports | BDIFF, Météo des forêts, MOS, artificialisation; sources manquantes demandées | Téléchargement/export manuel; source/API si validée | Q1–Q4 selon source |
| Données brutes | Conservées sans modification | Fichiers d'origine, métadonnées, date d'import, critères d'extraction, empreinte | Git pour documentation/scripts; stockage de fichiers versionnés ou dépôt de données selon taille/licence | Toutes, reproductibilité |
| Données nettoyées | Types, formats, clés, doublons et manquants contrôlés | Dates normalisées; codes INSEE en chaîne; surfaces numériques; valeurs manquantes préservées; contrôles de qualité | Python/pandas (proposition), scripts reproductibles | Q1–Q4 |
| Données consolidées | Sources croisées au même grain | Table incendie événement; table territoire/commune; table département-date-danger; table commune-millésime artificialisation; MOS polygonal contrôlé | Python/pandas; jointures par code INSEE, département et date; SIG si analyse spatiale | Q1, Q2, Q3; contexte Q4 |
| Données prêtes pour l'analyse | Tables agrégées et features explicites | Agrégats commune/département/année/mois/heure; jours-départements avec feu recensé; matrices de confusion J+1 et J+2; scénarios de seuil; indicateurs de territoire | Python; exports CSV/Parquet si outil validé | Q1–Q4 |
| Restitution | Résultats lisibles et reproductibles | Cartes, tableaux, graphiques temporels, matrices de confusion et comparaison de scénarios; synthèse des limites | Notebook/outil de visualisation gratuit à choisir | Q1–Q4 |

Hypothèses : commencer par une chaîne locale de fichiers CSV et scripts Python plutôt que par une infrastructure cloud ou un ETL complexe. Les données brutes sont archivées avant toute transformation. Les scripts doivent pouvoir reproduire les tables analytiques à partir des archives sans re-télécharger les sources. Les jointures doivent respecter le grain : événement, commune, département-date ou commune-millésime; aucune jointure ne doit être faite uniquement sur un nom de commune.

## 11. Contraintes

| Contrainte | Comment l'architecture la respecte |
|---|---|
| Outils gratuits uniquement | Privilégier Python, pandas, Jupyter et un outil de visualisation gratuit; choix définitif à valider en groupe. |
| Conserver les données brutes | Répertoire raw/ ou stockage versionné séparé; aucune modification des fichiers sources. |
| Pouvoir retraiter sans rappeler les API | Scripts locaux alimentés par les archives; journaliser les paramètres et versions. |
| Données incomplètes | Profil de qualité, champs facultatifs, indicateurs de complétude, exclusion justifiée des lignes/champs inutilisables. |
| Accès à une source limité ou interrompu | Conserver l'export, la date de récupération, l'URL/fiche et les critères; signaler l'absence de nouveaux millésimes. |
| Taille des fichiers / dépôt Git | Les gros fichiers (MOS ~66 Mo, données brutes) peuvent être conservés hors Git ou dans un stockage convenu; le dépôt doit contenir la documentation, scripts et échantillons/agrégats nécessaires. Décision à consigner. |
| Données publiques et minimisation | Pas de données personnelles; pour des données opérationnelles futures, préférer les agrégats équipes/missions et restreindre l'accès si nécessaire. |

## 12. Planning de réalisation

| Jalon | Couche | Responsable | Date | Preuve qu'il est atteint |
|---|---|---|---|---|
| Valider questions, sources et matrice | Cadrage | Chef·fe de projet + responsable sources | 20–24 novembre 2026 (à confirmer) | `docs/specification.md` relu; matrice complète; sources référencées |
| Finaliser fiches, manques et décisions | Cadrage/qualité | Responsable sources + qualité | 24–27 novembre (à confirmer) | Fiches sources à jour; décisions numérotées dans le journal |
| Archiver et profiler les sources | Brutes/qualité | Responsable qualité | 27 novembre–1 décembre (à confirmer) | Script de profil; rapports qualité reproductibles; données brutes archivées |
| Construire le nettoyage et les clés | Nettoyées | Responsable pipeline | 1–4 décembre (à confirmer) | Tables normalisées; tests de clés, dates, doublons et valeurs passent |
| Consolider les sources | Consolidées | Responsable pipeline + membres concernés | 4–7 décembre (à confirmer) | Tables jointes au grain défini; tests de jointure et contrôles de cardinalité |
| Produire les analyses et restitution v0 | Analyse/restitution | Membres par Q1–Q4; chef·fe de projet coordonne | 7–10 décembre (à confirmer) | Graphiques/tableaux reproductibles; résultats et limites documentés |
| Vérifier, fusionner et préparer soutenance | Livraison | Tous; relecteurs par rôle | 10–11 décembre 2026 | PR relues/fusionnées; dépôt complet; démo reproductible; préparation soutenance |

Ce qui est prévu pendant les trois semaines sans cours : à préciser par le groupe selon les dates de calendrier et la disponibilité. Les jalons proposés sont une trame de travail, pas un planning validé.

## 13. Glossaire

Lien : `docs/glossaire.md` · Nombre de termes : à compter après relecture · Termes encore « à vérifier » : seuil officiel Météo des forêts, codes niveaux, convention J+1/J+2, type de feu F, MOS 79 postes, clé BDIFF.

Termes à vérifier / ajouter au glossaire : BDIFF, Météo des forêts, MOS, artificialisation, code INSEE, grain, clé composite, faux positif, faux négatif, sensibilité, spécificité, précision, J+1, J+2, historisation, données brutes, données consolidées.

## 14. Limites connues

- La base BDIFF reçue contient les événements selon les critères de l'export (Île-de-France, type F) et ne garantit pas l'exhaustivité de tous les départs de feu.
- Les champs descriptifs BDIFF sont très incomplets; `Type de peuplement` est entièrement vide dans l'extraction.
- L'heure de première alerte n'est pas nécessairement l'heure exacte du départ de feu; sa convention doit être documentée.
- L'archive Météo des forêts fournie ne couvre que 2024; les codes de niveaux et le seuil officiel ne sont pas documentés dans le CSV. La première analyse de Q3 est exploratoire et sépare J+1/J+2.
- Le champ MOS 2025 est uniforme (code 1) dans le fichier reçu et doit être vérifié avant analyse d'évolution.
- L'artificialisation décrit une évolution territoriale, pas un risque direct d'incendie.
- Les données de budget, moyens, coûts, plannings et interventions ne sont pas fournies; Q4 ne pourra pas produire une optimisation opérationnelle ou financière mesurée sans elles.
- Une corrélation territoriale ou temporelle ne démontre pas de causalité.
- Les résultats et recommandations doivent être validés par le commanditaire; la spécification pourra évoluer et tout changement sera inscrit dans le journal des décisions.
