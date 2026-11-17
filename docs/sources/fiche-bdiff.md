# Fiche source – BDIFF

## 1. Propriétaire et système

- **Nom de la source :** Base de Données sur les Incendies de Forêts en France (BDIFF).
- **Producteur indiqué dans les métadonnées :** Institut national de l'information géographique et forestière (IGN).
- **Système :** application nationale BDIFF, hébergée par l'IGN et alimentée par un réseau de contributeurs institutionnels.
- **Objectif :** centraliser les informations sur les incendies de forêt en France afin de suivre leur évolution et de contribuer à la prévention et à la lutte contre les incendies.

## 2. Mode d'accès et format

- **Mode d'accès :** téléchargement depuis le portail officiel BDIFF, après sélection des critères géographiques et temporels.
- **Format :** fichier CSV, téléchargé dans une archive ZIP avec des documents complémentaires.
- **Encodage :** UTF-8 recommandé pour afficher correctement les accents et les caractères spéciaux.

## 3. Grain

- **Une ligne de données correspond à un incendie.**
- Chaque incendie possède un numéro d'identification.
- Les informations sont rattachées à une commune et comprennent notamment une date de première alerte, les surfaces parcourues et les conséquences éventuelles.

## 4. Emprise géographique

- **Territoire de l'extraction étudiée :** région Île-de-France uniquement.
- Les données ont été filtrées à partir du portail BDIFF pour ne conserver que les incendies de cette région.
- La base BDIFF dans son ensemble couvre le territoire français.

## 5. Période réellement couverte par les données

- **Première année observée dans le fichier :** 2006.
- **Dernière année observée dans le fichier :** 2025.
- **Période étudiée :** 2006–2025, soit 20 années calendaires.

## 6. Date de dernière mise à jour affichée sur la fiche

- La fiche du jeu de données BDIFF sur data.gouv.fr indique une dernière mise à jour au **13 décembre 2025**.
- Cette date correspond à la mise à jour de la fiche du jeu de données et ne signifie pas nécessairement que chaque enregistrement du CSV a été actualisé à cette date.

## 7. Fréquence de mise à jour

- La collecte des données est organisée par campagnes annuelles, du 1er janvier au 31 décembre.
- Les fiches sont ensuite vérifiées et validées au cours de la période suivante, généralement de décembre à avril.
- Les données publiques sont diffusées après validation de la campagne.

## 8. Volumétrie

- **Nombre d'incendies recensés dans l'extraction :** 347, selon le décompte effectué dans le fichier.
- Le CSV contient également des lignes explicatives et une ligne d'en-têtes.
- Le fichier comporte des informations d'identification, de localisation, de date, de surfaces brûlées et de conséquences des incendies.

## 9. Clés disponibles

Les principaux champs pouvant servir à identifier les incendies ou à réaliser des jointures sont :

- `Numéro` : identifiant de l'incendie.
- `Année` : année de l'incendie.
- `Département` : code du département.
- `Code INSEE` : code de la commune.
- `Nom de la commune` : nom de la commune concernée.

Le code INSEE pourra notamment être utilisé pour joindre les données BDIFF avec d'autres sources géographiques à l'échelle communale.

## 10. Données personnelles

- Aucune donnée personnelle directement identifiable n'a été repérée dans les colonnes observées du fichier.
- Les champs concernent principalement les incendies, leur localisation, leurs surfaces et leurs conséquences.

## 11. Licence

- La fiche du jeu de données BDIFF sur data.gouv.fr indique la **Licence Ouverte / Open Licence version 2.0**.
- Les mentions légales du fichier téléchargé sont à consulter pour confirmer les conditions de réutilisation applicables à l'extraction.

## 12. Questions de l'analyse auxquelles cette source pourrait répondre

La source BDIFF peut permettre de répondre aux questions suivantes :

- Comment le nombre d'incendies a-t-il évolué en Île-de-France entre 2006 et 2025 ?
- Quels départements et quelles communes sont les plus touchés par les incendies ?
- Quelles sont les surfaces parcourues par les incendies ?
- Quels types de surfaces sont les plus touchés : forêts, surfaces agricoles ou autres espaces naturels ?
- Quelles conséquences humaines et matérielles sont recensées ?
- Existe-t-il des années ou des territoires particulièrement touchés qui nécessiteraient de renforcer les actions de prévention ?

## 13. Limites et qualité des données

L'observation du fichier CSV fait apparaître plusieurs limites :

- La colonne `Type de peuplement` est entièrement vide.
- Plusieurs autres colonnes sont partiellement renseignées, notamment celles relatives aux décès et aux bâtiments détruits.
- Certaines informations relatives aux surfaces et à leur précision sont manquantes.
- Les surfaces sont exprimées en mètres carrés (m²).
- La présence de valeurs manquantes peut limiter certaines analyses, notamment celles portant sur les conséquences humaines et matérielles.
- La BDIFF étant alimentée par un réseau de contributeurs, la documentation officielle signale que les données peuvent comporter des imprécisions ou manquer d'exhaustivité. Les résultats doivent donc être interprétés avec prudence.

## Sources documentaires

- Portail officiel BDIFF : https://bdiff.agriculture.gouv.fr/
- Aide BDIFF – Recherche et téléchargement : https://bdiff.agriculture.gouv.fr/aide/recherche
- Aide BDIFF – Généralités : https://bdiff.agriculture.gouv.fr/aide/generalites
- Fiche du jeu de données sur data.gouv.fr : https://www.data.gouv.fr/datasets/base-de-donnees-sur-les-incendies-de-forets-en-france-bdiff
