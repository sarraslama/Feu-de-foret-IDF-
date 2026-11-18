# Journal des décisions

Ce journal permet de garder une trace des décisions prises après avoir comparé nos questions d’analyse avec les sources disponibles.

---

## Décision 1 — Croiser les incendies avec le Mode d’occupation du sol (MOS)

**Question concernée :**  
Q1 — Quelles sont les caractéristiques des zones les plus touchées en Seine-et-Marne ?

**Manque identifié :**  
La **BDIFF** permet d’identifier et de localiser les incendies, mais elle ne permet pas à elle seule de caractériser précisément le type de territoire touché.

**Décision :**  
Croiser les données de la **BDIFF** avec le **Mode d’occupation du sol (MOS)**.

**Pourquoi ?**  
Cela permettra de déterminer dans quels types d’espaces les incendies se produisent le plus souvent : espaces forestiers, agricoles, urbains, naturels, etc.



---

## Décision 2 — Garder l’artificialisation des sols comme source complémentaire

**Question concernée :**  
Q1 et Q4.

**Manque identifié :**  
Le MOS et la BDIFF permettent de caractériser les territoires et les incendies, mais ne permettent pas à eux seuls d'évaluer précisément la pression liée à l'urbanisation.

**Décision :**  
Conserver la source **Artificialisation des sols** dans l’analyse.

**Pourquoi ?**  
Elle permet de caractériser le niveau d’artificialisation des territoires et d’étudier les zones où les espaces urbanisés sont proches des espaces naturels ou forestiers.


---

## Décision 3 — Ajouter les données de la Météo des forêts

**Question concernée :**  
Q3 — Quelle est l’ampleur des faux positifs et des faux négatifs sous le seuil actuel de la Météo des forêts ?

**Manque identifié :**  
La **BDIFF**, le **MOS** et les données d’**Artificialisation des sols** ne permettent pas de connaître les niveaux de danger annoncés par la Météo des forêts.

**Décision :**  
Rechercher et intégrer les données historiques de la **Météo des forêts**.

**Pourquoi ?**  
Pour calculer les faux positifs et les faux négatifs, il faut comparer les niveaux de danger annoncés avec les incendies réellement observés dans la **BDIFF**.



---

## Décision 4 — Vérifier les données temporelles de la BDIFF

**Question concernée :**  
Q2 — À quelles périodes et à quels moments de la journée les départs de feux sont-ils les plus fréquents ?

**Manque identifié :**  
Pour analyser précisément les périodes et les horaires des départs de feux, il faut disposer de données temporelles suffisamment précises dans la BDIFF.

**Décision :**  
Vérifier la présence des **dates et heures** des incendies dans les données BDIFF.

**Pourquoi ?**  
Les dates permettront d’étudier les périodes de l’année où les incendies sont les plus fréquents. Si les heures sont disponibles, il sera également possible d’analyser les moments de la journée les plus concernés.

**Ce que cela coûte :**  
Du temps pour vérifier les variables disponibles et éventuellement nettoyer les données temporelles.



---

## Décision 5 — Ne pas considérer la répartition du budget comme résolue

**Question concernée :**  
Q4 — Comment répartir au mieux le budget limité ?

**Manque identifié :**  
Nous n’avons pas encore les informations sur le budget disponible, les coûts des interventions, les coûts de surveillance, les effectifs et les moyens matériels disponibles.

**Décision :**  
Utiliser les données disponibles pour identifier les **zones et périodes potentiellement prioritaires**, mais considérer la question de la répartition budgétaire comme **à compléter**.

**Pourquoi ?**  
Le croisement du **MOS**, de la **BDIFF**, de l’**Artificialisation des sols** et de la **Météo des forêts** permet d’identifier les zones et les périodes présentant des enjeux importants. Cependant, ces données ne permettent pas à elles seules de déterminer comment répartir concrètement un budget.


---

## Synthèse des décisions

| Décision | Source(s) concernée(s) | Objectif |
|---|---|---|
| **1. Croiser les incendies avec le MOS** | BDIFF + MOS | Caractériser les types de territoires touchés par les incendies. |
| **2. Conserver l’artificialisation des sols** | Artificialisation + MOS + BDIFF | Étudier la pression urbaine et les zones d’interface. |
| **3. Ajouter la Météo des forêts** | Météo des forêts + BDIFF | Évaluer les faux positifs et les faux négatifs. |
| **4. Vérifier les données temporelles** | BDIFF | Étudier les périodes et horaires des départs de feux. |
| **5. Compléter la question budgétaire** | Les 4 sources + données complémentaires | Identifier les priorités sans prétendre calculer un budget optimal. |

## Conclusion

Après confrontation des questions et des sources, les quatre sources retenues sont :

- **Mode d’occupation du sol (MOS)** ;
- **BDIFF** ;
- **Artificialisation des sols** ;
- **Météo des forêts**.

Le principal choix méthodologique consiste à utiliser la **BDIFF pour caractériser les incendies observés**, le **MOS et l’Artificialisation des sols pour caractériser les territoires touchés**, et la **Météo des forêts pour analyser les niveaux de danger et leur concordance avec les incendies**.

