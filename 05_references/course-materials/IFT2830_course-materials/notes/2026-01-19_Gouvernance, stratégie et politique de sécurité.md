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
  - security/strategy
  - security/policy
  - security/security-measures
  - security/risk
  - security/risk/governance-link
  - security/risk/tolerance
  - security/cia
  - security/cia/confidentiality
  - security/cia/integrity
  - security/cia/availability
  - security/concepts/asset
  - security/concepts/threat
  - security/concepts/vulnerability
  - security/concepts/impact
  - security/concepts/control
---
# Gouvernance, stratégie et politique de sécurité

La sécurité s’inscrit dans la stratégie organisationnelle globale.

Elle ne se limite pas aux mesures techniques.  
Elle implique gouvernance, gestion des risques et responsabilité.

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

## 🗝 Key Concepts  

- Stratégie de sécurité 
- Analyse du risque 
- Politique de sécurité 
- Mesures de sécurité

---

## 📓 Notes

> **Summary**  
> - Stratégie de sécurité : protection, prévention, réaction, continuité et gestion de crise.
> - Analyse du risque : actifs, menaces, vulnérabilités, impacts, probabilités, priorisation des scénarios.
> - <span style="background:rgba(74, 82, 199, 0.2)">Travaux: L'énoncé du TP1 est disponible et peut être entamé dès aujourd'hui</span>
> 

### ✨ Terminology
#actif #menace #vulnerabilite #impact #probabilite #risque  
#contre-mesure #controle #gouvernance #strategie #politique  
#analyse-du-risque #gestion-du-risque #tolerance-au-risque  
#mesures-de-securite #cycle-de-securite  
  
| Terme | Définition |  
|-------|------------|  
| **Actif** | Élément ayant de la valeur pour l’organisation (données, systèmes, réputation, personnel). |  
| **Menace** | Entité ou événement susceptible de porter atteinte à un actif. |  
| **Vulnérabilité** | Faiblesse exploitable par une menace. |  
| **Impact** | Gravité des conséquences si le risque se réalise. |  
| **Probabilité** | Chance qu’une menace exploite une vulnérabilité. |  
| **Risque** | Combinaison de la probabilité qu’une menace exploite une vulnérabilité et de l’impact sur un actif. |  
| **Scénario de risque** | Situation où une menace exploite une vulnérabilité sur un actif. |  
| **Contre-mesure** | Mécanisme de protection visant à réduire la probabilité ou l’impact. |  
| **Contrôle** | Mesure technique, organisationnelle ou juridique appliquée pour maîtriser un risque. |  
| **Tolérance au risque** | Niveau de risque acceptable défini au niveau stratégique. |  
| **Gouvernance** | Cadre décisionnel encadrant la sécurité. |  
| **Stratégie de sécurité** | Plan global d’organisation de la protection. |  
| **Politique de sécurité** | Document formel définissant les règles obligatoires. |  
| **Mesure de sécurité** | Application concrète d’un contrôle. |  
| **Gestion du risque** | Processus d’identification, d’analyse, de traitement et de suivi des risques. |

---
### 🛡️La sécurité 

La sécurité des systèmes informatiques vise à protéger les valeurs informationnelles et technologiques d’une organisation.

Elle dépasse la technique.  
Elle inclut gouvernance, stratégie, politique et responsabilité.

#### 🔷 Vision stratégique de la sécurité

> [!PDF|note] [[2.gouvernance_strategie_politique.pdf#page=5&selection=0,0,0,33&color=note|2.gouvernance_strategie_politique, p.5]]
> > La vision stratégique de la sécurité 
> 
> La sécurité vise à protéger plusieurs **propriétés fondamentales** :
> 
> |Propriété|Description|
|---|---|
|**Disponibilité**|Aucun retard|
|**Intégrité / exactitude**|Aucune falsification, aucune erreur|
|**Confidentialité**|Aucune écoute illicite|
|**Pérennité**|Aucune destruction|
|**Non-répudiation / imputabilité**|Aucune contestation|
|**Authentification**|Aucun doute sur l’identité|
|**Intimité numérique (privacy)**|Protection de la sphère privée|
|**Protection des données personnelles**|Respect des contraintes légales|

**💡Important :**  
> La sécurité dépasse la CIA classique. Elle inclut aussi responsabilité, traçabilité et conformité légale. La CIA en est donc le noyau, mais pas la finalité.

---

#### 🔷 Principes de sécurité

> [!PDF|note] [[2.gouvernance_strategie_politique.pdf#page=6&selection=0,0,0,17&color=note|2.gouvernance_strategie_politique, p.6]]
> > Principes de base :
> 
> |Principe|Idée centrale|
> |---|---|
> |Vocabulaire|Langage commun|
|Volonté directoriale|Soutien de la direction|
|Proportionnalité|Coût adapté au risque|
|Cohérence|Système harmonisé|
|Simplicité|Applicable par tous|
|Dynamicité|Évolution constante|
|Continuité|Fonctionnement malgré incident|
|Évaluation|Amélioration continue|
> 

**💡Important :**  
> La sécurité est une question de compromis.

---
#### 🔷 Gouvernance

- **Définition** :
	C'est le cadre décisionnel qui définit: 
	- Les responsabilités
	- Les orientations
	- La supervision
	- Les rôles (CISO, direction, RH, utilisateurs)
- 📌 **Commentaire** :
	La gouvernance se situe au niveau stratégique supérieur. Elle décide mais ne met pas en oeuvre

##### Acteurs et responsabilités

> [!PDF|note] [[2.gouvernance_strategie_politique.pdf#page=12&selection=0,0,0,26&color=note|2.gouvernance_strategie_politique, p.12]]
> > Acteurs et responsabilités: 
> 
> - CISO (Chef de la sécurité organisationnelle) → pilotage sécurité
> - RH (Resources Humaines) → sensibilisation, gestion des accès
> - Chefs de service → application locale
> - Utilisateurs → respect des règles

---

#### 🔷 Stratégie de sécurité

- **Définition** : 
	Planification globale pour protéger l’organisation en ce qui concerne: 
	- Protection
	- Prévention
	- Organisation de la défense
	- Plans de réaction
	- Gestion de crise
	- Continuité et reprise des activités
	- Poursuites pénales si nécessaire
- 📌 **Commentaire** :
	La stratégie de sécurité accompagne la la stratégie organisationnelle Elle est :
	- Proactive
	- Réactive
	- Alignée sur la stratégie d’entreprise

> [!PDF|note] [[2.gouvernance_strategie_politique.pdf#page=3&selection=40,0,50,6&color=note|2.gouvernance_strategie_politique, p.3]]
> > S’inscrit dans démarche proactive et réactive
> 
> La stratégie permet d'anticiper les problèmes et de réagir face aux incidents de sécurité. **Étapes de réalisation d'une démarche sécuritaire**
 ![[2.gouvernance_strategie_politique.pdf#page=3&rect=585,56,957,350&color=note|2.gouvernance_strategie_politique, p.3]]

##### Axes stratégique, tactique et opérationnel

La sécurité se déploie sur **trois niveaux complémentaires**, chacun ayant un rôle distinct. 

| Axe              | Horizon     | Rôle      | Acteurs            | Résultat             |
| ---------------- | ----------- | --------- | ------------------ | -------------------- |
| **Stratégique**  | Long terme  | Décider   | Direction, CISO    | Politique, objectifs |
| **Tactique**     | Moyen terme | Organiser | Gestionnaires IT   | Plans, procédures    |
| **Opérationnel** | Court terme | Exécuter  | Admin, techniciens | Mise en œuvre        |

###### 🧭 Axe stratégique
- **Niveau**: 
	Supérieur/Décisionnel
	- Vision à long terme
	- Orientation globale
	- Définition des objectifs de sécurité
	- Détermination du niveau de tolérance au risque
	- Allocation des ressources
- **Acteurs**: 
	- Direction
	- Comité exécutif
	- Gouvernance
	- CISO (au niveau stratégique)
- **Produit** :
	- Politique de sécurité
	- Objectifs stratégiques
	- Priorités organisationnelles
- ❓ Il répond à la question :  
	**“Quel niveau de sécurité voulons-nous atteindre ?”**

###### ⚙️ Axe tactique
- **Niveau** : 
	Intermédiaire/planification.
	- Traduction de la stratégie en plans concrets
	- Choix des solutions technologiques
	- Définition des procédures
	- Organisation des mécanismes de contrôle
- **Acteurs** :
	- Responsables sécurité
	- Chefs de service
	- Architectes sécurité
	- Gestionnaires IT
- **Produit** :
	- Plans d’implémentation
	- Sélection des outils
	- Programmes de formation
	- Plans de gestion d’incident
- ❓ **Il répond à la question** :  
	**“Comment allons-nous appliquer la stratégie ?”**

###### 🛠 Axe opérationnel

- **Niveau**
	Quotidien/opérations
	- Mise en œuvre technique
	- Administration des systèmes
	- Surveillance
	- Application des règles
	- Gestion des incidents
- **Acteurs**
	- Administrateurs systèmes
	- Techniciens
	- Utilisateurs
	- SOC
- **Produit** :
	- Application réelle des mesures
	- Journalisation
	- Intervention en cas d’incident
- ❓**Il répond à la question** :  
	**“Comment la sécurité fonctionne-t-elle concrètement au quotidien ?”**

![[2.gouvernance_strategie_politique.pdf#page=7&rect=181,162,802,463&color=note|2.gouvernance_strategie_politique, p.7]]

Cycle continu : Contrôle → Évaluation → Optimisation


**💡Important** : 
> La sécurité s’articule sur trois axes : stratégique, tactique et opérationnel.  
> Le niveau stratégique définit les orientations et le niveau de sécurité visé.
> Le niveau tactique traduit ces orientations en plans concrets.
> Le niveau opérationnel met en œuvre les mesures au quotidien. L’ensemble est régi par un cycle continu d’évaluation et d’optimisation.

---

#### 🔷 Politique de sécurité

- **Définition** : 
	Document formel qui traduit la stratégie en règles concrètes. Il contient :
	- Principes
	- Règles
	- Obligations
	- Sanctions
- 📌 **Commentaire** :
	La politique de sécurité est un **outil normatif**.

---

#### 🔷 Chaîne décisionnelle en sécurité

La sécurité organisationnelle suit une logique hiérarchique :

1. Analyse du risque → identifie les priorités
2. Stratégie → définit les orientations
3. Politique → formalise les règles
4. Mesures → implémentation concrète
5. Contrôle → évaluation
6. Ajustement → amélioration continue

Cela crée un cycle :

Analyse → Décision → Formalisation → Mise en œuvre → Contrôle → Optimisation


**💡Important**: 
> Gouvernance → Décide et encadre.
> Stratégie → Planifie et organise.
> Politique → Formalise les règles.  
> Analyse du risque → Évalue les menaces et priorise les actions.

---
### ⚠️ Les risques

> Un risque est la probabilité qu’une valeur soit perdue en fonction d’une vulnérabilité liée à une menace ainsi que l'impact engendré par cette perte. 

> [!PDF|note] [[2.gouvernance_strategie_politique.pdf#page=4&selection=0,0,0,48&color=note|2.gouvernance_strategie_politique, p.4]]
> > Étapes de réalisation d’une démarche sécuritaire
> 1. Identification des actifs (valeurs)
> 2. Identification des menaces
> 3. Identification des vulnérabilités
> 4. Évaluation des impacts
> 5. Évaluation des probabilités
> 6. Priorisation des risques
> 7. Mise en place des mesures
>    
> ![[2.gouvernance_strategie_politique.pdf#page=4&rect=186,13,766,470&color=note|2.gouvernance_strategie_politique, p.4]]

---
#### 🔴 Identification des risques

##### ⚙️Risque opérationnel

>Risque affectant la capacité de l’organisation à assurer ses activités normales.
- **Impact** :
	- Interruption de service
	- Retards
	- Perte de productivité
	- Désorganisation interne
- **Lien CIA** : 
	Surtout **Disponibilité**, parfois Intégrité.
- **Exemples** :
	- Panne majeure du système ERP
	- Indisponibilité du personnel clé
	- Sabotage interne
##### 🖥️ Risque informatique

> Risque lié aux infrastructures technologiques et aux systèmes informatiques.

- **Impact** :
	- Serveurs
	- Réseaux
	- Applications
	- Bases de données
- **Lien CIA** : 
	Peut affecter les trois piliers.
- **Exemples** :
	- Attaque par ransomware
	- Exploitation d’une vulnérabilité 
	- Mauvaise configuration d’un pare-feu
##### ℹ️ Risque informationnel

> Risque portant spécifiquement sur la valeur de l’information.

- **Impact** :
	- Données sensibles
	- Propriété intellectuelle
	- Données personnelles
- **Lien CIA** : 
	Directement lié aux trois piliers, en particulier :
	- Confidentialité (fuite)
	- Intégrité (altération)
	- Disponibilité (perte ou suppression)
- **Exemples** :
	- Fuite de données
	- Altération d’un dossier médical
	- Suppression accidentelle d’archives
##### ⚖️ Risque juridique

> Risque lié au non-respect des lois, règlements ou obligations contractuelles.

- **Impact** :
	- Amendes
	- Poursuites
	- Perte de réputation
	- Sanctions réglementaires
- **Lien CIA** : 
	Souvent conséquence d’un risque informationnel ou informatique.
- **Exemples** :
	- Non-conformité à la Loi 25
	- Non-respect du RGPD
	- Défaut de notification d’une violation de données



**💡Important :** 
>**Risque informatique ≠ Risque informationnel**
>	 - Informatique = système technique
>	 - Informationnel = valeur des donnée

> **Relation entre les risques** :  
> 	- Risque informatique → peut entraîner un risque informationnel
> 	- Risque informationnel → peut entraîner un risque juridique
> 	- Risque opérationnel → peut résulter des trois autres

----
#### 🔴Analyse du risque


$$ R=P×I $$

##### Probabilité

La probabilité mesure la chance qu’un scénario se produise.

Échelle semi-objective d'évaluation de la probabilité:

| Valeur | Probabilité   |
| ------ | ------------- |
| 1      | Presque nul   |
| 2      | Peu probable  |
| 3      | Probable      |
| 4      | Très probable |

La probabilité dépend de :
1. **Capacité**
    - Savoir
    - Outils
    - Argent
2. **Opportunité**
    - Accès physique
    - Connectivité
    - Temps
3. **Motivation**
    - Gain
    - Intérêt
    - Bénéfice

##### Impact

L’impact mesure la gravité des dommages si le risque se réalise.

Échelle semi-objective d'évaluation de l'impact:

| Valeur | Impact     |
| ------ | ---------- |
| 1      | Faible     |
| 2      | Moyen      |
| 3      | Élevé      |
| 4      | Très élevé |

Exemples :
- Perte mineure → 1
- Indisponibilité de plusieurs heures → 2
- Perte financière importante → 3
- Divulgation massive de données sensibles → 4

---
#### 🔴 Interprétation du risque

Une matrice permet de classer les risques :

![[2.gouvernance_strategie_politique.pdf#page=24&rect=558,110,955,445|2.gouvernance_strategie_politique, p.24]]

- Zone rouge → traitement prioritaire
- Zone jaune → selon tolérance
- Zone verte → acceptable

Le niveau de tolérance est fixé au niveau stratégique.

---
#### 🔴 Traitement du risque

Après analyse, un risque peut être :

- Réduit (mise en place de mesures)
- Accepté (tolérance stratégique)
- Transféré (assurance, sous-traitance)
- Éliminé (arrêt de l’activité)

👉 L’analyse du risque oriente la stratégie de sécurité et la politique.



---
## ⚙️ Examples and Exercises

![[2.gouvernance_strategie_politique.pdf#page=11&rect=104,39,946,450&color=note|2.gouvernance_strategie_politique, p.11]]

1. La sécurité est l'affaire de tous: <span style="background:rgba(3, 135, 102, 0.2)">Universalité</span>
2. La notion d'attractivité selon la cible: <span style="background:rgba(3, 135, 102, 0.2)">Financier, cohérence</span>
3. La sécurité n'est jamais acquise définitivement, elle se vit au quotidien: 


![[2.activités.pdf#page=2&rect=27,36,881,412|2.activités, p.2]]






![[Pasted image 20260119204804.png]]

---

## ❓Example Exam Questions 

> **Quelle est la différence entre gouvernance et stratégie ?**
> 	 Gouvernance → cadre décisionnel et supervision.
> 	 Stratégie → planification concrète de la protection.

> **Quelle est la différence entre stratégie et politique ?**
> 	- Stratégie → vision globale.
> 	- Politique → règles formalisées.

> **Qui fixe la tolérance au risque ?**
> 	Le niveau stratégique.

> **Le niveau opérationnel décide-t-il des orientations ?**
> 	Non : Il exécute.

> **Expliquez la chaîne décisionnelle en sécurité.**
>	 Analyse du risque → Stratégie → Politique → Mesures → Contrôle → Ajustement

> **Décrivez l’axe stratégique.**
> 	- Long terme, Décisionnel
> 	- Fixe objectifs et tolérance au risque
> 	- Produit : politique et priorités

> **Décrivez l’axe tactique.**
> 	- Traduction de la stratégie en plans
> 	- Choix des solutions
> 	- Organisation des procédures

> **Décrivez l’axe opérationnel.**
> 	- Mise en œuvre quotidienne
> 	- Surveillance
> 	- Gestion des incidents

> **Pourquoi les trois axes sont-ils complémentaires ?**
>	 Parce que la décision, l’organisation et l’exécution sont distinctes mais interdépendantes.

> De quoi dépend la probabilité ?
> 	Capacité, Opportunité et Motivation

> **Quels sont les traitements possibles d’un risque ?**
> 	- Réduction
> 	- Acceptation
> 	- Transfert
> 	- Élimination

> **Expliquez la relation entre risque informatique et risque informationnel.**
> 	Risque informatique = infrastructure technique.
> 	Risque informationnel = valeur des données.
> 	Un risque informatique peut provoquer un risque informationnel.

> **Pourquoi la sécurité est-elle un compromis ?**
> 	Parce qu’elle a un coût. Elle doit être proportionnelle au risque. Elle dépend de la tolérance stratégique.

> **Pourquoi dit-on que la sécurité est un cycle continu ?**
> 	Parce que :  Contrôle → Évaluation → Optimisation
> 	Les menaces évoluent.


---

## ✅ To Review

- [ ] 

---

## 🔗 Links and Materials

- Cours 2 : Gouvernance, stratégie et politique de sécurité
  ![[2.gouvernance_strategie_politique.pdf]]
- Activité Labo 1
  ![[2.activités.pdf]]



---