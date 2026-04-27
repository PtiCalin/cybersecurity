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
  - security/attack
  - security/attack/lifecycle
  - security/attack/reconnaissance
  - security/attack/scanning
  - security/attack/vulnerability-analysis
  - security/attack/intrusion
  - security/attack/exploit
  - security/attack/privilege-escalation
  - security/attack/compromise
  - security/attack/persistence
  - security/attack/cleanup
  - security/network
  - security/network/port
  - security/network/ttl
  - security/network/scan
  - security/network/sniffer
  - security/network/spoofing
  - security/vulnerability
  - security/vulnerability/cve
  - security/vulnerability/exploit
  - security/authentication
  - security/authentication/bruteforce
---
# Attaques sur les systèmes informatique


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

- Cycle complet d’une attaque
- Collecte d’informations
- Balayage (scan)
- Repérage des failles
- Intrusion
- Exploit
- Extension des privilèges
- Compromission
- Porte dérobée
- Nettoyage des traces

---

## 📓 Notes

> Une attaque est l’exploitation d’une vulnérabilité afin de compromettre un système, ses données ou ses services.
> 
> Elle suit une progression logique : 
> 
> Reconnaître → Scanner → Trouver une faille → Entrer → Élever privilèges → Maintenir accès → Effacer traces.
> 
> Chaque étape augmente le contrôle et réduit la détection.
> 
> Cette note décrit **la chaîne complète d’une attaque réseau**, de la reconnaissance jusqu’au nettoyage des traces.

### ✨ Terminology

| Terme                                | Définition ultra synthétique                                                                       |
| ------------------------------------ | -------------------------------------------------------------------------------------------------- |
| **Attaque**                          | Exploitation d’une vulnérabilité                                                                   |
| **Reconnaissance**                   | Collecte d’informations sur la cible                                                               |
| **Scan**                             | Cartographie technique du réseau                                                                   |
| **Port**                             | Point d’accès logique à un service                                                                 |
| **Sniffer**                          | Outil d’écoute du trafic réseau                                                                    |
| **Exploit**                          | Code exploitant une faille                                                                         |
| **Extension de privilèges**          | Passage utilisateur → admin                                                                        |
| **Compromission**                    | Perte de contrôle du système                                                                       |
| **Backdoor**                         | Accès caché persistant                                                                             |
| **Rootkit**                          | Outil de dissimulation avancée                                                                     |
| **Spoofing**                         | Usurpation d’identité réseau                                                                       |
| **TTL**                              | Durée de vie d’un paquet réseau                                                                    |
| **Portscan**                         | Scan des ports ouverts                                                                             |
| **CVE**                              | Base publique de vulnérabilités                                                                    |
| **Force brute**                      | Test automatisé massif de mots de passe                                                            |
| **Persistance**                      | Maintien durable de l’accès                                                                        |
| **ACK**                              | Drapeau TCP confirmant la réception correcte d’un segment.                                         |
| **SYN**                              | Drapeau TCP utilisé pour initier une connexion.                                                    |
| **DNS**                              | Système traduisant un nom de domaine en adresse IP.                                                |
| **TCP**                              | Protocole de transport fiable basé sur connexion et accusés de réception.                          |
| **UDP**                              | Protocole de transport sans connexion, rapide mais non fiable.                                     |
| **MFA**                              | Authentification nécessitant au moins deux facteurs distincts.                                     |
| **SYN-ACK**                          | Réponse TCP combinant SYN et ACK pour confirmer et synchroniser une connexion.                     |
| **Three-way handshake**              | Processus TCP en trois étapes (SYN → SYN-ACK → ACK) établissant une connexion fiable.              |
| **Botnet**                           | Réseau de machines compromises contrôlées par un attaquant.                                        |
| **Rate limiting**                    | Mécanisme limitant le nombre de requêtes acceptées sur une période donnée.                         |
| **Segment TCP**                      | Unité de données transportée par TCP contenant en-tête et données.                                 |
| **Port réseau**                      | Identifiant numérique permettant d’orienter le trafic vers un service spécifique.                  |
| **Firewall stateful**                | Pare-feu analysant le contexte et l’état des connexions pour filtrer le trafic.                    |
| **Load balancing**                   | Répartition du trafic entre plusieurs serveurs pour éviter la surcharge.                           |
| **CDN (Content Delivery Network)**   | Réseau distribué de serveurs diffusant du contenu depuis le point le plus proche de l’utilisateur. |
| **Stack TCP/IP**                     | Ensemble des protocoles réseau permettant la communication sur Internet.                           |
| **File de connexions semi-ouvertes** | Liste temporaire des connexions TCP en attente d’ACK final après un SYN-ACK.                       |
| **Latence**                          | Temps nécessaire pour qu’un paquet atteigne sa destination.                                        |
| **Bande passante**                   | Capacité maximale de transmission de données d’un réseau.                                          |
| **Couche réseau (OSI)**              | Niveau 3 du modèle OSI chargé du routage des paquets IP.                                           |

---

### 🔁 Cycle complet d’une attaque

1. Collecte d’informations
2. Balayage
3. Repérage des failles
4. Intrusion
5. Extension des privilèges
6. Compromission
7. Porte dérobée
8. Nettoyage des traces

C’est un **processus progressif**.  
Chaque étape réduit l’incertitude et augmente le contrôle de l’attaquant.

### 🔎 Collecte d’informations
Objectif : comprendre la cible sans l’attaquer directement.
**Cette phase est souvent passive.**

#### Cibles

- **Où est la cible ?**
    - Adresses IP
    - Plages IP
    - Nom de domaine
- **Quels services expose-t-elle ?**
    - Protocoles (HTTP, SMTP, DNS, etc.)
    - Services actifs
    - Technologies utilisées
- **Comment est-elle organisée ?**
    - Architecture réseau
    - Fournisseurs
    - Structure interne
    - Identités des employés

#### Méthodes

##### 1️⃣ Collecte technique

- **Bases publiques (IANA, RIPE, ARIN)**
    - propriétaire d’un bloc IP
	- contacts administratifs
	- informations d’enregistrement
	➡ Utile pour cartographier l’infrastructure officielle.
- **Whois**
    Interroge les bases d’enregistrement de domaines pour obtenir :
	- nom du registrar
	- contacts techniques
	- dates de création
	➡ Peut révéler des emails exploitables.
- **Moteurs de recherche**
	Permet la recherche de: 
	- pages oubliées
	- documents publics
	- erreurs de configuration
	- informations exposées
	➡ Exemple : Google dorking.

##### 2️⃣ Collecte humaine et organisationnelle

- **Réseaux sociaux**
    Permettent d’identifier :
	- employés
	- technologies mentionnées
	- structure hiérarchique
	➡ Sert à préparer une attaque par ingénierie sociale.
- **Offres d’emploi**
    Indiquent :
	- systèmes utilisés
	- logiciels en place
	- lacunes organisationnelles
	➡ Révèle indirectement la pile technologique.
- **Dumpster diving**
    Recherche d’informations dans les déchets :
	- documents internes
	- notes techniques
	- supports physiques
	➡ Très simple, souvent négligé.
- **Ingénierie sociale**
    Manipulation psychologique pour obtenir :
	- informations sensibles
	- accès
	- identifiants
	➡ Peut transformer une phase passive en intrusion indirecte.

> La collecte prépare le balayage et conditionne la réussite des phases suivantes.
### 🧹 Balayage (scan)
Objectif : cartographier techniquement le réseau.
➡ Acquisition active ou passive d’informations.
##### Techniques
- Portscan
	Identifier ports ouverts
- Traceroute
	Cartographie des routeurs via TTL
- Lecture de bannières
- Scan actif (Nmap)
- Scan passif

> Contrairement à la collecte, le balayage est généralement actif et peut être détecté.

### 🧪 Repérage des failles
Objectif : identifier des vulnérabilités exploitables.

- **Outils**
	- Nessus
	- SAINT
	- Bases CVE (cve.mitre.org)

> Cette phase transforme l’information brute en opportunités exploitables.

### 🦹‍♀️ Intrusion
Objectif : obtenir un accès.
➡ Ici, l’attaquant entre réellement dans le système.

- **Méthodes**
	- Exploitation de vulnérabilité
	- Force brute
	- Ingénierie sociale
	- Recherche de comptes valides

> L’intrusion marque la transition entre reconnaissance et compromission.

### 🧨 Exploit
Un programme exploitant une vulnérabilité spécifique.

Types :
- Extension de privilèges
- Provocation d’erreur système

Un exploit est dépendant d’une version précise.

### 🤲 Extension des privilèges
Objectif : devenir root / administrateur

- Conséquence :
	- Contrôle total
	- Accès à d’autres systèmes
	- Installation d’outils (sniffer)

> Sans extension de privilèges, l’attaque reste limitée.

### 🕷️ Compromission

- Exploitation des relations de confiance
- Spoofing
- Accès à réseaux privilégiés

> La compromission signifie que l’attaquant contrôle désormais le système à un niveau critique.

### 🚪Porte dérobée
Installer un accès permanent.

But :
- Revenir plus tard
- Maintenir le contrôle
- Persistance


### 🧼 Nettoyage des traces
Objectif : invisibilité
	➡ C’est la phase de camouflage.
- Suppression logs
- Effacement fichiers
- Installation rootkit
- Remplacement outils système

> Cette phase vise à retarder la détection et à préserver la persistance.

---
## 🏋️ Exercice

> **Quelles-sont les 8 étapes du cycle d’une attaque dans l’ordre.**
> 	Reconnaissance → Scan → Repérage des failles → Intrusion → Extension des privilèges → Compromission → Backdoor → Nettoyage des traces.

> **Pourquoi dit-on qu’une attaque est progressive ?**
> 	Chaque étape réduit l’incertitude et augmente le contrôle de l’attaquant.

> **Quelle est la différence entre collecte passive et active ?**
>	 Passive → sans interaction directe détectable.  
>	 Active → interaction pouvant être détectée.

> **Pourquoi les offres d’emploi sont utiles à un attaquant ?**
> 	Elles révèlent la pile technologique et les outils internes.

> **Donner deux exemples de collecte humaine.**
> 	- Réseaux sociaux
> 	- Dumpster diving

> **Quel est l’objectif stratégique de la reconnaissance ?**
> 	Réduire l’incertitude avant l’attaque.

> **Quelle différence entre reconnaissance et scan ?**
> 	Reconnaissance → collecte large d’informations.
> 	Scan → cartographie technique précise.

> **Pourquoi un scan est-il plus détectable ?**
> 	Il génère du trafic réseau actif.

> **Quel rôle joue le TTL dans traceroute ?** 
> 	Permet d’identifier les routeurs intermédiaires.

> **Quelle est la différence entre scan réseau et scan de vulnérabilité ?**
> 	Scan réseau → ports/services ouverts.  
> 	Scan vulnérabilité → failles exploitables.

> **À quoi sert une base CVE ?**
> 	Recenser publiquement les vulnérabilités connues.

> **Quelle est la différence entre intrusion et exploit ?**
> 	Intrusion → obtention d’accès. 
> 	Exploit → code utilisé pour obtenir cet accès.

> **Pourquoi un exploit dépend-il d’une version précise ?**
>	 Car la vulnérabilité est liée à une implémentation spécifique.

> **Pourquoi l’élévation de privilèges est-elle critique ?**
> 	Elle accroît le contrôle du système.

> **Une attaque sans élévation de privilèges est-elle complète ?**
> 	Non. Elle reste limitée aux droits initiaux.

> **Quand considère-t-on qu’un système est compromis ?**
> 	Quand l’attaquant a un contrôle critique ou persistant.

> **Quelle différence entre compromission et backdoor ?**
> 	Compromission → prise de contrôle.  
> 	Backdoor → accès persistant futur.




---
## ✅ To Review

- [ ] 

---

## 🔗 Links and Materials

- Diapositives du cours
![[5.Attaques_sur_les_reseaux_informatiques.pdf]]




---