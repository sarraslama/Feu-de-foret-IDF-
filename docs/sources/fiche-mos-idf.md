# Fiche d’identité · Mode d’occupation du sol (MOS) Île-de-France

**Exploré par** Hassina Yasmine Kenane

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | Producteur indiqué par le portail : Institut Paris Region. Inventaire cartographique du Mode d’occupation du sol (MOS), diffusé sur le portail Open Data Île-de-France. |
| Mode d’accès et format | Téléchargement par export CSV depuis le portail régional. L’extrait étudié contient notamment les colonnes `Geo Point` et `Geo Shape`. |
| Grain | Une ligne par zone cartographiée rattachée à une commune, avec sa classification en 2021 et en 2025. Le code INSEE `78030` apparaît deux fois dans l’extrait avec des géométries distinctes. |
| Emprise géographique | Le jeu couvre l’Île-de-France. Les trois lignes étudiées portent sur deux communes des Yvelines (codes INSEE `78029` et `78030`). |
| Période réellement couverte | Deux millésimes, 2021 et 2025. Les colonnes `mos2021`, `Poste 2021`, `mos2025` et `Poste 2025` renseignent ces deux années. Dans l’extrait, les trois zones relèvent de la catégorie « Bois ou forêts » aux deux millésimes. |
| Date de dernière mise à jour affichée sur la fiche | Métadonnées modifiées le 13 avril 2026 à 16 h 43. Dernier traitement des données le 6 février 2026 à 18 h 45. |
| Fréquence de mise à jour | Deux publications par an sont annoncées pour les versions de cette livraison. De nouvelles publications peuvent réviser les millésimes antérieurs. |
| Volumétrie | Non vérifiée pour l’export filtré complet. L’extrait consulté contient trois enregistrements. |
| Clés disponibles | `insee` permet de rattacher chaque zone à une commune, puis à un département via un référentiel géographique. Plusieurs zones partagent le même code INSEE. Pour une comparaison par département, agréger les surfaces du MOS et les comptages d’incendies à leurs grains respectifs avant le rapprochement. |
| Données personnelles | Aucune donnée personnelle repérée dans les colonnes consultées. Elles décrivent les zones géographiques et leur occupation du sol. |
| Licence | Licence Ouverte v2.0 (Etalab). |
| Questions de l’analyse auxquelles la source pourrait répondre | **Question 1**, sur la concentration des départs de feu par département et par saison. Le MOS apporte une estimation de la surface classée « Bois ou forêts » par département. En combinant cette estimation avec les comptages issus de la source incendies, on peut comparer le nombre de feux recensés pour 1 000 hectares boisés, après vérification de l’unité et avec un périmètre de feux cohérent avec la catégorie retenue. |

## Limites pour l’analyse

- L’unité du champ `st_area_sh` reste non vérifiée dans la documentation consultée. Elle doit être confirmée avant de convertir les surfaces en hectares.
- La documentation indique une numérisation au 1/5 000 et une unité minimale de collecte de 500 m². Cette valeur décrit la collecte cartographique.
- Le MOS renseigne deux états de l’occupation du sol. Pour une analyse sur plusieurs saisons, indiquer le millésime de surface retenu et distinguer le comptage brut des feux du taux rapporté à la surface boisée.

## Sources consultées

- [Fiche du MOS 2021 et 2025 sur Open Data Île-de-France](https://data.iledefrance.fr/explore/dataset/mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france/)
- [Page d’export du MOS](https://data.iledefrance.fr/explore/dataset/mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france/export/)
- Extrait de trois enregistrements de l’export.
