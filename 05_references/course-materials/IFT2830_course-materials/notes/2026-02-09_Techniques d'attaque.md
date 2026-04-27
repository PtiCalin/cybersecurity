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
  - security/attack/password
  - security/attack/ip-spoofing
  - security/attack/dos
  - security/attack/ddos
  - security/attack/syn-flood
  - security/attack/amplification
  - security/attack/reflection
  - security/attack/ping-of-death
  - security/attack/fragmentation
  - security/network
  - security/network/tcp
  - security/network/ip
  - security/network/handshake
  - security/concepts
  - security/concepts/cia
  - security/concepts/availability
  - security/concepts/vulnerability
  - security/concepts/botnet
  - security/concepts/tcp-sequence
  - security/concepts/ip-offset
---
# Les Techniques d'attaque sur les systèmes informatiques 


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

- Attaques de mot de passe
- Usurpation d'adresse IP
- Attaques par déni de service
- Attaque "homme au milieu" / "man in the middle"
- Attaques par débordement de tampon
- Attaques biométriques
- Attaques par ingénierie sociale

---

## 📓 Notes

> Analyse des principales techniques d’attaque contre les systèmes informatiques, leurs mécanismes techniques et leurs impacts sur la sécurité, notamment sur la **disponibilité**. Il met en lumière les vulnérabilités exploitées au niveau réseau, protocolaire et applicatif ainsi que les stratégies de défense associées.

### ✨ Terminology
|Terme|Définition synthétique|
|---|---|
|DoS|Attaque visant à rendre un service indisponible depuis une seule source.|
|DDoS|Attaque par déni de service exécutée depuis plusieurs machines (botnet).|
|Saturation|Épuisement volontaire des ressources d’un système.|
|Exploitation de vulnérabilité|Utilisation d’une faille logicielle pour provoquer un dysfonctionnement.|
|SYN Flood|Envoi massif de paquets SYN pour saturer la file des connexions semi-ouvertes.|
|Connexion semi-ouverte|État intermédiaire d’une connexion TCP après SYN sans ACK final.|
|SYN|Drapeau TCP servant à initier une connexion.|
|SYN-ACK|Réponse TCP confirmant réception du SYN et proposant synchronisation.|
|ACK|Accusé de réception final validant la connexion TCP.|
|Amplification|Technique utilisant une petite requête pour générer une grande réponse vers la victime.|
|Réflexion|Technique exploitant des serveurs tiers pour rediriger du trafic vers la cible.|
|Ping of Death|Envoi d’un paquet IP dépassant la taille maximale autorisée.|
|Fragmentation IP|Découpage d’un paquet IP en fragments pour transmission.|
|Offset IP|Indicateur de position d’un fragment dans un paquet fragmenté.|
|IP Spoofing|Falsification de l’adresse IP source d’un paquet.|
|Datagramme IP|Unité de transmission du protocole IP.|
|Numéro de séquence TCP|Identifiant permettant d’ordonner les segments TCP.|
|Blind attack|Attaque réalisée sans voir les réponses de la cible.|
|Source routing|Technique permettant de spécifier un chemin réseau pour un paquet.|
|Amplification ratio|Rapport entre la taille de la réponse et celle de la requête initiale.|
|SYN cookies|Mécanisme empêchant l’allocation mémoire avant validation complète du handshake TCP.|
|Botnet|Réseau de machines compromises contrôlées par un attaquant.|
|Pile TCP/IP|Ensemble des protocoles réseau utilisés pour la communication Internet.|
|Disponibilité (CIA)|Capacité d’un système à rester accessible aux utilisateurs légitimes.|

---

### 🔐 Attaques de mot de passe

- **Objectif** : 
	Obtenir un accès non autorisé à un système via l’authentification.
- **Méthodologies** : 
	- Force brute: Tester **toutes les combinaisons possibles**.
		→ Dépend de :
		- Longueur du mot de passe
		- Complexité des caractères
		- Puissance de calcul (GPU, cloud, calcul distribué)
	 - Attaque par dictionnaire : Tester une liste de mots probables. 
		-  mots courants
		- mots du dictionnaire
		- mots de passe fréquemment utilisés (ex: 123456, admin)
	- Attaque hybride : Combinaison dictionnaire + variations
		- mot + chiffre
		- mot inversé
		- majuscule/minuscule
	- Keylogger : Logiciel qui enregistre les frappes clavier.
	- Ingénierie sociale : Manipulation psychologique pour obtenir le mot de passe.
- Parades : 
	- Longueur minimale élevée
	- MFA (authentification multi-facteurs)
	- Blocage temporaire après tentatives
	- Hashage + salage des mots de passe

### 🦹‍♀️ Usurpation d’adresse IP (IP Spoofing)

- **Objectif** : 
	Envoyer des paquets en falsifiant l’adresse IP source.
- **Méthodologies** : 
	- L’attaquant :
		- Modifie l’en-tête IP
		- Change l’adresse IP source
		- Tente de contourner le pare-feu
	- Three-way handshake TCP : 
		1. SYN
		2. SYN-ACK
		3. ACK
		Si IP spoofée :
		- La machine légitime répond par RST
		- L’attaquant doit invalider la machine usurpée
		- Il doit prédire les **numéros de séquence**
- Parades : 
	- Filtrage ingress/egress
	- Randomisation des numéros de séquence
	- Secure TCP/IP stack

![[4.techniques_attaque.pdf#page=8&rect=176,56,741,408|4.techniques_attaque, p.8]]
Figure: Modification de l'en-tête du datagramme IP

### Attaques par déni de service (DoS / DDoS)

Les attaques DoS peuvent être classées selon :

1. La ressource ciblée (bande passante, mémoire, CPU)
2. La couche réseau impactée (réseau, transport, application)
3. Le mode d’exécution (local ou distribué)

La défense repose sur :

- Réduction de surface d’attaque
- Filtrage intelligent
- Mise à jour constante
- Architecture distribuée

> [!PDF|8, 109, 221] [[4.techniques_attaque.pdf#page=12&annotation=1949R|4.techniques_attaque, p.12]]
> > • Denial of Service (DoS) • But: rendre indisponible pendant un temps indéterminé les services ou les ressources d’une organisation


- **Objectif** : 
	Les attaques DoS ciblent principalement la **disponibilité**, un des trois piliers du modèle CIA (Confidentiality, Integrity, Availability).
- **Mécanismes** :
	- Saturation : 
		Submerger une machine ou un service de requêtes afin d’épuiser :
		- CPU
		- Mémoire
		- Bande passante
		- Files de connexion
		On distingue généralement :
		- Attaques volumétriques (bande passante)
		- Attaques protocolaires (pile TCP/IP)
		- Attaques applicatives (couche 7)
	- Exploitation de vulnérabilité : 
		Exploiter une faille dans l’implémentation :
		- Bug protocolaire
		- Mauvaise gestion mémoire
		- Mauvais traitement des fragments IP
- **Architecture** : 
	- DoS: Attaque provenant d’une seule machine.
	- DDoS : Attaque coordonnée depuis plusieurs machines (souvent botnet).
- **Méthodologies** :
	- SYN Flood
		- Technique permettant au serveur de ne pas allouer de mémoire avant la validation complète du handshake TCP.
		- Remplit la file des connexions semi-ouvertes (Le serveur conserve en mémoire les connexions en attente d’ACK final, ce qui épuise progressivement les ressources.)
		- Empêche les connexions légitimes
		➡ Type : Saturation  
		➡ Peut être DoS ou DDoS
	- Attaque par réflexion (Smurf)
		- Falsification de l’IP source
		- Des serveurs tiers répondent vers la victime
		➡ Mécanisme : Saturation  
		➡ Architecture : Généralement DDoS
	- Attaque par amplification
		- Petite requête → très grosse réponse
		- Exploite des protocoles amplificateurs :
		    - DNS
		    - NTP
		    - SMTP
		➡ Mécanisme : Saturation  
		➡ Architecture : Très souvent DDoS
	- Ping of Death
		- Paquet IP > 65 536 octets
		- Exploite anciennes implémentations TCP/IP
		- Peut provoquer crash ou redémarrage
		➡ Mécanisme : Exploitation de vulnérabilité
	- Fragment Attack
		- Manipulation des offsets IP
		- Chevauchement ou vides dans les fragments
		- Crash lors du réassemblage
		➡ Mécanisme : Exploitation de vulnérabilité
- Parades : 
	- Contre saturation
		- Rate limiting
		- SYN cookies
		- Load balancing
		- CDN
		- Firewall stateful
		- Filtrage ingress/egress
	- Contre exploitation
		- Mise à jour logicielle
		- Patching régulier
		- Stack TCP/IP moderne
		- Surveillance réseau active

---
## 🏋️ Exercices

> **Différence entre force brute et attaque par dictionnaire ?**
>	 - Force brute → teste toutes les combinaisons.
>	 - Dictionnaire → teste une liste ciblée de mots probables.

> **Pourquoi le salage rend les attaques par dictionnaire inefficaces ?**
> 	Le sel rend chaque hash unique, même pour des mots de passe identiques.

> **Une entreprise stocke les mots de passe en clair. Quel pilier CIA est directement compromis ?**
> 	Confidentialité.

> **Pourquoi le MFA réduit drastiquement le risque ?**
> 	Même si le mot de passe est compromis, un second facteur bloque l’accès.

> **Pourquoi le spoofing IP fonctionne surtout avec UDP ?** 
> 	UDP est sans connexion, donc pas de handshake à valider.

> **Dans un spoofing TCP, pourquoi l’attaquant doit prédire le numéro de séquence ?**
> 	Pour compléter correctement le handshake sans voir la réponse.

> **Quel mécanisme réseau réduit fortement le spoofing ?**
> 	Filtrage ingress/egress.

> **Quelle différence fondamentale entre DoS et DDoS ?**
> 	- DoS → une seule source.
> 	- DDoS → plusieurs machines (botnet).

> **Pourquoi un DDoS est beaucoup plus difficile à bloquer ?**
> 	Trafic distribué, difficile à distinguer du trafic légitime.

> **Quelle ressource est ciblée dans un SYN Flood ?**
> 	File des connexions semi-ouvertes (mémoire).

> **Expliquez pourquoi SYN cookies sont efficaces.**
> 	Le serveur n’alloue pas de mémoire avant validation complète.

> **Pourquoi DNS est un bon protocole d’amplification ?**
> 	Petite requête → très grosse réponse possible.

> **Différence entre réflexion et amplification ?**
> 	- Réflexion → utilisation d’un tiers pour rediriger le trafic.
> 	- Amplification → augmentation volumétrique de la réponse.

> **Pourquoi Ping of Death ne fonctionne plus aujourd’hui ?**
> 	Stacks TCP/IP modernes corrigées.

> **Que provoque une attaque par fragmentation IP ?**
> 	Crash lors du réassemblage.

> **Quelle attaque cible principalement la disponibilité ?**
> 	DoS / DDoS.

> **Une attaque par keylogger affecte quel pilier CIA ?**
> 	Confidentialité.

> **Une attaque MITM affecte quels piliers ?**
> 	Confidentialité + Intégrité.

---
## ✅ To Review

- [ ] 

---

## 🔗 Links and Materials

- Notes de cours (diapos)
![[4.techniques_attaque.pdf]]

- Activités

![[4.activités.pdf]]

- Vieux site sketch qui parle des payloads : [The TCP/IP Guide - IP Datagram General Format](http://www.tcpipguide.com/free/t_IPDatagramGeneralFormat.htm#)



---