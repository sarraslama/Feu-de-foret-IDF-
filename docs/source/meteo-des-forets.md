# La Météo des forêts

## 1. Propriétaire et système

**Nom de la source :** La Météo des forêts  
**Producteur :** Météo-France  

**Système :** dispositif national destiné à sensibiliser la population aux risques d’incendie et à mieux protéger les forêts et la végétation.

**Objectif :** informer sur les conditions météorologiques susceptibles de favoriser les départs et la propagation des feux de forêt.

**Fonctionnement :** Météo-France publie quotidiennement des cartes indiquant le niveau de danger d'incendie par département. L’évaluation prend notamment en compte les conditions météorologiques, la sécheresse de la végétation et les caractéristiques du territoire.

---

## 2. Mode d’accès et format

**Mode d’accès :**
- Consultation sur le site officiel de Météo-France.
- Téléchargement et exploitation des données publiques via la plateforme `meteo.data.gouv.fr`.
- Les données publiques de Météo-France sont accessibles gratuitement depuis le **1er janvier 2024**.

**Site officiel :**  
https://meteofrance.com/meteo-des-forets

**Plateforme de données :**  
https://meteo.data.gouv.fr/

Les données de la Météo des forêts sont également consultables et exploitables en temps réel pendant la période de diffusion du dispositif.

---

## 3. Grain des données

Chaque observation correspond au **niveau de danger d’incendie prévu pour un département et une date donnée**.

Le niveau de danger est réparti en quatre catégories :

-  **Faible**
-  **Modéré**
-  **Élevé**
-  **Très élevé**

Les informations sont produites pour deux échéances :

- **Le lendemain**
- **Le surlendemain**

Le niveau de danger est donc défini pour chaque **département et chaque jour de prévision**.

---

## 4. Emprise géographique

Le dispositif couvre :

- l’ensemble de la **France métropolitaine** ;
- la **Corse** ;
- l’ensemble des départements concernés par le risque d’incendie.

Les informations sont présentées **département par département**. Chaque département dispose ainsi de son propre niveau de danger.

Ces données permettent notamment de :

- comparer les niveaux de risque entre départements ;
- analyser les différences entre régions ;
- étudier spécifiquement les territoires de l’Île-de-France.

La Seine-et-Marne est donc directement concernée par cette source.

---

## 5. Période réellement couverte par les données

- Le dispositif **Météo des forêts** a été lancé en **2023**.
- Il est principalement diffusé pendant la période où le risque d’incendie est le plus important.
- En **2026**, le dispositif est disponible du **28 mai au 30 septembre**.
- Les cartes présentent les niveaux de danger prévus pour les **deux jours à venir**.

La période réellement couverte peut cependant varier selon le fichier téléchargé depuis `meteo.data.gouv.fr`.

> **Point de vigilance :** avant toute analyse, il est nécessaire de vérifier les dates effectivement présentes dans le fichier utilisé.

---

## 6. Date de dernière mise à jour

La Météo des forêts est mise à jour quotidiennement pendant sa période de diffusion.

Les cartes sont publiées chaque jour à **17 h**.

Il faut distinguer :

- la **date de publication** d’une prévision ;
- la **date de prévision** à laquelle le niveau de danger s’applique ;
- la **date de dernière mise à jour** du jeu de données disponible sur `meteo.data.gouv.fr`.

Ces trois informations ne correspondent pas nécessairement à la même date.

---

## 7. Fréquence de mise à jour

**Fréquence : quotidienne** pendant la période de diffusion.

Chaque publication présente deux niveaux de danger :

1. le niveau prévu pour **le lendemain** ;
2. le niveau prévu pour **le surlendemain**.

Les niveaux de danger sont réévalués en fonction des nouvelles prévisions météorologiques et des informations disponibles sur l’état de la végétation.

Le dispositif fonctionne principalement **de la fin du printemps au début de l’automne**.

---

## 8. Volumétrie

La volumétrie dépend :

- de la période téléchargée ;
- du nombre de départements concernés ;
- du périmètre géographique retenu ;
- du format du fichier utilisé.

Chaque département possède un niveau de danger pour chacune des deux échéances de prévision.

Les données peuvent donc être utilisées pour constituer un **historique quotidien des niveaux de danger**.

> **À compléter :** le nombre exact d’enregistrements devra être déterminé à partir du fichier téléchargé depuis `meteo.data.gouv.fr`.

---

## 9. Clés et variables disponibles

Les principaux champs pouvant être utilisés pour identifier les observations et effectuer des jointures sont notamment :

| Champ | Description |
|---|---|
| **Code département** | Identifiant du département concerné |
| **Nom du département** | Nom du territoire associé au niveau de danger |
| **Date de prévision** | Date à laquelle le niveau de danger s’applique |
| **Date de diffusion** | Date à laquelle la prévision est publiée |
| **Niveau de danger** | Catégorie de danger attribuée au département |
| **Échéance de prévision** | Indique s’il s’agit du lendemain ou du surlendemain |

Ces variables pourront notamment être utilisées pour croiser la Météo des forêts avec les données d’interventions du **SDIS 77 / BDIFF**.

---

## 10. Données personnelles

La source ne contient pas de données personnelles directement identifiables.

Les informations concernent principalement :

- les conditions météorologiques ;
- les niveaux de danger ;
- les territoires concernés.

Les données sont produites à une échelle **départementale** et ne comportent pas, par nature, d’informations nominatives sur les habitants.

---

## 11. Licence et accessibilité

Les données publiques de Météo-France sont accessibles gratuitement depuis le **1er janvier 2024**.

Elles sont diffusées notamment via la plateforme :

https://meteo.data.gouv.fr/

Pour l'analyse, il est nécessaire de vérifier la licence et les éventuelles conditions d'utilisation associées au jeu de données effectivement téléchargé.

---

## 12. Questions d’analyse auxquelles la source peut contribuer

La Météo des forêts peut contribuer à répondre aux questions suivantes :

- Comment évolue le niveau de danger des feux de forêt en Île-de-France au cours de la période estivale ?
- Quels départements franciliens présentent les niveaux de danger les plus élevés ?
- Quelles sont les périodes de l’année où les conditions sont les plus favorables aux incendies ?
- Quelles périodes nécessitent un renforcement des actions de prévention et de surveillance ?
- Dans quelle mesure le niveau de danger annoncé est-il associé aux interventions réellement observées ?

La dernière question nécessite toutefois de **croiser cette source avec les données réelles de départs de feux**, notamment les données BDIFF.

---

## 13. Limites et qualité des données

La Météo des forêts présente plusieurs limites importantes :

- Les données correspondent à des **niveaux de danger prévus** et non à des incendies réellement observés.
- La source ne permet pas de connaître directement les feux en cours.
- Un niveau de danger **faible** ne signifie pas qu’aucun incendie ne peut se déclarer.
- Un niveau de danger **élevé ou très élevé** ne signifie pas qu’un incendie va nécessairement se produire.
- Le niveau de danger ne permet donc pas, à lui seul, de mesurer les faux positifs et les faux négatifs.
- Pour évaluer la pertinence du seuil d’alerte, il est nécessaire de comparer les prévisions avec les **interventions réellement observées**.

### Utilisation dans notre analyse

Dans le cadre de notre étude sur le **SDIS 77**, cette source sera principalement utilisée pour :

1. récupérer les niveaux de danger quotidiens ;
2. isoler les données concernant la Seine-et-Marne ;
3. croiser ces informations avec les dates et heures des interventions ;
4. comparer les niveaux de danger aux feux réellement observés ;
5. calculer les indicateurs permettant d'évaluer les **faux positifs et les faux négatifs** ;
6. identifier les périodes nécessitant potentiellement un renforcement des moyens de surveillance et de prévention.

---

## 14. Sources documentaires

- **Météo-France — La Météo des forêts**  
  https://meteofrance.com/meteo-des-forets

- **Météo-France — La Météo des forêts : s’informer sur le danger de feux**  
  https://meteofrance.com/actualites/la-meteo-des-forets-sinformer-sur-le-danger-de-feux

- **Plateforme des données publiques de Météo-France**  
  https://meteo.data.gouv.fr/

- **Météo-France — 10 questions pour comprendre la Météo des forêts**  
  https://meteofrance.com/sites/meteofrance.com/files/files/editorial/10-questions-pour-comprendre-meteo-des-forets_0.pdf

- **Météo-France — Dossier de presse Été 2026**  
  https://meteofrance.com/sites/default/files/files/editorial/DP-ete-2026-meteo-france.pdf
