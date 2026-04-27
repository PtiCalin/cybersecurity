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
  - security/cia
  - security/cia/confidentiality
  - security/cia/integrity
  - security/cia/availability
  - security/properties
  - security/properties/accessibility
  - security/properties/authenticity
  - security/properties/veracity
  - security/properties/traceability
  - security/properties/imputability
  - security/properties/non-repudiation
  - security/properties/perennity
  - security/network-security
  - security/application-security
  - security/physical-security
  - security/operational-security
  - security/cryptography
  - security/malware
  - security/threat
  - security/defense-in-depth
  - security/governance
  - security/strategy
  - security/policy
---
# Introductions et Généralités


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

- Objectifs et domaines d'application de la sécurité informatique 
- Gouvernance, stratégie et politique de sécurité
- Malwares
- Techniques d'attaque sur les réseaux informatiques
- La cryptographie et les protocoles sécurisés
- Les dispositifs de protection des réseaux informatiques
- La sécurités des réseaux sans fil
- La sécurité des applications et des contenus 

---

## 📓 Notes

> **Summary**  
> Présentation du déroulement du cours. 
> Objectifs et domaines d’application de la sécurité informatique

### ✨ Terminology
#accessibility #availability #perennity #integrity #authenticity #veracity #confidentiality #traceability #imputability #non-repudiation

---

## 🗨️ Topics

### 0. Déroulement du cours

Cours d’introduction portant sur les fondements de la sécurité informatique, combinant théorie, démonstrations pratiques et participation active des étudiants.

#### 💡Sujets à l'étude

- Objectifs et domaines d'application de la sécurité informatique 
- Gouvernance, stratégie et politique de sécurité
- Malwares
- Techniques d'attaque sur les réseaux informatiques
- La cryptographie et les protocoles sécurisés
- Les dispositifs de protection des réseaux informatiques
- La sécurités des réseaux sans fil
- La sécurité des applications et des contenus 

#### 🎓 Format pédagogique

- **Exposés magistraux**  
    Présentation des concepts fondamentaux, modèles, menaces et mécanismes de sécurité.
- **Démonstrations pratiques**  
    Réalisées lorsque pertinent (outils, attaques, protections, analyses).
- **Participation étudiante encouragée**  
    Discussions, questions, interactions en classe.
- **Matériel pédagogique**  
    Mis à jour progressivement sur **StudiuM**.

#### 📊 Modalités des évaluation

| Évaluation        | Pondération          |
| ----------------- | -------------------- |
| Examen Intra      | <center>25%</center> |
| Examen Final      | <center>35%</center> |
| Travaux pratiques | <center>40%</center> |
- Examens **écrits**, **sans documentation permise**.
- Les **TP sont remis via StudiuM**.
- Les énoncés des TP sont publiés au fur et à mesure.

---

### 1. 🛡️Objectifs et domaines d’application de la sécurité informatique

> La sécurité informatique couvre plusieurs champs complémentaires. Ensemble, ils forment une vision globale permettant de protéger **l’information**, **les systèmes**, **les réseaux**, **les applications**, **les infrastructures physiques** et **les opérations**.

#### 1.1. 🥅 Objectifs de sécurité

🔐 Modèle fondamental CIA
1. **(C) Confidentiality // [[Confidentialité]]** : 
	Protection des données contre toute **divulgation non autorisée**. Repose sur le contrôle d’accès, le chiffrement et la gestion des permissions.
2. **(I) Integrity // [[Intégrité]]** : 
	Assurance que les données, traitements ou systèmes **n’ont pas été altérés**, détruits ou modifiés de manière non autorisée, intentionnelle ou accidentelle.
3. **(A) Availability //  [[Disponibilité]]** : 
	Propriété garantissant qu’un service, un système ou une donnée est **opérationnel et utilisable** au moment où il est requis. Inclut la résilience, la redondance et la continuité de service. **Peut être calculé en terme du % de temps où un système est accessible à ses utilisateurs.**

**Critères de sécurité**
- [[Accessibilité]] : Capacité pour les utilisateurs autorisés d’accéder aux ressources (systèmes, données, services) **sans obstacles inutiles** et avec des **temps de réponse acceptables**. 
- [[Pérennité]] : Capacité d’une information ou d’un système à **demeurer valide, exploitable et durable dans le temps**, malgré l’évolution technologique, les incidents ou l’obsolescence.
- [[Authenticité]] : Garantie qu’une entité (utilisateur, système, message) est **bien celle qu’elle prétend être**. Repose sur l’ #identification et l’ #authentification
- [[Véracité]] : Assurance que l’information est **exacte, fiable et conforme à la réalité**, sans falsification ni erreur.
- [[Traçabilité]] : Capacité à **suivre la trace numérique** laissée par les actions, événements ou transactions afin de comprendre qui a fait quoi, quand et comment.
- [[Imputabilité]] : Possibilité d’attribuer une action ou un événement à une **entité spécifique** (personne, système, processus). Nécessaire pour la responsabilité et l’audit.
- [[Non-Répudiation]] : Propriété empêchant une entité de nier avoir réalisé une action, envoyé un message ou effectué une transaction. Assure la preuve d’origine et la preuve de réception.

	![[Pasted image 20260112223530.png]]
	
	Confidentialité ≠ Authenticité ≠ Non-répudiation
	
	Exemple :
	- Un message peut être authentique mais non confidentiel.
	- Un message peut être confidentiel mais non véridique.
	- Une signature numérique assure authenticité + non-répudiation, mais pas forcément confidentialité.


#### 1.2. 📲 Domaines d’application de la sécurité informatique

##### 1.2.1.🔐 Cybersécurité

La cybersécurité concerne la protection des environnements **connectés à Internet** et accessibles via le **cyberespace**.

- Porte sur les systèmes, réseaux, données et services exposés en ligne.
- Vise à contrer les **cyberattaques** (malwares, phishing, DDoS, exploitation de vulnérabilités, etc.).
- Impacte directement les individus, les organisations et les États.
- Reflète les enjeux politiques, économiques et sociaux du numérique.

##### 1.2.2.🗄️ Sécurité de l’information

Objectif : protéger **l’information** elle-même, peu importe son support ou son emplacement.

- Compréhension du rôle stratégique de l’information.
- Classification des données selon leur sensibilité (publique, privée, confidentielle, sensible).
- Protection de l’intégrité, de la pérennité et de la confidentialité des données.
- Respect de la **vie privée** et des données personnelles (privacy).

##### 1.2.3.🧩 Sécurité logique et applicative

Concerne les mécanismes logiciels assurant le bon fonctionnement des programmes et la protection des données.

- Qualité du développement logiciel et des tests de sécurité.
- Intégration correcte de la **cryptographie** (confidentialité, intégrité).
- Contrôles d’accès, authentification, gestion des permissions.
- Détection des logiciels malveillants et des intrusions.
- Sauvegardes, redondance, dimensionnement adéquat.
- Sécurité des progiciels et validation des applications.

##### 1.2.4.🌐 Sécurité des réseaux

Assure une connectivité fiable et sécurisée entre les systèmes.

- Protection des infrastructures de télécommunication.
- Sécurisation des accès réseau et du transport des données.
- Utilisation de plateformes matérielles et logicielles sécurisées.
- Gestion de réseau robuste et surveillance continue.
- Approche de **défense en profondeur** :
	- pare-feu, DMZ, VPN, antivirus, gestion des correctifs, politiques d’accès, etc.
	- La sécurité dépend du **maillon le plus faible**.

##### 1.2.5.🛠️ Sécurité de l’exploitation

Garantit le bon fonctionnement opérationnel des systèmes informatiques.

- Gestion du parc informatique et des configurations.
- Gestion des mises à jour et des correctifs.
- Gestion des incidents et suivi jusqu’à résolution.
- Plans essentiels :
	- sauvegarde, secours, continuité, tests.
	- Analyse des journaux (logs) et comptabilité.
	- Séparation des environnements (développement vs production).

##### 1.2.6.🏢 Sécurité physique et environnementale

Protège les infrastructures matérielles et l’environnement dans lequel elles opèrent.

- Contrôle des accès physiques aux locaux.
- Protection contre les risques environnementaux (incendie, inondation, coupure électrique).
- Redondance des sources d’énergie et des infrastructures.
- Marquage du matériel pour prévenir le vol.
- Maintenance préventive et corrective.

#### 1.3. 🛣️ Diriger la sécurité

Diriger la sécurité consiste à **organiser, piloter et maintenir** l’ensemble des mesures permettant de protéger les actifs informationnels d’une organisation. Cela implique une **vision stratégique**, l'adoption d'un plan méthodologique et d'une gouvernance claire et une adaptation continue aux risques.

##### 1.3.1 🎯 Objectifs de la direction de la sécurité

- Définir une **politique de sécurité** cohérente, alignée sur les besoins de l’organisation.
- Assurer la **motivation, la sensibilisation et la formation** du personnel.
- Mettre en place des mesures **proactives** (prévention) et **réactives** (détection, réponse).
- Optimiser l’usage des technologies de l’information et des solutions de sécurité.
- Réévaluer continuellement les besoins de sécurité en fonction :
	- de l’évolution des risques
	- des nouvelles menaces
    - des changements organisationnels
##### 1.3.2. 🧭 Composantes clés de la gouvernance de la sécurité

- **Politique de sécurité** : Document stratégique définissant les règles, responsabilités et objectifs de sécurité.
- **Processus de gestion des risques**: Identification, analyse, traitement et suivi des risques.
- **Organisation de la sécurité** : Rôles, responsabilités, comités, chaîne de décision.
- **Culture de sécurité** : Sensibilisation, comportements sécuritaires, responsabilisation des utilisateurs.
- **Contrôles et audits** : Vérification régulière de la conformité et de l’efficacité des mesures
#### 1.4. 🏗️ Architecture de sécurité

L’architecture de sécurité représente la **structure globale** qui organise les dimensions techniques, humaines, organisationnelles et juridiques nécessaires pour protéger un système d’information.  

Elle assure que les mesures de sécurité sont **cohérentes**, **complémentaires** et **alignées** avec les objectifs de l’organisation. 

| Dimensions                                              | Paramètres                                                                                                                                                                                                                                                                                            |
| ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🏢 Dimension politique, organisationnelle & managériale | - Définition des politiques, normes et procédures.<br>- Gouvernance, rôles et responsabilités.<br>- Gestion des risques et conformité.<br>- Alignement avec les objectifs stratégiques de l’organisation.                                                                                             |
| 👤 Dimension humaine                                    | - Sensibilisation et formation des utilisateurs.<br>- Gestion des accès et des identités.<br>- Culture de sécurité et comportements sécuritaires.<br>- Prévention des erreurs humaines et des abus.                                                                                                   |
| ⚙️ Dimension technique                                  | - Sécurisation des systèmes, applications et infrastructures.<br>- Mécanismes de protection :<br>	- cryptographie, pare-feu, IDS/IPS, antivirus, segmentation réseau.<br>- Surveillance, journalisation, détection d’incidents.<br>- Architecture réseau sécurisée (DMZ, VPN, défense en profondeur). |
| ⚖️ Dimension juridique & réglementaire                  | - Respect des lois et réglementations :<br>	- protection des données personnelles, confidentialité, conservation.<br>- Conformité aux normes (ISO 27001, PCI-DSS, etc.).<br>- Gestion contractuelle (fournisseurs, infonuagique, sous-traitants).<br>- Responsabilités légales en cas d’incident.     |



---

## ❓Example Exam Questions 

> **Définissez la confidentialité.**
> 	Protection contre toute divulgation non autorisée.

> **Définissez l’intégrité.**
> 	Assurance qu’une donnée n’a pas été altérée ou modifiée de manière non autorisée.

> **Définissez la disponibilité.**
> 	Propriété garantissant qu’un service est opérationnel lorsqu’il est requis.  
> 	Peut être exprimée en pourcentage de temps accessible.

> **Quelle est la différence entre accessibilité et disponibilité ?**
> 	Disponibilité = système fonctionnel.  
> 	Accessibilité = accès sans obstacle inutile pour les utilisateurs autorisés.

> **Définissez l’authenticité.**
> 	Garantie qu’une entité est bien celle qu’elle prétend être.

> **Définissez la non-répudiation.**
> 	Impossibilité pour une entité de nier avoir effectué une action.

> **Définissez la traçabilité.**
> 	Capacité de suivre qui a fait quoi, quand et comment.

> **Quelle est la différence entre une menace et une vulnérabilité ?**
> 	Une menace est une cause potentielle de dommage. Une vulnérabilité est une faiblesse exploitable par cette menace. La menace exploite la vulnérabilité pour affecter un actif.

> **Une signature numérique garantit quoi ?**
> 	- Authenticité
> 	- Non-répudiation  
> 	Pas nécessairement confidentialité.

> Un message peut-il être confidentiel mais non véridique ? 
> 	Oui : Le chiffrement protège le contenu, mais ne garantit pas qu’il soit exact.

> Quels sont les domaines d’application de la sécurité informatique ?
> 	- Cybersécurité
> 	- Sécurité de l’information
> 	- Sécurité logique/applicative
> 	- Sécurité des réseaux
> 	- Sécurité de l’exploitation
> 	- Sécurité physique

> **Quelle est la différence entre cybersécurité et sécurité de l’information ?**
> 	Cybersécurité → environnements connectés à Internet.  
> 	Sécurité de l’information → protection de l’information, peu importe le support.

> **Expliquez le principe de défense en profondeur.**
>	 Superposition de plusieurs mécanismes de protection.  
>	 La sécurité ne doit pas dépendre d’un seul contrôle.

> **Pourquoi dit-on que la sécurité dépend du maillon le plus faible ?**
> 	Parce qu’une seule vulnérabilité peut compromettre l’ensemble du système.

> **Que signifie diriger la sécurité ?**
> 	Organiser, piloter et maintenir l’ensemble des mesures de protection.
> 	Inclut stratégie, gouvernance et adaptation continue.

> **Quels sont les objectifs de la direction de la sécurité ?**
> 	- Définir une politique
> 	- Sensibiliser le personnel
> 	- Mettre en place prévention et réaction
> 	- Réévaluer les risques

> **Quelles sont les dimensions d’une architecture de sécurité ?**
> 	- Politique / organisationnelle
> 	- Humaine
> 	- Technique
> 	- Juridique

> **Pourquoi la dimension humaine est-elle critique ?** 
> 	Parce que l’erreur humaine est une cause majeure d’incident.

> **Un système peut-il être disponible mais non sécurisé ?**
> 	Oui : Un serveur peut fonctionner parfaitement tout en exposant des données sensibles.

> **La sécurité est-elle uniquement technique ?**
> 	Non : Elle inclut gouvernance, organisation, culture et cadre juridique.

> **Pourquoi la sécurité doit-elle être alignée avec la stratégie organisationnelle ?**
> 	Parce que :
> 	- Elle a un coût
> 	- Elle doit être proportionnelle au risque
> 	- Elle dépend des priorités métiers



---

## ✅ To Review

- [ ] Familiarisation avec le système d'explolitation Linux
	- [ ] Partition du disque
	- [ ] Installation de Linux sur une partition

---

## 🔗 Links and Materials

- Informations sur le déroulement du cours: ![[deroulement_cours_ift2830_h26.pdf]]
- Diapositives du cours: ![[1.objectifs_domaines_application.pdf]]

Références 
1. **S. Ghernaouti, Cybersécurité : Analyser les risques, mettre en œuvre les solutions, 7ème édition, Dunod, 2022.**
2. **S. Ghernaouti, Sécurité informatique et réseaux, 5ème édition, Dunod, 2016.** 
3. J-F. Pillou, J-P. Bay, Tout sur la Sécurité informatique, 4ème édition, Dunod, 2016. 
4. M. Ciampa, Security Awareness: Applying Practical Security in Your World, 4th Edition, 2014. 
5. M. T. Simpson, K. Backman, J. E. Corley, Hands-On Ethical Hacking and Network Defense, Course Technology, 2012.
6. Mark Ciampa, Security+ Guide to Network Security Fundamentals. 4th edition. 2011. 
7. R. Panko, Sécurité des systèmes d’information et des réseaux, Pearson Education, 2004.
8. D. Salomon, Foundations of Computer Security, Springer, 2006. 
9. H. F. Tipton, M. Krause, Information security management handbook, 5th edition, Auerbach, 2004. 
10. M. Bishop, Computer security: Art and science. Addison-Wesley, 2002. 
11. E. Skoudis, Counter hack: A step-by-step Guide to Computer Attacks and Effective Defenses, Prentice Hall, 2002.