# Indicateurs de Performance (KPI) — Projet SDIS 77

## Qu'est-ce qu'un KPI ?

Un **KPI** (*Key Performance Indicator*, ou indicateur clé de performance) est une mesure chiffrée qui permet de vérifier si un objectif précis est atteint et d'aider à la prise de décision.  
Dans le cadre de notre projet pour le **SDIS 77**, un KPI permet par exemple de suivre si l'allocation des moyens sur les **10 communes les plus vulnérables** réduit bien le nombre de feux de forêt majeurs ($\ge 1\text{ ha}$) et améliore les délais d'intervention.

---

## 📋 Fiches d'indicateurs — Jeu v0 (SDIS 77)

### 1. Fiche KPI principal : Nombre de feux majeurs ($\ge 1\text{ ha}$) en zones prioritaires

* **Objectif :** Réduire de **10 %** les feux $\ge 1\text{ ha}$ ($10\,000\text{ m}^2$) dans les 10 communes les plus touchées du 77 (`215 feux sur 293` ; `29 feux >= 1 ha sur 37`) d'ici le **30 septembre 2027**.
* **Formule :** 
  $$\text{Nombre de feux avec } \texttt{Surface parcourue (m2)} \ge 10\,000 \text{ dans les 10 communes cibles}$$
  *(accompagné du `%` d'évolution par rapport à la période de référence)*
* **Paramètres :** 
  * Périmètre : 10 communes cibles du 77
  * Seuil : $10\,000\text{ m}^2$ ($1\text{ ha}$)
  * Fréquence : Suivi mensuel
* **Source exacte :** `Incendies.csv` (`Département`, `Code INSEE`, `Année`, `Surface parcourue (m2)`, `Précision des surfaces`), croisé avec `mos-occupation-du-sol-2025-and-2021-en-79-postes-de-la-region-ile-de-france.csv` et `artif-commune.csv`.
* **Faisabilité :** ✅ OK dans `Incendies.csv` (`37` feux $\ge 1\text{ ha}$ dans le 77, dont `29` dans les 10 communes cibles).
* **Proxy et biais :** `Incendies.csv` remplace les bilans internes SDIS 77 ; la majorité des surfaces sont estimées (souvent arrondies à $10\,000\text{ m}^2$) et les effectifs annuels sont faibles (variation forte d'une année sur l'autre).

#### Critères RACER
* **R**elevant : Mesure directement l'impact des grands incendies sur les zones cibles.
* **A**ccepted : Le seuil d'1 hectare est clair et parlant pour le pilotage opérationnel.
* **C**redible : Appuyé sur 14 ans de données (`2012–2025`) et les codes INSEE.
* **E**asy : Calcul direct à partir du CSV des incendies.
* **R**obust : À lire avec une moyenne pluriannuelle pour éviter l'effet d'un seul feu.

---

### 2. Garde-fou : Taux de jours d'alerte sans feu en zone prioritaire

* **Formule :** 
  $$\left( \frac{\text{Jours d'alerte MDF activés sans feu recensé}}{\text{Total jours d'alerte MDF activés}} \right) \times 100$$
  *(en suivant également les feux $\ge 1\text{ ha}$ hors des 10 communes)*
* **Source :** `mdf_2024.csv`, `mdf_2025.csv`, `mdf_2026.csv` (`date`, `num_dep`, `niveau_j1`) + `Incendies.csv`.
* **Pourquoi il sert :** Empêche de faire baisser le KPI principal en gaspillant le budget sur trop d'alertes à vide ou en oubliant le reste du département.

---

### 3. Pre-mortem (3 risques d'échec)

1. **Mauvais ciblage météo/saison :** Se baser uniquement sur le seuil MDF fait rater des feux à niveau bas ou au printemps (`50` feux en avril) et déclenche beaucoup de jours sans feu.  
   >  **Garde-fou :** Croiser l'indice MDF avec les 10 communes cibles et le créneau `12h–18h` (`59 %` des feux).
2. **Données estimées et petits chiffres :** Quelques feux estimés autour de $1\text{ ha}$ peuvent faire bouger le score.  
   >  **Garde-fou :** Comparer à une moyenne pluriannuelle et suivre aussi les départs maîtrisés $< 1\,000\text{ m}^2$.
3. **Oubli hors zones cibles :** Concentrer tous les moyens sur les 10 communes laisse d'autres secteurs exposés (`8` des `37` feux $\ge 1\text{ ha}$ du 77 sont hors top 10).  
   >  **Garde-fou :** Garder une réserve mobile et surveiller la part de feux majeurs hors top 10.

---

### 4. Rôles du jeu d'indicateurs (v0)

| Indicateur | Rôle | Décision / Raison |
| :--- | :--- | :--- |
| **Feux majeurs ($\ge 1\text{ ha}$) en zones cibles** | **KPI principal** | Décider où concentrer les moyens pour atteindre `-10 %`. |
| **Couverture préventive sur créneaux à risque** | **KPI secondaire** | Vérifier que les patrouilles/vigies sont bien là au bon moment. |
| **Délai médian de première présentation** | **KPI secondaire** | Vérifier l'objectif de `-15 %` de délai d'intervention. |
| **Jours d'alerte sans feu / feux hors top 10** | **Garde-fou** | Éviter le surcoût budgétaire et l'abandon du reste du 77. |
| **Nombre de jours à indice MDF $\ge 2$ ou $3$** | **Contexte** | Expliquer une année plus ou moins sèche sans piloter la météo. |
| **Corrélation température / nombre de feux** | **Écarté** | Ne change aucune décision : la météo est déjà dans l'indice MDF. |
