# Qualité, complétude et conformité des données — Étude francilienne pour le SDIS 77

**Date du contrôle : 20 novembre 2026.**  
**Périmètre : toute l’Île-de-France ; interprétation opérationnelle particulière pour la Seine-et-Marne.**  
**Finalité : préparer un entrepôt permettant de décrire les feux recensés, contextualiser les territoires et étudier la concordance entre seuils météo et journées avec feu recensé.**

Les résultats chiffrés ci-dessous proviennent des analyses des bases de données predefinis, Les informations documentaires et les contrôles non réalisés sont distingués. 

## 1. Page de profil synthétique

| Source | Fichiers contrôlés et grain | Volume observé | Période réelle utile | Verdict pour le projet |
|---|---|---|---|---|
| MOS | Export CSV et nomenclature ; une zone cartographiée par ligne, rattachée à une commune | 42 115 zones, 9 colonnes ; nomenclature de 79 postes | États 2021 et 2025 ; export limité aux zones classées bois/forêts en 2025 | Exploitable pour un contexte forestier filtré ; analyses géométriques complètes bloquées par 305 géométries absentes |
| Artificialisation | `artif-departement.csv` ; un département par ligne | 100 lignes, 11 colonnes ; les 8 départements franciliens présents | 77 : 2017 → 2021 ; autres départements IDF : 2018 → 2021 | Exploitable pour le contexte départemental historique ; aucune granularité communale |
| Météo des forêts | `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv` ; département et horodatage d’archive, deux horizons par ligne | 35 616 lignes nationales ; 2 968 lignes franciliennes | Saisons archivées 2024, 2025 et 2026 | Bonne complétude interne ; codes et règle de date cible confirmés par le groupe ; mise en œuvre des jointures et fuseaux à contrôler |
| BDIFF | `Incendies.csv` ; un événement déclaré par ligne | 347 lignes, 24 colonnes ; 293 événements dans le 77 | Première alerte du 26/07/2006 au 05/11/2025 | Exploitable pour les événements recensés ; exhaustivité non démontrée, champs optionnels incomplets et doublon à revoir |

### Constats prioritaires

1. **Artificialisation : source départementale retenue.** Le contrôle porte sur `artif-departement.csv` pour cette source. Les huit départements franciliens sont présents, sans valeur absente ni clé dupliquée. Le 77 compare **2017 à 2021**, les sept autres **2018 à 2021** : les flux cumulés ne couvrent pas tous la même durée. La source permet une comparaison départementale descriptive, pas une mesure communale ni un état 2025/2027.
2. **MOS : filtre déterminant.** Toutes les 42 115 lignes ont `mos2025 = 1`, libellé « Bois ou forêts ». Le fichier ne représente pas toutes les occupations du sol et ne décrit pas à lui seul les interfaces habitat/forêt.
3. **MOS : absence géométrique peu visible en nombre.** 305 géométries manquent, soit 0,72 % des lignes, mais ces lignes représentent **11,96 % de la somme de `st_area_sh`**. Le calcul pondéré n’exige pas de connaître l’unité, seulement une unité homogène ; la conversion en hectares reste à confirmer.
4. **BDIFF : aucune observation de feu en 2026 dans l’extraction.** Ne pas interpréter les jours météo 2026 sans correspondance BDIFF comme des jours sans incendie.
5. **Jointure : risque de multiplication des événements.** Une jointure directe des 347 événements avec tous les polygones MOS sur le code communal produit **42 640 lignes**. Ce résultat est attendu d’une relation un-à-plusieurs, mais ne constitue pas 42 640 feux.


## 2. MOS — Occupation du sol 2021 et 2025

### 2.1. Identité et portée de l’extraction

Producteur : **L’Institut Paris Region**. Fichier contrôlé : `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv`. Nomenclature contrôlée : `nomenclature-du-mode-d-occupation-du-sol-francilien-79-postes.csv`.

Le grain est une zone cartographiée, avec code communal et classes des deux millésimes. Le code `insee` est une clé de rattachement communal, pas un identifiant unique de zone. L’export ne contient pas le champ `OBJECTID` mentionné dans la documentation de la source ; il faut conserver un identifiant de ligne technique et, si possible, récupérer l’identifiant source.

Les 42 115 zones concernent 1 204 codes communaux et les huit départements franciliens. Les 79 classes existent dans la nomenclature mais **une seule classe est observée en 2025 dans cette extraction**. Les zones sorties de la forêt avant 2025 peuvent être exclues du filtre : on ne peut donc pas mesurer toute la déforestation 2021–2025 avec cet export.

### 2.2. Tableau des six dimensions

| Dimension | Contrôle et résultat | Appréciation pour l’usage | Action |
|---|---|---|---|
| Complétude | Tous les champs autres que `Geo Shape` sont renseignés ; 305 géométries absentes ; 1 204 codes communaux présents | Partielle pour l’analyse spatiale ; complétude territoriale de l’inventaire complet non démontrée | Récupérer les géométries absentes et un export complet si l’étude porte sur les interfaces |
| Exactitude | Correspondances code/libellé conformes à la nomenclature ; aucune comparaison terrain ou imagerie indépendante réalisée | Exactitude thématique et géométrique non certifiée | Contrôle sur échantillon avec référentiel cartographique et millésime identiques |
| Cohérence | 0 désaccord code/libellé en 2021 et 2025 ; toutes les communes BDIFF trouvent un code dans ce MOS | Cohérence de rattachement constatée ; concepts et surfaces à harmoniser | Agréger avant jointure ; vérifier unités et limites communales historiques |
| Validité | Codes communaux à cinq chiffres ; codes MOS présents dans les 79 postes ; surfaces et longueurs strictement positives ; 41 810 géométries JSON lisibles | Formats contrôlés ; topologie non vérifiée | Contrôler le système de coordonnées et exécuter des tests géométriques spécialisés |
| Unicité | 0 doublon de ligne exacte ; 0 répétition textuelle de géométrie présente ; plusieurs zones par commune | Aucune clé métier de zone validée dans l’export | Ne pas dédupliquer sur `insee` ; conserver un identifiant de zone versionné |
| Actualité | Deux états 2021 et 2025 ; révisions des versions annoncées par le producteur | Adapté à un contexte historique récent ; pas une observation 2027 | Figer version, filtre et millésime de surface ; actualiser avant projection opérationnelle |

### 2.3. Complétude des valeurs


| Champ | Valeurs absentes | Remplissage | Usage |
| --- | --- | --- | --- |
| Geo Point | 0 | 100,00 % | Attribut géographique ou thématique |
| Geo Shape | 305 | 99,28 % | Géométrie polygonale |
| mos2021 | 0 | 100,00 % | Attribut géographique ou thématique |
| Poste 2021 | 0 | 100,00 % | Attribut géographique ou thématique |
| mos2025 | 0 | 100,00 % | Attribut géographique ou thématique |
| Poste 2025 | 0 | 100,00 % | Attribut géographique ou thématique |
| insee | 0 | 100,00 % | Attribut géographique ou thématique |
| st_area_sh | 0 | 100,00 % | Attribut géographique ou thématique |
| st_length_ | 0 | 100,00 % | Attribut géographique ou thématique |


### 2.4. Couverture départementale et géométries manquantes


| Département | Zones | Géométries absentes | Part de géométries absentes |
| --- | --- | --- | --- |
| 75 | 164 | 0 | 0,00 % |
| 77 | 20237 | 146 | 0,72 % |
| 78 | 8962 | 70 | 0,78 % |
| 91 | 7270 | 53 | 0,73 % |
| 92 | 220 | 1 | 0,45 % |
| 93 | 184 | 0 | 0,00 % |
| 94 | 355 | 2 | 0,56 % |
| 95 | 4723 | 33 | 0,70 % |


Les géométries présentes sont de type `Polygon`. 

Les coordonnées présentes sont de l’ordre de 1,46–3,56 en longitude et 48,12–49,24 en latitude, alors que la documentation du jeu d’origine mentionne EPSG:2154. L’export et la source peuvent utiliser des systèmes différents. Ne pas attribuer automatiquement EPSG:2154 aux coordonnées exportées. Vérifier le SCR avant calcul d’aires ou de distances ; ne pas calculer une aire métrique directement sur des coordonnées angulaires. `Geo Point` ne remplace pas le polygone pour une intersection.

Les unités de `st_area_sh` et `st_length_` restent à confirmer dans le contrat de données. L’unité minimale de collecte de 500 m² décrite dans la documentation ne doit pas devenir une règle automatique rejetant toute zone plus petite : des découpages peuvent produire de petites entités.

### 2.5. Trois règles minimales de qualité

| ID | Sélecteur | Prédicat | Seuil d’échec proposé | Résultat observé | Sévérité et décision |
|---|---|---|---|---|---|
| MOS-Q1 | `mos2021`, `mos2025`, libellés et nomenclature | Codes présents dans le référentiel et libellés concordants | Plus de 0 ligne fautive | Réussi : 0 anomalie | Bloquer la table thématique si échec ; isoler les lignes fautives |
| MOS-Q2 | Lignes destinées aux intersections géométriques | `Geo Shape` présent et JSON exploitable | Plus de 0 géométrie absente ou illisible dans la population publiée comme complète | Échec : 305 absences ; 0 JSON illisible parmi les présents | Bloquer la publication d’un résultat géométrique complet ; autoriser une analyse partielle explicitement étiquetée |
| MOS-Q3 | Zone de publication du lot | Le filtre est déclaré, et les classes attendues sont compatibles avec l’usage annoncé | Au moins un usage exigeant des classes absentes | Alerte : 100 % des lignes classées forêt en 2025 | Autoriser le contexte forestier ; bloquer les conclusions sur toutes les interfaces et sur la perte forestière totale |

### 2.6. Ce que la source permet d’affirmer

- Décrire les zones présentes et leur classification 2021/2025, sous le filtre de 2025.
- Préparer une agrégation de surface forestière communale après validation de l’unité et de la couverture.
- Contextualiser les feux par commune, sans prétendre localiser précisément chaque départ dans un polygone.

**Ne permet pas en l’état :** établir une carte exhaustive des interfaces, démontrer l’exactitude de terrain, cartographier tout le territoire avec les seules géométries présentes ou mesurer une évolution annuelle continue de 2021 à 2025.


## 3. Artificialisation des sols — Fichier départemental retenu

### 3.1. Identité, grain et périmètre

Producteur indiqué sur la fiche : **Mon Diagnostic Artificialisation** ; calculs fondés sur l’OCS GE. **Le seul fichier retenu pour l’analyse de cette source est désormais `artif-departement.csv`.** Les résultats de l’ancienne extraction ne sont pas utilisés dans cette version du rapport.

Le fichier contient **100 lignes et 11 colonnes**, avec **un département par ligne** et deux états d’artificialisation. Les 100 codes de département sont distincts. `region_code` sert de rattachement ; ce champ n’est pas une clé unique. Le filtre `region_code = "11"` restitue exactement les départements **75, 77, 78, 91, 92, 93, 94 et 95**, soit **8/8 départements attendus pour l’étude**. Les codes départementaux doivent être conservés en texte, notamment pour les zéros initiaux, la Corse et l’outre-mer.

### 3.2. Millésimes et valeurs franciliennes vérifiés

| Département | Nom | Premier millésime | Second millésime | Durée en années de millésime | % artificialisé au premier état | % artificialisé en 2021 | Évolution en points |
|---|---|---|---|---|---|---|---|
| 75 | Paris | 2018 | 2021 | 3 | 83,2963 | 83,3100 | 0,0137 |
| 77 | Seine-et-Marne | 2017 | 2021 | 4 | 11,7978 | 12,0362 | 0,2384 |
| 78 | Yvelines | 2018 | 2021 | 3 | 20,6286 | 20,8031 | 0,1745 |
| 91 | Essonne | 2018 | 2021 | 3 | 22,5216 | 22,8165 | 0,2950 |
| 92 | Hauts-de-Seine | 2018 | 2021 | 3 | 78,3715 | 78,5474 | 0,1760 |
| 93 | Seine-Saint-Denis | 2018 | 2021 | 3 | 82,8742 | 83,3030 | 0,4288 |
| 94 | Val-de-Marne | 2018 | 2021 | 3 | 74,6861 | 74,8908 | 0,2047 |
| 95 | Val-d'Oise | 2018 | 2021 | 3 | 24,5995 | 24,8555 | 0,2560 |

**Seine-et-Marne.** Le taux passe de **11,7978 % en 2017 à 12,0362 % en 2021**, soit **+0,2384 point de pourcentage**. Les surfaces passent de **698 951 387,2475** à **713 077 545,6702**, pour un solde de **+14 126 158,4227 unités de surface du fichier**. L’unité doit être confirmée avant conversion en hectares.

**Interprétation temporelle.** Le 77 couvre quatre années de millésime, les sept autres départements trois. Un classement sur le flux brut peut donc refléter des durées d’observation différentes. On peut produire un flux moyen par année de millésime en divisant le solde par la différence des années, mais cela reste une moyenne d’intervalle : cela ne reconstitue pas les observations de chaque année et ne tient pas compte de dates exactes d’acquisition non connues. Le taux du second état permet une comparaison au millésime 2021, sous réserve de méthodes et limites homogènes.

`flux_percent_1_2` est arithmétiquement la différence de `pourcent_artif_2` et `pourcent_artif_1`. Il s’exprime donc en **points de pourcentage**, pas en taux relatif de croissance. Un pourcentage départemental ne doit pas être additionné ou moyenné sans pondération pour obtenir une valeur régionale ; une agrégation exige les surfaces de référence appropriées et une méthode documentée.

### 4.3. Tableau des six dimensions

| Dimension | Contrôle et résultat | Appréciation pour l’usage | Action |
|---|---|---|---|
| Complétude | 0 valeur absente sur 1 100 cellules ; les 8 départements IDF sont présents une fois ; 0 conversion numérique invalide sur les six mesures | Bonne complétude des valeurs et couverture du périmètre départemental IDF ; aucune donnée communale | Autoriser le contexte départemental ; demander un fichier communal pour les analyses à ce grain |
| Exactitude | Pourcentages plausibles et calculs cohérents ; pas de validation indépendante contre l’OCS GE ni les surfaces de référence | Exactitude géographique non certifiée | Réconcilier un échantillon avec le producteur et confirmer unités et nomenclature |
| Cohérence | Flux de surface conforme à la différence des stocks à 10⁻⁶ près ; flux en points conforme à 10⁻¹⁰ près ; région 11 contient les huit codes IDF attendus | Cohérence arithmétique et rattachement IDF vérifiés ; durées différentes entre le 77 et les autres | Comparer les stocks 2021 et documenter les durées pour les flux ; ne pas confondre MOS et artificialisation |
| Validité | Codes départementaux conformes au motif contrôlé ; 0 date de millésime non analysable ; second millésime postérieur au premier ; pourcentages dans [0,100] et stocks non négatifs | Validité technique constatée sur le lot ; rattachement national au COG non vérifié | Conserver codes texte ; documenter l’unité ; vérifier un référentiel officiel millésimé avant validation de la couverture nationale |
| Unicité | 0 doublon de ligne et 0 doublon de `departement_code` | Unicité vérifiée au grain départemental | Clé département + version du lot ; garder une seule ligne par département pour un enrichissement many-to-one |
| Actualité | 77 : 2017/2021 ; sept autres départements IDF : 2018/2021 ; certains départements nationaux ont un second état 2023 | Contexte historique départemental ; pas une observation contemporaine des feux 2024/2025 ni de 2027 | Conserver les deux millésimes sur chaque ligne ; documenter le décalage temporel, sans interpolation annuelle |

### 4.4. Complétude des valeurs et contrôles détaillés

| Champ | Valeurs absentes sur 100 lignes | Taux de remplissage |
|---|---|---|
| `departement_code` | 0 | 100,00 % |
| `nom` | 0 | 100,00 % |
| `region_code` | 0 | 100,00 % |
| `millesimes_1` | 0 | 100,00 % |
| `pourcent_artif_1` | 0 | 100,00 % |
| `surface_artif_1` | 0 | 100,00 % |
| `millesimes_2` | 0 | 100,00 % |
| `pourcent_artif_2` | 0 | 100,00 % |
| `surface_artif_2` | 0 | 100,00 % |
| `flux_surface_1_2` | 0 | 100,00 % |
| `flux_percent_1_2` | 0 | 100,00 % |

| Contrôle exécuté | Résultat |
|---|---|
| Lignes nationales / lignes franciliennes | 100 / 8 |
| Clés départementales dupliquées / doublons exacts | 0 / 0 |
| Départements IDF absents du jeu attendu | 0 |
| Pourcentages hors [0,100] | 0 ligne |
| Stocks de surface négatifs | 0 ligne |
| Conversions numériques invalides dans les six mesures | 0 valeur |
| Millésimes non conformes au format quatre chiffres | 0 ligne |
| Second millésime inférieur ou égal au premier | 0 ligne |
| Écart maximal pour `surface_artif_2 - surface_artif_1 = flux_surface_1_2` | Environ 1,02 × 10⁻⁷ unité de surface |
| Écart maximal pour `pourcent_artif_2 - pourcent_artif_1 = flux_percent_1_2` | Environ 9,21 × 10⁻¹⁴ point |

Ces petits écarts sont compatibles avec les arrondis et calculs flottants. Le nombre de 100 lignes décrit les départements reçus et ne certifie pas une couverture nationale complète : la vérification exhaustive contre un référentiel national millésimé n’a pas été réalisée. La couverture **8/8 pour l’Île-de-France**, en revanche, a été contrôlée contre le périmètre attendu du projet.

Les valeurs positives et les égalités arithmétiques ne prouvent pas l’exactitude des surfaces observées sur le terrain. Un flux net négatif n’est pas interdit conceptuellement : il peut représenter une désartificialisation nette ; il ne doit donc pas être rejeté uniquement en raison de son signe.

### 4.5. Trois règles minimales de qualité

| ID | Sélecteur | Prédicat | Seuil d’échec proposé | Résultat observé | Sévérité et décision |
|---|---|---|---|---|---|
| ART-Q1 | `departement_code`, `region_code` et filtre Île-de-France | Code départemental présent et unique ; région 11 correspondant exactement aux huit départements attendus | Plus de 0 clé vide/dupliquée ou un département IDF absent, supplémentaire ou mal rattaché | Réussi : 100 clés distinctes et couverture IDF 8/8 | Bloquer l’enrichissement départemental si échec ; conserver le lot et les rejets |
| ART-Q2 | Pourcentages, stocks et flux | Pourcentages dans [0,100], stocks ≥ 0 et flux égaux aux différences à la tolérance près | Plus de 0 anomalie ; tolérance 10⁻⁶ pour les surfaces et 10⁻¹⁰ pour les points | Réussi sur 100 lignes ; écarts maximaux ≈ 1,02×10⁻⁷ et 9,21×10⁻¹⁴ | Bloquer l’agrégat transformé si échec ; contrôler types, arrondis et unité |
| ART-Q3 | Millésimes et comparaisons de flux | Années renseignées, analysables et ordonnées ; toute comparaison de flux documente les différences de durée | Plus de 0 année invalide ou une comparaison de flux de durées différentes sans avertissement | Années conformes ; alerte métier : intervalle de 4 ans pour le 77 et 3 ans ailleurs en IDF | Autoriser les stocks 2021 et analyses historiques ; bloquer une publication de flux présentés comme comparables sans traitement ou mention des durées |

Ces seuils sont des propositions de contrôle du groupe, pas des exigences réglementaires du producteur. Une jointure des événements BDIFF ou des jours météo avec cette table doit être **plusieurs-vers-un** sur le département, après choix de la version. La surface départementale répétée sur chaque événement ne doit pas ensuite être sommée comme une nouvelle surface à chaque feu.

### 4.6. Pertinence et limites pour les indicateurs

Le fichier permet de **comparer le contexte d’artificialisation des huit départements franciliens**, notamment leur part artificialisée au millésime 2021, et d’enrichir les observations météo et incendies au grain départemental. Il décrit aussi une évolution nette entre deux états, avec durées à préciser.

Il ne fournit pas les contrastes entre communes d’un même département, les polygones d’interface habitat/forêt, l’humidité des sols ou l’inflammabilité. Répéter la même valeur départementale sur toutes ses communes ne crée aucune information communale. Une association entre artificialisation et feux sur seulement huit départements reste descriptive et sensible aux effectifs, aux surfaces exposées et à l’hétérogénéité de collecte ; elle ne prouve pas une causalité. Les concepts et méthodes de l’OCS GE et du MOS ne doivent pas être supposés interchangeables.

## 5. Météo des forêts

### 5.1. Profil des archives

Producteur : **Météo-France**. Une ligne contient un département, un horodatage d’archive et les deux niveaux `niveau_j1` et `niveau_j2`. Après normalisation analytique, le grain devient département + date cible + horizon. L’horodatage est fourni en UTC. Le groupe confirme que `date` correspond à l’émission du bulletin. J+1 concerne le lendemain et J+2 le surlendemain de cette émission. Les dates cibles sont dérivées selon cette règle ; la mise en œuvre et les fuseaux doivent encore être contrôlés lors du rapprochement avec BDIFF.


| Fichier | Lignes nationales | Départements | Dates distinctes | Plage observée de `date` en UTC | Lignes IDF |
| --- | --- | --- | --- | --- | --- |
| mdf_2024.csv | 11520 | 96 | 120 | 2024-06-03 au 2024-09-30 | 960 |
| mdf_2025.csv | 11520 | 96 | 120 | 2025-06-03 au 2025-09-30 | 960 |
| mdf_2026.csv | 12576 | 96 | 131 | 2026-05-28 au 2026-10-05 | 1048 |


Le total francilien est de **2 968 lignes** et de **5 936 valeurs d’horizon**. Les huit départements sont présents chaque jour à l’intérieur des fenêtres observées. Cela ne prouve pas que le premier et le dernier jour de la saison officielle sont tous présents : un calendrier de diffusion de référence est nécessaire pour cette vérification externe.

### 5.2. Tableau des six dimensions

| Dimension | Contrôle et résultat | Appréciation pour l’usage | Action |
|---|---|---|---|
| Complétude | 0 valeur absente dans les trois fichiers ; 0 couple département-jour manquant à l’intérieur des fenêtres et des départements observés | Bonne complétude interne ; couverture de la saison officielle non certifiée | Comparer au calendrier attendu ; ne pas fabriquer des niveaux hors période |
| Exactitude | Niveaux plausibles dans {1,2,3,4}, sans comparaison indépendante aux bulletins archivés | Exactitude de transcription non vérifiée ; pas une vérité sur la survenue d’un feu | Contrôler un échantillon contre les bulletins ; distinguer danger et occurrence |
| Cohérence | Deux horizons présents ; `date` d’émission et décalages J+1/J+2 confirmés par le groupe ; schéma variable entre années | Règle temporelle explicitée ; application et fuseaux à vérifier | Harmoniser le schéma et contrôler la jointure sur département et date cible, séparément par horizon |
| Validité | 0 date non analysable ; 0 niveau hors domaine ; `num_dep` doit rester textuel | Validité technique vérifiée pour les contrôles exécutés | Préserver `2A`/`2B` dans les fichiers nationaux ; normaliser les zéros initiaux |
| Unicité | 0 doublon de département-jour par fichier, 0 doublon exact | Unicité quotidienne constatée dans les lots reçus | Prévoir plusieurs émissions futures et une règle de choix ; conserver l’historique des versions |
| Actualité | Archives 2024–2026 disponibles ; feux BDIFF arrêtés en 2025 | 2024–2025 candidats à la comparaison ; 2026 utilisable pour météo seule | Exclure 2026 de la matrice actuelle ; ne pas traiter le défaut de correspondance comme Y=0 |

### 5.3. Complétude des champs

| Champ source | Contrôle sur les trois lots | Normalisation proposée |
|---|---|---|
| `date` | 0 absence, dates analysables en UTC | `date_emission_utc` ; date d’émission confirmée par le groupe ; dates cibles dérivées séparément |
| `num_dep` | 0 absence | Texte ; conserver les codes alphanumériques et les zéros initiaux |
| `niveau_j1` | 0 absence, valeurs dans {1,2,3,4} | Niveau ordinal avec horizon J+1 |
| `niveau_j2` | 0 absence, valeurs dans {1,2,3,4} | Niveau ordinal avec horizon J+2 |
| `nom_dep` ou `dep_nom` | 0 absence ; nom de colonne différent en 2025 | Colonne canonique unique, par exemple `nom_departement` |

Le séparateur est une virgule pour 2024 et 2025, un point-virgule pour 2026. La lecture doit être configurée par lot ; un changement de séparateur ne doit pas produire silencieusement une colonne unique.

### 5.4. Distribution des niveaux en Île-de-France


| Année | Horizon | Code 1 | Code 2 | Code 3 | Code 4 | Total |
| --- | --- | --- | --- | --- | --- | --- |
| 2024 | J1 | 958 | 2 | 0 | 0 | 960 |
| 2024 | J2 | 959 | 1 | 0 | 0 | 960 |
| 2025 | J1 | 837 | 120 | 3 | 0 | 960 |
| 2025 | J2 | 841 | 116 | 3 | 0 | 960 |
| 2026 | J1 | 461 | 418 | 168 | 1 | 1048 |
| 2026 | J2 | 501 | 419 | 128 | 0 | 1048 |


La source officielle décrit quatre catégories. **Le groupe a confirmé la correspondance suivante le 20 novembre 2026.** Cette confirmation est une information fournie par le groupe ; elle ne correspond pas à une nouvelle vérification indépendante du dictionnaire de l’archive.

| Code CSV | Danger | Couleur |
|---|---|---|
| 1 | Faible | Vert |
| 2 | Modéré | Jaune |
| 3 | Élevé | Orange |
| 4 | Très élevé | Rouge |

Le **seuil de mobilisation du SDIS 77 reste à documenter** : il ne se déduit pas de la présence de ces quatre niveaux. Les seuils 2, 3 et 4 restent des scénarios d’analyse tant que la règle opérationnelle n’est pas fournie.

En Île-de-France, le code 4 n’apparaît pas en 2024–2025. Un scénario N=4 ne produit donc aucune journée signalée sur ces lots : certaines métriques auront un dénominateur nul. C’est une limite de variation et d’effectif, pas une preuve de défaut de fichier. Le niveau 1 domine très largement en 2024 ; publier les décomptes avec chaque taux.

### 5.4 bis. Dates et règle de rapprochement confirmées par le groupe

| Champ ou notion | Signification retenue | Utilisation |
|---|---|---|
| Météo : `date` | Date et heure d’émission du bulletin | Conserver l’horodatage source UTC et dériver le jour civil d’émission |
| Météo : `niveau_j1` | Niveau prévu pour le lendemain de l’émission | Date cible = jour d’émission + 1 jour calendaire |
| Météo : `niveau_j2` | Niveau prévu pour le surlendemain de l’émission | Date cible = jour d’émission + 2 jours calendaires |
| BDIFF : `Date de première alerte` | Signalement du feu, confirmé par le groupe | Retenir ce jour pour l’événement ; il peut différer du départ réel |

**Exemple.** Un feu signalé dans BDIFF le 12 juin est rapproché du niveau J+1 du bulletin émis le 11 juin et du niveau J+2 du bulletin émis le 10 juin, dans le même département. Les deux horizons produisent deux comparaisons distinctes ; ils ne sont pas additionnés dans un même taux.

**Statut de preuve.** Les sens des codes, de l’émission et des horizons sont confirmés par le groupe dans les échanges du 20 novembre 2026. Les contrôles d’exécution de la jointure ne sont pas déclarés réussis sur la seule base de ces confirmations. Conserver le dictionnaire producteur lorsqu’il est disponible.

**Contrôle restant.** Les horodatages météo sont explicites en UTC ; ceux de BDIFF ne portent pas de fuseau dans le CSV. Confirmer le fuseau de saisie BDIFF, convertir si nécessaire vers un même calendrier civil (Europe/Paris pour l’étude francilienne), puis extraire les jours et appliquer les décalages calendaires. Ne pas ajouter arbitrairement une heure ou deux à toutes les dates. Vérifier quelques correspondances à la main et conserver les émissions, dates cibles, horizons et exclusions dans la table de contrôle.

### 5.5. Trois règles minimales de qualité

| ID | Sélecteur | Prédicat | Seuil d’échec proposé | Résultat observé | Sévérité et décision |
|---|---|---|---|---|---|
| MDF-Q1 | Date, département, niveaux des deux horizons | Champs renseignés, date analysable et niveaux dans {1,2,3,4} | Plus de 0 ligne fautive | Réussi sur 35 616 lignes | Bloquer le lot transformé si échec et conserver les rejets |
| MDF-Q2 | Couples département-jour au sein de chaque lot | Unicité et grille complète sur les dates internes observées | Plus de 0 doublon ou couple interne absent | Réussi pour les trois lots | Bloquer un taux présenté comme complet ; alerter pour une série partielle documentée |
| MDF-Q3 | Lignes destinées au rapprochement BDIFF | Appliquer date d’émission + 1 ou + 2 jours selon l’horizon ; calendrier commun et année couverte par la collecte des feux | Plus de 0 ligne hors calendrier ou de date cible mal dérivée dans le panel annoncé | Règle et codes confirmés par le groupe ; contrôle de la jointure restant ; incompatibilité établie pour 2026 | Valider les fuseaux et la jointure avant publication de résultats validés ; exclure 2026 du calcul actuel |

### 5.6. Pertinence

La source permet de compter les journées de danger par scénario et d’étudier leur concordance avec des journées de feux recensés. Elle n’apporte pas de températures ou d’humidité horaires dans les cinq colonnes étudiées. Elle ne prouve ni une mobilisation des équipes, ni un coût, ni l’existence certaine d’un incendie à venir.


## 6. BDIFF — Incendies recensés

### 6.1. Périmètre de l’extraction

Fichier : `Incendies.csv`, séparateur point-virgule, **trois lignes de métadonnées avant l’en-tête**. Le filtre embarqué indique l’Île-de-France, une date maximale au 31 décembre 2025 et **type de feu `F`**. Le sens précis de ce filtre doit être rapproché du dictionnaire : ne pas annoncer une couverture de tous les feux de végétation ou de toutes les interventions SDIS sur la base de cette seule extraction.

Les **347 événements** ont 117 codes communaux distincts. Les premières alertes observées vont du **26 juillet 2006 à 15:05** au **5 novembre 2025 à 20:44:34**, dans le fuseau de saisie non documenté ici. Une date limite de sélection au 31 décembre n’est pas la date d’un dernier événement observé et ne prouve pas une campagne complètement validée.

### 6.2. Tableau des six dimensions

| Dimension | Contrôle et résultat | Appréciation pour l’usage | Action |
|---|---|---|---|
| Complétude | Champs identifiants, première alerte, commune, surface totale et forêt renseignés ; plusieurs colonnes vides ; trois départements sans ligne | Bonne présence des champs centraux ; exhaustivité des événements non démontrée | Réconcilier avec collecte/SDIS et distinguer absence d’événement et absence de collecte |
| Exactitude | 276 surfaces estimées, 61 mesurées, 10 sans précision ; aucune validation événementielle indépendante | Incertitude importante près d’un seuil de surface | Lire avec précision des surfaces, réaliser une analyse de sensibilité et contrôler un échantillon |
| Cohérence | 0 année discordante avec la première alerte ; 0 code communal au préfixe départemental discordant ; forêt ≤ surface totale sur toutes les lignes | Contrôles internes réussis ; formulaires historiques non harmonisés automatiquement | Conserver version et nature des champs ; ne pas additionner des rubriques historiques potentiellement recouvrantes |
| Validité | 0 date non analysable, codes communaux à cinq chiffres, 0 surface totale négative | Conformité des champs centraux constatée ; validité source limitée pour 11 événements signalés | Isoler ou étiqueter les lignes à qualité dégradée ; documenter les règles d’éligibilité |
| Unicité | 0 doublon exact ; 0 doublon de (Année, Numéro) ; deux numéros répétés entre années ; deux lignes identiques hors Numéro | Clé composée adaptée au lot, doublon métier potentiel | Ne pas utiliser Numéro seul ; revoir le couple de lignes sans suppression automatique |
| Actualité | Dernier événement reçu en novembre 2025 ; aucune donnée 2026/2027 | Historique exploitable ; insuffisant pour bilan opérationnel 2027 | Actualiser les extractions et tracer la validation des campagnes |

### 6.3. Complétude de chaque colonne


| Champ | Valeurs absentes | Taux de remplissage |
| --- | --- | --- |
| Année | 0 | 100,00 % |
| Numéro | 0 | 100,00 % |
| Département | 0 | 100,00 % |
| Code INSEE | 0 | 100,00 % |
| Nom de la commune | 0 | 100,00 % |
| Date de première alerte | 0 | 100,00 % |
| Surface parcourue (m2) | 0 | 100,00 % |
| Surface forêt (m2) | 0 | 100,00 % |
| Surface maquis garrigues (m2) | 347 | 0,00 % |
| Autres surfaces naturelles hors forêt (m2) | 0 | 100,00 % |
| Surfaces agricoles (m2) | 241 | 30,55 % |
| Autres surfaces (m2) | 241 | 30,55 % |
| Surface autres terres boisées (m2) | 106 | 69,45 % |
| Surfaces non boisées naturelles (m2) | 106 | 69,45 % |
| Surfaces non boisées artificialisées (m2) | 106 | 69,45 % |
| Surfaces non boisées (m2) | 106 | 69,45 % |
| Précision des surfaces | 10 | 97,12 % |
| Type de peuplement | 347 | 0,00 % |
| Nature | 216 | 37,75 % |
| Décès ou bâtiments touchés | 241 | 30,55 % |
| Nombre de décès | 299 | 13,83 % |
| Nombre de bâtiments totalement détruits | 299 | 13,83 % |
| Nombre de bâtiments partiellement détruits | 299 | 13,83 % |
| Précision de la donnée | 336 | 3,17 % |


**Interprétation des champs vides.** Les colonnes `Type de peuplement` et `Surface maquis garrigues (m2)` sont intégralement vides. Certaines surfaces diffèrent selon les générations de formulaire. Une absence ne doit pas être remplacée systématiquement par zéro. Les valeurs absentes sur décès et bâtiments ne démontrent pas une absence de conséquences.

La colonne `Précision de la donnée` comporte 11 mentions « Données partielles ou non valides » et 336 cellules vides. L’aide BDIFF indique que la mention signale des attributs obligatoires non renseignés ou non validés. **Un vide dans ce champ n’est donc pas traité comme une erreur de remplissage ordinaire** ; il ne constitue pas non plus une garantie d’exactitude de tous les attributs. Conserver le statut source.

### 6.4. Complétude de population et de période


| Département | Événements recensés | Lecture |
| --- | --- | --- |
| 75 | 0 | Aucune ligne : collecte à vérifier, pas une preuve de zéro feu |
| 77 | 293 | Événements présents ; exhaustivité à vérifier |
| 78 | 5 | Événements présents ; exhaustivité à vérifier |
| 91 | 39 | Événements présents ; exhaustivité à vérifier |
| 92 | 0 | Aucune ligne : collecte à vérifier, pas une preuve de zéro feu |
| 93 | 0 | Aucune ligne : collecte à vérifier, pas une preuve de zéro feu |
| 94 | 1 | Événements présents ; exhaustivité à vérifier |
| 95 | 9 | Événements présents ; exhaustivité à vérifier |


Aucun événement n’est présent pour 2007. Le nombre de lignes varie selon les années ; cette variation peut refléter les feux réels, l’évolution de la collecte ou le filtrage. Un référentiel de collecte est requis pour distinguer ces causes. Imposer « au moins un incendie par département et par année » serait une mauvaise règle métier : un véritable zéro est possible. Ce qui doit être attendu est une **preuve de couverture de collecte**, pas un événement artificiel.

### 6.5. Unicité et précision des surfaces

| Contrôle | Résultat |
|---|---|
| Clé `(Année, Numéro)` | 347 combinaisons distinctes sur 347 lignes |
| `Numéro` seul | Deux occurrences supplémentaires de numéros déjà vus dans une autre année |
| Doublon potentiel métier | Deux lignes de Fontainebleau (`77186`), première alerte le 11/06/2015 à 11:30, 300 m², numéros 523 et 524 |
| Surfaces estimées | 276/347 = 79,54 % |
| Surfaces mesurées | 61/347 = 17,58 % |
| Précision des surfaces absente | 10/347 = 2,88 % |
| Mention de qualité dégradée | 11/347 = 3,17 % |

Le couple 523/524 peut correspondre à deux événements distincts ou à une double déclaration. La similarité ne permet pas de trancher ; conserver les deux lignes en brut et demander une vérification. Les dénominateurs et la sensibilité des indicateurs doivent préciser le traitement retenu.

### 6.6. Trois règles minimales de qualité

| ID | Sélecteur | Prédicat | Seuil d’échec proposé | Résultat observé | Sévérité et décision |
|---|---|---|---|---|---|
| BDIFF-Q1 | Année, Numéro, département, commune, première alerte | Champs requis présents ; clé composée unique ; date analysable | Plus de 0 anomalie | Réussi pour ces contrôles | Bloquer la table de faits si échec ; isoler et tracer les rejets |
| BDIFF-Q2 | Année, date, codes et surfaces centrales | Année de la date concordante, préfixe communal cohérent, surface totale ≥ 0 et forêt ≤ total | Plus de 0 contradiction | Réussi : 0 contradiction observée | Bloquer les lignes contradictoires dans la table validée |
| BDIFF-Q3 | Statut qualité, précision des surfaces et candidats doublons | Signalements source et candidats doublons identifiés et documentés | Plus de 0 cas non revu | Alerte : 11 signalements qualité, 10 précisions de surface absentes et un couple de lignes à revoir | Autoriser l’exploration étiquetée ; bloquer une publication de résultats validés sans règle d’éligibilité et analyse de sensibilité |

### 6.7. Pertinence

Les données permettent de décrire les **feux recensés sous les critères de cette extraction**, leur distribution temporelle et communale et leurs surfaces renseignées. L’heure de première alerte est un proxy de l’heure de départ. Elles ne décrivent pas les présences de patrouilles, les coûts ni les temps d’arrivée des secours. Une tendance des feux recensés n’établit pas seule une tendance du risque réel.


## 7. Conformité et gouvernance des quatre sources

### 7.1. Tableau de conformité

| Domaine | MOS | Artificialisation | Météo des forêts | BDIFF |
|---|---|---|---|---|
| Licence affichée | Licence Ouverte v2.0 sur le portail régional | Licence Ouverte v2.0 sur la fiche officielle | Licence Ouverte v2.0 sur la fiche d’archives | Licence Ouverte v2.0 sur la fiche officielle |
| Provenance à conserver | Institut Paris Region, URL du jeu, version, filtre, millésimes | Mon Diagnostic Artificialisation, fichier départemental, version et deux millésimes par département | Météo-France, archive annuelle et dictionnaire | Portail BDIFF, producteur de la fiche IGN, critères d’extraction et mentions légales jointes |
| Identification directe dans les colonnes reçues | Aucun champ nominatif de personne repéré | Aucun champ nominatif de personne repéré | Aucun champ nominatif de personne repéré | Aucun champ nominatif de personne repéré ; événements et conséquences décrits |
| Vigilance de protection | Les zones de terrain ne constituent pas par elles-mêmes une donnée sur une personne | Agrégats départementaux ; risque d’identification non repéré dans ces champs | Niveaux départementaux ; risque d’identification non repéré dans ces champs | Date, commune et conséquences rares peuvent permettre des rapprochements avec des informations externes |
| Conformité technique | Schéma CSV contrôlé, géométries partielles, unité/SCR à confirmer | Grain départemental contrôlé ; durées 2017–2021 et 2018–2021 à distinguer en IDF | Types contrôlés, dérive de schéma interannuelle à normaliser | Lecture des métadonnées, clé composée, formulaires et valeurs manquantes à traiter |
| Statut de conformité du projet | Réutilisation à tracer ; aucune certification globale | Réutilisation à tracer ; usage départemental possible, analyse communale non justifiée | Réutilisation à tracer ; interprétation du dispositif à respecter | Réutilisation à tracer ; vérifier l’identifiabilité lors des enrichissements |

Les licences affichées ont été vérifiées sur les fiches officielles disponibles au 20 novembre 2026. Elles ne dispensent pas de conserver les conditions associées au lot effectivement téléchargé. Documenter la source, le lien, la version, les dates et les transformations dans le dépôt, et archiver la licence applicable.

**Protection des données.** L’absence de noms ne suffit pas à certifier l’anonymat : la CNIL rappelle qu’une identification peut résulter d’un croisement d’informations. Pour ce projet, les champs publics contrôlés ne présentent pas d’identifiant direct de personne repéré. Toute arrivée de données internes SDIS contenant agents, victimes, adresses ou récits exige une réévaluation de la finalité, des accès, de la conservation et des risques d’identification. Éviter de verser ces futures données internes dans le dépôt public ; publier les agrégats nécessaires à la restitution.

**Normes qualité.** Les six dimensions du cours structurent l’analyse ; aucune certification ISO, aucun audit de sécurité et aucune certification RGPD ne sont établis par ce profilage.

### 7.2. Traçabilité minimale dans l’entrepôt

| Métadonnée | Raison |
|---|---|
| `source`, URL du jeu et nom du fichier | Retrouver le producteur et le lot |
| Date d’extraction effective | Distinguer acquisition, publication et observation ; à renseigner depuis l’historique réel, sans l’inventer |
| Millésimes / période couverte | Éviter les comparaisons de périodes incompatibles |
| Filtres appliqués | Reproduire le sous-ensemble forêt MOS et le type de feu BDIFF |
| Empreinte SHA-256 | Identifier précisément les octets contrôlés |
| Version du script et des référentiels | Reproduire les contrôles et jointures |
| Rapports de rejets et règles d’éligibilité | Expliquer les exclusions sans supprimer les preuves |
| Licence et attribution | Conserver les conditions de réutilisation |

## 8. Cohérence intersources et barrières de publication

| Rapprochement | Résultat ou difficulté observée | Règle et décision |
|---|---|---|
| BDIFF ↔ MOS sur commune | 347/347 événements trouvent une commune dans le MOS filtré ; cela ne localise pas le feu dans une forêt | Vérifier le référentiel communal millésimé et agréger les polygones avant une jointure communale |
| BDIFF ↔ polygones MOS en jointure brute | 347 événements donnent 42 640 lignes après expansion sur `Code INSEE = insee` | Conserver une table d’événements distincte ; ne jamais compter les lignes de cette expansion comme des feux |
| BDIFF ↔ Météo | Seuls les jours comparables des saisons 2024 et 2025 sont candidats | Appliquer la règle d’émission et les horizons confirmés ; harmoniser les fuseaux et contrôler la jointure ; exclure les dates sans couverture ; ne pas inclure 2026 comme « sans feu » |
| MOS ↔ Artificialisation | Concepts et dates différents ; huit valeurs départementales IDF dans l’artificialisation fournie | Agréger le MOS au département avant comparaison ; confirmer unités, millésimes et sens des classes ; aucune interface précise déduite |
| BDIFF / Météo ↔ Artificialisation | Les huit départements IDF sont présents une fois dans le fichier d’artificialisation | Joindre BDIFF.`Département` ou météo.`num_dep` à `departement_code`, en texte ; valider la relation plusieurs-vers-un et conserver les effectifs avant/après |
| Codes région ↔ département | La région Île-de-France est `11`, la Seine-et-Marne est le département `77` | Employer un référentiel région-département ; ne pas joindre des codes parce que leurs valeurs sont numériques |
| Temporalité ↔ objectifs 2027 | Pas d’observations opérationnelles 2027 | Objectifs prospectifs uniquement ; aucune atteinte de cible ne peut être calculée aujourd’hui |

### Procédure de qualité proposée

1. Conserver les fichiers bruts et leurs empreintes ; vérifier séparateur, encodage et schéma.
2. Normaliser les types, codes et dates sans écraser les valeurs originales.
3. Exécuter les assertions et conserver le nombre de lignes fautives ainsi que leur identifiant.
4. En présence d’un échec bloquant, ne pas publier la table analytique concernée ; conserver le lot brut et les rejets.
5. En présence d’alertes uniquement, autoriser les usages compatibles en affichant leurs limites.
6. Réconcilier les effectifs et les agrégats avant/après transformation ; réexécuter les tests à chaque nouveau lot.

Bloquer une publication analytique n’implique pas de jeter les données. Une ligne incomplète pour une analyse géométrique peut rester exploitable pour un contexte communal ou un inventaire de qualité.

## 9. Conséquences pour les indicateurs du groupe

| Indicateur envisagé | Statut avec les données reçues | Conditions et limite de l’affirmation |
|---|---|---|
| KPI principal : part des jours avec feu recensé sous le seuil météo | Calcul exploratoire possible sur 2024–2025 ; publication validée conditionnelle | Grain département-date cible-horizon, collecte BDIFF documentée, jointures vérifiées, scénarios 2/3/4 et seuil réel SDIS distingués |
| Garde-fou : jours signalés sans feu recensé | Même condition que le principal | Dire « sans feu recensé » ; ne pas appeler ce chiffre coût réel, mobilisation à vide ou erreur certaine de prévision |
| Volume de jours signalés | Calculable pour les archives météo | Conserver période, horizon, code et seuil ; volume potentiel, pas des moyens réellement engagés |
| Répartition horaire et saisonnière | Calculable sur premières alertes BDIFF | Heure d’alerte distincte du départ ; petits effectifs et qualité de saisie à préciser |
| Concentration communale | Calculable pour les feux recensés | Ne démontre pas un risque corrigé de la surface exposée ni une interface exacte |
| Densité de feux par surface forestière | Conditionnelle | Valider unité, filtre, millésime, cohérence du type de feu et couverture du MOS |
| Couverture effective d’un feu par le dispositif | Non calculable avec les seules sources fournies | Positions précises et présences réalisées du SDIS nécessaires |
| Baisse des feux ≥ 1 ha en 2027 | Non mesurable aujourd’hui | Référence à calculer sur saisons comparables ; données futures nécessaires ; seuil ≥ 1 ha proposé pour l’analyse |
| Délai d’arrivée ou coût d’intervention | Non calculable | Données opérationnelles et financières absentes |
| Association départementale entre artificialisation et feux | Exploration descriptive possible sur les huit départements | Stocks 2021 ou flux à durées documentées ; décalage temporel et faibles effectifs à indiquer ; aucune causalité déduite |
| Effet communal de l’artificialisation sur les feux | Non évaluable avec la seule table départementale | Données communales et dates compatibles nécessaires ; pas de désagrégation artificielle |

Le KPI principal mesure une concordance entre danger annoncé et événements recensés, pas une prévision certaine de départ de feu ni l’efficacité intrinsèque de Météo-France ou du SDIS. Un taux à dénominateur nul est **non calculable**, pas égal à zéro. Chaque taux doit afficher son numérateur, son dénominateur, ses exclusions et sa période.

## 10. Plan de correction priorisé

| Priorité | Action | Responsable proposé | Résultat attendu |
|---|---|---|---|
| P0 | Mettre en œuvre et contrôler la jointure avec les codes et dates confirmés ; obtenir la règle de déclenchement réelle | Référent météo ; interlocuteur BDIFF pour le fuseau ; SDIS pour la mobilisation | Calendrier commun, correspondances vérifiées et scénarios distingués du seuil réel |
| P0 | Limiter la matrice météo/feux aux périodes communes 2024–2025 | Référent entrepôt | Aucun faux négatif de collecte traité comme un zéro en 2026 |
| P0 | Reporter les millésimes exacts du fichier départemental : 77 2017→2021, autres IDF 2018→2021 | Référent artificialisation | Périodes et grain départemental cohérents dans les fiches et livrables KPI |
| P0 | Empêcher la multiplication des feux dans les jointures MOS | Référent entrepôt | Effectif événementiel conservé après enrichissement |
| P1 | Récupérer géométries MOS manquantes, unités et SCR | Référent MOS | Surfaces, distances et intersections interprétables |
| P1 | Revoir les deux lignes BDIFF similaires et les 11 statuts dégradés | Référent BDIFF | Règle d’éligibilité documentée, analyse de sensibilité |
| P1 | Vérifier la couverture des feux par département et période | Référent BDIFF + interlocuteur SDIS | Distinction entre absence réelle d’événement et manque de collecte |
| P1 | Compléter par un fichier communal d’artificialisation seulement si l’usage exige une analyse par commune | Référent artificialisation | Profilage communal distinct ; le fichier départemental est déjà fourni et contrôlé |
| P2 | Tester géométries, frontières historiques et stabilité interversions | Référent géographie | Contrôles topologiques et référentiels complémentaires |
| P2 | Obtenir présences, moyens et délais si ces KPI sont maintenus | Groupe + SDIS 77 | Possibilité de mesurer le dispositif réel |

Les rôles sont proposés et doivent être attribués aux membres du groupe. Aucun de ces contrôles n’est déclaré réalisé tant que sa preuve n’est pas jointe.

## 11. Conclusion d’aptitude à l’usage

Les quatre sources sont complémentaires pour un entrepôt descriptif, avec des périmètres distincts. Les archives météo et les champs centraux BDIFF permettent de préparer le KPI principal sur 2024–2025, sous contrôle des dates et de la collecte. Le MOS est utilisable comme extrait forestier ; l’artificialisation fournie apporte un contexte départemental historique pour les huit départements franciliens. Les analyses géométriques exhaustives, les classements communaux fondés sur l’artificialisation et les mesures de performance opérationnelle demandent des données ou des validations supplémentaires.


