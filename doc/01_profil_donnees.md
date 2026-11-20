# Qualité, complétude des données 

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

