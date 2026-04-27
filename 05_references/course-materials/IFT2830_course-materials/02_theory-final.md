# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## La cryptographie

```
1
```

## Contenu

- Cryptographie
- Algorithmes de hachage
- Cryptographie symétrique
- Cryptographie asymétrique
- Cryptographie quantique
- Stéganographie

## Cryptographie: définitions

- Mots grecs : _kruptos_ et _graphein_ (caché et écrire)
- Terme générique qui désigne l’ensemble des techniques permettant

#### de chiffrer (crypter) l’information pour la rendre inintelligible

#### (incompréhensible)

- La science de la transformation de l’information dans un format

#### sécurisé pour qu’elle puisse être transmise et stockée sans que les

#### personnes non autorisées ne puisse y avoir accès

- Origines
  - Jules César (100 -44 av. J.-C.)
    - Décaler chaque lettre alphabétique trois positions dans l’alphabet : A ➔D, B ➔E, etc.

## Cryptographie: définitions (suite)

- Chiffrement ( _Encryption_ )
  - Changer le texte d’origine en un message secret en utilisant la cryptographie
- Déchiffrement ( _Decryption_ )
  - Transformer le message secret dans sa forme originale
- Message en clair ( _Cleartext / Plaintext_ )
  - Données stockées ou transmises sans chiffrement
  - Données à chiffrer
- Cryptogramme( _ciphertext_ )
  - Message chiffré
- Clé ( _key_ )
  - Valeur mathématique utilisée par l’algorithme de chiffrement pour produire une message
    chiffré ou un cryptogramme ( _ciphertext_ )
  - Utilisée par le processus inverse pour le déchiffrement

## Cryptographie: définitions (suite)

```
Algorithme de
Message en clair chiffrement
Cryptogramme
```

```
Clé
```

```
Message en clair Cryptogramme
```

```
Clé
```

```
Algorithme de
déchiffrement
```

```
Transmission
du message
```

```
Mémo confidentiel
Bonjour ...
```

```
Mémo confidentiel
Bonjour ...
```

## Cryptographie et sécurité

- La cryptographie protège l’information en fournissant
  - Confidentialité
    - Seulement les entités autorisées peuvent la consulter
  - Intégrité
    - S’assurer que l’information est correcte et non altérée
  - Disponibilité
    - Les utilisateurs autorisés peuvent y avoir accès
  - Authentification de l’émetteur
  - Non répudiation
    - Prouver que l’utilisateur a effectuer une action

## Algorithmes cryptographiques

- Catégories
  - Algorithmes de hachage
  - Algorithmes de cryptographie symétrique
  - Algorithmes de cryptographie asymétrique

## Algorithmes de hachage

- Le type le plus simple parmi les algorithmes cryptographiques
- Création d’un résumé(condensé ou _hash_ ) unique pour chaque

#### message

- Le résumé ne peut pas être utilisé pour retrouver le message d’origine
  - Utilisé principalement pour des raisons de comparaison
- Exemple
  Insérer carte Saisir
  code PIN

```
Condensé ( hash ) stocké
sur la carte
Comparer le condensé stocké sur la carte à celui
calculé à partir du PIN
```

## Algorithmes de hachage (suite)

- Caractéristiques
  - Taille fixe
    - Les message courts et longs doivent produire des résumés de même taille
    - Exemple
    - Deux message différents ne peuvent pas produire le même résumé (collision)
  - Original
    - On ne peut pas créer un message pour obtenir un résumé prédéfini
  - Sûr ( _secure_ )
    - Le résumé produit ne peut pas être renversé pour trouver le message d’origine

```
Résumé d’une lettre 86be7afa339d0fc7cfc 785e72f578d
Résumé d’un million de lettres 4a7f5723f954 eba1216c9d8f6320431f
```

## Algorithmes de hachage (suite)

- Fonction à sens unique : f
  - Facile à calculer y = f(x) à partir de x, mais difficile à calculer xà partir de y
  - Exemples :
    - Deux grands nombres premiers, pet q. On pense que la fonction f(p,q) = p\*q, est à sens
      unique
    - Soit n, un nombre composé. On pense que la fonction g(x) = x^2 mod n, qui calcule les
      carrés modulo n, est à sens unique

## Algorithmes de hachage (suite)

- Utilisations
  - Déterminer l’intégrité des messages
    - Peut protéger contre les attaques homme-au-milieu ( _man-in-the-middle_ )
  - Authentification
    - Hashed Message Authentication Code (HMAC)
      - Le chiffrement du résumé fournit une sécurité améliorée
      - Utilise une clé secrète partagée entre l’émetteur et le récepteur
      - Le récepteur utilise la clé pour déchiffré le résumé
  - Sites de téléchargement
    - Vérifier l’intégrité des fichiers téléchargés
      Message original

```
Bonne nouvelle de hachageAlgorithme
```

```
+ Résumé transmisMessage original
Bonne nouvelle
```

```
Attaque hommemilieu -au-
Mauvaise nouvelle de hachageAlgorithme Mauvaise nouvelle
```

```
Différence avec le résumé transmis
```

```
Différent résumé
```

## Algorithmes de hachage (suite)

- Protections des algorithmes de hachage
- Message Digest (MD)
- Secure Hash Algorithm (SHA)
- Whirlpool
- Race Integrity Primitives Evaluation Message Digest (RIPEMD)
- Mots de passe Windows: LM (LAN Manager) et NTLM (New Technology

##### LAN Manager)

- Linux et Mac OS: MD5, SHA-256, SHA-512, SHA- 1 avec une séquence de

##### bits aléatoire ajoutée en entrée ( salt )

```
Caractéristiques Protection?
Confidentialité Non
Intégrité Oui
Disponibilité Non
Authentification Non
Nonrépudiation Non
```

## Cryptographie symétrique

- La même clé est utilisée pour le chiffrement et le déchiffrement

```
Message en clair
```

```
Message en clair
```

```
Clé identique
```

```
Clé identique
```

```
Algorithme de chiffrement
Cryptogramme
```

```
Cryptogramme
```

```
Algorithme de déchiffrement
```

```
Transmission
du message
```

```
Mémo confidentiel
Bonjour ...
```

```
Mémo confidentiel
Bonjour ...
```

## Cryptographie symétrique (suite)

- Deux catégories d’algorithmes, en se basant sur la quantité de

#### données traitées à la fois

- Chiffrement de flux ( _stream cipher_ )
- Chiffrement par bloc ( _block cipher_ )
- Chiffrement de flux ( _stream cipher_ )
- Remplacer chaque caractère à chiffrer par un ou plusieurs caractères
- Avantage: rapide si le message à chiffrer est court
- Inconvénient: consommation élevée de puissance de calcul si le message à
  chiffrer est long

```
Message en clair Cryptogramme
```

```
Chiffrement de flux
Message en clair Messagechiffré
```

## Cryptographie symétrique (suite)

- Chiffrement par substitution mono-alphabétique
- Chiffrement par substitution homo-alphabétique
  - Substituer chaque caractère à chiffrer par plusieurs caractères
  - Exemple: A ➔ILS

```
Chiffrement de flux
Message en clair Messagechiffré
```

## Cryptographie symétrique (suite)

- Chiffrement par transposition
  - Réarranger les lettres sans les changer

```
1.Déterminer la clé
2.Attribuer une valeur à chaque position
3.Enregistrer le texte en clair par ligne
```

```
4.Extraire par colonne
```

```
Message en clair Messagechiffré
```

```
Chiffrement de flux
```

## Cryptographie symétrique (suite)

- Étape finale
  - Souvent le message en clair et le message chiffré sont combinés
  - Une clé aléatoire ( _One-Time Pad_ ) peut être combinée avec le message en clair
    - Considéré comme sûr si la clé est aléatoire, gardée secrète et non réutilisée
    - Approche théorique!

```
Message en clair
```

```
Cryptogramme
```

```
Messagechiffré
```

```
Bits différent,
donc résultat 1
```

```
Bits identiques,
donc résultat 0
```

## Cryptographie symétrique (suite)

- Chiffrement par bloc
  - Traite un bloc du message en clair à la fois
  - La taille des blocs varie de 8 à 16 octets ( _bytes_ )
  - Les blocs sont répartis de façon aléatoire pour augmenter la sécurité
  - Plus sécuritaire que le chiffrement de flux car le résultat est davantage
    aléatoire
- Protections offertes par la cryptographie symétrique

```
Caractéristiques Protection?
Confidentialité Oui
Intégrité Oui
Disponibilité Oui
Authentification Non
Nonrépudiation Non
```

## Cryptographie symétrique (suite)

- Data EncryptionStandard (DES)
  - Conçu au début des années 1970
  - Chiffrement par bloc (64-bits par bloc)
  - Clé de 56-bits
  - Il est déconseillé de l’utiliser aujourd’hui
- Triple Data Encryption Standard (3DES)
  - Remplace DES
  - Exécute trois tours ( _rounds_ ) de l’algorithme de
    chiffrement
  - Le message chiffré de chaque tour redevient
    l’entrée du tour suivant
  - Utilisation d’une clé différente pour chaque tour
    d’exécution

```
3DES
Message en clair Messagechiffré 1
```

```
Messagechiffré 1
```

```
Messagechiffré 1
```

```
Messagechiffré 2
```

```
Messagechiffré 2 Messagechiffré 3
```

```
Algorithme de chiffrement 1
```

```
Algorithme de chiffrement 2
```

```
Algorithme de chiffrement 3
```

## Cryptographie symétrique (suite)

- Advanced EncryptionStandard (AES)
  - Approuvé par le NIST en l’an 2000 comme remplacement de DES
  - Standard de chiffrement officiel pour le gouvernement des É-U
  - Blocs de 128-bits et clé de 128-bits à 256-bits
  - Effectue trois étapes de chiffrement sur chaque bloc du message en clair
  - Conçu pour être sécuritaire bien dans le future
- Rivest Cipher (RC1 à RC6)
  - RC4: chiffrement de flux (128-bits) utilisé dans WEP (Wired Equivalent Privacy)
- International Data Encryption Algorithm (IDEA)
  - Conçu au début des années 1990s et utilisé en Europe
  - Blocs de 64-bits et clé de 128-bits avec 8 tours d’exécution
- Blowfish
  - Blocs de 64-bits et clé de 32-bits à 448 bits

## Cryptographie asymétrique

- Faiblesse de la cryptographie symétrique
  - Distribuer et maintenir des pairs de clés pour un grand nombre d’utilisateurs
    géographiquement dispersés
  - Pour Nutilisateurs désirant communiquer deux à deux: chacun d’entre eux

###### doit posséder N\*(N-1)/2clés

- Cryptographie asymétrique
  - Cryptographie (chiffrement) à clé publique
  - Utilise deux clés mathématiquement liées
  - Une clé publique disponible à tout le monde
  - Une clé privée secrète connue uniquement par son propriétaire

## Cryptographie asymétrique (suite)

```
Message en clair
```

```
Algorithme de chiffrement
Cryptogramme
```

```
Algorithme de déchiffrement
```

```
Transmission
du message
```

```
Mémo confidentielBonjour ...
```

```
Message en clair
Mémo confidentielBonjour ...
```

```
Cryptogramme
```

```
Clé différente
```

```
Clé différente
```

```
Clé publique d’Alice
```

```
Clé privée d’Alice
```

```
(expéditeur)
```

```
(destinataire)
```

## Cryptographie asymétrique (suite)

- Principes de base
  - Pair de clés
    - Clé publique
    - Clé privée
  - Deux directions
- Signature numérique
  - Vérifier l’émetteur
  - Empêcher l’émetteur de nier le message
  - Preuve d’intégrité du message

## Cryptographie asymétrique (suite)

- Signature numérique
  **Message en clair**

```
Comparaison des résumés ( hashes )
```

```
de hachageAlgorithme
```

```
Transmission
du message
```

```
Mémo confidentielBonjour ...
```

```
de hachageAlgorithme Algorithme de chiffrement
Mémo confidentielBonjour ...
```

```
Algorithme de chiffrement
```

```
Signature numérique
```

```
Signature numérique
```

```
Étape 5
```

```
Étape 1
```

```
Étape 4
```

```
Étape 3
```

```
Étape 2
```

```
(expéditeur)
```

```
(destinataire)
```

```
Clé publique de Bob
```

```
Clé privée de Bob
```

```
Résumé
```

```
Résumé
```

```
Résumé
```

```
Mémo confidentiel Mémo confidentielBonjour ...
Bonjour ...
```

## Cryptographie asymétrique (suite)

Action Àqui appartient la clé? Quelle clé utiliser? Explication
Bobveut envoyer un
message chiffré

Clé d’Alice Clépublique Pour envoyerun message chiffré,
la clé publique du destinataire
est utilisée
Alice veut lire un message
chiffré envoyépar Bob

Clé d’Alice Clé privée Un message chiffré peut
seulement être déchiffré en
utilisant la clé privée du
destinataire
Bob veutenvoyer une
copie à lui-même du
message chiffré qu’il a
envoyé à Alice

```
Clé de Bob Clé publique pour
chiffrer
Cléprivée pour
déchiffrer
```

Un message chiffré peut
seulement être déchiffré par la
clé privée du destinataire; Bob
doit le chiffrer avec sa propre clé
publique et puis utiliser sa clé
privée pour le déchiffrer
Bob reçoitun message de
réponse chiffré d’Alice

```
Clé de Bob Cléprivée La clé privéedu destinataire doit
être utilisée pour déchiffrerle
message de réponse
```

## Cryptographie asymétrique (suite)

Action Àqui appartient la clé Quelle clé utiliser Explication
Bobveut que Susanne lit
la réponse d’Alice qu’il a
reçu

Clé de Susanne Clé publique Lemessage doit être chiffré avec
la clé publique de Susanne pour
qu’elle puisse le déchiffrer avec
sa clé privée
Bobveut envoyer à Alice
un message avec une
signature numérique

```
Clé de Bob Clé privée La clé privée de Bob est utilisée
pour chiffrer le résumé
```

Alice veut lire la signature
numérique de Bob

```
Clé de Bob Clé publique Parce quela clé publique et la clé
privée de Bob fonctionnent dans
les deux directions. Alice peut
utiliser la clé publique pour
déchiffrer le résumé
```

## Cryptographie asymétrique (suite)

- Protections de la cryptographie asymétrique

```
Caractéristiques Protection?
Confidentialité Oui
Intégrité Oui
Disponibilité Oui
Authentification Oui
Nonrépudiation Oui
```

## Cryptographie asymétrique (suite)

- RSA
  - Publié en 1973 et breveté par le MIT en 1983
  - L’algorithme de cryptographie asymétrique le plus utilisé
  - Utilise deux grands nombres premiers
  - La clé publique est (n, e) =(133, 5) et la clé privée est (n, d)=(133, 65)

Étape Exemple

1. Choisirdeux nombres premiers, pet q p = 7 et q = 19
2. Multiplier pet qpour obtenirn (n = p*q) n = 7 * 19 = 133
3. Calculerm=(p-1)_(q-1) m = ((7-1)_(19-1) = 6 \*18 = 108
4. Trouver un nombre etelque e < net eet msont premiers
   entre eux (leur plus grand commun diviseur est égal à 1)

```
e = 5
```

5. Trouver un nombreentierdtel que (e*d-1) est divisible par
   m(c-à-d.,e*d modulo m = 1) oud= (1+f\*m)/e)

```
d = (1 + ( 3 *108))/5 = 325/5 = 65
```

## Cryptographie asymétrique (suite)

- RSA (suite)
  - Pour chiffrer le message en clair aet produire un message chiffré c:
    - _c = aemod(n)_
    - _c = a_^5 _mod(133)_
  - Pour déchiffrer le message cet obtenir le message en clair a:
    - _a = cdmod(n)_
    - _a = c_^65 _mod(133)_
  - Inconvénient
    - Lenteur: DES est ~ 100 fois plus rapide sur logicielle et entre 1,000 et 10,000 sur matériel

## Cryptographie asymétrique (suite)

- Système à courbe elliptique ( _Elliptic curve_

#### cryptography, ECC)

- Problème du logarithme discret sur des courbes
  elliptiques
- Utilisation des points d’une courbe elliptique
- Nécessite moins de puissance de calcul que RSA
- Intéressant pour les composantes mobiles
- NTRUEncypt
- Basé sur des ensembles de points dans l’espace
  (réseaux) et sur le problème du plus court vecteur
- Plus rapide que RSA et ECC
- Résistant aux attaques qui utilisent le calcul quantique

## Cryptographie quantique

- Exploite les caractéristiques des objets microscopiques tels que les photons
- Ne dépend pas des problèmes basés sur une difficulté mathématique (de calcul)

## Stéganographie

- Cacher l’existence des données
- Fichiers images, audios ou vidéos contenant des messages cachés

#### incorporés

- Diviser les données et les incorporer dans les parties inutilisés des

#### fichiers

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Certificats numériques et

## protocoles sécurisés

```
1
```

## Contenu

- Certificats numériques
- Infrastructure à clé publique
- Protocoles sécurisés

## Certificat numérique

- Signature numérique - Prouver l’origine d’un document - Inconvénient: un imposteur peut publier une fausse clé publique d’un autre
  utilisateur 1. Bob Crée le
  message original 2. Ralph l’intercepte et
  crée un nouveau message 3. Ralph remplace la clé
  publique de Bob par la sienne 4. Alice récupère la clé
  publique de l’imposteur
  (Ralph)
  **Message original Message altéré
  Appelles moi Pas besoin de m’appeler**

```
Clé publique
de Bob
```

## Certificat numérique (suite)

- Solution: Tiers de confiance
  - Aider à résoudre le problème de vérification d’identité
  - Vérifier le propriétaire et que la clé publique lui appartient
  - Aider à prévenir les attaques de type homme-au-milieu( _man-in-the-middle_ )qui
    imitent le propriétaire d’une clé publique
- Informations contenues dans un certificat
  - Nom ou alias du propriétaire
  - Clé publique du propriétaire
  - Nom de l’émetteur du certificat
  - Signature numérique du propriétaire
  - Numéro de série du certificat
  - Date d’expiration de la clé publique
  - ...

## Gestion des certificats numérique

- Entités et technologies impliquées
  - Autorité de Certification ( _Certificate Authority_ , CA)
  - Autorité d’Enregistrement ( _Registration Authority,_ RA)
  - Liste de Révocation de Certificats ( _Certificate Revocation List_ , CRL)
  - Dépôt de Certificats ( _Certificate Repository_ , CR)
  - Navigateur Web

## Gestion des certificats numérique (suite)

- Autorité de Certification (CA)
  - Délivrance des certificats numériques
  - Interne ou externe à l’organisation

Fonctions
Générer et délivrer des certificats de clés publiques
Délivrer des certificats pour d’autres CA
Générer et publier des informations sur l’état des
certificats
Inscrire des demandes de révocation
Révoquer des certificats de clés publiques
Maintenir la sécurité, la disponibilité et la continuité
du service de signature de certificats

```
Un abonné qui demande un certificat numérique
Génère sa clé publique et sa clé privée
Envoie sa clé publique à la CA (la CA peut dans
certains cas générer les deux clés)
La CA insère la clé publique dans un certificat
La CA signe le certificat avec sa clé privée
```

## Gestion des certificats numérique (suite)

- Autorité d’Enregistrement (RA)
  - Entité subordonnée à une CA qui réalise une partie de ses fonctions
    - Recevoir, authentifier et traiter les demandes de révocation
    - Identifier et authentifier les abonnées
    - Obtenir la clé publique de l’abonné
    - Vérifier l’identité d’un individu
      - Email
      - Documents (certificat de naissance, badge employé, etc.)
      - En personne (permis de conduire, passeport, etc.)
    - Initier le processus de certification avec la CA

## Gestion des certificats numérique (suite)

- Liste de Révocation de Certificats (CRL)
  - Le certificat n’est plus utilisé
  - Les détails du certificat ont changé
    - Exemple: l’adresse du propriétaire a changé
  - La clé privée a été perdue ou exposée (ou suspectée de l’être)
- Dépôt de Certificats (CR)
  - Annuaire centralisé des certificats numériques accessible au public
  - Consulter l’état des certificats
  - Peut être crée et géré localement comme une zone de stockage connecté au
    serveur CA

## Gestion des certificats numérique (suite)

- Gestion du navigateur Web
  - Les navigateurs Web modernes sont préconfigurés avec des listes de CA par
    défaut
  - Avantages
    - Les utilisateurs peuvent profiter des certificats numériques sans faire recours au
      téléchargement manuel des informations
    - Les utilisateurs n’ont pas à télécharger les listes de révocation manuellement (mises à jour
      automatiques)

## Types de certificats numériques

- Classe 1: certificats personnelles
  - Délivrés par une RA
  - Souvent utilisés pour sécuriser la transmission de courriels
  - Nécessite le nom du propriétaire et son adresse courriel

## Types de certificats numériques

- Classe 2: certificats de serveurs - Envoyés au clients par un serveur Web - 1) Assure l’authenticité du serveur Web - 2) Assure la confidentialité de la connexion avec le serveur Web - 1) et 2) peuvent être combinés en un seul certificat
  **1.** crée les clés et la L’administrateur Web
  signature numérique
  **2.** «Payer maintenantL’utilisateur clique sur »
  **3.** numérique avec Certificat
  clé publique acceptée par le
  navigateur
  **4.** chiffré avec la clé publiqueNuméro de la carte de crédit
  **5.** le numéro de carte de Le serveur Web déchiffre
  crédit avec sa clé privée

```
Clé publique
```

```
Clé privée
```

```
Payer Clé publique
```

## Types de certificats numériques (suite)

- Certificat SSL à validation étendue ( _Extended Validation SSL_ , EV SSL)
  - Nécessite une vérification plus approfondie de la légitimité de l'entreprise
- Classe 3: certificats numériques des éditeurs de logiciels ( _software_

#### publisher digital certificates )

- Fournit par les éditeurs de logiciels
- But: vérifier la sécurité des logiciels
- Classe 4: transactions commerciales en ligne entre compagnies
- Classe 5: sécurité des organisations privées ou gouvernementales
- Certificats à double clé ( _Dual-key_ )
- Authentification (signature numérique) et confidentialité
- Certificats à double sens ( _Dual-sided_ )
- Serveur et client

## Types de certificats numériques (suite)

- Certificats numérique X.509
  - Standard le plus utilisé pour déterminer le format des certificats numériques

## Infrastructure à clé publique

- _Public Key Infrastructure_ (PKI)
- Cadre ( _framework_ ) pour toutes les entités impliquées dans la gestion

#### des certificats numériques

- Outil important pour la gestion des certificats numériques et la

#### cryptographie asymétrique

- Actions facilitées par la PKI: créer, stocker, distribuer et révoquer les

#### certificats numériques

- Aspects de la PKI
  1. Standards de cryptographie à clé publique
  2. Modèle de confiance
  3. Gestion des clés

## Standards de cryptographie à clé publique

- _Public-Key Cryptographic Standards_ (PKCS)
- Ensemble numéroté de standards PKI définis par la compagnie RSA
  - Largement accepté dans l’industrie
  - Basé sur l’algorithme cryptographique à clé publique RSA

PKCS # Version actuelle Nom Description
PKCS #1 2.1 RSA Cryptography
Standard

```
Définit le chiffrement et le format de la signature numérique en utilisant
l’algorithme RSA
PKCS #2 S/O S/O Originalement, définit le chiffrementdu message résumé (fait partie de
PKCS #1 maintenant)
PKCS #3 1.4 Diffie-Hellman Key
Agreement Standard
```

```
Échange de clés secrètes en utilisant l’algorithme Diffie-Hellman
PKCS #4 S/O S/O Originalement,définit la syntaxe des clés RSA (fait partie de PKCS #1
maintenant)
PKCS#5 2.0 Password-Based
Cryptography Standard
```

```
Décrit la méthodede génération d’une clé secrète à partir d’un mot de
passe (PBE)
PKCS #6 1.5 Extended-Certificate
Syntax Standard
```

```
Décrit lasyntaxe d’un certificat étendu (retiré graduellement)
```

## Standards de cryptographie à clé publique (suite)

PKCS # Version actuelle Nom Description
PKCS #7 1.5 Cryptographic Message
Syntax Standard

```
Définitune syntaxe générique pour la signature numérique
PKCS #8 1.2 Private-Key Information
Syntax Standard
```

```
Définitla syntaxe et les attributs des clés privés. Aussi définit une
méthode pour trier les clés
PKCS #9 2.0 Selected Attribute
Types
```

```
Définit les type d’attributs utilisés dans lesformats de données définis
dans PKCS #6, PKCS #7, PKCS #8, and PKCS #10
PKCS #10 1.7 Certification Request
Syntax Standard
```

```
Décrit la syntaxe d’une requête envoyée à un CApour demander un
certificat numérique
PKCS #11 S/O Cryptographic Token
Interface Standard
```

```
...
PKCS #12 1.0 Personal Information
Exchange Syntax
Standard
```

```
...
```

```
PKCS #13 En développement Elliptic Curve
Cryptography Standard
```

```
...
PKCS #14 En développement PRNG Standard ...
PKCS #15 Cryptographic Token
Information Format
```

```
...
```

## Modèles de confiance

- _Trust models_
- Le type de relations de confiance qui peut exister entre individus et

#### entités

- Directe
  - Une personne connait l’autre
- Tiers de confiance
  - Deux personnes se font confiance car les deux font confiance à une troisième personne

## Modèles de confiance (suite)

- Modèle hiérarchique
  - Une seule hiérarchie avec une CA à la racine
    ( _Root_ )
  - La CA racine signe tous les certificats avec la
    même clé
  - Approprié au sein d’une même organisation
  - Inconvénients
    - Charge de travail pour la CA racine
    - Compétition entre CAs
    - Et si la clé privée de la racine est compromise!
- Modèle distribué
  - Plusieurs CAspeuvent signer les certificats
  - Élimine les limitations du modèle
    hiérarchique

## Modèles de confiance (suite)

- Passerelle ( _Bridge_ )
  - Une CA facilite la connexion entre toutes
    les autres CAs
  - La CA facilitatrice ne délivre pas de
    certificats
  - Permet la liaison entre différents modèles
    de confiance
  - Exemple de passerelles
    - Gouvernements fédéral et gouvernements
      provinciaux
    - Industrie pharmaceutique
    - Industrie Aérospatiale
    - Etc.

## Gestion d’une PKI

- Politique de certification ( _Certificate Policy_ , CP)
  - Détermine les règles qui gouvernent le fonctionnement d’une PKI
  - Fournit les recommandations en termes de besoins de sécurité pour la CA, les RA et
    les autres entités
- Déclaration des pratiques de certification ( _Certificate Practice Statement_ ,

##### CPS)

- Décrit en détail comment la CA doit utiliser et gérer les certificats
- Cycle de vie d’un certificat
- Création
- Après l’identification positive de l’utilisateur
- Suspension
- Exemple: absence prolongée d’un employé
- Révocation
- Exemple: compromission de la clé privée
- Expiration

## Gestion des clés

- Stockage de la clé publique
  - Intégration dans un certificat numérique
- Stockage de la clé privée
  - Sur le système local du propriétaire
  - Logiciel ou matériel
- Plusieurs paires de clés
  - Si les besoins de sécurité les requièrent
    - Une paire de clés pour le chiffrement de l’information
    - Une paire pour la signature numérique
- Autorité de séquestre ( _Key Escrow_ )
  - Les clés sont gérés par une tiers partie
  - Diviser la clé en deux, chiffrer chaque partie et la stocker dans un endroit
    différent

## Gestion des clés (suite)

- Expiration
  - Les clés expirent après une période de temps prédéfinie
- Renouvellement
  - Les clés existantes peuvent être renouvelées
- Révocation
  - Les clés peuvent être révoquées avant leur date
    d’expiration
  - Les clés révoquées ne peuvent être restaurées
- Récupération
  - Exemple: besoin de récupérer la clé d’un employé
    hospitalisé pour une période prolongée
  - Utilisation d’un agent de récupération (personne de
    confiance)
  - Utiliser un groupe de personnes (contrôle M-de-N)

## Protocoles sécurisés

- SSL/TLS
- SSH
- S-HTTP
- SET
- DNSsec

## SSL/TLS

- SSL ( _Secured Socket Layer_ ou couche de sockets sécurisée)
- Procédé de sécurisation des transactions effectuées sur Internet:

#### établir un canal sécurisé de communication (chiffré) entre deux

#### machines: un client et un serveur

- Repose sur la cryptographie asymétrique (à clé publique)
- Transparent à l’utilisateur
  - Indépendant du protocole utilisé (HTTP, FTP, POP, IMAP, etc.)
  - Couche supplémentaire assurant la sécurité entre la couche application et la
    couche transport
- 2001
  - Brevet de SSL racheté par l’IETF ( _Internet Engineering TaskForce_ )
  - Rebaptisé TLS( _Transport Layer Security_ )

## SSL/TLS (suite)

```
Principe de fonctionnement (SSL 2.0)
```

```
Demande d’authentification
+
Cryptosystèmessupportés
```

```
Client (sécurisé par SSL )Serveur
```

```
Certificat numérique (clé publique)
+
Le meilleur crypto-système supporté en
Vérifier la validité du certificat+ commun
Création d’une clé de session aléatoire
+
Chiffrer la clé de session avec la clé
publique du serveur Déchiffrer la clé de session à l’aide de
la clé privée du serveur
```

```
...
```

```
Suite de l’échange
en utilisant la clé de
session
```

## SSH

- SSH ( _Secure Shell_ ) permet à des utilisateurs (ou services TCP/IP)

#### d’accéder à une machine à travers une canal chiffré ( tunnel )

- Ouvrir une session interactive sur un serveur pour envoyer des

#### commandes ou des fichiers

- Alternative à _telnet_ , _rsh_ , _rlogin_ et _rexec_
- Principe de fonctionnement
  - Le client et le serveur s’authentifient mutuellement
    - Le serveur envoie sa clé publique
    - Le client génère une clé de session de 256 bits, la chiffre avec la clé publique du serveur et
      l’envoie à ce dernier
  - Les données circulant entre le client et le serveur sont chiffrées
    - En utilisant clé se session

## S-HTTP

- _Secure HTTP_ (Protocole HTTP sécurisé)
- Une amélioration du protocole HTTP pour offrir la sécurisation des

#### échanges lors de transactions de commerce électronique

- Chiffrer directement les messages HTTP (couche applicative)
- S-HTTP et SSL sont complémentaires

## SET

- SET ( _Secure Electronic Transaction_ )
- Protocole de sécurisation des transactions électroniques qui s’appui

#### sur SSL

- Utilisation d’une signature numérique de l’acheteur
- Une transaction mettant en jeu non seulement le client et le

#### marchand, mais aussi leurs banques respectives

- Le marchand n’a pas accès aux informations bancaires sensibles du client

## DNSsec

- DNSsec ( _Domain Name System Security Extensions_ )
- Les serveurs DNS sont des ordinateurs qui structurent le Web mondial
- DNSsec: une extension du protocole DNS
- Buts
  - Assurer l’authentification et l’intégrité des enregistrements DNS
  - Contrer les failles du protocole DNS et le DNS _poisoning_
- Principe de fonctionnement
  - Vérification des signatures numériques et échange de données chiffrées

## Activité 6.1

- Explorer le fonctionnement de l’algorithme de cryptographie

#### asymétrique RSA en utilisant le lien suivant:

#### http://www.umaranis.com/rsa_calculator_demo.html

## Activité 6.2

- Ouvrir Internet Explorer puis saisir [http://www.google.ca](http://www.google.ca) dans la barre d’adresse.
- Cliquer sur le signe du cadenas qui s’affiche à côté de la barre d’adresse.
- Cliquer sur « Afficher les certificats ».
- Cliquer sur l’onglet « Détails» et noter les détails du certificat.
- Cliquer sur « Clé publique» pour afficher la clé publique associée au

##### certificat.

- Cliquer sur l’onglet « Chemin d’accès de certification ». Noter la hiérarchie

##### des autorités de certifications qui indique un modèle de confiance

##### hiérarchique.

- Cliquer sur le certificat racine puis cliquer sur « Afficher le certificat ».
- Comparer le champ « Valide jusqu’au» de ce certificat à celui du certificat

##### de http://www.google.ca.

## Activité 6.3

- Ouvrir « Google Chrome » (ou le navigateur Web de votre choix) puis

#### cliquer sur « Paramètres » ➔ « Sécurité » ➔ « Gérer les certificats »

#### (les étapes peuvent être différentes si vous utilisez un autre navigateur

#### Web)

- Cliquer sur « Autorités de certification racine de confiance ». Pourquoi

#### y en a-t-il plusieurs?

- Cliquer sur « Avancé ». Quel est le format d’exportation par défaut?
- Explorer les autres formats d’exportation

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Dispositifs de protection

```
1
```

## Contenu

- Dispositifs de protection
- Technologies réseau
- Conception sécuritaire des réseaux informatiques

## Pourquoi des dispositifs de protection?

- Pas toutes les applications conçues et développées avec la sécurité en

#### perspective

- Le réseau doit fournir une protection
- Un réseau avec une faible sécurité est une invitation aux pirates
- Aspects de la construction d’un réseau sécurisé
- Dispositifsde protection du réseau
- Technologiesréseau
- Conceptiondu réseau lui-même

## Le modèle de réseau OSI

Émetteur Récepteur
Couche 7:
Application
Couche 6:
Présentation
Couche 5:
Session
Couche 4:
Transport
Couche 3:
Réseau
Couche 2:
Liaison de données
Couche 1:
Physique

```
Application
```

```
Système
d'exploitation
```

```
Matériel
Connexion physique
```

```
Protocole «Liaison de données»
```

```
Protocole «Réseau»
```

```
Protocole de transport
```

```
Protocole de session
```

```
Protocole de présentation
```

```
Conversation d’applications
```

## Dispositifs réseau

- Concentrateur ( _Hub_ )
  - Connecte plusieurs dispositifs du réseau local
  - Couche 1 du modèle OSI
- Commutateur ( _Switch_ )
  - Connecte plusieurs segments du réseau
  - Couche 2 du modèle OSI
  - Utilise l’adresse MAC pour identifier une machine sur le réseau
- Routeur ( _Router_ )
  - Routage des paquets entre les différents réseaux
  - Couche 3 du modèle OSI
  - Peut filtrer un type spécifique du trafic réseau (routeur filtrant)
- Répartiteur de charge ( _load balancer_ )
  - Logiciel ou matériel

## Dispositifs réseau (suite)

- L’administrateur réseau doit être capable de surveiller le trafic réseau

```
Ordinateur de surveillance
```

**Ordinateur de surveillance** Port
Miroir

## Pare-feu

- _Firewall_
- Inspecter les paquets pour les accepter

#### ou les rejeter

- Logiciel ou matériel
- Habituellement situé à l’extérieur du

#### périmètre sécuritaire du réseau

- Actions sur les paquets en transit
  - Autoriser ( _allow_ )
  - Bloquer ( _deny_ )
  - Demander l’action appropriée
    **Réseau interne**

## Pare-feu (suite)

- Règles de filtrage
  - Ensemble de règles ( _rules_ ) pour contrôler les actions du pare-feu
  - Exemple d’une règle
  - Dernière règle: BLOQUER TOUT
- Ces règles peuvent être des paramètres de haut niveau

```
Description de la règle Explication Filtrage
AdresseIP source = tout L’adresse IP source d’un
ordinateur quelconque sur
Internet
```

```
Car l’adresse IP d’un client du serveur Web ne
peut pas être connueau préalable, cette règle
autorise un paquet provenant de n’importe
quelle adresse d’accéder au réseau
Adresse IP destination =
Adresse IP interne
```

```
L’adressedestination est
l’adresse IP d’un serveur
Web public dans leréseau
interne
```

```
Cette règle autorise le passage des paquets
destinés au serveur Web public mais bloque
les paquets avec une adresse destination
arbitraire ou invalide
Port = 80 Indique quelport est ouvert
pour accepter le paquet
```

```
Aucunautre port n’est ouvert sauf si c’est
clairement indiqué
```

## Pare-feu (suite)

- Filtrage simple de paquets ( _stateless_

#### packet filtering )

- Inspecte les paquets, un par un, pour
  appliquer l’action appropriée
- Liste de contrôle pour le filtrage
  séquentiel en entrée - Adresse IP source - Fanions TCP - Numéros de ports - Message ICMP - Etc.
- Liste de contrôle pour le filtrage
  séquentiel en sortie - ...

```
Exemple de liste de filtrage en entrée
```

```
Exemple de liste de filtrage en sortie
```

## Pare-feu (suite)

- Filtrage dynamique ( _stateful inspection_ )
  - Enregistrement des deux adresses IP et numéros de ports dans une table
    d’états lors de l’ouverture d’une connexion
  - Acceptation de tous les paquets appartenant aux connexions enregistrées avec
    un minimum d’inspection

## Pare-feu (suite)

- Filtrage dynamique (suite)
  - Liste de contrôle (inspection dynamique)
    - Comme dans le cas statique, mais pour des paquets applicatifs
  - Accepter ou bloquer les paquets en provenance d’applications spécifiques
  - Pas besoin de règles spécifiques pour bloquer les paquets de balayage de ports
    ne faisant partie d’aucune connexion enregistrée

## Pare-feu (suite)

- Pare-feu applicatif (Web)
  - Inspecte en profondeur les paquets qui acheminent du trafic HTTP
    - Navigateurs Web
    - FTP
    - Telnet
  - Peut être logiciel ou matériel, côté client ou serveur
  - Peut bloquer des sites spécifiques ou des attaques avec signature bien connue
  - Peut bloquer les attaques de type XSS et de type injection SQL

## Serveur mandataire

- _Proxy_
- Un serveur ou une application qui

#### intercepte et traite les demandes des

#### utilisateurs internes

- Si une page Web a été précédemment

#### demandée

- Une copie de cette page peut se retrouver
  dans le cachedu serveur proxy
- Sinon, le serveur proxy demandera la

#### page Web en utilisant son adresse IP

## Serveur mandataire (suite)

- Avantages
  - Améliorer les temps de réponse (utilisation du cache)
  - Réduire les coûts (la bande passante nécessaire)
  - Améliorer la gestion de la sécurité
    - Bloquer des sites/pages Web spécifiques
  - Renforcer la sécurité
    - Intercepter les maliciels( _malwares_ )
    - Cacher les adresses IP des utilisateurs internes

## Serveur mandataire (suite)

- _Reverse proxy_
  - Servir les utilisateurs externes
  - Diriger les requêtes provenant de l’extérieur vers le bon serveur
  - Seulement l’adresse IP du _reverse proxy_ est visible de l’extérieur
    - Les adresses IP internes sont cachées
      Le vers le bon serveur **_reverse proxy_** achemine

```
Récupérer la page Web du
serveur 1
```

```
Le source par son adresse proxy remplace l’adresse IP
```

```
Récupérer la page 123.org Récupérer la page 123.org
```

```
L’utilisateur lanceune requête
```

## Serveur mandataire (suite)

## Système de détection d’intrusion

- _Intrusion detection system_ (IDS)
- Système qui permet de détecter et de signaler les intrusions
- Principe
  - Observer:capteurs, fichiers de journaux applicatifs, fichiers de traces système,
    paquets réseau, etc.
  - Analyser:identification d’indices d’attaques
    - Recherche de signes de reconnaissance: signature connue
      - Exemple: succession de paquets spécifiques
    - Recherche d’anomalies: recherche de comportements suspects
  - Agir:signal d’alarme, envoi de courriels, actions dynamiques
    - Exemple: demander au pare-feu de bloquer les entrées du réseau

## Système de détection d’intrusion (suite)

- Méthodologies de surveillance
  - Basée sur les anomalies ( _anomaly-based monitoring_ )
    - Comparer les comportements présents à une base d’activités normales
  - Basée sur la signature
    - Chercher des signatures d’attaques bien connues
  - Basée sur le comportement
    - Détecter les actions anormales des processus ou des programmes
    - Alerter l’utilisateur qui décide s’il souhaite autoriser ou bloquer l’activité
  - Basée sur des heuristiques
    - Utiliser des techniques basées sur les expériences passées

## Système de détection d’intrusion (suite)

```
Méthodologiede surveillance
```

```
Détecteles
applications de
balayage de ports?
```

```
Commentaire
```

```
Basée sur les anomalies Probablement Seulementsi une entrée dans la base
d’anomalies a été créée pour l’application
qui avait essayé auparavant de faire un
balayage
Basée sur la signature Probablement Seulementsi la signature du balayage par
cette application a été créée auparavant
Basée sur le comportement Probablement Seulementsi les actions de cette
application sont différentes des autres
applications
Basée sur des heuristiques Oui L’IDS est déclenché sin’importe quelle
application essaye de balayer plusieurs
ports
```

## Système de détection d’intrusion (suite)

- Deux grandes familles distinctes d’IDS:
  - NIDS( _Network Based Intrusion Detection System_ )
    - Assure la sécurité d’un réseau
  - HIDS( _Host Based Intrusion Detection System_ )
    - Assure la sécurité d’une machine

## Système de détection d’intrusion (suite)

- HIDS
  - Application logicielle qui détecte une attaque dès son apparition
  - Installé sur chaque machine qui requiert une protection
  - Surveille les appels et l’accès aux fichiers système
  - Reconnaît les modifications non autorisées au registre système
  - Surveille toutes les communications en entrée et en sortie
    - Détecte les activités anormales
  - Inconvénients
    - Ne peut pas surveiller le trafic qui ne parvient pas aux machines locales
    - Les données de journalisation sont stockées localement
    - Consommation élevée des ressources (possibilité de ralentissement du système)

## Système de détection d’intrusion (suite)

- NIDS - Surveille les attaques sur le réseau - Capteurs installés sur les pare-feu et les routeurs - Collecte d’informations pour le NIDS - Un NIDS passif va seulement déclencher un signal d’alarme - Un NIDS actif va déclencher un signal d’alarme et exécuter des actions - Exemple d’action: filtrer l’adresse IP de l’intrus ou terminer la session TCP
  Technique d’évaluation Description
  Vérification de la pile protocolaire
  ( _Protocol stackverification_ )

Certainesattaques utilisent des configurations de protocoles invalides (IP,
TCP, UDP ou ICMP). La vérification de la pile protocolaire peut identifier des
paquets invalides comme des paquets IP fragmentés
Vérification des protocoles applicatifs
( _Application protocolverification_ )

Certaines attaques essayent d’exploiterun comportement invalide des
protocoles applicatifs ou une signature d’attaque bien connue (ex. _DNS
poisoning_ ). Le NIDS essayera de vérifier les protocoles applicatifs pour
détecter ces signatures caractéristiques
Créationde journaux étendus Un NIDS peut journaliserles évènements inhabituels pour les rendre
disponibles aux autres systèmes de surveillance

## Système de détection d’intrusion (suite)

- Système de prévention d’intrusion ( _Network Intrusion Prevention_

#### System , NIPS)

- Similaire à un NIDS actif
- Surveille le trafic réseau pour bloquer immédiatement toute attaque
- Capteurs situés au niveau du pare-feu
- Appareils de sécurité tout-en-un( _All-in-one network security_

#### appliances )

- Dispositifs intégrés qui remplacent plusieurs dispositifs de sécurité
- À combiner avec les dispositifs réseau traditionnels tels qu’un routeur
- Avantage de l’approche
  - Les dispositifs réseau déjà inspectent tous les paquets entrants et sortants

## Filtrage Web

- Les pare-feu et IDS protègent les réseaux des attaques provenant de

#### l’extérieur (Internet)

- Les pirates essayeront donc de les contourner en utilisant des utilisateurs
  internes au réseau - Visite de sites Web malicieux - Installation de codes malicieux à partir des attachements des courriels
- Pas besoin d’intrusion directe à travers le pare-feu
- Les pare-feu applicatifs peuvent ne pas détecter ce genre d’attaques
- Filtrage Web
- Peut bloquer les contenus malicieux en temps réel
- Filtrage au niveau applicatif
- Exemple de trafic Web bloqué: adware, spyware, partage de fichiers

#### pair à pair, exploits de type script, objets ActiveX, etc.

## NAT

- _Network address translation_ (NAT)
- Permet l’utilisation des adresses IP privées sur le réseau public

#### (Internet)

- Remplace une adresse IP privée par une adresse IP publique
- _Port address translation_ (PAT)
- Variante du NAT
- Attribuer la même adresse IP aux paquets sortants, mais avec un numéro de port différent
- Adresses privées

```
Classe Adressede début Adressede fin
Classe A 10.0.0.0 10.255.255.255
Classe B 172.16.0.0 172.31.255.255
Classe C 192.168.0.0 192.168.255.255
```

## NAT (suite)

- Avantages
  - Masquer les adresses IP des machines internes
  - Permet à plusieurs machines de partager un nombre restreint d’adresses IP
    publiques

```
Paquet généré sur l’ordinateur
avec l’adresse IP privées
192.168.0.3
```

```
Le NAT remplace l’adresse IP par son
alias
```

```
Paquet envoyé avec l’adresse alias
```

## Réseau privé virtuel

- _Virtual private network_ (VPN)
- Connexion de plusieurs sous-réseaux (et clients) de façon sécuritaire à

#### travers un réseau intermédiaire non sécurisé

- Techniques
  - Tunneling
    - Permettre aux données, passant d’une extrémité du VPN à l’autre, d’être sécurisées
      (chiffrement)
    - Encapsulation des paquets: l’ancien paquet devient le message (nouvel en-tête)
  - Chiffrement
    - Le message est chiffré pour éviter l’interception ou la modification sur le réseau
      intermédiaire
  - Contrôle d’accès
    - Seuls les paquets provenant des clients ou des sous-réseaux autorisés sont réacheminés
      vers le réseau interne

## Réseau privé virtuel (suite)

- Types de VPNs
  - Accès à distance
    - Connexion d’un utilisateur au réseau local
  - Site à site
    - Plusieurs sites (réseaux locaux) peuvent se connecter à d’autres sites en utilisant Internet

## Réseau privé virtuel (suite)

- Terminaux ( _Endpoints_ )
  - Utilisés pour la transmission des données
  - Peut être un logiciel sur un ordinateur local
  - Peut être matériel (concentrateur VPN)
  - Peut être intégré dans un autre dispositif réseau
- Un VPN peut être logiciel ou matériel
  - Un VPN matériel possède, généralement, un meilleur niveau de sécurité
  - Un VPN logiciel possède une meilleure flexibilité dans la gestion du trafic
    réseau

## Conception sécuritaire du réseau

- Bastionnage du réseau
  - Bloquer le trafic non pertinent
  - Segmentation
    - Utilisation de routeurs, passerelles et serveurs proxy pour
      - Cacher les adresses IP internes
      - Protéger les serveurs et services critiques
  - Défense en profondeur
    - Principe de l’ oignon
    - Gérer un contexte différent à chaque niveau
- Éléments d’une conception sécuritaire
  - Zone démilitarisée (DMZ)
  - Subnetting
  - Virtual LANs
  - Accès distant

## Zone démilitarisée

- _Demilitarized Zone_ (DMZ)
- Un réseau séparé situé à l’extérieur du périmètre sécurisé
- Les utilisateurs externes peuvent accéder à la DMZ, mais pas au réseau sécurisé

```
DMZ avec un pare-feu IFT 2830 -Sécurité des systèmes informatiques DMZ avec deux pare-feu 31
```

```
Réseau interne Réseau interne
```

## Zone démilitarisée (suite)

- Services fournis à l’extérieur
  - Serveur DNS externe (adresses DMZ seulement)
  - Serveur SMTP
  - Serveur Web
  - Passerelle VPN
- Services fournis à l’intérieur
  - Serveur proxy Web
  - Serveur SMTP
  - Connexion serveur Web et serveur de base de données

## Subnetting

- Les 32 bits d’une adresse IP peuvent être divisés pour représenter
  - Le réseau
  - Le sous-réseau
  - La machine
- Chaque réseau peut contenir plusieurs sous-réseaux
- Chaque sous-réseau contient plusieurs machines
- Avantages
  - Améliorer la sécurité en isolant des groupes de machines
  - Permettre aux administrateurs réseau de cacher la structure interne du réseau

## Subnetting (suite)

## Vue d’ensemble

## Honeypot

- Ordinateur placé dans la zone démilitarisée
  - Contient des informations pour attirer et piéger les pirates
  - Configuré pour avoir des vulnérabilités
- Garde les pirates connectés suffisamment longtemps pour pouvoir les

#### retracer

- Outil de collecte des données sur les attaques et les pirates
- Système d'alerte précoce
- Disponible sous forme
  - Commerciale: KFSensor, NetBait, Specter, etc.
  - Open source: Nepenthes, Valhala, Honeyd, etc.

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## IPsec

```
1
```

## Contenu

- Contexte
- Mode transport
- Mode Tunnel
- Mécanisme AH
- Mécanisme ESP
- Association de Sécurité ( _Security Association_ )

## IPsec

- Authentification et chiffrement au niveau de la couche IP
- But : établir une communication sécurisée (tunnel) entre des entités

#### éloignées et séparées par un réseau non sécurisé ou public tel que

#### Internet

- Applications
  - Utilisation d’un réseau publique comme un intranet sécurisé
  - Communications sécuritaires de l'extérieur vers l'intérieur d'un intranet
    sécurisé
  - Établir une connexion sécurisée entre deux intranets
  - Sécurité supplémentaire pour les applications ayant leur propre sécurité

## Mode transport

- Seules les données du protocole supérieur, transportées par le paquet

#### IP, sont protégées

- Seulement équipements terminaux

## Mode tunnel

- Protection du paquet IP dans son intégralité
- Ajout d’un nouvel en-tête IP (protection de l’en-tête IP original)
- Protection contre l’analyse du trafic
  - Masquer les adresses IP source et destination

## Mécanisme AH ( Authentication Header )

- Ajout d’un en-tête supplémentaire au paquet IP

## Mécanisme ESP ( Encapsulating Security Payload )

- Principe d’encapsulation
  - Données originales chiffrées puis encapsulées entre un en-tête et un _en-queue_

## AH vs ESP

```
Services AH ESP
Contrôle d’accès Oui Oui
Intégrité des messages Oui Oui
Authentification des entités (origine des données) Oui Oui
Confidentialité Non Oui
Protection contre les attaques de Rejeu ( Replay Attack ) Oui Oui
```

## Notion d’Association de Sécurité

## ( Security Association - SA)

- Relation unidirectionnelle entre un émetteur et un récepteur
- Identification
  - SPI ( _SecurityParameterIndex_ )
  - Adresse IP de destination
  - Identificateur du mécanisme de sécurité: AH ou ESP
- Paramétrée par
  - Numéros de séquence des messages (pour éviter leur réutilisation)
  - Indicateur de l’action à prendre en cas de débordement du compteur des numéros de
    séquence
  - Largeur de la fenêtre de séquencement
  - Informations spécifiques sur le mécanisme choisi
  - Durée de vie de l’association (en octets transmis ou en temps)
  - Mode IPsec(transport ou tunnel)
  - Taille maximale des paquets

## Internet Key Exchange (IKE)

- _Internet Key Exchange_
- Le protocole utilisé pour établir des Associations de Sécurité (SA)
- ISAKMP ( _Internet Security Association and Key Management Protocol_ )
  - Utilise des algorithmes cryptographiques à clé publiquepour établir des clés de
    session
  - Ces clés de session protègent les paquets dans le cadre d’une SA
- Certaines attaques tentent de compromettre IKE en utilisant la force

#### brute sur la clé pré-échangée ( pre-shared key ) et en utilisant des outils

#### spécifiques

- IKECrack
- Cain & Abel
- Etc.

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## La sécurité des applications

## et des contenus

```
1
```

## Contenu

- Messagerie électronique
- Sécurité des applications Internet
- Sécurité du commerce électronique
- _Cross-Site Scripting_ (XSS)
- Injection SQL
- Injection des commandes et traversée des répertoire
- Détournement de session

## Messagerie électronique

- Une application critique
- Risques et besoins de sécurité
  - La perte, l’interception, l’altération, la destruction de messages
  - La divulgation d’informations confidentielles
  - L’infection des systèmes par le biais de messages contenant des codes
    malveillants (virus, vers ou cheval de Troie)
  - L’inondation de messages ( _junk mail_ , spam, etc.)
  - L’usurpation d’identité et le harcèlement des utilisateurs
  - La répudiation
  - Tous les risques liés aux réseaux et à leurs modes de fonctionnement

## Messagerie électronique (suite)

- Mesures de sécurité
  - Antispamset des Antivirus installésde manière complémentaire sur les
    serveurs et les postes de travail
  - Serveur de messagerie de désincubationqui examine systématiquement tous
    les messages et leurs pièces jointes
- Protocoles de messagerie sécurisés
  - SMTP ( _Simple Mail Transfer Protocol_ ) avec l’intégration des mécanismes de
    sécurité comme: - S/MIME ( _Secure Multipurpose Internet Mail Extension_ ) - Extension de sécurité intégrant un processus de sécurité - PEM( _PrivacyEnhancementfor Internet ElectronicMail_ ) - Pour chiffrer des messages électroniques (utilise RSA et DES)  peu utilisé - PGP( _PrettyGood Privacy_ ) - Confidentialité et authentification de l’émetteur

## Messagerie électronique (suite)

- Recommandations pour sécuriser un système de messagerie
  - Du côté du serveur
    - Implanter des logiciels antivirus et antispam
    - Filtrer les messages sur certains critères paramétrables (tailles, fichiers attachés, etc.)
    - Configurer correctement les serveurs
    - Effectuer une gestion efficace pour en assurer la disponibilité
    - Éviter les comptes de maintenance par défaut
    - Assurer une protection physique du serveur
  - Du côté de l’utilisateur
    - Installer, gérer et imposer l’usage de logiciels antivirus
    - Définir des règles d’utilisation de la messagerie (ne pas ouvrir des fichiers exécutables, etc.)
    - Sensibiliser suffisamment les utilisateurs aux risques encourus
    - Faire engager les utilisateurs sur un usage approprié des ressources informatiques
    - Configurer correctement le poste de travail de l’utilisateur et son application de messagerie
    - Implanter des versions de messagerie sécurisées
    - Utiliser des procédures de chiffrement pour les messages confidentiels et réaliser
      l’authentification des sources

## Sécurité des applications Internet

- Secure Sockets Layer (SSL) – Transport Layer Security (TLS)

## Sécurité des applications Internet (suite)

- SSL permet de
  - Chiffrer les communications entre deux machines et d’assurer la confidentialité
    des données
  - L’authentification de l’utilisateur et du serveur
  - L’intégrité des données par signature électronique (via des certificats
    numériques)
- Secure-HTTP (S-HTTP)
  - Sécurité pour les flux de données HTTP
  - Offre de manière complémentaire les mêmes facilités de sécurité que SSL/TLS
    avec les mêmes contraintes de certification
  - Il est possible de combiner S-HTTP et SSL/TLS  attention aux performances!

## Sécurité des applications Internet (suite)

- Authentification des applications
  - Nécessaire pour effectuer des transactions de manière fiable sur Internet
  - Permet d’établir la confiance nécessaire à la réalisation d’une communication
  - Des protocoles cryptographiques permettent de répondre à ce besoin
    - Comme l’usage de certificats numériques

## Sécurité du commerce électronique

- Le commerce électronique pose des problèmes de sécurité

#### informatique semblables à ceux rencontrés avec les applications

#### stratégiques d’une entreprise

- Leurs résolutions emprunteront les mêmes voies méthodologiques,
  organisationnelles et techniques
- Risque élevé de fraude
- Des mesures antifraude accompagnent généralement la mise en place de
  solutions de commerce en ligne

## Sécurité du commerce électronique (suite)

- Protection des transactions commerciales
  - Requiert une démarche globale de
    - Gestion de la sécurité
    - Protection des valeurs de l’entreprise et du consommateur
    - La maîtrise des risques
    - La mise en place de procédures et d’outils de sécurité du côté des clients et des marchands
- Les technologies de la sécurité permettent de contribuer au déroulement

##### correct d’une transaction commerciale, en assurant aux systèmes

##### informatiques les capacités à

- Pouvoir être utilisés
- Ne permettre l’accès aux données et aux ressources informatiques qu’aux personnes
  et aux processus informatiques habiletés
- Pour que des actions, évènements, transactions ont bien eu lieu
- Exécuter les actions et rendre les services attendus dans des conditions de
  performance et d’utilisation adaptées

## Sécurité du commerce électronique (suite)

- Risque pour le client
  - Divulgation d’informations confidentielles ou d’ordre privé
  - Ingénierie sociale (leurre)
  - Infection virale
  - Escroquerie et non-livraison des produits commandés et payés
- Risque pour l’entreprise
  - Intrusion dans son environnement informatique à partir de son site marchand
    Internet ...

## Sécurité du commerce électronique (suite)

- Sécuriser la connexion entre l’acheteur et le vendeur
  - Protocoles promus par les banques et utilisant un canal de communication
    séparé - SET( _Secure Electronic Transaction_ ) - 3 - D Secure (service « _Verifiedby Visa_ ») - MasterCard SecureCode - Etc.
- Sécurité des paiements en ligne
  - Le mode de payement préféré est celui par carte de crédit

## Sécurité du commerce électronique (suite)

- Sécurité des paiements en ligne (suite)

## Sécurité du commerce électronique (suite)

- Sécuriser le serveur revient à
  - Contrôler les requêtes qui lui sont adressées
  - Renforcer la sécurité de la plate-forme matérielle et logicielle
  - Sécuriser le système d’information

## Infrastructure d’une application Web

## Attaques sur les applications Web

- _Cross-site scripting_

#### (XSS)

- Injection SQL
- Injection XML
- Injection des

#### commandes

#### et traversée des

#### répertoires

- Détournement de

#### session

```
Attaques sur les
applications Web
```

```
Attaques
traditionnelles
```

```
Défenses
réseau
```

```
Niveau
applicatif
Niveau
service
Niveau système
d’exploitation
Défenses
additionnelles
```

## Cross-Site Scripting (XSS)

- Injection JavaScript
- Injecter des scripts dans un serveur Web
- Puis les rediriger vers les clients

```
Attaquant
```

```
Victime
```

```
Injecter les scripts XSS
Accéder au serveur Web
```

```
Serveur Web
```

```
XSS utilisé pour attaquer
l’ordinateur de la victime
```

## Cross-Site Scripting (suite)

## Cross-Site Scripting (suite)

- La victime visite le site Web infecté
  - Le code malicieux est envoyé au navigateur Web de la victime
- Le navigateur Web de la victime ne peut pas distinguer un code valide

#### d’un code malicieux

- Exigences du site Web cible
  1. Accepter les entrées des utilisateurs sans validation
  2. Utiliser ces entrées dans la réponse sans les encoder
- Certaines attaques XSS sont conçues pour voler les informations

#### retenues par le navigateur Web lors de transactions sensibles

## Injection SQL

- Cibler les serveurs de bases de données en y injectant des instructions

#### SQL (Structured Query Language )

- Utilisé pour manipuler les données stockées dans une base de données
  relationnelle
- Scénario de mot de passe oublié
- L’attaquant saisit une adresse courriel mal formée
- La réponse lui permet de savoir si les entrées sont validées ou non
- L’attaquant utilise le champ, adresse courriel, pour insérer des instructions SQL
- **SELECT courriel FROM tableutilisateurs WHERE
  courriel = ‘nimportquoi’ OR ‘a’=‘a’**
- Résultat: la liste des identifiants (adresses courriel) de tous les

#### utilisateurs

## Injection SQL (suite)

- Exemples

```
InstructionSQL Résultat
nimportquoi’ AND courriel IS
NULL; -
```

```
Nom des colonnes dela table
```

```
nimportquoi’ OR nom LIKE ‘%Mia%’ Trouver un utilisateur spécifique
nimportquoi’; DROP TABLE
tableusers;
```

```
Supprimer la table des utilisateurs
```

```
nimportquoi’; UPDATE tableusers
SET courriel = ‘courriel-
attaquant@mauvais.net’ WHERE
courriel = ‘Mia@courriel.net’
```

```
Changerl’identifiant d’un utilisateur
spécifique. Le mot de passe peut être
envoyé à l’adresse courriel de
l’attaquant en utilisant le système de
récupération des mots de passe
```

### Injection des commandes et traversée des répertoires

- Serveur Web Windows: C:\Inetpub\ wwwroot ➔ cmd.exe
- Serveur Web Linux: /var/www ➔ /etc/passwd
- Traversée des répertoires - Exploiter les vulnérabilités des applications Web et du Serveur Web - L’attaquant se déplace du répertoire racine ( _root_ ) aux répertoires restreints qui
  contiennent des fichiers sensibles - Exemple: pour afficher la page Web afficher.html
  URL _[http://www.server.net/dynamic.asp?view=afficher.html](http://www.server.net/dynamic.asp?view=afficher.html)_

###### ➔URL http://www.server.net/dynamic.asp?view=../../../../../TopSecret.docx

- Injection des commandes
  - L’attaquant injecte des commandes à exécuter sur le Serveur Web

## Détournement de session

- _Session hijacking_
- L’attaquant cherche à voler ou à deviner l’identifiant de session en

#### cours entre la victime et le serveur Web

```
Victime
```

```
Serveur Web
```

```
L’attaquant écoute la session
```

```
Serveur Web
```

```
L’attaquant utilise l’identifiant volé
```

```
Attaquant
```

```
Attaquant
```

```
Identifiant session
```

```
Identifiant session
```

# Sécurité des systèmes informatiques

```
AbdeltouabBelbekkouche
a.belbekkouche@umontreal.ca
```

## Sécurité des réseaux sans fil

```
1
```

## Contenu

- Attaques sur les réseaux sans fil
- Quelques vulnérabilités des réseaux sans fil
- Solutions de sécurité

## Contexte

- Les technologies sans fil ont révolutionné les réseaux de

#### communication

- Les réseaux sans fil sont partout
- Les réseaux sans fil ont toujours été l’objet d’attaques
- Les premiers standards de réseaux sans fil ont souffert de vulnérabilités
- Certaines solutions proposées à ces vulnérabilités sont aussi vulnérables
- L’amélioration de la sécurité des réseaux sans fil les rend comparables aux
  réseaux filaires

## Réseaux locaux sans fil

- _Wireless LAN_
- IEEE 802.11a
  - Vitesse de transfert maximale de 54 Mbps
- IEEE 802.11g
  - Caractéristiques stables et largement acceptées du standard 802.11b
  - Vitesse de transfert similaire au standard 802.11a
- IEEE 802.11n
  - Ratifié en 2009
  - Vitesse
  - Portée
  - Interférence
  - Sécurité
- IEEE 802.11ac
- IEEE 802.11ax

## Réseaux locaux sans fil (suite)

- Composantes
  - Interfaces / cartes réseau sans fil
    - Mêmes fonctions qu’une carte réseau filaire
    - Antenne pour envoyer et recevoir les signaux
  - Point d’accès ( _Access Point_ – AP)
    - Antenne pour envoyer et recevoir les signaux
    - Logiciel pour faire l’interfaçage entre les dispositifs
      filaires et sans fil
    - Interface / carte réseau filaire qui permet la connexion
      par câble au réseau filaire et Internet
- Fonctions du point d’accès
  - Station de base pour le réseau sans fil
  - Pont entre le réseau sans fil et le réseau filaire
  - Authentification, chiffrement et gestion du réseau
  - Éventuellement pare-feu, routeur, etc.

## Réseaux locaux sans fil: attaques

- Découverte du réseau
- Attaques sur le spectre des fréquences radio
- Attaques impliquant le point d'accès

## Découverte du réseau

- Parmi les premières étapes d’une attaque sur un réseau sans fil
- Balisage ( _Beaconing_ )
  - Le point d’accès envoie des trames ( _frames_ ) à intervalles réguliers pour
    annoncer sa présence et fournir les informations de connexion
  - Le dispositif sans fil fait un balayage pour découvrir ces trames
- _War driving_
  - Découverte «passive» des emplacements des réseaux sans fil
  - Outils
    - Dispositif mobile, interface sans fil, antenne externe, logiciel de _Wardriving_ , GPS

## Découverte du réseau (suite)

- _War chalking_
  - Documenter et publier les emplacements des réseaux sans fil découverts
  - Dessiner des signes distinctifs sur les trottoirs ou les murs autour de la zone du
    réseau
  - Les emplacements peuvent être publiés sur des sites Web

```
Nom du réseau Nom du réseau Nom du réseau
```

```
Réseau fermé Réseau ouvertRéseau ouvert
```

```
Bande passante Bande passante
Réseau chiffré
```

## Attaques sur le spectre des ondes radio

- Analyseur de trafic sans fil
  - Capturer le trafic sans fil pour analyser le
    contenu des ces paquets
  - L’interface réseau doit opérer en mode
    moniteur ( _promiscuous_ )
- Interférences
  - Les transmissions des autres dispositifs sans fil
    peuvent perturber les communications sans fil
  - Dispositifs qui peuvent causer des
    interférences - Fours à micro-ondes - Dispositifs de protection contre le vol - Dispositifs Bluetooth - Etc.

```
Dispositif de
l’attaquant
```

```
Ne peut pas
communiquer avec AP
```

```
Ordinateur de la
victime
```

## Attaques impliquant des points d’accès

- Point d'accès non autorisé ( _Rogue_

#### AP )

- Permet à un attaquant de contourner
  la configuration sécuritaire du réseau
- Ouvre le réseau aux attaquants s’il est
  placé derrière le pare-feu
- Jumeau maléfique ( _evil twin_ )
- Point d’accès installé par l’attaquant
- Essaye d’imiter le point d’accès
  autorisé
- L’attaquant capture les transmissions
  des utilisateurs à ce point d’accès

```
AP non autorisé
```

```
Ordinateur A
```

```
Ordinateur B Ordinateur C Serveur Périmètre sécuritaire du réseau protégé par le pare-feu
```

```
Pare-feu
Bloqué
```

```
Ordinateur de l’attaquant
```

```
Accède à travers l’AP non autorisé
```

## Vulnérabilités IEEE 802.11

- Le comité original IEEE 802.11 avait reconnu que les transmissions

#### sans fil peuvent être vulnérables

- Implémenter plusieurs protections de sécurité dans le standard lui-même
- D’autres protections laissées à la discrétion des fabricants des équipements
  sans fil
- Certaines protections se sont avérées vulnérables à leur tour
- Catégories des vulnérabilités
- Filtrage par adresse MAC
- Diffusion SSID ( _SSID broadcast_ )
- Chiffrement WEP ( _Wired Equivalent Privacy_ )

## Filtrage par adresse MAC

- Permettre ou bloquer une liste d’adresses MAC pour contrôler l’accès

#### au point d’accès

- Les adresses MAC sont échangées en clair
  - Ces adresses sont visibles et peuvent être utilisées (substitution) par un attaquant
- Gérer un grand nombre d’adresses peut s’avérer difficile

```
Exclure ces dispositifs seulement
Autoriser ces dispositifs seulement
```

## Diffusion SSID

- _Service Set Identifier_ (SSID)
- Authentification “ _Open system authentication_ ”
- Faible niveau de sécurité (basée seulement sur la comparaison des

#### SSIDs)

- L’attaquant peut récupérer le SSID lorsque celui-ci est diffusé
- Le SSID peut être découvert dans d’autres trames même lorsque sa

#### diffusion est désactivée

**2. Je veux me connecter à 3. Autorisation de se connecter à**

## Chiffrement WEP

- Protocole de sécurité IEEE 802.11
- Chiffrement des paquets (texte en clair)
- Clé secrète partagée entre le client sans fil et le point d’accès (AP)
  - La même clé utilisée pour chiffrer et déchiffrer les paquets
- Vulnérabilités WEP
  - Taille de la clé: 64-bits ou 128-bits
  - Vecteur d’initialisation ( _Initialization Vector_ – IV) de 24-bits
    - Reproduction des mêmes valeurs quand un vecteur d’initialisation est réutilisé (collision)
    - Attaque IV ( _keystream attack_ ): utiliser l’opérateur XOR pour découvrir le texte en clair

## Chiffrement WEP (suite)

- Étapes du chiffrement WEP

```
Étape 1
```

```
Étape 2 Étape 3
```

```
Étape 4
```

```
Étape 5 Texte chiffré
```

```
Clé secrète
```

```
Cyclic
Redundancy
Check
```

```
Integrity
Check
Value
```

```
Pseudo-
Random
Number
Generator
```

## Chiffrement WEP (suite)

- Opérations XOR

```
Texte en clair A
```

```
Texte chiffré B
```

```
Texte en clair B
```

```
Texte chiffré A
Texte chiffré A
Texte chiffré B
```

```
Texte en clair A
Texte en clair B
```

## Chiffrement WEP (suite)

- Exemple d’attaque IV

```
Texte chiffré 1
Texte chiffré 222
```

```
Texte en clair 1
Texte en clair 222
```

```
Paquet 1:
Paquet 222:
```

## Solutions de sécurité

- Besoin d’une approche unifiée de sécurité
  - IEEE et Wi-Fi Alliance développent des solutions de sécurité
- Standards résultants
  - IEEE 802.11i
  - WPA et WPA2

## WPA

- _Wi-Fi Protected Access_
- Introduit en 2003 par Wi-Fi Alliance
- Chiffrement TKIP ( _Temporal Key Integrity Protocol_ ) pour remplacer

#### WEP

- Utilise des clés de 128-bits
- Clé générée dynamiquement pour chaque paquet ( _per-packet keys_ )
- Authentification PSK ( _Preshared Key_ )
- Clé et mot de passe partagés entre le point d’accès et les clients
- Vulnérabilités WPA
- Gestion des clés
- Partage manuel des clés
- Cas des clients invités
- Mots de passe: faible si inférieur à 20 caractères

## WPA 2

- Introduit en 2004
- Basé sur la version finale du standard IEEE 802.11i
- Authentification basée sur IEEE 802.1x (ou PSK)
  - Initialement développé pour les réseaux filaires
- Chiffrement basé sur AES ( _Advanced Encryption Standard_ – AES)
  - Clé entre 128 - bits et 256-bits
  - Exécution sur matériel préférée

```
Standard Chiffrement Authentification Niveaude sécurité
WEP WEP Clé partagée Bas
WPA TKIP PSK ou 802.1x Moyen
WPA2 AES 802.1x Élevé
```

## Autres mesures de sécurité

- Emplacement des antennes sans fil
  - Au centre de la zone à couvrir
- Contrôler la puissance des transmissions sans fil
  - Certains points d’accès (AP) permettent de contrôler la puissance de
    transmission du signal
  - Réduire la puissance du signal permet de contenir les ondes radio dans le
    périmètre sécuritaire du réseau
- Chercher des AP non autorisés
  - Approche manuelle utilisant un analyseur de trafic sans fil
  - Matériel dédié et / ou spécialisé
- Réseaux locaux sans fil virtuels (Wireless VLANs)
  - VLAN employés, VLAN invités, etc.
