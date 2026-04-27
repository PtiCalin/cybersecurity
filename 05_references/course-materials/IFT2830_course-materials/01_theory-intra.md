# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Objectifs et domaines

## d’application de la sécurité

## informatique

```
1
```

### Contenu

- Objectifs de sécurité
- Domaines d’application de la sécurité informatique
- Diriger la sécurité
- Architecture de sécurité

### Objectifs de sécurité

- La notion de sécurité fait référence à la propriété d’un système, d’un

##### service ou d’une entité

- Elle s’exprime le plus souvent par les objectifs suivants
  - La disponibilité (D)
  - L’intégrité (I)
  - La confidentialité (C)
- Plus des fonctions de sécurité
  - Authentification
  - Non-répudiation
  - Imputabilité

```
Critères DIC (ou CIA en anglais)
```

### Objectifs de sécurité (suite)

### Disponibilité

- Des services, systèmes, données, etc.
- La période de temps pendant laquelle le service offert par une

##### ressource est opérationnel

- Capacité
  - Le volume de travail susceptible d’être pris en charge durant la période de
    disponibilité d’un service (serveur ou réseau par exemple)
- Accessibilité (pour l’ensemble des ayants droit)
  - Avec des temps de réponse acceptables
- Dimensionnement approprié, redondance des infrastructures, gestion

##### opérationnelle, maintenance efficace

### Intégrité

- Des ressources physiques et logiques (équipements, données,

##### traitements, transactions, services)

- Non détruites (altération totale) ou modifiées (altération partielle) à

##### l’insu de leurs propriétaires de manière intentionnelle ou accidentelle

- À satisfaire par des mesures appropriées (chiffrement par exemple)

##### afin de pouvoir atteindre un certain niveau de confiance dans les

##### contenus et le fonctionnement des infrastructures informatiques et

##### télécoms

- Télécommunications: transfert de données (écoutes actives)
- Traitement de l’information: logiciels d’application, systèmes

##### d’exploitation, procédures de sauvegarde, etc.

### Confidentialité

- « _La confidentialité est le maintien du secret des informations ..._ » - Le

##### Petit Robert

- Dans le contexte de l’informatique et des réseaux de communication
  - _« La protection des données contre une divulgation non autorisée»_
- Contrôle d’accès
- Chiffrement

### Identification et authentification

- Confidentialité et intégrité des données
  - seuls les ayants droit identifiés et authentifiés peuvent accéder aux ressources
    (contrôle d’accès) et les modifier
- Non-répudiation et imputabilité
  - Seules les entités identifiées et authentifiées ont pu réaliser une certaine
    action (preuve de l’origine d’un message ou d’une transaction, etc.)
  - Traçabilité

### Non-répudiation

- Le fait de ne pouvoir nier ou rejeter qu’un évènement (action,

##### transaction) a eu lieu

- Imputabilité
  - L’attribution d’une action (un évènement) à une entité déterminée (ressource,
    personne)
  - Enregistrement fiable d’informations sur les entités et les évènements
- Traçabilité
  - Suivre la trace numérique laissée par la réalisation d’un évènement
- L’auditabilité
  - La capacité d’un système à garantir la présence d’informations nécessaires à
    une analyse ultérieure d’un évènement (courant ou exceptionnel)

### Domaines d’application de la sécurité informatique

### Cybersécurité

- Le préfixe « cyber » est devenu relatif à l’environnement informatique et aux

###### activités rendus possibles par les technologies du numérique

- Cyberespace
  - L’ensemble des infrastructures numériques, des données et des services mis en
    réseaux
  - Extension de notre espace naturel qui reflète notre société avec ses réalités politique,
    économique, sociale et culturelle
- Cybersécurité
  - Concerne la sécurité informatique et des réseaux des environnements connectés à
    Internet et accessible _via_ le cyberespace
  - Peut être mise en défaut, entre autres, par des cyberattaquesinformatiques
- Usage extensif d’Internet ➔
  - Nouvelles menaces générant des risques additionnels
  - Impact potentiel sur les individus, les organisations ou les états

### Sécurité de l’information

- Bien protéger l’information c’est
  - Comprendre son rôle et son importance stratégique
  - L’impact des décisions qui la concernent
  - Assurer son exactitudeet sa pérennité
- Classification des données pour qualifier leur degré de sensibilité

##### (confidentielles, privées, sensibles, publiques) et les protéger en

##### conséquence

- Respect de l’intimité numérique ( _privacy_ ) de l’utilisateur et de ses

##### données personnelles

### Sécurité logique et applicative

- La sécurité logique fait référence à la réalisation de mécanismes de

##### sécurité par logiciel contribuant au bon fonctionnement des

##### programmes, des services offerts et à la protection des données

- La qualité des développements logiciels et des tests de sécurité
- Une mise en œuvre adéquate de la cryptographie (intégrité et confidentialité)
- Des procédures de contrôle d’accès logique et d’authentification
- Des procédures de détection de logiciels malveillants, de détection d’intrusion
  et d’incidents
- Dimensionnement suffisant de ressources, redondance, sauvegarde
- Etc.

### Sécurité logique et applicative (suite)

- La sécurité applicative comprend le développement pertinent de

##### solutions logiciels ainsi que leur intégration et exécution harmonieuse

##### dans des environnements opérationnels

- Une méthodologie de développement
- La robustesse des applications
- Des contrôles programmés
- Des jeux de tests
- Des procédures de recettes
- L’intégration des mécanismes de sécurité
- La sécurité des progiciels (choix des fournisseurs, etc.)
- Un plan de migration des applications critiques
- La validation et l’audit des programmes
- La qualité et la pertinence des données
- Etc.

### Sécurité des réseaux

- Sécurité des infrastructures de

###### télécommunication

- Consiste à offrir à l’utilisateur final et aux

###### applications communicantes une

###### connectivité fiable « de bout en bout »

- Réalisation d’une infrastructure réseau
  sécurisée au niveau des accès au réseau et du
  transport
- Usage de plates-formes matérielles et
  logicielles sécurisées et une gestion de réseau
  de qualité
- N’est qu’un maillon dans la chaîne

###### sécuritaire ➔ La sécurité est toujours celle

###### du maillon le plus faible!

- Besoin de sécuriser l’infrastructure
  informatique

### Sécurité des réseaux (suite)

- Défense en profondeur

### Sécurité de l’exploitation

- Permet un bon fonctionnement opérationnel des systèmes

##### informatiques

- Gestion du parc informatique
- Gestion des configurations et des mises à jour
- Gestion des incidents et suivi jusqu’à leur résolution
- Plan de sauvegarde
- Plan de secours
- Plan de continuité
- Plan de tests
- Analyse des fichiers de journalisation et de comptabilité
- Gestion des contrats de maintenance
- Séparation des environnements de développent et de production des
  applications
- Etc.

### Sécurité physique et environnementale

- Concerne tous les aspects liés à la maîtrise des systèmes et de

##### l’environnement dans lequel ils se situent

- La protection des sources énergétiques et de la climatisation
- La protection de l’environnement (risques d’incendie, d’inondation, etc.)
- Gestion et contrôle des accès physiques aux locaux
- La redondance physique des infrastructures et sources énergétiques
- Marquage du matériel pour dissuader le vol
- Le plan de maintenance préventive (tests) et corrective (pièces de rechange)
- Etc.

### Diriger la sécurité

- Définition d’une politique de sécurité
- La motivation et la formation du personnel
- La mise en place de mesures proactives et réactives
- L’optimisation de l’usage des technologies de l’information et de

##### communication et des solutions de sécurité

##### Les besoins de sécurité doivent être clairement identifiés et constamment

##### réévalués au regard des risques encourus et de leur évolution.

### Architecture de sécurité

- L’ensemble des dimensions organisationnelle, juridique, humaine et

##### technologique de la sécurité informatique

```
Sécurité des systèmes informatiquesIFT2830
```

## 2.1: analyse du risque

La compagnie ABCdispose d’un serveur Web à travers lequel des revendeurs se
connectent, à partir de leurs propres serveurs, pour vendre des produits aux clients.
Les profits sont distribués au prorata des ventes faites pendant une période de
temps. ABC est préoccupée par l’intégrité de ses résultats.

- Quels sont les agents de menace?
- Définir quelques scénarios de risque.
- Dresser un tableau d’analyse du risque.

```
1
```

```
Sécurité des systèmes informatiquesIFT2830
```

## 2.2: terminologie du risque

- Placer les bon termes sur les flèches

```
2
```

```
augmentent
exploitent
réduisent
qui exposent
accompagnées des
ayant
protégeant contre
demandent
augmente
```

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Gouvernance, stratégie et

## politique de sécurité

```
1
```

### Contenu

- Stratégie de sécurité
- Analyse du risque
- Politique de sécurité
- Mesures de sécurité

### Stratégie de sécurité

- Consiste à concevoir une conduite générale

###### de

- Protection
- Prévention
- Organisation de la défense
- Élaboration de plans de réaction
- Gestion de crises
- Gestion de la continuité et de la reprise des
  activités
- Gestion des poursuites pénales (s’il y a lieu)
- S’inscrit dans démarche proactive et réactive
- Anticiper et être préparé à prévenir et à gérer les
  incidents de sécurité

### Étapes de réalisation d’une démarche sécuritaire

### Vision stratégique de la sécurité

➔ Réalisésavec: des outils technologiques(antivirus, pare-feu, etc.), procédures(gestion
des identifications et du contrôle d’accès, etc.) et de personnes(recrutement,
sensibilisation, formation, etc.)

Propriété Description
Disponibilité Aucun retard

Intégrité et exactitude Aucune falsificationAucune erreur

Confidentialité Aucune écoute illicite
Pérennité Aucune destruction
Non-répudiation et imputabilité Aucune contestation

Authentification Aucun doute sur l’identité d’une ressource, sur l’origine ou la destination d’une transaction

Intimité numérique ( _privacy_ ) Aucune mise à défaut de la protection de la sphère privée de l’utilisateurProtection des données personnelles

Respect des contraintes légales
ou règlementaires Aucun risque juridique

### Principes de base

Principe Description
Principe de vocabulaire Langagecommun de définition de la sécurité

Principe de volonté directoriale

Laconsidération de l’information comme ressource stratégique
Les dirigeants doivent libérer les moyens nécessaires à la mise en œuvre et à
la gestion de la sécurité informatique
Principe financier Le coûtde la sécurité doit être en rapport avec les risques encourus

Principe de cohérence Une accumulation d’outils sécuritairesniveau global, cohérent, et satisfaisant de sécuritén’est pas suffisante pour réaliser un

Principe de simplicité
et d’universalité

```
Les mesures de sécuritédoivent être simples, compréhensibles pour les
utilisateurs et doivent s’appliquer à l’ensemble du personnel
```

Principe de dynamicité La sécuritévie des systèmes et l’évolution des besoins et des risquesdoit être dynamique pour intégrer la dimension temporelle de la

Principe de continuum L’organisation doitcontinuer à fonctionner même après la survenue de sinistre
Principe d’évaluation,de
contrôle et d’adaptation

```
Ilest impératif de pouvoir évaluer régulièrement l’adéquation des mesures de
sécurité au regard des besoins effectifs et évolutif de la sécurité
```

#### Axes stratégique, tactique et opérationnel de la sécurité

### Contexte d’une stratégie de sécuritaire

### Stratégie de sécurité: questions à poser?

- Nécessité: bon sens, vision, analyse, compromis et choix
- Quelles sont les valeurs (actifs) de l’organisation?
- Quel est leur niveau de sensibilité ou de criticité?
- De qui, de quoi doit-on se protéger?
- Quels sont les risques réellement encourus?
- Ces risques sont-ils supportables?
- Quel est le niveau actuel de sécurité?
- Quel est le niveau de sécurité que l’on désire atteindre?
- Comment passer du niveau actuel au niveau désiré?
- Quelles sont les contraintes effectives?
- Quels sont les moyens disponibles?

### Compromis et bon sens

- La sécurité est une question de compromis ... et de bon sens

### Compromis et bon sens (suite)

```
Principe
Principe de vocabulaire
Principe de volonté directoriale
Principe financier
Principe de cohérence
Principe de simplicité
et d’universalité
Principe de dynamicité
Principe de continuum
Principe d’évaluation,de
contrôle et d’adaptation
```

### Acteurs et responsabilités

Acteur Responsabilités

Responsablede sécurité
(CISO : _Chief Information
Security Officer_ )

- Contrôlerla gestion et l’administration des moyens et des mesures de sécurité
- Définir les privilèges d’accès aux ressources et les réévaluer régulièrement
- Élaborer et maintenir la documentation utilisateur et administrateur
- S’assurer que les cibles de sécurité sont sous surveillance

Responsabledes
ressources humaines

- Effectuer les contrôlesnécessaires avant l’engagement des nouveaux collaborateurs
- Sensibiliser les nouveaux collaborateurs à leurs responsabilités en termes de sécurité
- Coordonner les activités lors d’une rupture de contrat d’un collaborateur
  Chefs de service • Veiller à ce que leurs collaborateurs soient informés dela politique de sécurité
- Informer les administrateurs de la sécurité de toutes les modifications ayant un
  impact potentiel sur le niveau de sécurité ou sa gestion
- Analyser, valider et prendre position par rapport aux demandes d’accès aux
  ressources
- Recenser et récupérer les informations sensibles détenues par un collaborateur qui
  quitte l’organisation
  Utilisateurs • Respecter les règleset les pratiques définies par la politique de sécurité
- Informer le responsablede sécurité de tout élément ayant un impact sur la sécurité

### Le risque

- Un risque est un danger éventuel plus ou moins prévisible
- Il se mesure à la probabilité qu’il se produise et aux impacts et dommages

###### consécutifs à sa réalisation

- C’est la prise en compte de l’exposition à un danger, un préjudice ou tout

###### autre évènement dommageable

- Un risque exprime la probabilité qu’une valeur soit perdue en fonction

###### d’une vulnérabilitéliée à une menace, à un danger ou événement non

###### sollicité

- Traitement du risque
  - Réduction
  - Acceptation
  - Transfert
  - Arrêt de l’activité

### Terminologie du risque

Terme définition exemple
Actif Objet ayant de la valeur (y compris l’humain) Serveur de production

Menace Entité physiqueou morale qui met un actif à
risque

```
Virus
```

Vulnérabilité Faille qui donne l’opportunité de porter
atteinte à un actif et donc de concrétiser une
menace

```
Absence d’antivirus sur le
serveur
```

Impact Perte ou dommage causé à un actif Perte de la base de données

Scénario Exploitation d’une vulnérabilité par une
menace pour causer un impact

```
Le virus est introduit dans le
serveur pour détruire le
contenu de la base de
données
```

Contre-mesure
(parade)

```
Protection d’un actif contre une menace Antivirus
```

### Terminologie du risque (suite)

- La menace peut être
  - Interne ou externe
  - Acte accidentel (erreur) ou délibéré
- Origines de la menace
  - Catastrophes naturelles
  - Pirates ( _hackers_ )
  - Compétiteurs
  - États étrangers
  - Crime organisé
  - Terrorisme
  - Ceux à qui on fait confiance ...

### Terminologie du risque (suite)

### Analyse du risque

##### Risque = f (vulnérabilité, menace, impact)

- Difficulté d’évaluer le risque avec précision
- Plusieurs méthodologies
  - ISACA
    - _Risk IT Framework_
  - EBIOS
    - Expression des besoins et identification des objectifs de sécurité
  - MEHARI
    - _Méthode harmonisée d’analyse des risques_
  - OCTAVE
    - _OperationallyCritical Threat, Asset and VulnerabilityEvaluation_
  - Etc.

### Analyse du risque (suite)

- Formule:
- Évaluation de l’impact
- Faire le recensement et la classification des actifs informationnels
  - S’appuyer sur les propriétaires des actifs
  - Exemples
    - Le directeur informatique est le propriétaire du système VPN, des composantes pare-feu
    - Le directeur de la paie est le propriétaire du système informatique qui gère la paie
- Quantifier l’impact en fonction
  - de la classification de l’impact
  - de l’échelle choisie
  - des processus et objectifs d’affaires

##### R(Risque) = P(Probabilité) x I(Impact)

### Analyse du risque (suite)

- Évaluation de l’Impact (suite)
- Définir une échelle d’appréciation de l’impact (Exemple: échelle semi-objective)
- Exemples
  - Le vol d’une base de données de clients pourrait coûter la réputation à une compagnie
  - L’incendie d’une salle de serveurs de petite taille (une dizaine de serveurs) pourrait coûter plus
    de $100.000 à la compagnie

Valeur Impact

```
1 Faibleetc. : perte d’argent ou de données négligeable, courte indisponibilité, effet minime sur la réputation,
```

```
2 Moyenheures, etc.:perte d’argent significative, perte de données peu dommageable, indisponibilité de plusieurs
```

```
3 Élevéetc. : importante perte d’argent, perte d’un grand volume de données, indisponibilité de plusieurs jours,
```

```
4 Très élevéindisponibilité indéfinie, etc.: perte de plusieurs centaines de milliers (millions) de dollars, divulgation de secrets d’affaires,
```

```
R(Risque) = P(Probabilité) x I(Impact)
```

### Analyse du risque (suite)

- Évaluation de la Probabilité
- Il est question de déterminer la probabilité d’observer un impact dans

##### un scénario de risque donné

- Pour les risques accidentels
  - Utilisation d’une échelle exacte: données actuarielles
- Pour les risques délibérés
  - Utilisation d’une échelle semi-objective
    Valeur Probabilité
    1 Faible: probabilité presque nulle
    2 Moyen:peu probable

(^3) Élevé: probable
(^4) Très élevé: très probable
**R(Risque) = P(Probabilité) x I(Impact)**

### Analyse du risque (suite)

- Évaluation de la Probabilité (suite)
- Dépend de l’intervenant (attaquant)
  - Experts en sécurité, experts en systèmes, propriétaire du système, etc.
- Trois grandes composantes de la probabilité

```
R(Risque) = P(Probabilité) x I(Impact)
```

```
Composante Description
```

```
Capacité
```

- Savoir et connaissances
- Outils et argent
- Accès au savoir et aux ressources humaines

```
Opportunité
```

- Espace: avoir un accès physique
- Connectivité: existence d’un lien physique et logique
- Temps: être «là» au bon moment

```
Motivation
```

- Qui: à quiprofite le crime?
- Quoi: que va gagner le malfaiteur?
- Combien: Combien va gagner le malfaiteur?

### Analyse du risque (suite)

- Évaluation de la Probabilité (suite)
- Combinaison des composantes (Capacité, Opportunité, Motivation)
  - Produit des trois composantes?
  - Médiane des trois composantes?
  - Minimum ou maximum des trois composantes?
  - Moyenne des trois composantes?

```
R(Risque) = P(Probabilité) x I(Impact)
```

### Analyse du risque (suite)

- Tableau d’analyse du risque

```
R(Risque) = P(Probabilité) x I(Impact)
```

- Dans cet exemple, la probabilité est le maximum
  des trois composantes: Capacité, Opportunité et
  Motivation

Scénario Capacité Opportunité Motivation Probabilité Impact Risque
1 1 4 3 4 3 12
2 3 2 1 3 2 6
3 2 2 3 3 4 12
...
n 3 1 4 4 2 8

```
Échelle LOG
```

### Analyse du risque (suite)

- Tableau d’analyse du risque
- Interprétation de l’échelle LOG
  - Prioritairement, on doit s’occuper de la zone
    rouge (scénarios 1 et 3)
  - Selon le niveau de tolérance au risque, on
    peut aussi s’occuper de la zone jaune - Scénarios n et 2 - Si on est très tolérant, on accepte tout ce qui se
    trouve dans la zone jaune - Si on est peu tolérant, on contrôle même ce qui
    se trouve dans la zone jaune
  - Le contrôle se fait à travers la mise en place
    de parades (contre-mesures)

### Politique de sécurité

- Permet l’expression et la

###### concrétisation d’une stratégie de

###### sécurité

- Exprime la volonté managériale

###### de protéger les valeurs

###### informationnelles et les

###### ressources technologiques de

###### l’organisation

- Spécifie les moyens (ressources,

###### procédures, outils ...) qui

###### répondent de façon complèteet

###### cohérente aux objectifs

###### stratégiques de sécurité

### Contexte d’une politique de sécurité (suite)

### Politique de sécurité (suite)

- Réalisation de mesures, fonctions, procédures et de services

```
Exemples
Règles de classificationde l’informationet d’utilisation des ressources
Outils:contrôle d’accès, chiffrementdes données, authentification, systèmes
de pare-feuou de détection d’incidents, de surveillance et d’enregistrement,
journalisationet de traçabilité
Des contratsde service: clauses de responsabilité, devoirs et obligations
Des plans de gestion decrise, de secours, de continuité et de reprise
Des plans d’action de poursuite en justice
```

#### Composantes et propriétés d’une

#### politique de sécurité

- La définition de la politique de sécurité doit être:
  - Simple et compréhensible
  - Aisément réalisable
  - De maintenance facile
  - Vérifiable et contrôlable
  - Adoptable par un personnel sensibilisé et formé

### Normes ISO/IEC 27000

Norme Description
ISO 27000 Notions fondamentales, vue d’ensemble et formalisation du vocabulaire.
ISO 27001 Exigences de sécurité d’un système de management de la sécurité.
ISO 27002 Code de bonnes pratiques pour la gestion de la sécurité de l’information.
ISO 27003 Lignes directrices pour la mise en œuvre et l’implémentationdu Système de Management
de la Sécurité de l’Information (SMSI).
ISO 27004 Métriquesdu management de la sécurité de l’information.
ISO 27005 Gestion du risque en matière de sécurité de l’information.
ISO 27006 Exigencespour les organismes auditant et certifiant un SMSI.
ISO 27007 Directives concernantle processus d’audit d’un SMSI.
ISO 27008 Directivespour les auditeurs concernant les contrôles à effectuer dans un SMSI.
ISO 27011 Management de la sécurité de l’informationpour les organismes de télécom.
ISO27031/33 Plan de continuité desaffaires et principes généraux de la sécurité des réseaux.
ISO 27799 Gestion de la sécurité de l’information relativeà la santé.

### Exemple: chapitres de la norme ISO 27002

### Mesures de sécurité

- De la politique aux mesures de sécurité ...
- Il s’agit:
  - De mesures procédurales et managériales
    - Procédures de gestion, de surveillance, d’évaluation, de mises à jour, de sauvegarde, de
      gestion des ressources humaines, etc.
  - D’outils technologiques matériels ou logiciels
    - Protocoles cryptographiques, pare-feu, système de filtrage, de contrôle d’accès, etc.
  - De personnes

### Mesures de sécurité (suite)

- Mesures préventives
  - Barrières afin d’empêcher la réalisation d’incidents, d’une malveillance ou
    d’une erreur
  - Procédures de contrôle d’accès physique, détecteurs de virus ...
- Mesures structurelles
  - Agissent sur la structure, l’architecture, l’organisation du système d’information
  - Cloisonnement d’environnements, redondances, fragmentation de
    l’information, etc.
- Mesures de dissuasion
  - Décourager les agresseurs de mettre à exécution une menace
  - Procédures juridiques et administratives touchant à la sensibilisation et à la
    gestion des ressources humaines, moyens de détection et de traçage, etc.

### Mesures de sécurité (suite)

- Mesures de protection
  - Renforcer la sécurité et la robustesse des ressources et diminuer les
    détériorations suite àla réalisation d’une menace
  - Contrôle de cohérence, détecteurs d’intrusions, d’incendies ... pour se
    protéger des agressions ou d’en limiter l’ampleur
- Mesures palliatives ou correctives
  - Pallier ou réparer les dégâts engendrés par un incident et continuer les
    activités
  - Sauvegardes, plans de continuité, redondances, réparations ou corrections ...
- Mesures de récupération
  - Retour à un fonctionnement normal, limiter les pertes consécutives à un
    sinistre, réduire le préjudice subi en transférant les pertes à de tierces parties
    (assurances)

### Activité 3.1

- Chercher sur Internet des informations sur les derniers malwares

##### découverts. Vous pouvez visiter les sites web des fournisseurs de

##### solutions de sécurité tels que Norton, McAfee, ou Microsoft ou le

##### blogue de la sécurité de l’information de l’Université de Montréal :

##### https://wiki.umontreal.ca/pages/viewpage.action?pageId=130454504

- De quels types sont les malwares reportés?
- Quels types de dommages peuvent-ils causer?
- Quelles plateformes sont les plus vulnérables?
- Trouver des statistiques récentes sur les attaques par malwares.

### Activité 3.2

- Classifier les malwares identifiés dans l’activité précédente selon leur

##### objectif principal dans cet organigramme:

```
Malware par objectif
principal
```

```
Se propager et infecter
d’autres systèmes:
```

```
Dissimuler son existence: Réaliser un profit:
```

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Les malwares

### Contenu

- Virus
- Ver
- Cheval de Troie
- Botnet
- Porte dérobée
- Bombe logique
- Rootkit
- Spyware
- Adware
- Keylogger
- Ransomware

### Malware

- Programme malveillant ou maliciel
- Un programme ou une partie de programme destiné à perturber, altérer

##### ou détruire tout ou partie des éléments logiciels indispensables au bon

##### fonctionnement d’un système informatique

- Entre dans un système informatique (ordinateur)
  - Sans l’autorisation ni la connaissance de son propriétaire
- Fait référence à une large variété de logiciels malicieux néfastes ou

##### gênants

### Virus

- Tout programme d’ordinateur capable d’infecter un autre programme

##### d’ordinateur en le modifiant de façon à ce qu’il puisse à son tour se

##### reproduire

- Un « petit » programme informatique situé dans le corps d’un autre,

##### qui lorsqu’on le lance se charge en mémoire et exécute les instructions

##### que son auteur a programmées

- Code malicieux qui se reproduit sur ​​le même ordinateur
- Ne peut pas se propager automatiquement à un autre ordinateur
  - Repose sur l'action de l'utilisateur pour se propager à d’autres ordinateurs
- Les virus sont attachés aux fichiers
- Les virus se propagent en transférant les fichiers infectés

### Virus (suite)

- Types d’arrangements dans un fichier

##### infecté

```
Split (scission)
```

```
Swiss cheese (fromage suisse)
```

```
Appender (ajout)
```

### Virus (suite)

- Quand un programme infecté est lancé
  - Le virus se propage à un autre fichier sur le même ordinateur
  - Le virus actionne sa charge utile ( _payload_ )
- Le virus peut afficher un message ennuyeux à l’écran
  - Ou peut être beaucoup plus néfaste
- Exemples
  - Éteindre l’ordinateur régulièrement
  - Effacer des fichiers ou reformater le disque dur
  - Changer les paramètres de sécurité de l’ordinateur

### Virus (suite)

- Quelques types de virus
  - Virus mutant
    - Virus réécrits par d’autres utilisateurs afin de modifier leur comportement ou leur
      signature (c.-à-d. la succession de bits qui les identifie)
  - Virus polymorphe
    - Virus qui peuvent prendre plusieurs formes en changeant leur signature et qui ont la
      capacité de chiffrer et de déchiffrer leur signature
  - Rétrovirus (Virus flibustier ou _bounty hunter_ )
    - Virus ayant la capacité de modifier les signatures des antivirus afin de les rendre
      inopérants
  - Virus de secteur d’amorçage (virus de _boot_ )
    - Virus capable d’infecter le secteur de démarrage d’un disque dur (MBR, _Master Boot_
      _Record_ )
  - Virus trans-applicatif (virus de macros)
    - Généralement, les applications Microsoft qui utilisent VBScript du langage de Visual Basic,
      incluant la messagerie électronique

### Ver

- _Worm_
- Exploite les vulnérabilités des applications et des systèmes

##### d’exploitation

- Envoie des copies de lui-même à d'autres machines sur le réseau
- Un ver peut
  - Consommer des ressources
  - Laisser une charge utile pour endommager les systèmes infectés
- Exemple d’actions
  - Supprimer des fichiers
  - Permettre le contrôle à distance de la machine infectée par l’attaquant

### Ver (suite)

- Principe de fonctionnement: exemple du Ver créé par Robert T. Morris

##### de l’université Cornell en 1988

- S’introduire dans une machine de type Unix
- Dresser une liste des machines qui lui sont connectées
- Se faire passer pour un utilisateur auprès des autres machines
- Forcer (utiliser) les mots de passe à partir d’une liste de mots
- Créer un petit programme sur la machine infectée pour pouvoir se reproduire
- Se dissimuler sur la machine infectée, et ainsi de suite ...
- Parades (contre-mesures)
- Mise à jour régulière des systèmes d’exploitation et des applications
- Utilisation d’un pare-feu qui empêche l’accès à des services réseau de façon
  non autorisée

### Virus versus Ver

Action Virus Ver

Propagation à d’autres
ordinateurs

```
Par l’utilisateur En utilisant le réseau
```

Méthode d’infection Insère son code dans
un fichier

```
Exploite les vulnérabilités
d’uneapplication ou d’un
système d’exploitation
```

Requiert une action de
l’utilisateur?

```
Oui Non
```

Peut être contrôlé à distance? Non Oui

### Cheval de Troie

- _Trojan horse_
- Un code (programme) nuisible placé dans un programme sain
- Logiciel qui fait autre chose que ce qui est annoncé
- Un programme informatique ouvrant une porte dérobée ( _backdoor_ ) dans un

###### système pour y faire entrer un pirate ou d’autres programmes indésirables

- Typiquement, un programme exécutable
- Parfois apparaît comme un fichier de données
- Exemple
  - L’utilisateur télécharge un logiciel gratuit
  - Ce programme scanne le système pour chercher des mots de passe et des numéros
    de carte de crédit
  - Puis envoie les informations trouvées à l’attaquant distant via le réseau

### Cheval de Troie (suite)

- Symptômes d’une infection
  - Activité anormale de la carte réseau de l’ordinateur: des données sont transférées en
    l’absence d’activité de la part de l’utilisateur
  - Des réactions anormales de la souris
  - Des ouvertures impromptues de programmes
  - Des plantages à répétition
- Principe de fonctionnement
  - Le pirate insère son code troyen dans un programme (un petit jeu, une copie piratée
    d’un logiciel, etc.)
  - Une fois ce fichier lancé, le cheval de Troie ouvre un port réseau sur la machine pour
    permettre à un pirate d’en prendre le contrôle
  - Le programme peut informer le pirate du bon déroulement de l’opération ou le pirate
    peut utiliser un scanneur de port pour recenser les machines infectées sur le réseau
    mondial
  - Le pirate peut injecter n’importe quel autre programme et créer un Botnet

### Botnet

- Il s’agit de rassemblement de machines piratées et contrôlées à distance par

###### des pirates

- Un ordinateur infecté par un programme qui permet son contrôle à distance

###### est appelé Zombie

- Souvent cheval de Troie, ver ou virus
- Un groupe d’ordinateurs zombies est appelé Botnet
- Un Botnet peut comporter des milliers de machines qui sont loués à des

###### personnes désirant avoir des activités frauduleuses (pollupostage

###### ( spamming ), déni de service distribué (DDOS), propagation de malwares,

###### manipulation des sondages en ligne, etc.)

- Le protocole HTTP est souvent utilisé pour contrôler les zombies à distance
- Peut rester actif pendant plusieurs années
- Un large pourcentage de zombies sont accessibles à tout moment
  - Grâce à la démocratisation de l’accès à Internet

### Porte dérobée

- _Backdoor_
- Code malicieux qui change les paramètres de sécurité du système

##### informatique pour donner accès au système infecté

- Pratique courante par les développeurs d’applications
  - L’intention est d’enlever le _backdoor_ dans la version de production de
    l’application

### Bombe logique

- Code malveillant qui reste dormant
  - Déclenché à une date donnée ou suite à un évènement logique spécifique
  - Puis exécute son activité malicieuse
- Difficile à détecter avant son déclenchement
- Exemple
  Description Raison de l’attaque Résultats
  Une bombe logique a
  été implantée dans un
  réseau d’ordinateurs
  d’une compagnie de
  services financiers.
  Conséquence: des
  données sensibles ont
  été supprimées de 1000
  ordinateursde la
  compagnie.

```
Un employémécontent
qui croyait que cet
évènement allait faire
chuter la valeur en
bourse de l’action de
cette compagnie et qu’il
pourra en profiter.
```

```
La bombe s’est
déclenchée mais
l’employéa été attrapé
et condamné à 8 ans de
prison et 3,1 millions de
$ de compensation à
son ex employeur.
```

### Rootkit

- Outil logiciel utilisé pour cacher l’existence d’autres logiciels

##### malveillants

- Nettoyer les entrées correspondantes dans les fichiers de

##### journalisation ( log )

- Remplacer certains fichiers du système d’exploitation
  - Avec des versions conçues pour ignorer les activités malveillantes
- Détecter un rootkit peut être effectuée par
  - La plupart des antivirus actuels
  - Des utilitaires qui comparent le contenu des fichiers avec la version originale
    (Tripwire, AIDE, Windows Defender Offline, etc.)
- Supprimer un rootkit peut s’avérer difficile
  - Écraser le rootkit, reformater le disque dur, réinstaller les systèmes
    d’exploitation, etc.

### Spyware

- Espiogiciel
- Un programme chargé de recueillir des informations sur l’utilisateur de
  l’ordinateur dans lequel il est installé (on l’appelle parfois mouchard)
- Ces informations sont envoyées à l’entité qui le diffuse pour lui permettre de
  dresser le profil des internautes (on parle de profilage)
- Les informations récoltées peuvent être:
  - Les adresses Web (URL) des sites visités
  - Les mots-clés saisis dans les moteurs de recherche
  - L’analyse des achats réalisés via Internet, voire les informations de paiement bancaire
  - Des informations personnelles (numéro d'assurance sociale, date de naissance, etc.)
- Les spywares s’installent généralement en même temps que d’autres logiciels
  (gratuiciels ( _freeware_ ) ou partagiciels ( _shareware_ ) en général) - La gratuité est obtenue contre la cession de données à caractère personnel

### Spyware (suite)

- Souvent utilisé pour
  - La publicité
  - Collecter des informations personnelles
  - Changer la configuration de l’ordinateur
- Effets négatifs
  - Consommation de mémoire vive
  - Utilisation d’espace disque
  - Mobilisation des ressources du processeur
  - Plantage d’autres applications
  - Gêne ergonomique: ouverture d’écrans publicitaires ciblés en fonction des
    données collectées par exemple

### Adware

- Programme qui livre un contenu publicitaire
  - D’une manière non prévue et non voulue de l’utilisateur
- Afficher des bannières publicitaires et des _popups_
- Ouvrir, aléatoirement, de nouvelles fenêtres du navigateur
- Peut effectuer le suivi ( _tracking_ ) des activités de l’utilisateur en ligne
- Inconvénients
  - Affichage de contenus indésirables
  - Dégradation des performances de l’ordinateur et perte de productivité
  - Nuisance

### Keylogger

- Littéralement « enregistreur de touches »
- Dispositif chargé d’enregistrer les frappes de touches du clavier et de les

###### enregistrer, à l’insu de l’utilisateur ➔ dispositif d’espionnage!

- Peut servir pour récupérer les mots de passe et d’autres informations

###### personnelles des utilisateurs de l’ordinateur infecté

- Certains Keylogger sont capables d’enregistrer
  - Les mots de passe
  - Les URL visitées
  - Les courriels consultés ou envoyés
  - Les fichiers ouverts
  - Voire, créer une vidéo retraçant toute l’activité de l’ordinateur
- L’information enregistrée est récupérée plus tard par l’attaquant

### Keylogger (suite)

- Peut être logiciel ou matériel
- Parades
  - Vigilance: ne pas installer de logiciels dont la provenance
    est douteuse
  - Prudence: lors de la connexion à partir d’un ordinateur
    tiers

### Ransomware

- Rançongiciel
- Logiciel malveillant don’t le but est de soutirer de l’argent à leurs victimes
- Il existe deux types de ransomwares
  - Logiciels qui se contentent de faire peur aux utilisateurs:l’ordinateur de la victime
    devient très difficile à utiliser, car le logiciel bloque la plupart des applications
  - Les ransomwares «chiffreur»:beaucoup plus agressifs, car ils chiffrent tout ou partie
    des espaces de stockage de données de la victime - Les données sont chiffrées en tâche de fond - Le malware affiche en suite un message demandant le versement d’une rançon contre un
    moyen de déchiffrer les données
- Parades
  - Toujours utiliser un antivirus à jour
  - Procéder à des sauvegardes périodiques: en utilisant des solutions d’infonuagique
    ( _Cloud_ ) par exemple

### Activité 4. 1

- Explorer les liens suivants sur la vulnérabilité _Heartbleed_ :
  1. [http://fr.wikipedia.org/wiki/Heartbleed](http://fr.wikipedia.org/wiki/Heartbleed)
  2. [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-) 2014 - 0160
  3. [http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-) 2014 - 0160
  4. [http://heartbleed.com/](http://heartbleed.com/)
- Quelles versions de l’application OpenSSL sont-elles affectées par cette

##### vulnérabilité?

- Quels sont les systèmes d’exploitation affectés par cette vulnérabilité?
- Est-ce que les systèmes de détection d’intrusion (IDS) peuvent bloquer

##### les attaques qui exploitent cette vulnérabilité?

### Activité 4. 1 (suite)

- S’agit-il d’une attaque homme-au-milieu (man-in-the-middle ou

##### MITM)? Pourquoi?

- Qui a découvert ce bogue en premier?
- Explorer les bases de données des vulnérabilités des questions # 2

##### (CVE) et # 3 (NVD).

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Les techniques d’attaque sur

## les systèmes informatiques

```
1
```

### Contenu

- Attaques de mot de passe
- Usurpation d’adresse IP
- Attaques par déni de service
- Attaques « homme au milieu »
- Attaques par débordement de tampon
- Attaques biométriques
- Attaques par ingénierie sociale

### Attaques de mot de passe

- Identifiant / mot de passe
  - Moyen de connexion à un système informatique
- Bloquer temporairement le compte d’un utilisateur après un certain

##### nombre de tentatives non réussies ➔ difficile de s’infiltrer dans de tels

##### systèmes de cette manière

- Bloquer l’ensemble des comptes utilisateurs ➔ Déni de service
- Moyen permettant au pirate d’obtenir les mots de passe
  - Keylogger
  - Ingénierie sociale
  - Espionnage
  - Etc.

### Attaques de mot de passe (suite)

- Suite à une intrusion à un premier compte utilisateur, si le pirate réussi

##### à obtenir le fichier chiffré des mots de passe

- Attaque par force brute
- Attaque par dictionnaire
- Attaque hybride
- Utilisation du calcul distribué
- Puissance des ... cartes graphiques
- ~1 000 000 000 mots de passes / seconde (supercalculateur d’une université
  par exemple)
- 392 262 404 189 mots de passe / seconde (distributed.net: projet RC5 72 )
- 92 000 participants
- Informatique en nuage ( _cloud computing_ )

### Choix de mot de passe

- Plus un mot de passe est simple, plus il est facile de le casser
  - 4 chiffres ➔10 000 possibilités (10^4 )
  - 4 lettres ➔456 972 possibilités (26^4 )
  - Chiffres, lettres (minuscules et majuscules) et caractères spéciaux ...
- Politique de sécurité en matière de mots de passe
  - Une longueur minimale
  - La présence de caractères particuliers
  - Un changement de casse (minuscule et majuscule)
  - Durée d’expiration des mots de passe
  - Utiliser des logiciels de cassage de mots de passe en interne

#### Choix de mot de passe (suite)

- Mots de passe à éviter
  - Votre identifiant
  - Votre nom
  - Le nom d’un proche
  - Un mot du dictionnaire
  - Un mot à l’envers
  - Un mot suivi d’un chiffre

```
Source: https://www.comparitech.com/news/minecraft-qwerty-and-india123-among-2025s-most-common-passwords-report/
```

```
En 2025 ...
```

### Usurpation d’adresse IP

- _IP spoofing_
- Remplacer l’adresse IP de l’expéditeur d’un paquet IP par l’adresse IP

##### d’une autre machine

- Permet à un pirate d’envoyer des paquets de façon anonyme
- But: faire passer des paquets sur un réseau sans que ceux-ci ne soient

##### interceptés par le système de filtrage de paquets (pare-feu)

### Usurpation d’adresse IP (suite)

- Modification de l’en-tête du datagramme IP

### Usurpation d’adresse IP (suite)

- Les datagrammes IP encapsulent des segments TCP
  - Numéro d’ordre
  - Drapeaux
    - SYN
    - ACK
    - FIN
    - RST
    - Etc.
  - Etc.

### Usurpation d’adresse IP (suite)

- Les trois étapes pour établir une connexion TCP ( _three-way_

##### handshake )

- Le client envoie un paquet SYNau serveur
- Le serveur répond par un paquet SYN-ACK
- Le client répond par un paquet ACK

### Usurpation d’adresse IP (suite)

- La machine usurpée va répondre par un paquet RST
  - Ce qui mettra fin à la connexion
  - Attaque à l’aveugle ( _blind attack_ )
- Le travail du pirate consiste à invalider la machine

###### usurpée

- c.-à-d., la rendre injoignable durant toute la durée de
  l’attaque
- Prédiction des numéros de séquence émis par la cible
- _Source routing_
- Indiquer une route de retour spécifique pour les paquets
- Le pirate envoie des accusés de réception à la cible

###### pour maintenir la communication

### Attaques par déni de service

- _Denial of Service_ (DoS)
- But: rendre indisponible pendant un temps indéterminé les services ou

##### les ressources d’une organisation

- Nuire à la réputation et/ou au bon fonctionnement d’organisations

##### ayant une présence sur Internet

- La plupart des attaques DoS exploitent des failles liées à

##### l’implémentation d’un protocole de la pile TCP/IP

```
Attaque DDoS
Trafic de l’attaque DDoS
```

```
Trafic légitime
```

```
Site Web indisponible à cause de l’attaque DDoS
```

### Attaques par déni de service (suite)

- Deux types
  - Déni de service par saturation
    - Submerger une machine de requêtes
  - Déni de de service par exploitation de
    vulnérabilité - Exploiter une faille du système cible
- Déni de service distribué ( _Distributed_

##### Denial of Service: DDoS )

- Lorsque provoqué par plusieurs
  machines

### Attaques par déni de service (suite)

- Attaque par réflexion
  - _Smurf_
  - Trouver une liste de serveurs de diffusion
  - Falsifier l’adresse IP source du message ping
- Attaque par amplification
  - Utiliser des serveurs dont la réponse à une
    requête renvoie bien plus de données que la
    requête originale
  - Network Time Protocol (NTP) ➔la réponse est
    environ 200 fois la taille du paquet original
  - Protocoles DNS et SMTP ➔ taux d’amplification
    allant jusqu’à 650 fois le flux original

### Attaques par déni de service (suite)

- Attaque du ping de la mort
  - _Ping of death_
  - Créer un paquet IP dont la taille totale excède la taille maximum autorisée
    (65 536 octets)
  - Repose sur les vulnérabilités des vieilles implémentations des protocoles TCP/IP
- Attaque par fragmentation
  - _Fragment attack_
  - Exploite le principe de fragmentation du protocole IP
    - Fragmenter les paquets de taille importante en plusieurs paquets IP possédant tous un
      numéro de séquence et un numéro d’identification commun
    - À la réception, le destinataire réassemble les paquets grâce aux valeurs de décalage ( _offset_ )
      qu’ils contiennent
  - Insérer dans des paquets fragmentés des informations de décalage erronées
  - Les vides et les recoupements ( _overlappings_ ) peuvent provoquer une instabilité du
    système
  - Les systèmes récents ne sont plus vulnérableà cette attaque

### Attaques par déni de service (suite)

- Attaque SYN
  - _TCP SYN Flooding_
  - Envoyer un grand nombre de requêtes SYN à
    une machine avec une adresse IP source
    inexistante ou invalide
  - La machine cible met en file d’attente (dans
    une structure de données en mémoire) les
    connexions « à moitié» ouvertes
  - Attend de recevoir les ACKscorrespondants
  - Un mécanisme d’expiration des connexions
    « à moitié» ouvertes après un certain délai
    existe mais il peut ne pas suffire
  - Plantage ou redémarrage des systèmes
    vulnérables

### Attaques par déni de service (suite)

- Attaque par requêtes élaborées
  - Envoyer en masse des requêtes légitimes à la couche applicative
  - Rendre inaccessible un site Web ou un service en lui faisant traiter des
    demandes qui sollicitent beaucoup de ressources (base de données par
    exemple)
  - Requiert une analyse fine de la cible
    - Pages HTML qui ne sont pas en cache
    - Pages qui requièrent beaucoup de données
    - Pages qui créent des erreurs sur le serveur
    - Module du site Web connu pour une faille particulière
    - Etc.
- Parades
  - Veille active sur les nouvelles attaques et vulnérabilités
  - Appliquer les correctifs ( _patchs_ ) et les mises à jour logicielsC

#### Attaques par déni de service (suite) - Réalité des attaques

```
Source: https://blog.cloudflare.com/ddos-threat-report-for- 2025 - q2/
```

- Attaque de pointe (2025, 2ièmetrimestre):
  - Intensité: 7.3 térabits par seconde (Tbps) et4.8 milliards de paquets par
    seconde
  - Durée:45 secondes

```
Origine des attaques Attaques DDoS par année
```

### Attaques des failles TLS/SSL

- (2009) dissymétrie de charge entre le client et le serveur

##### (~1:15)

- Le client envoie de nombreuses demandes de renégociation des
  paramètres de sécurité - Générer une nouvelle clé de chiffrement pour la connexion en cours - Grande consommation des ressources sur le serveur Web
- DDoS contre des cibles utilisant le protocole HTTPS
- (2014) Heartbleed
- Implémentation OpenSSL (depuis 2012)
- Traitement de mémoire incorrect pour les paquets du module
  de pulsation ( _heartbeat_ ) du protocole TLS
- Permet à un attaquant de lire la mémoire d'un serveurou
  d'unclient pour récupérer des informations confidentielles (clés
  privées p. ex.)

### Attaques des failles TLS/SSL (suite)

- Heartbleed: comment ça marche?
  **Fonctionnement normal Fonctionnement malicieux**

### Attaques « homme au milieu »

- Attaque de l’homme au milieu ou attaque de l’intercepteur
- _Man in the middle_
- Un pirate écoute une communication entre deux interlocuteurs et

##### falsifie les échanges afin de se faire passer pour l’une des parties

##### communicantes

- Écouter le réseau à l’aide d’outils d’écoute du réseau
  - Wireshark
  - tcpdump
  - Etc.

### Attaques « homme au milieu » (suite)

- Attaque par rejeu ( _replay attack_ )
  - Intercepter des paquets de données et les rejouer
    - Les retransmettre tels quels au serveur destinataire (sans aucun déchiffrement)
  - Le pirate espère bénéficier des droits de l’utilisateur légitime
  - Exemple: envoyer un paquet qui contient un nom d’utilisateur et un mot de
    passe chiffrés à un serveur pour s’authentifier

### Attaques « homme au milieu » (suite)

- Détournement de session TCP ( _TCP session hijacking_ )
  - Intercepter une session TCP initiée entre deux machines afin de la détourner
    - L’authentification s’effectue uniquement à l’ouverture de la session
  - Prédire les numéros de séquence ( _source routing_ )

### Attaques « homme au milieu » (suite)

- Attaque du protocole ARP
  - _Address Resolution Protocol_ (ARP) permet de retrouver l’adresse IP d’une
    machine en connaissant son adresse physique (adresse MAC)
  - S’interposer entre deux machines locales en envoyant un paquet ARP falsifié
    indiquant que l’adresse MAC de l’autre machine a changé - L’adresse MAC fournie est celle de l’attaquant
  - Les deux machines cibles vont mettre à jour leur table dynamique appelée
    _cache ARP_ - _ARP Cache poisoning_ - _ARP spoofing_ - _ARP redirect_

### Attaques « homme au milieu » (suite)

- Attaque du protocole ARP (suite)

```
Fonctionnement normal
```

```
Fonctionnement avec
attaque du protocole ARP
```

### Attaques « homme au milieu » (suite)

- Attaque du protocole BGP
  - _Border Gateway Protocol_
  - Utilisé entre les routeurs des organisations qui structurent Internet
  - Quelle est la route la plus courte pour chaque paquet traversant Internet? ➔
    Utilisation de tables de routage
  - Un pirate peut détourner le trafic Internet destiné à un site donné vers la
    machine de son choix - Introduire (ou prendre le contrôle) d’un routeur - Modifier sa table de routage - Cette modification sera reproduite et généralisée sur Internet - Exemple: cas de Pakistan Telecom et Youtube
  - Parade: _Secure BGP_

### Attaques par débordement de tampon

- _Buffer overflow_
- Exécution de code arbitraire par un programme en lui envoyant plus de

###### données qu’il n’est censé en recevoir ➔donner un accès au système

- Programmes acceptant des données en entrée (passées en paramètres)
- Exemple: la fonction strcpydu langage C
- Parades
  - Utilisation de langages à contexte d’exécution managé implémentant la vérification de
    bornes des tableaux (Exemple: le langage de programmation Java)
  - Bannir l’utilisation des fonctions dites « non protégées »: préférer strncpyà
    strcpypar exemple
  - Rendre la pile non exécutable
  - Etc.

### Attaques par débordement de tampon (suite)

```
IFT 2830 -Sécurité des systèmes informatiques 28
```

```
Instructions du
programme
```

```
Tampon des données de
type numérique
```

```
Tampon des données de
type caractère Adresse de retour
```

```
Traitement normal
```

```
Instructions du
programme
```

```
Tampon des données
numérique
```

```
Tampon des caractères Adresse de retour
```

```
Débordement de tampon
```

```
Le programme réalise un saut vers l’instruction suivante
```

```
Malware débordementDonnées du Nouvelle adresse de retour
```

```
Le programme
réalise un saut vers
le code du malware
```

### Attaques par débordement de tampon (suite)

- Cas de la fonction strcpy

### Attaques biométriques

- L’identification biométrique est basée sur le principe de l’unicité de

##### certains caractères d’un individu

- Empreinte digitale
- Reconnaissance faciale
- Iris
- Agencement des veines dans un doigt ou au fond de l’œil
- ADN
- Etc.
- Le matériel de sécurité biométrique peut faire l’objet d’attaques pour

##### récupérer les droits d’accès d’un individu

- L’efficacité dépend fortement de la qualité du matériel

### Attaques biométriques (suite)

- Empreintes digitales
  - Récupérer l’empreinte digitale laissée par un individu et la réutiliser
- Reconnaissance faciale
  - Il suffit de montrer une image de la personne pour tromper le système de reconnaissance
- Parades
  - Combiner plusieurs techniques biométriques
    - La reconnaissance de l’empreinte digitale avec la reconnaissance de la structure interne des veines
      du doigt par exemple
  - Mixer plusieurs systèmes d’indentification
    - Croiser l’identification biométrique avec d’autres techniques comme une carte à puce ou un mot de
      passe par exemple

### Attaques par ingénierie sociale

- Collecter les informations directement des individus
  - Repose sur leur confiance
- Approches psychologiques
  - Persuasion (persuader la victime de fournir une information ou de prendre des
    actions)
  - Flatteries
  - Conformité
  - Amitié
- Réseaux sociaux
  - Collecter des informations personnelles sur les individus (noms, noms des
    proches, noms des amis, noms des employés d’une entreprise, etc.)
  - Trouver des mots de passe ou passer pour ces individus

### Attaques par ingénierie sociale (suite)

- Attaques de type trou d’arrosage ( _watering hole_ )
  - Repose à la fois sur l’exploitation de failles informatiques et l’utilisation de
    l’ingénierie sociale - S’introduire dans l’un des sites Web ou services utilisés par les employés d’une entreprise
    et y insérer un code malveillant à télécharger (cibler l’entreprise par ses adresses IP) - Une fois le contenu malveillant téléchargé par un employé, s’attaquer aux infrastructures
    de l’entreprise ou récupérer des informations renvoyées par le code malveillant
- L’aide de la voix sur IP (VoIP)
  - Appeler un employé en affichant un numéro interne de l’entreprise
  - L’employé victime sera donc plus enclin à donner des renseignements
    sensibles

### Attaques par ingénierie sociale (suite)

- Attaque par réinitialisation du mot de passe
  - Solliciter le service en ligne pour demander la réinitialisation du mot de passe
    d’un compte - Détenir des informations personnelles sur le détenteur du compte - Intercepter le courriel de réinitialisation si on contrôle le compte de secours ➔le niveau
    de sécurité du compte est celui du maillon le plus faible - Créer un message (courriel ou SMS) qui renverra la victime à une page de réinitialisation
    contrefaite (hameçonnage ou _phishing_ )
- Attaque par usurpation d’identité informatique
  - Tromper directement les utilisateurs: hameçonnage ( _phishing_ )
    - Faire passer un site Web pour un autre
  - Tromper les logiciels et les procédures automatisées du système d’exploitation
    1.  Générer de de vrais faux certificats numériques
    2.  Détourner des requêtes DNS ( _DNS poisoning_ )

### Attaques par ingénierie sociale (suite)

```
Détournement des requêtes DNS
```

```
Serveur DNS de l’attaquant
ns.mauvais.ca
```

```
192.168.1.1
```

**5.** 192.168.1.1(adresse IP de l’attaquant)

```
Victime
```

```
AttaquantAdresse IP: 192.168.1.1
```

### Attaques par ingénierie sociale (suite)

- Spam
  - Courriels non sollicités
  - Peut être un véhicule pour la distribution de malwares
- Canulars ( _hoaxes_ )
  - Fausses alertes ou revendications
  - Peut constituer la première étape d’une attaque
- Fouille de poubelles ( _Dumpster diving_ )
  - Fouiller dans les poubelles pour trouver des informations utiles
- Talonnage ( _Tailgating_ )
- Regards indiscrets _(shoulder surfing)_
- _Deep fake_

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Attaques sur les réseaux

## informatiques

```
1
```

### Contenu

- Étapes d’une attaque sur un réseau informatique
- Collecte d’informations
- Balayage
- Repérage des failles
- Intrusion
- Extension des privilèges
- Compromission
- Porte dérobée
- Nettoyage des traces

### Terminologie (rappels)

- Menace ( _threat_ )
  - Une action susceptible de nuire
- Vulnérabilité (faille ou brèche)
  - Niveau d’exposition à une menace dans un contexte particulier
- Contre-mesure (parade)
  - L’ensemble des actions mises en œuvre en prévention de la menace
  - Pas uniquement des solutions techniques (formation, sensibilisation, ensemble de
    règles, etc.)
- Sur Internet, les attaques sont automatisées à raison de plusieurs attaques

###### par seconde

Une attaque est l’exposition d’une vulnérabilité d’un système informatique (système
d’exploitation, logiciel ou même l’utilisateur) à des fins non connues par l’exploitant
du systèmeetgénéralementpréjudiciables.

### Motivation des attaquants

- Obtenir un accès au système
- Voler des informations, telles que des secrets industriels ou des

##### propriétés intellectuelles

- Recueillir des informations personnelles sur un utilisateur
- Récupérer des données bancaires
- S’informer sur une organisation
- Troubler le bon fonctionnement d’un service
- Utiliser un système comme « rebond » pour attaquer un autre système
- Utiliser les ressources d’un système (puissance de calcul, bande

##### passante, etc.)

### Étapes d’une attaque sur une réseau informatique

```
Collecte d informations
```

```
Balayage
```

```
Repérage des failles
```

```
Intrusion
```

```
Compromission
```

```
Extension de privilèges
```

```
Porte dérobée
```

```
Nettoyage des traces
```

```
Déni de service
```

### Collecte d’informations: quoi?

- Rassembler l’information disponible sur la cible
  - Adressage IP
  - Nom du domaine
  - Protocoles réseau
  - Services activés
  - Architecture des serveurs
  - etc.

### Collecte d’informations: comment?

- Consultation des bases de données publiques
  - [http://www.iana.net](http://www.iana.net)
  - [http://www.ripe.net](http://www.ripe.net) (Europe)
  - [http://www.arin.net](http://www.arin.net) (États-Unis)
- Consultation de moteurs de recherche
  - Structure d’une entreprise
  - Nom de ses principaux produits
  - Noms de certains employés
  - Etc.
- Outils: whois, Sam Spade, Paros
- Ingénierie sociale

### Collecte d’informations: comment? (suite)

- Fouille de poubelles ( _dumpster diving_ )
- Descriptions d’offres d’emploi
  - Types des systèmes utilisés
  - Savoir s’il manque des administrateurs système, etc.
- Nom et contact des responsables
- Questions des employés sur les forums
- Communiqués de presse
- Partenaires
- Réseaux sociaux

### Collecte d’informations: contre-mesures

- Limiter et contrôler les informations publiques
- Responsabilité partagée entre la direction, les relations publiques et

##### les ressources humaines

- Faire des recherches sur son organisation pour voir les informations

##### qui filtrent

- Analyser les pages Web qui référencent le site Web de l’organisation

### Balayage

- Balayer (scanner) le réseau
  - Déterminer à l’aide d’un outil logiciel appelé scanneur ( _scanner_ )
    - Les adresses IP actives sur le réseau
    - Les ports ouverts correspondant à des services accessibles
    - Les systèmes d’exploitation des machines et les versions des applications associées aux
      ports: caractérisation de version
  - L’acquisition active d’informations
    - Envoyer un grand nombre de paquets avec des en-têtes caractéristiques
    - Exemple: Nmap
  - L’acquisition passive d’informations
    - Analyser l’évolution des valeurs des champs sur des séries de paquets (fragments)
    - Exemple: Siphon

### Balayage (suite)

- Lecture de bannières
  - Examiner les fichiers journaux ( _logs_ ) des outils utilisés pour connaître les
    adresses IP des machines connectées au réseau et les ports ouverts sur celles-
    ci
  - Exemple: pour connaître la version d’un serveur HTTP

### Balayage: Traceroute

- Envoie de paquets ICMP en modifiant le champ TTL ( _Time To Live_ )
- Le routeur ou l’hôte qui reçoit un paquet avec TTL = 1 va le rejeter et

##### envoyer un message Time-to-live exceeded in transit à la source

- En incrémentant la valeur du TTL, on peut obtenir la liste des routeurs

##### qui nous séparent de la cible

- En exécutant des requêtes traceroute sur les adresses de

##### l’organisation, on obtient une bonne image de la structure

##### (cartographie) du réseau

- Contre-mesures
  - Bloquer les messages sortants de type ICMP _Time-to-live exceeded in transit_
  - Bloquer les messages pingentrants
  - Bloquer les paquets avec un TTL faible

### Balayage: Portscan

- Savoir quels ports sont ouverts sur un système (les « portes » ouvertes

##### sur le système)

- Consiste généralement à envoyer un paquet en direction de chaque port (TCP
  et UDP): 65536 ports possibles (32 bits)
- On peut se contenter des ports connus
  - 80/TCP = HTTP, 443/TCP = HTTPS, 53/UDP et 53/TCP = DNS, 25/TCP =
    SMTP, 110/TCP = POP3, etc.
- Contre-mesures
- Fermer les ports non utilisés
- Désactiver les protocoles non utilisés
- Utiliser un pare-feu _stateful_

### Écoute du réseau

- Un analyseur réseau ( _sniffer_ ) est un dispositif qui permet d’écouter le

##### trafic d’un réseau (capturer les informations qui y circulent)

- Mode _promiscuous_
  - Écouter tout le trafic passant par une interface (carte) réseau (Ethernet, Wi-Fi,
    etc.)
- Il sert généralement aux administrateurs pour diagnostiquer les

##### problèmes sur leurs réseaux et connaître le trafic qui y circule

- Les systèmes de détection d’intrusion (IDS) sont basés sur un sniffer

##### pour la capture des trames

- Peut également servir à une personne malveillante ayant un accès

##### physique au réseau pour collecter des informations

- Risque plus important sur les réseaux sans-fil (Wi-Fi, Bluetooth, etc.)

### Écoute du réseau (suite)

- Exemples d’outils
  - Wireshark
  - TCP dump / WinDump
  - Microsoft Message Analyzer
- Contre-mesures
  - Utiliser des protocoles chiffrés
  - Segmenter le réseau afin de limiter la diffusion des informations
    - Préférer l’utilisation de commutateurs ( _switch_ ) à celle des concentrateurs ( _hub_ )
  - Utiliser un détecteur d’analyseurs réseau ( _sniffers_ ): sonder le réseau à la
    recherche de matériel utilisant le mode _promiscuous_
  - Réduire la puissance de transmission des dispositifs sans-fil

### Repérage des failles

- Déterminer si des vulnérabilités (failles) existent
- Scanneurs de vulnérabilités
  - Nessus
  - SAINT
- Bases de données de vulnérabilités
  - CVE - Common Vulnerabilities and Exposures: cve.mitre.org
  - [http://www.securityfocus.com](http://www.securityfocus.com)
  - [http://www.insecure.org](http://www.insecure.org)
  - Etc.

### Intrusion

- Le pirate a déjà dressé une cartographie des ressources et des

##### machines présentes sur le réseau

- Le pirate a besoin d’accéder à des comptes valides sur les machines

##### qu’il a recensées. Plusieurs méthodes utilisées:

- L’ingénierie sociale
- La consultation de l’annuaire(ou des services de messagerie ou de partage de
  fichiers): trouver des noms d’utilisateur valides
- L’exploitation des vulnérabilitésdes logiciels
- Les attaques par force brute( _brute force cracking_ ): essayer, de façon
  automatique, différents mots de passe sur une liste de comptes

### Exploit

- Un exploit est un programme informatique mettant en œuvre

##### l’exploitation d’une vulnérabilité publiée ou non

- Chaque exploit est spécifique à une version d’une application, car il

##### permet d’en exploiter les failles

- Types d’exploits
  - Extension des privilèges
    - Permettre de contrôler les programmes exécutés avec les privilèges d’administrateur
  - Provocation d’une erreur système
- Souvent écrit en langage C ou en Perl

### Extension des privilèges

- Le pirate va chercher à élargir ses privilèges après avoir obtenu un ou

##### plusieurs accès au réseau en se connectant à un ou plusieurs comptes

- Accès _root_ : super-utilisateur ou superadministrateur ➔

##### compromission

- Le pirate a alors la possibilité d’examiner le réseau à la recherche

##### d’informations supplémentaires

- Installer un analyseur réseau ( _sniffer_ )
- Attaquer d’autres comptes (ou machines, serveurs, etc.) dans le réseau

### Compromission et porte dérobée

- Compromission
  - Exploit des relations d’approbation existantes entre les différentes machines
  - Usurpation d’identité ( _spoofing_ )
  - Permettre au pirate de s’introduire dans des réseaux privilégiés auxquels la
    machine compromise a accès
- Porte dérobée
  - Installer une application afin de créer une faille de sécurité
    - Porte dérobée ou trappe ( _backdoor_ )

### Nettoyage des traces

- Effacer les traces de passage de l’intrus des machines dans lesquelles il

##### s’est introduit

- Supprimer les fichiers qu’il avait créés
- Nettoyer les journaux des activités ( _logs_ )
- Installer un _rootkit_
- Remplacer les outils d’administration du système par des versions modifiées
  pour masquer la présence de l’intrus
