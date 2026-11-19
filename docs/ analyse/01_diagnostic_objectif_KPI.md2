# Diagnostic et objectif SMART — Évaluation des faux positifs et faux négatifs de la Météo des forêts

Autrice — Sarra Slama  
Version individuelle de travail — 19 novembre 2026  
Commanditaire — SDIS 77  
Périmètre d'étude — Ensemble de l'Île-de-France (75, 77, 78, 91, 92, 93, 94 et 95), avec restitution départementale et lecture particulière du 77.

## 1. Diagnostic stratégique

| **Niveau** | **Formulation** | **Statut et justification** |
|---|---|---|
| Stratégie | Améliorer l'aide à la décision pour la prévention et la préparation opérationnelle face au risque de feux de forêt en Île-de-France. | Orientation cohérente avec la commande du projet. |
| Enjeu | Un niveau de danger trop souvent élevé sans incendie recensé peut conduire à mobiliser inutilement des moyens. À l'inverse, un niveau faible ou modéré lorsqu'un incendie est recensé peut conduire à sous-estimer certaines situations. | Enjeu analytique. Les conséquences opérationnelles et les coûts réels doivent être confirmés avec le SDIS. |
| Objectif | Mesurer la concordance entre les niveaux de danger de Météo des forêts et les journées où un incendie est recensé, puis comparer plusieurs seuils de déclenchement. | Proposition à valider. Les niveaux, leur signification et le seuil opérationnel actuellement utilisé doivent être confirmés. |
| Action | Croiser les archives Météo des forêts avec les événements BDIFF par département et date, calculer les indicateurs de classification et tester des seuils alternatifs. | Action analytique proposée. Elle ne remplace pas la validation opérationnelle du SDIS ou de Météo-France. |

## 2. Hypothèse et verdict

**Hypothèse initiale** — Le seuil actuel de la Météo des forêts pourrait produire des faux positifs (niveau de danger élevé sans incendie recensé) et des faux négatifs (incendie recensé alors que le niveau de danger reste sous le seuil). Une comparaison de plusieurs seuils pourrait améliorer l'équilibre entre détection des journées avec incendie et limitation des alertes sans événement recensé.

**Pièces de départ** — Le fichier `mdf_2024.csv` contient les niveaux codés J+1 et J+2 par département et date. Le fichier `Incendies.csv` contient 347 événements BDIFF en Île-de-France sur 2006–2025. Pour l'année 2024, l'extraction comporte 11 événements, dont 7 entre le 4 juin et le 30 septembre, période couverte par les dates de prévision exploitables du fichier Météo des forêts.

**Confirmation attendue** — Les journées avec incendie recensé sont majoritairement classées au-dessus du seuil choisi, tandis que les journées sans incendie recensé sont majoritairement sous ce seuil. Le résultat doit rester interprétable par département et ne pas dépendre d'un seul choix de seuil.

**Infirmation attendue** — Une part importante des journées avec incendie recensé reste sous le seuil, ou un seuil plus sensible provoque un volume d'alertes sans événement recensé trop important.

**Résultat exploratoire sur les fichiers reçus** — Le fichier Météo des forêts fourni dans l'archive ne contient que `mdf_2024.csv`. Il couvre 120 dates de publication, du 3 juin au 30 septembre 2024, pour chacun des huit départements, soit 960 lignes. Les colonnes `niveau_j1` et `niveau_j2` ne prennent que les valeurs codées 1 et 2. En retenant provisoirement le niveau codé 2 ou plus comme signal positif, aucun des 7 jours-départements avec incendie BDIFF recensé pendant la fenêtre de comparaison n'est détecté : J+1 donne 0 vrai positif, 2 faux positifs, 7 faux négatifs et 951 vrais négatifs ; J+2 donne 0 vrai positif, 1 faux positif, 7 faux négatifs et 952 vrais négatifs.

**Verdict provisoire** — Avec les seules données reçues et le seuil exploratoire `niveau >= 2`, les deux horizons ne détectent aucun des sept jours-départements avec incendie recensé. Ce résultat ne permet pas de conclure que le dispositif officiel produit 100 % de faux négatifs : la signification des codes 1 et 2, le seuil opérationnel officiel, la convention exacte de date J+1/J+2 et l'exhaustivité des événements BDIFF doivent être confirmés. Le résultat est limité à 2024 et ne constitue pas une évaluation robuste du seuil actuel.

| **Horizon** | **Jours-départements avec incendie recensé** | **Vrais positifs** | **Faux positifs** | **Faux négatifs** | **Vrais négatifs** |
|---|---:|---:|---:|---:|---:|
| J+1 | 7 | 0 | 2 | 7 | 951 |
| J+2 | 7 | 0 | 1 | 7 | 952 |

Les résultats sont calculés au grain département-jour. Plusieurs incendies dans un même département le même jour compteraient comme un seul jour positif pour la matrice ; aucun doublon de ce type n'a été observé dans les sept jours retenus. Un jour sans événement BDIFF est appelé « sans incendie recensé », et non « absence certaine de feu ».

## 3. De l'action à l'objectif SMART

1. **Action** — Évaluer la capacité des niveaux de danger Météo des forêts à signaler les jours-départements où un incendie est recensé en Île-de-France.
2. **Objectif** — Quantifier les faux positifs et les faux négatifs et comparer plusieurs seuils de classement, séparément pour J+1 et J+2.
3. **Objectif SMART proposé** — D'ici au 11 décembre 2026, produire une évaluation reproductible de la concordance entre les niveaux Météo des forêts et les événements BDIFF sur la période commune disponible, pour les huit départements d'Île-de-France, en calculant les taux de faux positifs et de faux négatifs, la sensibilité, la spécificité et la précision pour J+1 et J+2, puis en comparant au moins deux seuils documentés. La validation du seuil opérationnel et l'extension à plusieurs années dépendront de l'obtention des archives et de la documentation manquantes.

| **Critère** | **Spécification** |
|---|---|
| Spécifique | Évaluer la classification des journées par département à partir du niveau de danger prévu par Météo des forêts et de la présence d'au moins un événement BDIFF recensé. Le périmètre géographique couvre les huit départements d'Île-de-France. |
| Mesurable | KPI principaux : taux de faux positifs et taux de faux négatifs. KPI complémentaires : sensibilité, spécificité et précision. Afficher systématiquement les effectifs VP, FP, FN et VN. |
| Atteignable | Les fichiers reçus permettent un premier calcul exploratoire sur 2024. Une évaluation du seuil officiel exige le dictionnaire des codes, la documentation de la date de prévision et la confirmation du seuil utilisé. |
| Réaliste | Limiter les conclusions à la période commune, distinguer J+1 et J+2, documenter les données manquantes et ne pas assimiler l'absence de ligne BDIFF à une absence certaine de feu. |
| Temporel | Première analyse et restitution méthodologique au 11 décembre 2026, conformément au calendrier du projet. Extension pluriannuelle après réception des archives complémentaires. |

**État de validation** — Objectif SMART proposé. Le seuil officiel, la correspondance des codes numériques aux niveaux de danger et la période d'évaluation pluriannuelle restent à confirmer. Les fichiers disponibles ne permettent pas encore une conclusion définitive sur la performance du dispositif.

## 4. Situation de référence et faisabilité

- **Périmètre Météo des forêts reçu** — `mdf_2024.csv`, du 3 juin au 30 septembre 2024, 120 dates × 8 départements = 960 lignes.
- **Départements couverts** — 75, 77, 78, 91, 92, 93, 94 et 95, avec 120 lignes par département.
- **Valeurs observées** — `niveau_j1` et `niveau_j2` prennent uniquement les valeurs codées 1 et 2 dans l'extraction reçue. Les libellés correspondants ne figurent pas dans le CSV.
- **BDIFF** — `Incendies.csv` comporte 347 événements sur 2006–2025 pour l'Île-de-France. Onze événements sont datés de 2024 ; sept se situent entre le 4 juin et le 30 septembre.
- **Jours positifs de référence** — 7 jours-départements avec au moins un événement BDIFF recensé pendant la fenêtre comparée : un dans le 78 et six dans le 77.
- **Alignement temporel utilisé pour le calcul exploratoire** — La date de publication Météo des forêts est interprétée comme la date d'émission ; J+1 est rapproché du lendemain et J+2 du surlendemain. Cette convention doit être vérifiée dans la documentation officielle avant validation.
- **Seuil exploratoire** — `niveau >= 2`. Il s'agit d'un seuil numérique provisoire, pas d'une affirmation sur le seuil officiel ni sur le sens du niveau 2.
- **Données complémentaires** — L'archive contient également des fichiers MOS et artificialisation. Ils peuvent contextualiser le territoire, mais ne sont pas nécessaires au calcul de la matrice de confusion.

La comparaison est limitée à 2024 car l'archive fournie contient uniquement `mdf_2024.csv`. Il faut récupérer les archives Météo des forêts 2025 et 2026 si elles existent dans le jeu collectif, et vérifier que les périodes BDIFF correspondantes sont complètes. Les périodes doivent être fixées avant tout calcul comparatif.

## 5. Test de cohérence stratégique

**Comment améliorer le KPI sans améliorer réellement la détection ?** Abaisser le seuil peut augmenter la sensibilité, mais également le nombre de faux positifs. À l'inverse, relever le seuil peut réduire les alertes sans événement recensé tout en augmentant les faux négatifs. Il ne faut donc pas sélectionner un seuil uniquement parce qu'il améliore un indicateur isolé.

Pour éviter cette dérive :
- comparer les seuils sur la même période, les mêmes départements et le même grain département-jour ;
- publier les effectifs VP, FP, FN et VN avec chaque taux ;
- calculer séparément J+1 et J+2 ;
- conserver une définition stable d'un jour positif ;
- ne pas interpréter un jour sans événement BDIFF comme une absence certaine de feu ;
- faire valider les seuils et les conséquences opérationnelles par le SDIS et les interlocuteurs compétents.

**Risque résiduel** — La Météo des forêts est un indicateur de danger, pas une prédiction certaine d'un départ de feu. La présence d'un incendie dépend aussi de facteurs humains, locaux et accidentels. La matrice mesure une concordance avec les événements recensés, pas la qualité intrinsèque de toute la chaîne de prévision ni l'efficacité des interventions.

## 6. Articulation avec le livrable de séance 2

La fiche des indicateurs figure dans `02_fiches_indicateurs_sarra.md`. Ce document constitue la proposition individuelle à mettre en commun avec les travaux des autres membres. Les seuils retenus, les règles de comparaison et le jeu collectif v0 restent à valider en groupe.
