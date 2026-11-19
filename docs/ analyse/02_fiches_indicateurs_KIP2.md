# Fiches d'indicateurs — Évaluation des faux positifs et faux négatifs de la Météo des forêts

Autrice — Sarra Slama  
Version individuelle de travail — 19 novembre 2026  
Commanditaire — SDIS 77. Étude de l'ensemble de l'Île-de-France.  
Diagnostic et objectif associés — `01_diagnostic_objectif_sarra.md`

## 1. KPI principal — Taux de faux négatifs

| **Rubrique** | **Spécification** |
|---|---|
| Question et objectif | Parmi les jours-départements où un incendie est recensé, quelle part n'a pas été signalée au-dessus du seuil de danger retenu ? Réduire les situations non signalées, sans provoquer une hausse non maîtrisée des alertes. |
| Numérateur | Nombre de jours-départements avec au moins un événement BDIFF recensé et dont le niveau Météo des forêts reste sous le seuil positif choisi (FN). |
| Dénominateur | Nombre total de jours-départements avec au moins un événement BDIFF recensé (FN + VP). |
| Formule | 100 × FN / (FN + VP). Dénominateur nul → valeur non calculable. |
| Unité | Pourcentage, accompagné des effectifs FN et VP. |
| Paramètres | Seuil de danger, horizon J+1 ou J+2, date cible, département, période, définition d'un jour positif. |
| Grain | Une ligne par département et date de validité de la prévision. Un jour avec plusieurs incendies dans un même département compte une fois pour la matrice journalière. |
| Période et fréquence | Première référence calculable : période commune 2024 couverte par les deux fichiers. Actualisation à chaque nouvelle archive validée. |
| Sources et champs | BDIFF : `Département`, `Date de première alerte`, `Numéro`. Météo des forêts : `date`, `num_dep`, `niveau_j1`, `niveau_j2`. |
| Lignes utilisables | Météo : 960 lignes pour 8 départements et 120 dates de publication. BDIFF : 7 jours-départements avec événement recensé dans la fenêtre de validité comparée. |
| Situation de référence | Avec le seuil exploratoire `niveau >= 2`, FN = 7 et VP = 0, pour J+1 comme pour J+2 ; taux de faux négatifs = 100 % dans cette petite fenêtre. |
| Proxy et biais | Un événement BDIFF représente un incendie recensé, pas nécessairement tous les départs de feu. Les jours sans ligne BDIFF sont classés négatifs par convention et peuvent inclure des événements non recensés. |
| Décision | Un taux élevé appelle une revue du seuil, des codes, de la période et des données. Ne pas abaisser le seuil sans examiner simultanément les faux positifs et les moyens mobilisés. |
| Propriétaire proposé | Sarra pour le calcul et la documentation ; responsable qualité du groupe pour la relecture ; SDIS 77 pour l'interprétation opérationnelle. |

## 2. KPI complémentaire — Taux de faux positifs

| **Rubrique** | **Spécification** |
|---|---|
| Question et objectif | Parmi les jours-départements sans incendie BDIFF recensé, quelle part est signalée au-dessus du seuil retenu ? Mesurer le volume d'alertes sans événement recensé. |
| Numérateur | Nombre de jours-départements sans événement BDIFF recensé et dont le niveau Météo des forêts atteint ou dépasse le seuil positif (FP). |
| Dénominateur | Nombre total de jours-départements sans événement BDIFF recensé (FP + VN). |
| Formule | 100 × FP / (FP + VN). Dénominateur nul → valeur non calculable. |
| Unité | Pourcentage, accompagné des effectifs FP et VN. |
| Paramètres | Même seuil, horizon, période, département et grain que le KPI principal. |
| Grain | Une ligne par département et date de validité de la prévision. |
| Sources et champs | BDIFF : `Département`, `Date de première alerte`. Météo : `date`, `num_dep`, `niveau_j1`, `niveau_j2`. |
| Situation de référence | Seuil exploratoire `niveau >= 2` : J+1, FP = 2 et VN = 951, soit 0,21 % ; J+2, FP = 1 et VN = 952, soit 0,10 %. |
| Proxy et biais | Un faux positif signifie ici « niveau au-dessus du seuil sans incendie BDIFF recensé ce jour-là dans le département ». Il ne prouve pas que le danger météo était absent ni que l'alerte était inutile. |
| Décision | Examiner les faux positifs par date, département et horizon. Une réduction de ce taux ne doit pas être recherchée au prix d'une hausse excessive des faux négatifs. |
| Propriétaire proposé | Sarra pour le calcul ; responsable qualité pour la relecture ; SDIS 77 pour l'interprétation. |

## 3. Indicateurs complémentaires — Sensibilité, spécificité et précision

| **Indicateur** | **Formule** | **Interprétation** | **Résultat exploratoire J+1** | **Résultat exploratoire J+2** |
|---|---|---|---:|---:|
| Sensibilité (rappel) | 100 × VP / (VP + FN) | Part des jours avec incendie recensé détectés par le seuil. | 0 % | 0 % |
| Spécificité | 100 × VN / (VN + FP) | Part des jours sans incendie recensé correctement classés sous le seuil. | 99,79 % | 99,90 % |
| Précision | 100 × VP / (VP + FP) | Parmi les jours signalés, part avec incendie recensé. | 0 %* | 0 %* |

*La précision vaut 0 % dans le calcul exploratoire car il existe des jours signalés (FP) mais aucun vrai positif. Si aucun jour n'était signalé (VP + FP = 0), la précision serait non calculable.*

La spécificité élevée doit être interprétée avec prudence : les jours sans incendie recensé sont très majoritaires dans la base département-jour. Un indicateur élevé peut donc coexister avec une sensibilité nulle.

## 4. Matrice de confusion — Référence exploratoire 2024

**Règle provisoire** — Un jour-département est positif si au moins un événement BDIFF y est recensé. Une prévision est positive si le niveau numérique est supérieur ou égal à 2. Les codes 1 et 2 n'étant pas documentés dans le CSV, ce seuil est uniquement exploratoire.

| **J+1** | **Incendie recensé : oui** | **Incendie recensé : non** | **Total** |
|---|---:|---:|---:|
| Signal positif (`niveau >= 2`) | VP = 0 | FP = 2 | 2 |
| Signal négatif (`niveau < 2`) | FN = 7 | VN = 951 | 958 |
| **Total** | **7** | **953** | **960** |

| **J+2** | **Incendie recensé : oui** | **Incendie recensé : non** | **Total** |
|---|---:|---:|---:|
| Signal positif (`niveau >= 2`) | VP = 0 | FP = 1 | 1 |
| Signal négatif (`niveau < 2`) | FN = 7 | VN = 952 | 959 |
| **Total** | **7** | **953** | **960** |

### Test de cohérence des horizons

La date du fichier Météo des forêts est interprétée provisoirement comme la date de publication. Le niveau J+1 est donc rapproché du lendemain et le niveau J+2 du surlendemain. Les sept jours-départements avec incendie recensé dans la fenêtre comparée sont : 78 le 12 juin ; 77 les 10, 12 et 29 juillet, le 29 août, les 20 et 24 septembre 2024.

Dans l'extraction, les deux jours codés 2 en J+1 concernent le 78 et le 95 pour le 12 août ; aucun n'a d'incendie BDIFF recensé ce jour-là. En J+2, un seul jour est codé 2 : le 78 pour le 12 août, également sans incendie BDIFF recensé. Cette vérification doit être refaite après confirmation de la convention de date officielle.

## 5. Comparaison de seuils — À compléter après documentation des niveaux

| **Scénario** | **Règle de classement proposée** | **Statut** | **Données nécessaires** |
|---|---|---|---|
| S0 | Seuil officiel actuellement utilisé | Non calculable à ce stade | Documentation officielle du seuil et des codes. |
| S1 | Niveau numérique `>= 2` | Calcul exploratoire réalisé | Valeurs présentes dans `mdf_2024.csv`, mais libellés non fournis. |
| S2 | Seuil alternatif à définir après identification des niveaux disponibles | À tester | Archives pluriannuelles et signification des codes. |

Un seuil plus bas peut augmenter la sensibilité et réduire les faux négatifs, mais aussi augmenter les faux positifs. Un seuil plus haut peut réduire les faux positifs, mais manquer davantage de jours avec incendie recensé. Le choix ne doit pas reposer sur un seul taux.

## 6. Garde-fou — Volume de jours signalés

| **Rubrique** | **Spécification** |
|---|---|
| Risque visé | Réduire les faux négatifs en abaissant le seuil jusqu'à signaler une part excessive des jours-départements. |
| Mesure | Nombre et part des jours-départements classés positifs par le seuil ; afficher aussi FP et VP. |
| Formule | 100 × (VP + FP) / nombre total de jours-départements évalués. |
| Périmètre | Même période, mêmes départements et même horizon que les KPI principaux. |
| Sources et faisabilité | Calculable à partir des colonnes Météo des forêts et du calendrier département-jour. |
| Seuil et décision | Aucun plafond opérationnel n'est fourni. Le volume acceptable d'alertes doit être discuté avec le SDIS ; ne pas fixer arbitrairement une cible. |
| Limite | Le nombre de jours signalés ne mesure pas directement le coût, la mobilisation ou l'utilité d'une alerte. |
| Propriétaire proposé | Sarra pour le calcul ; SDIS 77 pour la validation de l'acceptabilité opérationnelle. |

**Détournement possible** — Présenter uniquement la baisse du taux de faux négatifs après abaissement du seuil. Le garde-fou impose de publier en parallèle le taux de faux positifs, le volume de jours signalés et la matrice complète.

## 7. Jugement RACER

| **Critère** | **Jugement** |
|---|---|
| Pertinent | Les taux répondent directement à la question de concordance entre danger annoncé et incendies recensés. Ils ne mesurent pas à eux seuls la qualité météorologique de l'indice. |
| Accepté | Définitions du jour positif, du seuil officiel et des niveaux à faire valider par le groupe et le commanditaire. |
| Crédible | Calcul reproductible si la convention J+1/J+2, le fuseau horaire, le grain département-jour, la période et les règles de dédoublonnage sont documentés. |
| Facile | Calcul techniquement accessible avec les deux CSV. L'interprétation est limitée par l'absence de documentation des codes et par une seule année météo reçue. |
| Robuste | Publier les effectifs, séparer les horizons et comparer plusieurs années et départements. Les biais de recensement BDIFF et le déséquilibre entre jours positifs et négatifs restent importants. |

## 8. Pré-mortem

Classement qualitatif proposé, sans estimation statistique des probabilités.

| **Rang** | **Cause plausible d'échec** | **Probabilité appréciée** | **Gravité** | **Protection** |
|---:|---|---|---|---|
| 1 | Les codes 1 et 2 sont interprétés à tort comme des niveaux opérationnels sans vérifier le dictionnaire. | Plausible | Élevée | Obtenir la documentation et distinguer le seuil exploratoire du seuil officiel. |
| 2 | La date de publication est rapprochée du mauvais jour de validité J+1/J+2. | Plausible | Élevée | Vérifier la convention temporelle, le fuseau et un exemple officiel avant le calcul définitif. |
| 3 | L'absence de ligne BDIFF est assimilée à une absence certaine de feu. | Plausible | Élevée | Employer « aucun incendie recensé », vérifier l'exhaustivité et documenter les limites. |
| 4 | Le seuil est choisi pour optimiser un seul indicateur, sans tenir compte des alertes supplémentaires. | Plausible | Élevée | Publier matrice, sensibilité, spécificité, précision et volume d'alertes pour chaque seuil. |
| 5 | Une seule année est utilisée pour tirer une conclusion générale sur la région. | Élevée avec les fichiers actuels | Élevée | Récupérer les archives météo 2025 et 2026 et comparer les années à périmètre constant. |

## 9. Jeu individuel proposé pour la mise en commun v0

| **Rôle** | **Indicateur** | **Situation et raison** |
|---|---|---|
| KPI principal | Taux de faux négatifs | Mesure la part des jours avec incendie recensé qui ne franchissent pas le seuil choisi. Résultat exploratoire 2024 : 100 % pour J+1 et J+2 avec `niveau >= 2`. |
| KPI complémentaire | Taux de faux positifs | Mesure la part des jours sans incendie recensé qui franchissent le seuil. Résultat exploratoire : 0,21 % en J+1 et 0,10 % en J+2. |
| Qualité de détection | Sensibilité, spécificité et précision | Évite d'interpréter un seul taux isolément et rend visible le déséquilibre des classes. |
| Garde-fou | Part des jours-départements signalés | Évite de diminuer les faux négatifs en déclenchant des alertes sur trop de jours. |
| Écarté à ce stade | Coût financier réel des faux positifs et conséquences des faux négatifs | Aucun coût de mobilisation, historique des moyens engagés ni dommage évité n'est fourni dans les bases reçues. |

Ce jeu reste une proposition individuelle. Les autres objectifs et indicateurs du groupe doivent être mis en commun avant validation du jeu collectif v0.

## 10. Limites et éléments à obtenir

- Le ZIP reçu contient `mdf_2024.csv`, mais pas les archives Météo des forêts 2025 et 2026. La comparaison pluriannuelle n'est donc pas encore réalisable avec ce ZIP.
- Les colonnes de niveaux ne contiennent que les codes 1 et 2 ; leurs libellés et leur ordre officiel doivent être documentés.
- Le seuil opérationnel actuel n'est pas identifié dans les fichiers. `niveau >= 2` est un seuil exploratoire, pas le seuil officiel.
- La convention de date et le fuseau de validité de J+1 et J+2 doivent être confirmés. Les résultats sont provisoires tant que ce point n'est pas validé.
- BDIFF recense des événements, mais l'absence d'événement dans l'extraction ne prouve pas l'absence de feu.
- La base Météo des forêts commence le 3 juin 2024, tandis que les événements BDIFF existent sur toute l'année. Seuls les jours de validité couverts par les deux sources sont comparés.
- Aucun coût financier, niveau de mobilisation ou dommage évité n'est disponible pour chiffrer les conséquences opérationnelles.
- Les fichiers MOS et artificialisation apportent du contexte territorial mais ne permettent pas de qualifier les faux positifs ou faux négatifs météorologiques.

## 11. Sources de travail

- `Incendies.csv` — extraction BDIFF fournie par le groupe : 347 événements, Île-de-France, années 2006–2025 ; filtre export indiqué dans les métadonnées : région administrative Île-de-France et type de feu F.
- `mdf_2024.csv` — archive Météo des forêts fournie dans `BD.zip` : dates, numéro de département, niveaux codés J+1 et J+2, nom du département.
- `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv` — source de contexte territorial, non utilisée dans la matrice de confusion.
- `artif-commune.csv` et `artif-departement.csv` — sources de contexte territorial, non utilisées dans le calcul des KPI.
