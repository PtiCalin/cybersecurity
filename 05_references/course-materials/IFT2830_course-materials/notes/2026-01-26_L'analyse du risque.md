---
sticker: lucide//file-text
course:
  - ift2830
type: Lecture
Lecture date:
tags:
  - school
  - school/udem
  - school/udem/ift2830
  - school/udem/ift2830/h26
  - school/lecture
  - school/note
  - security
  - security/information-security
  - security/cybersecurity
  - security/governance
  - security/governance/strategic-axis
  - security/governance/tactical-axis
  - security/governance/operational-axis
  - security/risk
  - security/risk/identification
  - security/risk/analysis
  - security/risk/evaluation
  - security/risk/treatment
  - security/risk/tolerance
  - security/risk/acceptance
  - security/risk/transfer
  - security/risk/elimination
  - security/cia
  - security/cia/confidentiality
  - security/cia/integrity
  - security/cia/availability
  - security/concepts/asset  
  - security/concepts/threat
  - security/concepts/vulnerability
  - security/concepts/impact
  - security/concepts/probability 
  - security/concepts/control
  - security/concepts/scenario
  - security/concepts/likelihood
  - security/concepts/countermeasur
  - security/methodology
  - security/methodology/ebios
  - security/methodology/mehari
  - security/methodology/octave
  - security/methodology/risk-it
  - security/methodology/iso-27005
  - security/threat
  - security/threat/malware
  - security/threat/ransomware
  - security/threat/network-attack
  - security/threat/social-engineering
---
# L'analyse et facteurs risque


```table-of-contents
title: CONTENTS
style: nestedList # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
minLevel: 0 # Include headings from the specified level
maxLevel: 0 # Include headings up to the specified level
include:
exclude:
includeLinks: true # Make headings clickable
hideWhenEmpty: false # Hide TOC if no headings are found
debugInConsole: false # Print debug info in Obsidian console
```

## ⚙️ Topics

- 

---

## 📓 Notes

> **Summary**  
> Compléter la théorie sur l'analyse des risque
> Exercice en groupe de l'analyse du risque 
> 

### ✨ Terminology

| Terme                 | Définition synthétique                                       |
| --------------------- | ------------------------------------------------------------ |
| Actif                 | Élément ayant de la valeur pour l’organisation               |
| Menace                | Cause potentielle pouvant nuire à un actif                   |
| Vulnérabilité         | Faiblesse exploitable par une menace                         |
| Impact                | Gravité des conséquences si le risque se réalise             |
| Probabilité           | Chance qu’un scénario se produise                            |
| Risque                | Probabilité × Impact                                         |
| Scénario de risque    | Menace exploitant une vulnérabilité causant un impact        |
| Capacité              | Compétences et moyens de l’attaquant                         |
| Opportunité           | Conditions favorables à l’attaque                            |
| Motivation            | Intérêt ou bénéfice attendu par l’attaquant                  |
| Contre-mesure         | Action réduisant la probabilité ou l’impact                  |
| Mesure préventive     | Action empêchant la réalisation du risque                    |
| Mesure corrective     | Action réduisant les effets après incident                   |
| Traitement du risque  | Décision : réduire, accepter, transférer ou éliminer         |
| Acceptation du risque | Tolérer le risque sans action supplémentaire                 |
| Transfert du risque   | Déplacer le risque (ex. assurance, sous-traitance)           |
| Élimination du risque | Supprimer la source du risque                                |
| Matrice de risque     | Outil visuel classant les risques selon P × I                |
| EBIOS                 | Méthode stratégique basée sur scénarios et objectifs métiers |
| MEHARI                | Méthode semi-quantitative avec référentiels structurés       |
| OCTAVE                | Méthode organisationnelle basée sur auto-évaluation          |
| Risk IT               | Cadre ISACA intégrant le risque IT à la gouvernance          |
| ISO 27005             | Norme internationale de gestion du risque en SSI             |

---

### Éléments relatifs au rique

#### 💰Actifs 

Élément ayant de la valeur pour l’organisation.

Exemples :
- Serveur
- Base de données
- Réputation
- Information sensible
- Employé clé

#### 📛 Menace

Entité ou événement pouvant porter atteinte à un actif.

Peut être :
- Interne / externe
- Accidentelle / délibérée
- Naturelle / humaine

Exemples :
- Hacker
- Employé mécontent
- Incendie
- Malware

#### 😰Vulnérabilité

Faiblesse exploitable par une menace.

Exemples :
- Absence de chiffrement
- Mot de passe faible
- Wi-Fi public non sécurisé
- Système non mis à jour

#### 🌡️ Impact

Conséquence négative si le scénario se réalise.

Peut affecter :
- Confidentialité
- Intégrité
- Disponibilité
- Réputation
- Légal / financier

#### 🎬 Scénario de risque

Exploitation d’une vulnérabilité par une menace causant un impact.

Structure logique :
Menace exploite Vulnérabilité → Affecte Actif → Cause Impact

#### 🧱 Contre-mesure (parade)

Mesure visant à réduire :
- La probabilité
- L’impact
- Ou les deux

Exemples :
- Antivirus
- Pare-feu
- Chiffrement
- Sauvegardes
- Politique de mots de passe

---
### Les outils d'analyse du risque

#### Formule d'analyse du risque

> [!PDF|yellow] [[2.gouvernance_strategie_politique.pdf#page=22&selection=34,0,34,37&color=yellow|2.gouvernance_strategie_politique, p.22]]
> > R(Risque) = P(Probabilité) x I(Impact)
> 
> 

#### Tableau d'analyse du risque

| Sénario | Capacité (C) | Opportunité (O) | Motivation (M) | Probabilité (P = median(C ,O,M)) | Impact (I) | Risque(R = P x I)<br> |
| ------- | ------------ | --------------- | -------------- | -------------------------------- | ---------- | --------------------- |
| 1       |              |                 |                |                                  |            |                       |
| 2       |              |                 |                |                                  |            |                       |
| 3       |              |                 |                |                                  |            |                       |
| ...     |              |                 |                |                                  |            |                       |
| n       |              |                 |                |                                  |            |                       |


Chaque critère obtient un score de 1 à 4 

| Score | Descriptif                                |
| ----- | ----------------------------------------- |
| 1     | Risque Faible (Probabilité presque nulle) |
| 2     | Moyen (Peu probable)                      |
| 3     | Élevé (Assez probable)                    |
| 4     | Très élevé (Très probable)                |

### Méthode d'analyse

#### 1️⃣ Calcul du facteur de probabilité

> Prendre la valeur médiane de la capacité, opportunité et motivation
##### Capacité 
L’attaquant a-t-il :
- Les compétences ?
- Les outils ?
- Les ressources ?
👉 Attribuer un score de 0 (faible) à 4 (très élevée) 
##### Opportunité
A-t-il :
- Un accès physique ?
- Un accès réseau ?
- Le bon timing ?
👉 Attribuer un score de 0 (faible) à 4 (très élevée) 
##### Motivation
- Qui profite du crime ?
- Quel gain ?
- Quelle valeur stratégique ?
👉 Attribuer un score de 0 (faible) à 4 (très élevée) 

#### 2️⃣ Évaluation de l'impact

Évaluer l’impact mesure la gravité des dommages si le risque se réalise.

| Valeur | Impact     |
| ------ | ---------- |
| 1      | Faible     |
| 2      | Moyen      |
| 3      | Élevé      |
| 4      | Très élevé |

#### 3️⃣ Calcul du risque


#### 4️⃣ 




### Méthodologies formelles
#### 🔹 EBIOS
**Expression des Besoins et Identification des Objectifs de Sécurité**
- **Origine** :
	France (ANSSI)
- **Philosophie** :
	Approche **orientée objectifs métiers**.
- **Basée sur** :
	- les besoins de sécurité
	- les valeurs à protéger
	- les scénarios de menace
- **Logique** : 
	1. Identifier les biens essentiels
	2. Identifier les événements redoutés
	3. Identifier les menaces
	4. Construire des scénarios stratégiques
	5. Définir les mesures de sécurité
- **Forces** : 
	- Très structuré
	- Orienté gouvernance
	- Adapté aux environnements critiques
- **Limites** : 
	- Complexe
	- Nécessite expertise
	- Plus lourd à implémenter

#### 🔹 MEHARI
**Méthode Harmonisée d’Analyse de Risque**
- **Origine** : 
	Club de la Sécurité de l’Information Français (CLUSIF)
- **Philosophie** :
	Approche **quantitative et semi-quantitative**.
- **Basée sur** :
	- des bases de scénarios types
	- des matrices de calcul
	- des référentiels prêts à l’emploi
- **Logique** : 
	1. Analyse des actifs
	2. Identification des vulnérabilités
	3. Scénarios prédéfinis
	4. Calcul du niveau de risque
	5. Plan de traitement
- **Forces** : 
	- Méthode opérationnelle
	- Pratique
	- Modèles déjà structurés
- **Limites** : 
	- Moins stratégique qu’EBIOS
	- Peut devenir mécanique

#### 🔹 OCTAVE
**Operationally Critical Threat, Asset and Vulnerability Evaluation**
- **Origine** :
	Carnegie Mellon University (USA)
- **Philosophie** :
	Approche **organisationnelle**. Le risque est vu comme un problème stratégique lié à l’entreprise.
- **Basée sur** :
	- auto-évaluation interne.
- **Logique** : 
	1. Identifier les actifs critiques
	2. Identifier les menaces internes et externes
	3. Évaluer les vulnérabilités
	4. Développer une stratégie de protection
- **Forces** : 
	- Fortement centré sur le métier
	- Favorise la responsabilisation interne
	- Moins dépendant d’experts externes
- **Limites** : 
	- Moins technique
	- Moins adapté aux environnements très complexes


#### 🔹Risk IT (ISACA)

- **Origine** :
	ISACA (même organisme que COBIT)
- **Philosophie** :
	Approche **gouvernance IT**.
- **Basée sur** :
	- la gestion du risque informatique
	- dans la gouvernance globale de l’entreprise
	- gestion stratégique du risque IT.
- **Logique** : 
	1. Risk Governance
	2. Risk Evaluation
	3. Risk Response
- **Forces** : 
	- Aligné avec COBIT
	- Idéal pour grandes organisations
	- Vision stratégique
- **Limites** : 
	- Moins opérationnel
	- Nécessite maturité organisationnelle

#### 🔹 5️⃣ ISO 27005
Norme internationale de gestion du risque en sécurité de l’information.
- **Origine** :
	Complément de ISO 27001.
- **Philosophie** :
	Approche **normative et standardisée**.
- **Basée sur** :
	- 
- **Logique** : 
	1. Établissement du contexte
	2. Identification des risques
	3. Analyse des risques
	4. Évaluation
	5. Traitement
	6. Communication
	7. Surveillance continue
- **Forces** : 
	- Compatible avec ISO 27001
	- Universel
	- Flexible
- **Limites** : 
	- Ne fournit pas d’outils concrets
	- Doit être combiné avec une autre méthode

---

## 🏋️ Exercices

> **Quelle méthodologie est la plus adaptée à une organisation cherchant la conformité ISO 27001 ?**
> 	ISO 27005.

> **La plus stratégique orientée scénarios ?**
> 	Réponse : EBIOS.

> **La plus intégrée à la gouvernance IT ?**
> 	Réponse : Risk IT.

> **Définir les termes suivants :**
> **a) Actif**
> **b) Menace** 
> **c) Vulnérabilité**  
> **d) Scénario de risque**
> 	- **Actif** : Élément ayant de la valeur pour l’organisation.
> 	- **Menace** : Cause potentielle pouvant nuire à un actif.
> 	- **Vulnérabilité** : Faiblesse exploitable par une menace.
> 	- **Scénario de risque** : Menace exploitant une vulnérabilité causant un impact sur un actif.

> **Donner la formule du risque et expliquer chaque composante.**
> 	R = P × I
> 	- **P (Probabilité)** : chance que le scénario se produise
> 	- **I (Impact)** : gravité des conséquences

> **Quelle est la différence entre probabilité et impact ?**
> 	- La probabilité mesure la chance que l’événement se produise.
> 	- L’impact mesure la gravité si l’événement se produit.

> **Quelle méthodologie est la plus adaptée pour :**
> 	a) Organisation critique nationale ?  
> 	→ **EBIOS**
> 	b) Entreprise cherchant conformité ISO 27001 ?
> 	→ **ISO 27005**
> 	c) Grande organisation avec gouvernance IT structurée ?  
> 	→ **Risk IT**
> 	d) Organisation voulant auto-évaluation interne ? 
> 	→ **OCTAVE**

> **Comparer EBIOS et MEHARI.**
> 	- EBIOS : stratégique, orienté scénarios, gouvernance
> 	- MEHARI : plus opérationnel, matrices prêtes à l’emploi.

> **Pourquoi l’analyse du risque est-elle un processus continu ?**
> 	- Les menaces évoluent
> 	- Les vulnérabilités changent
> 	- Les actifs se transforment
> 	- Le contexte organisationnel évolue
> 	Donc réévaluation constante nécessaire.



---

## ✅ To Review

- [ ] 

---

## 🔗 Links and Materials

- Fin des diapositives du cours 2
![[2.gouvernance_strategie_politique.pdf]]
- Diapositives du cours 3 (Les Malwares)
![[3.malwares.pdf]]

- Activités du cours 3
![[3.activités.pdf]]

- Normes de ## Management de la sécurité de l’information ISO : [ISO - La famille ISO/IEC 27000 — Management de la sécurité de l’information](https://www.iso.org/fr/standard/iso-iec-27000-family


---