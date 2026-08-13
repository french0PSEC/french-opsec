# french-opsec

**Guide francophone de sécurité opérationnelle (OPSEC) et d'hygiène numérique.**

Ce dépôt explique comment réduire concrètement son exposition numérique : ce qui vous menace réellement, quelles mesures fonctionnent, ce qu'elles ne protègent pas, et comment éviter les erreurs qui annulent la protection.

Il s'adresse aux débutants complets comme aux personnes déjà expérimentées. Aucune connaissance préalable en cybersécurité n'est nécessaire pour commencer : chaque terme technique est défini à sa première apparition et repris dans le [glossaire](#40-glossaire).

**Dernière vérification générale du contenu : août 2026.**

---

## Avertissement

Quelques principes qui gouvernent tout ce document.

1. **Aucun outil ne rend anonyme.** Aucune application, aucun VPN, aucun système d'exploitation ne rend « intraçable ». Toute affirmation contraire est du marketing. Ce guide décrit ce que chaque outil protège et, tout aussi important, ce qu'il ne protège pas.
2. **L'OPSEC est un processus, pas un produit.** Installer douze applications sans comprendre le raisonnement produit une fausse sécurité, souvent pire que l'absence de mesure, parce qu'elle encourage des comportements risqués.
3. **La bonne solution dépend de votre situation.** Un parent qui veut limiter le pistage publicitaire, une journaliste qui protège une source et une personne victime de harcèlement n'ont pas le même modèle de menace, donc pas les mêmes réponses.
4. **Ce document n'est pas un conseil juridique.** Les références légales sont fournies à titre informatif et évoluent vite.
5. **L'information périme.** Un outil recommandé aujourd'hui peut être racheté, abandonné ou compromis demain. Les sections sensibles portent une date de vérification. En cas de doute, remontez toujours à la [source officielle](#41-ressources).

---

## Comment lire ce document

Le document est long parce que le sujet l'est. Il n'est pas fait pour être lu d'une traite.

| Votre situation | Parcours conseillé |
| --- | --- |
| Je débute, je veux les bases utiles ce week-end | Sections [1](#1-comprendre-lopsec), [2](#2-construire-son-modèle-de-menace), [7](#7-démarrage-rapide), [8](#8-mots-de-passe-et-gestionnaires), [9](#9-authentification-multifacteur-et-passkeys), [34](#34-que-faire-en-cas-de-fuite-de-données) |
| Mes données ont fuité, je fais quoi maintenant | Section [34](#34-que-faire-en-cas-de-fuite-de-données) directement, puis [8](#8-mots-de-passe-et-gestionnaires), [9](#9-authentification-multifacteur-et-passkeys), [36](#36-phishing-et-ingénierie-sociale) |
| Je veux réduire le pistage au quotidien | Sections [15](#15-dns), [16](#16-vpn), [18](#18-navigateurs-et-empreinte-numérique), [29](#29-réseaux-sociaux-et-exposition-publique), [30](#30-courtiers-en-données-et-effacement) |
| Je suis journaliste, chercheur, militant, enquêteur OSINT | Sections [2](#2-construire-son-modèle-de-menace), [3](#3-les-six-notions-à-maîtriser), [17](#17-tor), [22](#22-systèmes-spécialisés-pour-usages-sensibles), [28](#28-compartimentation-et-identités), [37](#37-opsec-avancée-pour-profils-exposés), [38](#38-études-de-cas-déchecs-opsec) |
| Je veux juste des listes d'actions | Section [39](#39-checklists) |

Les sections consacrées à un outil ou à une technique suivent toujours la même trame :

> **Pourquoi** (quelle menace cela réduit) → **Comment** (mise en place) → **Ce que cela ne protège pas** (limites) → **Pièges** (erreurs qui annulent la protection) → **Alternatives**.

Trois marqueurs de niveau apparaissent dans le texte :

- 🟢 **Base** : recommandé à tout le monde, coût faible, bénéfice élevé.
- 🟡 **Intermédiaire** : demande un peu d'apprentissage ou change des habitudes.
- 🔴 **Avancé** : réservé aux modèles de menace élevés, coût d'usage réel, échec probable si mal appliqué.

---

## Sommaire

**Partie I. Raisonner**

1. [Comprendre l'OPSEC](#1-comprendre-lopsec)
2. [Construire son modèle de menace](#2-construire-son-modèle-de-menace)
3. [Les six notions à maîtriser](#3-les-six-notions-à-maîtriser)
4. [Les erreurs de raisonnement les plus courantes](#4-les-erreurs-de-raisonnement-les-plus-courantes)

**Partie II. Le terrain en 2026**

5. [Le paysage des menaces en 2026](#5-le-paysage-des-menaces-en-2026)
6. [Contexte réglementaire européen et français](#6-contexte-réglementaire-européen-et-français)

**Partie III. Les fondations**

7. [Démarrage rapide](#7-démarrage-rapide)
8. [Mots de passe et gestionnaires](#8-mots-de-passe-et-gestionnaires)
9. [Authentification multifacteur et passkeys](#9-authentification-multifacteur-et-passkeys)
10. [Sauvegardes et chiffrement des supports](#10-sauvegardes-et-chiffrement-des-supports)
11. [Adresses email et alias](#11-adresses-email-et-alias)
12. [Numéro de téléphone et carte SIM](#12-numéro-de-téléphone-et-carte-sim)

**Partie IV. Communiquer**

13. [Messageries chiffrées](#13-messageries-chiffrées)
14. [Email chiffré et PGP](#14-email-chiffré-et-pgp)

**Partie V. Réseau et navigation**

15. [DNS](#15-dns)
16. [VPN](#16-vpn)
17. [Tor](#17-tor)
18. [Navigateurs et empreinte numérique](#18-navigateurs-et-empreinte-numérique)
19. [Moteurs de recherche](#19-moteurs-de-recherche)

**Partie VI. Appareils**

20. [Smartphones](#20-smartphones)
21. [Ordinateurs et systèmes d'exploitation](#21-ordinateurs-et-systèmes-dexploitation)
22. [Systèmes spécialisés pour usages sensibles](#22-systèmes-spécialisés-pour-usages-sensibles)
23. [Objets connectés et domicile](#23-objets-connectés-et-domicile)
24. [Sécurité physique et voyages](#24-sécurité-physique-et-voyages)

**Partie VII. Données**

25. [Fichiers et métadonnées](#25-fichiers-et-métadonnées)
26. [Chiffrement des données et coffres](#26-chiffrement-des-données-et-coffres)
27. [Cloud et auto-hébergement](#27-cloud-et-auto-hébergement)

**Partie VIII. Identité et exposition**

28. [Compartimentation et identités](#28-compartimentation-et-identités)
29. [Réseaux sociaux et exposition publique](#29-réseaux-sociaux-et-exposition-publique)
30. [Courtiers en données et effacement](#30-courtiers-en-données-et-effacement)
31. [Auto-audit OSINT](#31-auto-audit-osint)
32. [Confidentialité financière](#32-confidentialité-financière)
33. [Intelligence artificielle](#33-intelligence-artificielle)

**Partie IX. Réagir**

34. [Que faire en cas de fuite de données](#34-que-faire-en-cas-de-fuite-de-données)
35. [Réagir à un incident](#35-réagir-à-un-incident)
36. [Phishing et ingénierie sociale](#36-phishing-et-ingénierie-sociale)

**Partie X. Aller plus loin**

37. [OPSEC avancée pour profils exposés](#37-opsec-avancée-pour-profils-exposés)
38. [Études de cas d'échecs OPSEC](#38-études-de-cas-déchecs-opsec)

**Partie XI. Références**

39. [Checklists](#39-checklists)
40. [Glossaire](#40-glossaire)
41. [Ressources](#41-ressources)
42. [Sources](#42-sources)
43. [Contribuer et maintenir ce projet](#43-contribuer-et-maintenir-ce-projet)

---

# Partie I. Raisonner

## 1. Comprendre l'OPSEC

**OPSEC** est l'abréviation de *operational security*, en français « sécurité opérationnelle ». La notion vient du domaine militaire : pendant la guerre du Vietnam, l'armée américaine constate que l'adversaire anticipe ses opérations sans avoir cassé le moindre chiffrement. Il lui suffisait d'observer des éléments individuellement anodins et publics (mouvements logistiques, trafic radio, habitudes) et de les recouper.

C'est exactement le problème auquel vous faites face en ligne. Personne n'a besoin de « pirater » quoi que ce soit pour savoir où vous habitez, où vous travaillez, qui vous fréquentez et à quelle heure vous dormez. Ces informations sont déjà éparpillées, publiques ou revendues, et il suffit de les rassembler.

### La différence entre sécurité, vie privée et anonymat

Trois objectifs distincts, souvent confondus, qui appellent des mesures différentes.

| Objectif | Question à laquelle il répond | Exemple de mesure |
| --- | --- | --- |
| **Sécurité** | Mes données et mes comptes sont-ils protégés contre un accès non autorisé | Mot de passe unique, MFA, mises à jour |
| **Vie privée** | Qui peut observer ce que je fais, même légitimement | Bloquer les traqueurs, limiter la collecte, chiffrer |
| **Anonymat** | Peut-on relier cette activité à mon identité civile | Tor, pseudonymes cloisonnés, absence de paiement traçable |

Ils ne progressent pas ensemble. Un compte bancaire est très sécurisé et absolument pas anonyme. Un compte jetable sur un forum peut être anonyme et très mal sécurisé. Savoir lequel des trois vous cherchez évite 90 % des mauvaises décisions.

### L'OPSEC comme boucle, pas comme achat

La démarche classique en cinq étapes, transposée au numérique :

```
   ┌──────────────────────────────────────────────────────┐
   │                                                      │
   ▼                                                      │
1. IDENTIFIER    Quelles informations me nuiraient si     │
   les actifs    elles étaient connues ou perdues         │
   │                                                      │
   ▼                                                      │
2. IDENTIFIER    Qui pourrait vouloir ces informations    │
   l'adversaire  et de quels moyens dispose-t-il          │
   │                                                      │
   ▼                                                      │
3. ANALYSER      Par où fuient-elles aujourd'hui          │
   les failles   (comptes, appareils, habitudes, tiers)   │
   │                                                      │
   ▼                                                      │
4. ÉVALUER       Quelle est la probabilité et l'impact    │
   le risque     réel de chaque scénario                  │
   │                                                      │
   ▼                                                      │
5. APPLIQUER     Mesures proportionnées, puis on          │
   des mesures   recommence quand la situation change ────┘
```

La cinquième étape ramène à la première : un changement de travail, une rupture, une prise de parole publique, un déménagement, une nouvelle loi, tout cela modifie le modèle. Une OPSEC figée devient fausse avec le temps.

### Ce que l'OPSEC n'est pas

- Ce n'est pas une collection d'applications. Installer Signal ne protège rien si votre correspondant met la conversation en sauvegarde cloud non chiffrée.
- Ce n'est pas une course au maximum. Une configuration trop lourde finit contournée par son propre utilisateur, ce qui produit une exposition pire et surtout imprévisible.
- Ce n'est pas réservé aux personnes qui ont « quelque chose à cacher ». Vous avez des choses à protéger : vos comptes, votre argent, votre réputation, la sécurité de vos proches, votre santé, votre position politique ou syndicale, votre carrière.

---

## 2. Construire son modèle de menace

Le **modèle de menace** (*threat model*) est la pièce centrale. Tout le reste en découle. Il tient en cinq questions, popularisées notamment par l'Electronic Frontier Foundation.

1. **Qu'est-ce que je veux protéger** (vos actifs : messages, localisation, identité civile, argent, photos, sources, appartenance à un groupe)
2. **Contre qui** (votre adversaire : un annonceur, un ex-conjoint, un collègue, un escroc opportuniste, un employeur, une administration, un service de renseignement)
3. **Quelles sont les conséquences si j'échoue** (gêne, perte financière, licenciement, harcèlement, violence physique, poursuites)
4. **Quelle est la probabilité que cela arrive** (une attaque ciblée par un service étatique n'a pas la même probabilité qu'un vol d'identifiants par réutilisation de mot de passe)
5. **Combien suis-je prêt à payer** (en argent, en temps, en confort, en relations sociales)

### Écrire son modèle de menace

Prenez dix minutes et remplissez ce tableau, honnêtement. C'est l'exercice le plus rentable de tout ce guide.

| Actif à protéger | Adversaire réaliste | Impact si échec | Probabilité | Mesure choisie |
| --- | --- | --- | --- | --- |
| Compte bancaire | Escroc, credential stuffing | Élevé | Élevée | Mot de passe unique + MFA + surveillance |
| Adresse du domicile | Harceleur en ligne | Très élevé | Moyenne | Nettoyage OSINT, cloisonnement pseudos |
| Historique médical | Employeur, assureur, courtier de données | Élevé | Faible à moyenne | Compartimentation, pas d'appli santé tierce |
| Identité d'une source | Adversaire disposant d'accès légaux | Critique | Variable | Tails, Tor, appareil dédié, pas de croisement |

### Profils types

Ces profils sont des points de départ, pas des cases. Beaucoup de personnes en combinent plusieurs.

**Profil A. Particulier, adversaire opportuniste.** La menace dominante est automatisée et non ciblée : fuites de données, réutilisation de mots de passe, phishing de masse, arnaques, pistage publicitaire. Les sections [7](#7-démarrage-rapide) à [12](#12-numéro-de-téléphone-et-carte-sim) couvrent l'essentiel du risque réel. Tor et Qubes OS ne vous concernent probablement pas.

**Profil B. Exposition publique.** Créateur de contenu, élu local, personne médiatisée, modérateur. La menace dominante est le doxing, c'est-à-dire la publication d'informations personnelles pour nuire, et le harcèlement coordonné. Priorité : [auto-audit OSINT](#31-auto-audit-osint), [courtiers en données](#30-courtiers-en-données-et-effacement), [compartimentation](#28-compartimentation-et-identités), sécurité du domicile.

**Profil C. Adversaire relationnel.** Ex-conjoint violent, membre de la famille, colocataire, collègue. C'est le modèle le plus difficile, parce que l'adversaire connaît vos réponses de sécurité, a eu un accès physique à vos appareils, et peut être présent sur vos comptes partagés. Priorité : accès physique, *stalkerware*, partages de localisation oubliés, comptes familiaux, [section 35](#35-réagir-à-un-incident). En France, le [3919](https://www.solidaritefemmes.org/) et les associations spécialisées accompagnent aussi le volet numérique.

**Profil D. Journaliste, source, lanceur d'alerte, militant, chercheur.** Adversaire disposant de moyens légaux, techniques et de temps. Priorité : cloisonnement strict, [Tor](#17-tor), [Tails](#22-systèmes-spécialisés-pour-usages-sensibles), appareils dédiés, protection des métadonnées, procédures écrites et répétées.

**Profil E. Professionnel de la sécurité, enquêteur OSINT, administrateur.** Le risque particulier est le retour de flamme : votre activité d'investigation révèle votre identité ou celle de votre employeur. Priorité : [section 37](#37-opsec-avancée-pour-profils-exposés).

### Le budget de risque

L'OPSEC n'est pas gratuite. Chaque mesure coûte du temps, du confort ou de l'argent, et parfois de l'isolement social. Un modèle de menace correct sert d'abord à ne **pas** appliquer les mesures inutiles, pour pouvoir tenir dans la durée celles qui comptent.

Ordre de grandeur pour un particulier : un gestionnaire de mots de passe et une authentification à deux facteurs bien mise en place éliminent la grande majorité du risque réel, pour environ deux heures d'installation. Passer à Qubes OS coûte des semaines et n'apporte rien contre ces menaces-là.

---

## 3. Les six notions à maîtriser

Six notions suffisent à raisonner correctement dans presque toutes les situations décrites dans ce guide.

### 3.1 Surface d'exposition

Tout ce qui, vous concernant, est accessible à quelqu'un d'autre : comptes ouverts, applications installées, permissions accordées, publications, appareils connectés, données confiées à des tiers, informations détenues par des entreprises avec lesquelles vous avez signé un contrat.

Deux règles simples et efficaces :

- **La donnée qui n'existe pas ne fuit pas.** Ne pas créer un compte est plus efficace que le sécuriser. Supprimer un compte inutilisé supprime la fuite future qui l'accompagne.
- **La donnée que vous ne contrôlez pas est déjà perdue en puissance.** Toute information confiée à un tiers doit être considérée comme potentiellement publique un jour, par piratage, par revente, par changement de politique ou par réquisition légale.

### 3.2 Corrélation

C'est le mécanisme central de la désanonymisation. Chaque élément pris isolément est banal ; c'est leur recoupement qui identifie.

```
Pseudo "kirin_92"  ─┐
Photo de profil    ─┤
Adresse email      ─┼──►  Même personne, avec un bon niveau de certitude,
Numéro de téléphone─┤     même si aucun élément n'était identifiant seul
Horaires d'activité─┤
Style d'écriture   ─┘
```

Exemples de vecteurs de corrélation qu'on oublie presque toujours :

- **La réutilisation d'un pseudonyme** entre un compte anonyme et un compte nominatif, même très ancien, même supprimé (les archives et les moteurs conservent).
- **Le numéro de téléphone**, identifiant quasi universel qui relie compte bancaire, réseaux sociaux, livraisons et état civil.
- **La photo**, via la recherche d'image inversée ou la reconnaissance faciale, y compris recadrée.
- **Les horaires**, un compte « anonyme » qui n'écrit qu'aux heures de bureau d'un fuseau donné restreint énormément le champ.
- **Le style d'écriture** (stylométrie), analysable automatiquement, y compris par des modèles de langage récents.
- **Le paiement**, une carte bancaire ou un abonnement mensuel relie tout.
- **L'adresse IP**, souvent stable chez un particulier, partagée entre tous vos usages.
- **L'appareil**, une même empreinte de navigateur ou un même identifiant publicitaire relie des sessions séparées.

Un principe en découle, valable partout : **une identité, un canal, un appareil, une raison d'être**. Dès que deux identités partagent un élément, considérez-les comme reliées.

### 3.3 Compartimentation

Séparer volontairement ses activités pour qu'une compromission dans un compartiment n'affecte pas les autres. C'est le principe des cloisons étanches d'un navire.

```
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│  IDENTITÉ    │  │  IDENTITÉ    │  │  IDENTITÉ    │
│  CIVILE      │  │  PRO         │  │  PSEUDONYME  │
├──────────────┤  ├──────────────┤  ├──────────────┤
│ banque       │  │ email pro    │  │ forum        │
│ impôts       │  │ LinkedIn     │  │ blog         │
│ santé        │  │ outils métier│  │ chat         │
├──────────────┤  ├──────────────┤  ├──────────────┤
│ email A      │  │ email B      │  │ email C      │
│ tél. réel    │  │ tél. pro     │  │ pas de tél.  │
│ navigateur 1 │  │ navigateur 2 │  │ navigateur 3 │
└──────────────┘  └──────────────┘  └──────────────┘
   Aucun élément partagé entre deux colonnes
```

La compartimentation échoue toujours par la même cause : la fatigue. Elle doit être simple, écrite, et assez peu nombreuse pour être tenue. Trois compartiments tenus valent mieux que huit abandonnés. Voir la [section 28](#28-compartimentation-et-identités).

### 3.4 Métadonnées

Les **métadonnées** sont les données autour du contenu : qui, quand, où, avec qui, combien de temps, à quelle fréquence, depuis quel appareil.

Elles sont plus révélatrices que le contenu lui-même, parce qu'elles sont structurées, faciles à analyser à grande échelle, et rarement chiffrées. Le contenu d'un message chiffré est illisible ; le fait que vous ayez échangé quarante messages avec un avocat spécialisé en droit du travail à 23 h la veille de votre démission ne l'est pas.

Sources classiques de métadonnées : en-têtes d'email, EXIF des photos (modèle d'appareil, date, coordonnées GPS), propriétés des documents bureautiques et PDF, journaux de connexion, données de facturation télécom, historique DNS, listes de contacts synchronisées.

### 3.5 Chaîne de confiance

À chaque action, demandez-vous : qui doit être honnête et compétent pour que ma protection tienne ?

Exemple pour un simple message chiffré :

```
Vous → votre appareil → votre OS → l'application → le serveur du fournisseur
     → le réseau → l'appareil du destinataire → le destinataire lui-même
```

Le chiffrement de bout en bout protège le segment réseau. Il ne protège ni les extrémités (appareil compromis, capture d'écran, sauvegarde cloud) ni le destinataire (qui peut transmettre). C'est la raison pour laquelle un téléphone compromis annule le bénéfice de n'importe quelle messagerie, et pourquoi la sécurité de l'appareil prime sur le choix de l'application.

### 3.6 Coût et proportionnalité

Une mesure a un coût d'usage. Si ce coût dépasse votre tolérance, vous la contournerez, et le contournement sera pire que l'absence de mesure parce qu'il sera improvisé.

Grille de décision utile :

| | Impact faible | Impact élevé |
| --- | --- | --- |
| **Probabilité faible** | Ignorer, accepter | Mesure simple, plan de réaction |
| **Probabilité élevée** | Mesure automatique, peu coûteuse | Priorité absolue, mesure robuste et vérifiée |

---

## 4. Les erreurs de raisonnement les plus courantes

Ces erreurs coûtent plus cher que les erreurs techniques, parce qu'elles orientent tous les choix suivants.

**« Cet outil me rend anonyme. »** Aucun outil ne le fait. Tor cache votre adresse IP à un site, il ne vous empêche pas de vous connecter à votre compte nominatif depuis Tor, ce qui annule tout. L'anonymat est une propriété de votre comportement complet, pas d'un logiciel.

**« J'ai un VPN, je suis protégé. »** Un VPN déplace la confiance de votre fournisseur d'accès vers le fournisseur de VPN. Il ne bloque ni les traqueurs, ni le fingerprinting, ni les malwares, ni le phishing, et il ne fait rien contre le fait que vous soyez connecté à votre compte. Voir [section 16](#16-vpn).

**« Je n'ai rien à cacher. »** Le contre-argument utile n'est pas moral mais pratique : ce ne sont pas des secrets qui vous exposent, ce sont des informations banales recoupées par quelqu'un de mal intentionné, aujourd'hui ou dans cinq ans, dans un contexte que vous ne contrôlez pas. Vous fermez la porte de vos toilettes sans avoir de secret à y cacher.

**« Je suis trop insignifiant pour être visé. »** La grande majorité des attaques ne visent personne en particulier. Elles moulinent des listes d'identifiants issues de fuites. L'absence d'intérêt ne protège pas d'un traitement automatisé.

**« C'est open source, donc c'est sûr. »** Le code ouvert est une condition d'auditabilité, pas une preuve d'audit. La bonne question est : ce code a-t-il été audité, par qui, quand, et le rapport est-il public ? Un projet open source abandonné depuis trois ans est plus dangereux qu'un logiciel propriétaire maintenu.

**« C'est chiffré, donc c'est privé. »** Précisez toujours : chiffré **en transit** (entre vous et le serveur, le fournisseur voit tout), **au repos** (sur le disque du serveur, le fournisseur détient souvent la clé), ou **de bout en bout** (seuls les correspondants peuvent lire). Ces trois choses sont vendues avec le même mot.

**« Le mode navigation privée me protège. »** Il empêche l'enregistrement local de l'historique et des cookies. Le site visité, votre fournisseur d'accès, votre employeur et les traqueurs vous voient exactement comme d'habitude.

**« J'ai tout configuré, c'est fini. »** L'OPSEC se dégrade toute seule : mises à jour qui réactivent des options, nouveaux comptes, nouvelles applications, changement de politique d'un service. Prévoyez une révision, par exemple deux fois par an.

**« Je vais tout faire d'un coup. »** L'approche « big bang » échoue presque toujours et fait souvent perdre l'accès à des comptes. Procédez par lots, en commençant par les comptes critiques (email principal, banque, opérateur).

**« Mon adversaire est la NSA. »** Pour presque tout le monde, l'adversaire réel est un escroc automatisé, un annonceur, un proche, ou un employeur. Se protéger contre un adversaire fantasmé fait négliger le vrai.

---

# Partie II. Le terrain en 2026

## 5. Le paysage des menaces en 2026

Cette section décrit ce qui se passe réellement, pas ce qui fait peur. Elle est datée volontairement.

*Vérifié : août 2026.*

### 5.1 Les fuites de données sont devenues structurelles

En France, la CNIL a reçu 6 167 notifications de violations de données personnelles en 2025, soit environ 10 % de plus que l'année précédente, et le rythme a encore augmenté début 2026 avec plus de 2 700 notifications sur le seul premier trimestre. La tendance la plus significative n'est pas le nombre, mais la taille : la part des incidents touchant plus d'un million de personnes augmente, ce qui indique que les attaquants ciblent désormais les grandes bases (santé, distribution, opérateurs, services publics, courtiers).

Conséquences pratiques pour vous :

- Vos données personnelles de base (nom, adresse postale, date de naissance, email, téléphone, parfois IBAN ou numéro de sécurité sociale) sont probablement déjà en circulation. Le raisonnement utile n'est pas « comment empêcher cela » mais « comment faire en sorte que cela ne suffise pas à me nuire ».
- Une fuite ancienne reste dangereuse. Les données d'identité ne se changent pas : votre date de naissance de 2019 est toujours valable en 2026. Les jeux de données fuités sont agrégés, recoupés et revendus pendant des années.
- Le risque principal après une fuite n'est pas le contenu lui-même, mais **l'attaque secondaire** : phishing très crédible parce qu'il cite vos vraies informations, usurpation auprès d'un service client, SIM swapping, fraude au conseiller bancaire.

Voir le mode opératoire complet en [section 34](#34-que-faire-en-cas-de-fuite-de-données).

### 5.2 Les infostealers, menace numéro un pour les particuliers

Un **infostealer** est un logiciel malveillant qui, une fois exécuté, siphonne en quelques secondes tout ce que contient votre navigateur : mots de passe enregistrés, cookies de session, jetons d'authentification, portefeuilles de cryptomonnaies, fichiers de configuration.

Deux points sont mal compris :

1. **Le vol de cookie de session contourne l'authentification à deux facteurs.** Un cookie de session est la preuve que vous vous êtes déjà authentifié. Le rejouer sur une autre machine ouvre le compte sans redemander de code. C'est aujourd'hui le mode d'entrée dominant dans les compromissions de comptes.
2. **La contamination vient surtout de l'utilisateur.** Logiciel « craqué », faux installeur, extension de navigateur vérolée, pièce jointe, faux CAPTCHA demandant de coller une commande dans une fenêtre système (technique dite *ClickFix*), fichier reçu d'un contact déjà infecté.

Les volumes annoncés par les entreprises du secteur se comptent en milliards d'identifiants et en millions d'appareils infectés par an. Ces chiffres varient beaucoup selon la méthodologie, mais l'ordre de grandeur et la tendance ne sont pas contestés.

Contre-mesures réellement efficaces : ne pas exécuter de logiciel non vérifié, se déconnecter des sessions sensibles, révoquer les sessions actives régulièrement, préférer les [passkeys et clés matérielles](#9-authentification-multifacteur-et-passkeys) qui résistent au rejeu, chiffrer et verrouiller le gestionnaire de mots de passe plutôt que d'utiliser celui du navigateur.

### 5.3 Phishing moderne et contournement de la MFA

Le phishing par courriel truffé de fautes appartient au passé. En 2026, on observe :

- des pages de connexion relayées en temps réel (*adversary in the middle*) qui capturent le mot de passe **et** le code à usage unique, puis la session ;
- du *vishing* (appel téléphonique) et du *smishing* (SMS) utilisant vos vraies données issues de fuites, y compris le nom de votre conseiller ou vos dernières commandes ;
- de la fraude au support technique, au livreur, à l'assurance maladie, aux amendes ;
- des voix clonées par IA à partir de quelques secondes d'enregistrement public, utilisées pour la fraude au président en entreprise et l'arnaque au proche en détresse chez les particuliers.

Seules deux familles de protections résistent structurellement : l'authentification **liée à l'origine** (passkeys, WebAuthn, clés FIDO2, qui refusent de s'authentifier sur un faux domaine) et la **vérification hors bande** (rappeler soi-même un numéro officiel, utiliser un mot de passe familial convenu à l'avance).

### 5.4 Le pistage a basculé du cookie vers l'empreinte

Le cookie tiers a perdu sa place centrale, sans que le pistage ne diminue. Google a renoncé en 2025 à supprimer les cookies tiers de Chrome tout en assouplissant sa politique publicitaire sur l'usage des empreintes d'appareil, ce qui a validé un mouvement déjà engagé.

Les techniques dominantes aujourd'hui :

- **Fingerprinting** : identification par la combinaison de dizaines de caractéristiques (rendu graphique canvas et WebGL, polices installées, résolution, fuseau horaire, langues, extensions détectables, comportement audio). Rien n'est stocké chez vous, donc supprimer ses cookies ne change rien.
- **Suivi côté serveur** et **CNAME cloaking** : le traqueur est servi depuis le domaine du site lui-même, ce qui le rend indiscernable du contenu légitime pour beaucoup de bloqueurs.
- **Identifiants dans les URL** (`gclid`, `fbclid`, `utm_*`) qui survivent au partage d'un lien.
- **Pixels de suivi dans les emails** qui signalent l'ouverture, l'heure, l'appareil et l'adresse IP approximative.
- **Graphes d'identité inter-appareils** qui relient téléphone, ordinateur et téléviseur connecté d'un même foyer, souvent via l'adresse IP et l'heure.
- **SDK publicitaires mobiles** intégrés dans les applications, source majeure de données de localisation revendues.

Réponses proportionnées : [navigateur résistant au fingerprinting](#18-navigateurs-et-empreinte-numérique), blocage au niveau [DNS](#15-dns), cloisonnement par navigateur ou par profil, réduction du nombre d'applications mobiles.

### 5.5 Courtiers en données et OSINT commercial

Les **courtiers en données** (*data brokers*) achètent, agrègent et revendent des profils : identité, adresses successives, entourage, revenus estimés, centres d'intérêt, déplacements. En France, s'ajoutent des sources publiques légales très riches (annuaires, registres d'entreprises, avis de décès, listes électorales consultables, cadastre, données immobilières). Un profil complet peut se reconstituer en une heure sans aucune intrusion.

Voir [section 30](#30-courtiers-en-données-et-effacement) et [section 31](#31-auto-audit-osint).

### 5.6 Téléphonie, SIM swapping et localisation

Le numéro de téléphone est devenu un identifiant central et un point de défaillance unique. Le **SIM swapping** consiste à convaincre un opérateur de transférer votre numéro vers une carte SIM ou un profil eSIM contrôlé par l'attaquant, à l'aide d'informations personnelles souvent issues de fuites. Tout ce qui repose sur les SMS (réinitialisation de mot de passe, code de validation bancaire) tombe alors.

Le passage à l'eSIM a supprimé la nécessité d'un accès physique, ce qui rend l'attaque plus discrète, même si les procédures de vérification d'identité se sont durcies.

Par ailleurs, votre opérateur connaît en permanence votre position approximative, et les données de localisation issues des applications mobiles alimentent un marché parallèle.

### 5.7 Intelligence artificielle

Trois effets distincts, à ne pas confondre :

- **Ce que vous donnez à l'IA.** Les conversations avec un service en ligne sont stockées, parfois utilisées pour l'entraînement, et peuvent être exigées par la justice. Aux États-Unis, un litige a conduit en 2025 à une obligation de conservation étendue des journaux de conversation d'un grand fournisseur, y compris de conversations supprimées, et des décisions ultérieures ont confirmé l'absence de secret professionnel attaché à ces échanges. Une conversation avec un assistant IA n'est pas confidentielle au sens juridique.
- **Ce que l'IA permet contre vous.** Clonage de voix et de visage, phishing rédigé sans faute et personnalisé, corrélation stylométrique, reconnaissance faciale de masse, analyse automatisée d'images pour en déduire un lieu.
- **Ce que l'IA vous apporte.** Exécutée localement, elle permet de traiter des documents sensibles sans les envoyer à un tiers. Voir [section 33](#33-intelligence-artificielle).

### 5.8 Surveillance légale et évolution des règles

Détaillée en [section 6](#6-contexte-réglementaire-européen-et-français). L'essentiel à retenir : la protection technique et la protection juridique évoluent en sens contraire sur plusieurs dossiers, ce qui rend le choix de la juridiction d'un fournisseur moins déterminant qu'auparavant, et le chiffrement de bout en bout, avec des clés que le fournisseur ne détient pas, plus déterminant.

---

## 6. Contexte réglementaire européen et français

Cette section explique des dossiers techniques, sans prendre parti politiquement. Elle décrit ce qui change concrètement pour vous et ce qui, techniquement, y résiste ou non. Le droit évolue vite : vérifiez toujours l'état d'avancement à la date de votre lecture.

*Vérifié : août 2026.*

### 6.1 Chat Control, ou règlement CSAR

**De quoi il s'agit.** La Commission européenne a proposé en mai 2022 un règlement destiné à prévenir et combattre les abus sexuels sur enfants en ligne (*Child Sexual Abuse Regulation*, CSAR), surnommé « Chat Control » par ses opposants. Le point contesté est la possibilité d'imposer aux fournisseurs de services de communication la détection de contenus dans les messages privés, y compris pour des services chiffrés de bout en bout.

**Pourquoi c'est un sujet technique et pas seulement politique.** Sur un service chiffré de bout en bout, le fournisseur ne peut pas lire les messages. La seule façon de les analyser est de le faire **avant chiffrement, sur l'appareil de l'utilisateur** : c'est le *client-side scanning*, l'analyse côté client. Une large partie de la communauté cryptographique considère qu'un tel dispositif crée un mécanisme d'inspection généralisé, extensible à d'autres finalités, et qu'il affaiblit la garantie du chiffrement de bout en bout indépendamment de la légitimité de l'objectif poursuivi.

**Où en est le dossier en août 2026.** Il faut distinguer deux textes qu'on confond souvent.

| Texte | Nature | État |
| --- | --- | --- |
| **Régime intérimaire** (« Chat Control 1.0 ») | Dérogation à la directive ePrivacy autorisant le scan **volontaire** par les fournisseurs sur les services non chiffrés de bout en bout | A expiré début avril 2026 après le rejet d'une prolongation par le Parlement en mars 2026, puis a été rétabli et prolongé jusqu'au 3 avril 2028 (vote du Parlement le 9 juillet 2026, confirmation du Conseil le 23 juillet 2026), en excluant les services chiffrés de bout en bout |
| **Règlement CSAR** (« Chat Control 2.0 ») | Texte permanent, incluant la question des injonctions de détection, de la vérification d'âge et de l'accès des mineurs | Non adopté. Position du Parlement en novembre 2023, position du Conseil en novembre 2025, trilogues successifs jusqu'au 29 juin 2026 sans accord, reprise des négociations à partir de septembre 2026 |

**Ce que cela change pour vous, concrètement.**

- Aujourd'hui, aucun scan obligatoire de vos messages chiffrés de bout en bout n'est en vigueur dans l'Union européenne.
- Le scan **volontaire** existe et est massivement pratiqué depuis des années par les grandes plateformes sur les services **non chiffrés** : messagerie web, réseaux sociaux, stockage cloud, courriels classiques. Si vous utilisez Gmail, Messenger ou un cloud grand public, vos contenus sont déjà analysables.
- Le risque à surveiller porte sur le texte permanent et sur deux dispositions annexes souvent négligées : la **vérification d'âge généralisée**, qui met mécaniquement fin à la possibilité d'ouvrir un compte de communication anonyme, et les restrictions d'accès des mineurs à certaines applications.

**Que faire, indépendamment de l'issue.** Les mesures utiles sont les mêmes que dans le reste du guide : privilégier les services où le fournisseur ne détient pas les clés, réduire la dépendance à une plateforme unique, préférer les logiciels libres dont on peut vérifier les binaires, savoir migrer rapidement. Un service dont le code est ouvert et reproductible rend une modification silencieuse plus difficile à dissimuler.

**Pour suivre le dossier** : [exitchatcontrol.eu](https://exitchatcontrol.eu/), le suivi de [Patrick Breyer](https://www.patrick-breyer.de/en/posts/chat-control/), [EDRi](https://edri.org/), [La Quadrature du Net](https://www.laquadrature.net/).

### 6.2 Vérification d'âge et fin de l'anonymat par effet de bord

La France a adopté en juillet 2026 une loi interdisant les réseaux sociaux aux moins de 15 ans, avec vérification d'âge obligatoire à la création de compte à partir du 1er septembre 2026 et régularisation des comptes existants d'ici le 1er janvier 2027. Le mouvement est européen : déclaration commune de ministres du numérique en octobre 2025, résolution du Parlement européen en novembre 2025 en faveur d'une majorité numérique harmonisée.

**L'enjeu technique.** Une vérification d'âge peut être conçue de deux manières :

- **Divulgation directe** : vous envoyez votre pièce d'identité ou votre visage à la plateforme. C'est simple à mettre en œuvre, et cela crée une base de données d'identités civiles reliée à vos usages, donc une cible de fuite majeure.
- **Preuve à divulgation minimale** (*double anonymat*, attestation d'âge délivrée par un tiers, portefeuille d'identité numérique européen) : un tiers vérifie votre âge et remet à la plateforme une attestation « cette personne a plus de 15 ans » sans transmettre votre identité, et sans que le tiers sache quel site vous consultez.

La seconde approche est celle recommandée notamment par la CNIL. Sa qualité réelle dépend de l'implémentation, en particulier de l'impossibilité de recoupement entre le vérificateur et la plateforme.

**Conséquence OPSEC.** Quel que soit le mécanisme, l'ouverture d'un compte anonyme sur une grande plateforme devient plus difficile. Pour les usages qui exigent réellement l'anonymat, cela renforce l'intérêt des services décentralisés ou qui ne demandent aucun identifiant, et des [messageries sans identifiant](#13-messageries-chiffrées).

### 6.3 France, chiffrement et enquête

Une disposition du projet de loi contre le narcotrafic (l'« article 8 ter »), adoptée au Sénat début 2025, aurait imposé aux fournisseurs de messageries chiffrées de fournir aux services d'enquête l'accès au contenu déchiffré. Elle a été supprimée en commission des lois à l'Assemblée nationale en mars 2025, à une très large majorité, après une opposition unanime des acteurs techniques (Signal a indiqué qu'il quitterait le marché plutôt que d'implémenter un tel accès) et des autorités de sécurité.

Le sujet revient régulièrement. Ce qui reste applicable aujourd'hui en France :

- l'obligation de remettre une **convention secrète de déchiffrement** (article 434-15-2 du code pénal), c'est-à-dire un code de déverrouillage, sur réquisition dans certaines conditions ; la Cour de cassation a confirmé que le code de déverrouillage d'un téléphone peut entrer dans ce champ ;
- les techniques spéciales d'enquête, dont la captation de données à distance sur un appareil, qui contournent le chiffrement en s'attaquant à l'extrémité plutôt qu'au transport ;
- la conservation des données de connexion par les opérateurs, encadrée par la jurisprudence européenne et le Conseil d'État.

**Ce qu'il faut en retenir** : la protection technique du transport est solide et le restera probablement ; le point faible est l'appareil. C'est pourquoi les sections [20](#20-smartphones) et [24](#24-sécurité-physique-et-voyages) comptent autant que le choix d'une messagerie.

### 6.4 Suisse, un exemple de risque juridique sur la juridiction

La Suisse a longtemps été considérée comme une juridiction favorable pour héberger des services de confidentialité. Un projet de révision de l'ordonnance sur la surveillance de la correspondance par poste et télécommunication, présenté en janvier 2025, prévoyait d'étendre les obligations d'identification des utilisateurs et de conservation à des fournisseurs qui en étaient exemptés, avec remise de clés lorsque le fournisseur les détient.

Réaction concrète : Proton a gelé ses investissements en Suisse et déplacé une partie de son infrastructure vers l'Allemagne et la Norvège ; Threema et Tuta ont publiquement critiqué le projet. En février 2026, le Conseil fédéral a annoncé revoir sa copie et commandé une analyse d'impact.

**Leçon générale, plus importante que le cas suisse** : la juridiction d'un fournisseur est un critère instable. Un service qui **ne peut pas** lire vos données, par construction, vous protège mieux qu'un service situé dans un pays réputé favorable mais qui **pourrait** techniquement le faire.

### 6.5 RGPD, vos droits utilisables

Le règlement général sur la protection des données reste l'outil le plus concret à votre disposition. Les droits les plus utiles en pratique :

| Droit | Usage concret | Délai de réponse |
| --- | --- | --- |
| Accès (art. 15) | Savoir ce qu'un service détient sur vous, utile avant de décider quoi supprimer | 1 mois, extensible à 3 |
| Effacement (art. 17) | Faire supprimer un compte, une donnée, une fiche chez un courtier | 1 mois |
| Opposition (art. 21) | Refuser la prospection et certains profilages | Immédiat pour la prospection |
| Rectification (art. 16) | Corriger une information fausse | 1 mois |
| Portabilité (art. 20) | Récupérer ses données avant de quitter un service | 1 mois |

En cas de non-réponse ou de refus, plainte en ligne auprès de la [CNIL](https://www.cnil.fr/fr/plaintes). Modèles de courriers disponibles sur le site de la CNIL. Voir [section 30](#30-courtiers-en-données-et-effacement) pour la méthode.

---
# Partie III. Les fondations

Cette partie couvre ce qui élimine la plus grande part du risque réel pour la plupart des gens. Si vous ne devez lire que 40 pages de ce guide, lisez celles-ci.

## 7. Démarrage rapide

Objectif : atteindre en deux à trois heures un niveau de sécurité supérieur à celui de la grande majorité des utilisateurs. Aucune connaissance technique requise.

### Étape 1. Sécuriser l'email principal en premier

Votre adresse email principale est la clé de tout le reste : elle permet de réinitialiser presque tous vos autres comptes. Elle se traite avant la banque.

1. Changez son mot de passe pour un mot de passe long et unique (voir [section 8](#8-mots-de-passe-et-gestionnaires)).
2. Activez l'authentification à deux facteurs, de préférence par application ou clé de sécurité, pas par SMS (voir [section 9](#9-authentification-multifacteur-et-passkeys)).
3. Dans les paramètres de sécurité, vérifiez et supprimez : les **règles de transfert automatique** inconnues, les **appareils connectés**, les **applications tierces autorisées**, les **adresses de récupération** obsolètes.
4. Notez les codes de secours et rangez-les hors ligne.

Le point 3 est le plus souvent oublié : une règle de transfert créée par un attaquant survit à un changement de mot de passe.

### Étape 2. Installer un gestionnaire de mots de passe

Sans lui, rien d'autre ne tient. Voir [section 8](#8-mots-de-passe-et-gestionnaires).

### Étape 3. Traiter les comptes critiques

Par ordre : email principal, opérateur téléphonique, banques, comptes d'achat contenant des moyens de paiement, cloud et sauvegardes, comptes professionnels, réseaux sociaux.

Pour chacun : mot de passe unique, MFA, révision des sessions actives, suppression des accès tiers inutilisés.

### Étape 4. Mettre à jour et activer le chiffrement

- Systèmes et navigateurs à jour, mises à jour automatiques activées.
- Chiffrement du disque activé : BitLocker sur Windows Pro, FileVault sur macOS, LUKS sur Linux, chiffrement par défaut sur Android et iOS récents à condition d'avoir un code d'au moins 6 chiffres.
- Verrouillage automatique de l'écran.

### Étape 5. Vérifier son exposition existante

Testez vos adresses email sur [Have I Been Pwned](https://haveibeenpwned.com/) et changez en priorité les mots de passe des services listés, ainsi que tout compte où vous avez réutilisé le même mot de passe.

### Étape 6. Nettoyer

- Désinstallez les applications mobiles inutilisées, et pour celles qui restent, révisez les permissions (localisation, micro, contacts, photos).
- Supprimez les extensions de navigateur inutilisées, en particulier celles installées il y a longtemps : le rachat d'une extension populaire par un tiers malveillant est une technique courante.
- Fermez les comptes en ligne que vous n'utilisez plus.

### Ce que cela ne couvre pas

Ce démarrage rapide traite les menaces automatisées et opportunistes. Il ne traite ni le pistage publicitaire fin, ni l'anonymat, ni un adversaire qui a un accès physique à vos appareils. Continuez avec les parties suivantes selon votre modèle de menace.

---

## 8. Mots de passe et gestionnaires

🟢 **Base. Priorité absolue.**

### Pourquoi

La réutilisation de mots de passe est la cause la plus fréquente de compromission de comptes personnels. Le mécanisme est simple : un site sans importance se fait pirater, votre couple email et mot de passe se retrouve dans une liste, et des robots l'essaient automatiquement sur des centaines de services (technique dite du **credential stuffing**). Si vous avez réutilisé ce mot de passe, tous les comptes concernés tombent en même temps, sans qu'aucun « piratage » vous visant n'ait eu lieu.

### Les trois règles

1. **Un mot de passe différent par service.** C'est la règle qui compte le plus, avant la complexité.
2. **Long plutôt que compliqué.** La longueur apporte bien plus de résistance que les caractères spéciaux. Une phrase de passe de quatre à six mots aléatoires (méthode *diceware*) est à la fois solide et mémorisable. `girafe-torchon-nuage-tramway-42` vaut mieux que `P@ssw0rd!`.
3. **Vous n'avez à mémoriser que deux ou trois mots de passe** : celui du gestionnaire, celui de la session de votre ordinateur, éventuellement celui de votre email principal. Le reste est généré aléatoirement et stocké.

À propos des règles anciennes : le changement périodique obligatoire sans raison est déconseillé par les référentiels actuels (NIST, ANSSI), parce qu'il pousse à des variantes prévisibles. On change un mot de passe quand il y a une raison : fuite, doute, partage.

### Comment choisir un gestionnaire

| Solution | Modèle | Open source | Synchronisation | Points forts | Limites |
| --- | --- | --- | --- | --- | --- |
| **Bitwarden** | Cloud, offre gratuite complète | Oui, audits réguliers | Automatique multiplateforme | Bon compromis pour débuter, partage familial, hébergement possible chez soi via Vaultwarden | Coffre chiffré stocké chez un tiers, dépend de votre mot de passe maître |
| **KeePassXC** | Fichier local | Oui | À vous de gérer (Syncthing, cloud chiffré) | Aucun tiers de confiance, contrôle total, gratuit | Synchronisation manuelle, risque de perte si pas de sauvegarde, moins pratique en mobilité |
| **Proton Pass** | Cloud | Oui | Automatique | Intégré à un écosystème avec alias email et 2FA | Dépendance à un fournisseur unique pour plusieurs services |
| **1Password** | Cloud, propriétaire | Non | Automatique | Ergonomie, clé secrète en plus du mot de passe maître, usage familial et entreprise | Code fermé, abonnement |
| **Gestionnaire du navigateur** | Intégré | Variable | Selon compte | Mieux que rien | Cible privilégiée des infostealers, extraction facile depuis un poste compromis |

**Recommandation par défaut** : Bitwarden pour la plupart des gens, KeePassXC si vous refusez tout stockage chez un tiers et savez gérer vos sauvegardes.

### Comment le mettre en place

1. Installez l'application de bureau, l'application mobile et l'extension de navigateur.
2. Créez un mot de passe maître en phrase de passe longue, que vous n'utilisez nulle part ailleurs. Écrivez-le sur papier le temps de le mémoriser, rangé en lieu sûr.
3. Notez la clé de récupération ou la clé secrète et stockez-la hors ligne, séparément.
4. Activez la MFA sur le compte du gestionnaire.
5. Importez les mots de passe enregistrés dans votre navigateur, puis **supprimez-les du navigateur** et désactivez l'enregistrement intégré.
6. Ne remplacez pas tout d'un coup. Traitez d'abord les comptes critiques, puis les autres au fil de vos connexions.
7. Utilisez la fonction de rapport intégrée : elle liste les mots de passe réutilisés, faibles ou apparus dans des fuites.

### Ce que cela ne protège pas

- **Un poste compromis.** Si un infostealer tourne sur votre machine pendant que le coffre est déverrouillé, il peut en extraire le contenu. Verrouillez le coffre automatiquement après quelques minutes.
- **Le phishing.** Un gestionnaire aide beaucoup, puisqu'il ne propose pas de remplir un formulaire sur un domaine qu'il ne reconnaît pas, mais rien n'empêche un utilisateur de copier son mot de passe à la main sur un faux site.
- **La perte du mot de passe maître.** Il n'existe pas de récupération miracle : c'est le prix du chiffrement de bout en bout.

### Pièges à éviter

- Stocker les codes de récupération à deux facteurs dans le même coffre que les mots de passe, sans aucune copie ailleurs : la perte du coffre coûte alors tous les accès.
- Utiliser un mot de passe maître dérivé d'une information publique (date de naissance, nom de l'animal, groupe de musique visible sur vos réseaux).
- Ne pas sauvegarder son fichier KeePass, ou le sauvegarder uniquement sur la machine qui contient déjà l'original.
- Répondre honnêtement aux **questions secrètes**. Le nom de jeune fille de votre mère est une donnée publique. Traitez ces réponses comme des mots de passe aléatoires stockés dans le coffre.

### Alternatives

- Un carnet papier rangé dans un tiroir fermé est acceptable dans un modèle de menace où l'adversaire est distant, jamais dans un modèle où quelqu'un a accès à votre domicile.
- Vaultwarden est une réimplémentation légère et libre du serveur Bitwarden, à héberger chez soi : le coffre ne sort plus de votre réseau, mais la disponibilité et la sauvegarde deviennent votre responsabilité.

*Vérifié : août 2026.*

---

## 9. Authentification multifacteur et passkeys

🟢 **Base.**

### Pourquoi

L'**authentification multifacteur** (MFA, ou 2FA pour deux facteurs) ajoute une preuve supplémentaire à votre mot de passe. Même si celui-ci fuite, le compte ne s'ouvre pas. C'est, avec l'unicité des mots de passe, la mesure la plus rentable qui existe.

### Les méthodes, de la moins bonne à la meilleure

| Méthode | Résiste au vol de mot de passe | Résiste au phishing | Résiste au SIM swap | Commentaire |
| --- | --- | --- | --- | --- |
| SMS | Oui | Non | **Non** | À éviter quand une autre option existe, mais toujours mieux que rien |
| Email de validation | Oui | Non | Sans objet | Dépend entièrement de la sécurité de la boîte mail |
| Application TOTP (codes à 6 chiffres) | Oui | Non | Oui | Bon standard, largement disponible |
| Notification push avec numéro à recopier | Oui | Partiellement | Oui | Réduit la fatigue de validation aveugle |
| **Passkey** (WebAuthn) | Oui | **Oui** | Oui | Lié au domaine, donc inutilisable sur un faux site |
| **Clé de sécurité matérielle** (FIDO2) | Oui | **Oui** | Oui | Meilleur niveau, la clé privée ne quitte jamais la clé |

Le point décisif est la colonne « résiste au phishing ». Un code TOTP peut être recopié en temps réel sur un faux site par un attaquant qui le rejoue immédiatement. Une passkey ou une clé FIDO2 ne le peut pas : le navigateur vérifie que le domaine correspond exactement à celui enregistré, et refuse sinon.

### TOTP, comment faire

**TOTP** signifie *time-based one-time password* : un code à 6 chiffres calculé à partir d'un secret partagé et de l'heure.

Applications recommandées : **Aegis** (Android, libre, coffre chiffré, exports sauvegardables), **Ente Auth** (multiplateforme, libre, synchronisation chiffrée de bout en bout), **2FAS** (multiplateforme, libre). Sur ordinateur, KeePassXC gère aussi les codes TOTP.

Deux principes :

1. **Sauvegardez les secrets TOTP.** Un téléphone perdu sans sauvegarde signifie perdre l'accès à tous les comptes concernés. Exportez le coffre chiffré et conservez-le hors ligne, ou utilisez une application à synchronisation chiffrée.
2. **Ne stockez pas les codes TOTP dans le même outil que vos mots de passe** si votre modèle de menace inclut le vol du coffre. Le faire est un compromis acceptable pour beaucoup de gens (deux facteurs restent meilleurs qu'un seul), mais ce n'est plus vraiment deux facteurs indépendants.

Évitez Google Authenticator dans sa version historique (pas de chiffrement de bout en bout de la synchronisation, pas d'export standard) et Authy pour son verrouillage d'export.

### Passkeys, ce que c'est vraiment

Une **passkey** est une paire de clés cryptographiques : la partie publique est déposée chez le service, la partie privée reste sur votre appareil ou dans votre gestionnaire. Vous vous authentifiez en déverrouillant l'appareil, sans mot de passe. Le mécanisme sous-jacent est WebAuthn et FIDO2.

Deux familles, souvent confondues :

- **Passkey synchronisée** : stockée dans un trousseau (Apple, Google, Bitwarden, Proton Pass) et disponible sur tous vos appareils. Pratique, avec pour conséquence que la sécurité du compte du trousseau devient critique.
- **Passkey liée à l'appareil** (*device-bound*), typiquement sur une clé matérielle : la clé privée ne sort jamais du composant. Plus sûr, moins commode, aucune récupération si l'objet est perdu.

Où en est-on en 2026 : l'adoption grand public a fortement progressé, plusieurs grands fournisseurs activent les passkeys par défaut, et la portabilité entre écosystèmes reste le point faible. Un protocole d'échange de justificatifs entre gestionnaires (*Credential Exchange Protocol*) est en cours de standardisation par la FIDO Alliance, mais tant qu'il n'est pas déployé partout, une passkey créée dans un écosystème ne se déplace pas facilement ailleurs.

**Conseil pratique** : créez vos passkeys dans un gestionnaire indépendant de la plateforme (Bitwarden, Proton Pass) plutôt que dans le trousseau du système, pour éviter de vous enfermer chez un fournisseur. Et **conservez toujours une méthode de secours** (clé matérielle secondaire ou codes de récupération).

### Clés de sécurité matérielles

Objets physiques au format USB ou NFC qui prouvent votre présence par un contact.

| Modèle | Points forts | Points d'attention |
| --- | --- | --- |
| **YubiKey 5** | Très large compatibilité, gère FIDO2, TOTP, PIV, OpenPGP | Micrologiciel non ouvert, non mettable à jour |
| **Nitrokey** | Matériel et micrologiciel ouverts, fabrication européenne | Compatibilité et ergonomie parfois en retrait |
| **Token2** | Bon rapport prix/fonctions, modèles programmables | Écosystème plus petit |
| **SoloKeys** | Ouvert | Projet à la maintenance irrégulière, à vérifier avant achat |

**Règle absolue : achetez-en deux.** Une clé principale, une clé de secours enregistrée sur les mêmes comptes et rangée ailleurs (coffre, domicile d'un proche de confiance). La perte d'une clé unique est le scénario d'échec le plus fréquent.

Usage recommandé, par ordre de priorité : email principal, gestionnaire de mots de passe, comptes professionnels, comptes cloud, réseaux sociaux à forte visibilité.

### Ce que cela ne protège pas

- **Le vol de session.** Une fois authentifié, votre session est matérialisée par un cookie. Un infostealer qui vole ce cookie n'a pas besoin de refaire la MFA. Se déconnecter des services sensibles et révoquer périodiquement les sessions actives limite la fenêtre.
- **Les procédures de récupération.** Un service qui permet de réinitialiser un accès avec une simple photo de pièce d'identité ramène la sécurité au niveau de son service client.
- **Les codes de secours mal rangés.** Ils contournent la MFA par conception.

### Pièges à éviter

- Utiliser le même numéro de téléphone comme second facteur et comme moyen de récupération pour tous les comptes.
- Activer la MFA puis perdre l'accès faute de sauvegarde des secrets ou des codes de secours. Testez la récupération **avant** d'en avoir besoin.
- Valider machinalement une notification push que vous n'avez pas déclenchée. Une demande inattendue signifie que quelqu'un possède votre mot de passe : refusez, puis changez-le immédiatement.

*Vérifié : août 2026.*

---

## 10. Sauvegardes et chiffrement des supports

🟢 **Base.**

### Pourquoi

La perte de données est plus fréquente que le piratage : panne, vol, incendie, rançongiciel, mauvaise manipulation. La sauvegarde est aussi la seule réponse réelle aux rançongiciels. Le chiffrement du support, lui, garantit qu'un appareil perdu ou volé ne livre pas son contenu.

### La règle 3-2-1

```
3 copies des données  (l'original + 2 sauvegardes)
2 supports différents (disque interne + disque externe, ou cloud)
1 copie hors du domicile (résistance à l'incendie, au dégât des eaux, au vol)
```

Variante utile en 2026 : **3-2-1-1-0**, avec une copie **hors ligne ou non réinscriptible** (une sauvegarde connectée en permanence est chiffrée en même temps que le reste par un rançongiciel) et **zéro erreur de restauration vérifiée**.

### Comment faire, sans se compliquer

**Niveau simple** : un disque externe chiffré, branché une fois par semaine, avec l'outil intégré du système (Historique des fichiers sur Windows, Time Machine sur macOS) plus une copie chiffrée dans un cloud.

**Niveau robuste** : [Restic](https://restic.net/) ou [Borg](https://www.borgbackup.org/), deux outils libres qui font des sauvegardes chiffrées, incrémentales et dédupliquées vers un disque local ou un stockage distant. Interface graphique disponible via Vorta pour Borg. Automatisez, puis vérifiez.

**Règle non négociable** : une sauvegarde jamais restaurée n'est pas une sauvegarde. Testez une restauration réelle au moins une fois par an, et notez la date.

### Chiffrement des supports

| Système | Outil | Remarque importante |
| --- | --- | --- |
| Windows | BitLocker (éditions Pro et Entreprise) | **Sauvegardez la clé de récupération ailleurs que dans votre compte Microsoft** si vous ne voulez pas qu'un tiers la détienne |
| macOS | FileVault | La clé peut être liée à l'identifiant Apple, ce qui a la même conséquence ; préférez la clé de récupération locale |
| Linux | LUKS, configuré à l'installation | Chiffrez tout le disque, pas seulement le dossier personnel |
| Android | Actif par défaut sur les versions récentes | La protection réelle dépend de la force du code de déverrouillage |
| iOS | Actif par défaut | Idem, et activer la protection avancée des données iCloud pour le chiffrement de bout en bout des sauvegardes |
| Disques externes, clés USB | VeraCrypt, ou l'outil natif du système | Voir [section 26](#26-chiffrement-des-données-et-coffres) |

### Ce que cela ne protège pas

Le chiffrement de disque protège un appareil **éteint**. Une fois la session ouverte, les données sont en clair pour tout logiciel qui tourne. Éteignez complètement votre machine si vous la laissez sans surveillance ou franchissez une frontière, plutôt que de la mettre en veille.

### Pièges à éviter

- Sauvegarder sur un disque toujours branché, ou sur un cloud synchronisé en temps réel : une corruption ou un chiffrement malveillant se propage à la sauvegarde. Gardez des versions et une copie déconnectée.
- Chiffrer une sauvegarde et perdre la phrase de passe. Rangez-la comme un objet de valeur, avec une seconde copie ailleurs.
- Oublier le téléphone dans le plan de sauvegarde : photos, messages, codes 2FA.

---

## 11. Adresses email et alias

🟢 **Base pour la partie alias, 🟡 pour la migration complète.**

### Pourquoi

Votre adresse email est l'identifiant qui relie tous vos comptes. Une seule adresse pour tout, c'est un point de défaillance unique et un identifiant de corrélation parfait pour les courtiers de données.

### Structure recommandée

| Rôle | Contenu | Diffusion |
| --- | --- | --- |
| **Adresse de récupération** | Sert uniquement à sécuriser les autres comptes | Jamais communiquée à personne |
| **Adresse critique** | Banque, impôts, santé, assurance, opérateur | Communiquée uniquement à ces organismes |
| **Adresse courante** | Amis, famille, correspondance | Diffusion normale |
| **Alias jetables** | Inscriptions, commerces, newsletters, essais | Un alias différent par service |

### Les alias, la mesure la plus rentable de cette section

Un **alias** est une adresse unique qui redirige vers votre vraie boîte. Avantages concrets :

- Vous savez **qui a fait fuiter votre adresse** : si `netflix.a7x9@monalias.fr` reçoit du spam, la fuite vient de là.
- Vous coupez un alias compromis sans changer d'adresse principale ni prévenir qui que ce soit.
- Vous cassez le principal identifiant utilisé par les courtiers pour recouper vos comptes entre eux.

| Service | Modèle | Points forts | Limites |
| --- | --- | --- | --- |
| **SimpleLogin** (Proton) | Freemium, open source, auto-hébergeable | Alias illimités en payant, domaine personnalisé, PGP | Appartient à Proton, concentration des services |
| **addy.io** | Freemium, open source | Généreux en gratuit, chiffrement des mails transférés | Interface moins grand public |
| **Proton Pass / Firefox Relay / iCloud Masquer mon email** | Intégrés à un écosystème | Très simple | Enfermement, options limitées |
| **Domaine personnel avec attrape-tout** | Vous possédez le domaine | Portabilité totale : vous changez d'hébergeur sans changer d'adresse | Le domaine est enregistré à votre nom (voir WHOIS), à éviter pour l'anonymat |

### Choisir un fournisseur de messagerie

| Fournisseur | Chiffrement | Juridiction | Points forts | Limites |
| --- | --- | --- | --- | --- |
| **Proton Mail** | De bout en bout entre utilisateurs Proton, au repos sinon | Suisse, infrastructure partiellement déplacée vers l'Allemagne et la Norvège | Écosystème complet, applications libres, audits | Les emails entrants venant de l'extérieur arrivent en clair avant chiffrement au repos |
| **Tuta** | Chiffrement de bout en bout, y compris sujets et calendrier, cryptographie post-quantique | Allemagne | Chiffre plus d'éléments que la plupart des concurrents | Pas de protocole standard IMAP, PGP non pris en charge |
| **Mailbox.org, Posteo** | Chiffrement au repos, PGP | Allemagne | Standards ouverts, prix bas, sobriété | Moins d'automatisation, pas de chiffrement de bout en bout par défaut |
| **Gmail, Outlook** | En transit et au repos, clés détenues par le fournisseur | États-Unis | Ergonomie, filtrage du spam très efficace | Analyse des contenus possible, modèle publicitaire, cible d'ordre judiciaire |

**Le point le plus important**, et il vaut pour tous les fournisseurs : l'email n'a pas été conçu pour être confidentiel. Même avec le meilleur fournisseur, si votre correspondant est chez un grand acteur, la copie de la conversation qui se trouve chez lui est lisible. Les **métadonnées** (expéditeur, destinataire, sujet dans la plupart des cas, horodatage, serveurs traversés) circulent en clair. Pour une conversation qui doit rester privée, utilisez une [messagerie chiffrée](#13-messageries-chiffrées), pas l'email.

### Comment migrer sans casse

1. Ouvrez la nouvelle adresse, ne fermez rien.
2. Mettez en place le transfert de l'ancienne vers la nouvelle.
3. Sur trois mois, changez l'adresse de contact dans vos comptes au fil des courriels reçus, en commençant par les comptes critiques.
4. Au bout de six à douze mois, ne conservez l'ancienne boîte qu'en réception, sans y répondre.
5. Ne supprimez jamais brutalement l'ancienne adresse : quelqu'un pourrait la réenregistrer et l'utiliser pour réinitialiser des comptes oubliés.

### Pièges à éviter

- Choisir un alias qui contient votre nom ou un pseudonyme réutilisé ailleurs.
- Utiliser un domaine personnalisé pour une identité qui doit rester anonyme : le WHOIS, l'historique DNS et les certificats TLS sont archivés publiquement.
- Charger les images distantes dans les courriels : c'est ce qui déclenche les pixels de suivi. Désactivez le chargement automatique.
- Cliquer sur « se désinscrire » dans un spam non sollicité : cela confirme que l'adresse est active. Marquez comme spam et coupez l'alias.

*Vérifié : août 2026.*

---

## 12. Numéro de téléphone et carte SIM

🟢 **Base.**

### Pourquoi

Le numéro de téléphone est devenu, en pratique, un identifiant national : il relie votre banque, vos réseaux sociaux, vos livraisons, votre état civil et souvent votre adresse. Il est aussi le maillon le plus faible, parce que sa sécurité dépend d'un service client humain.

### Trois risques distincts

1. **SIM swapping.** Un attaquant obtient le transfert de votre numéro vers sa propre SIM ou son profil eSIM, grâce à des informations personnelles issues de fuites. Il reçoit alors vos SMS de validation et peut réinitialiser vos comptes.
2. **Corrélation.** Donner votre numéro à un service lui permet de vous relier à tous les autres services qui le connaissent, et aux bases de courtiers.
3. **Localisation et interception.** L'opérateur connaît votre position ; le protocole SS7, encore utilisé pour l'interconnexion, présente des faiblesses documentées permettant, pour des acteurs disposant d'accès réseau, l'interception de SMS ou le suivi de position.

### Comment se protéger

**Chez l'opérateur** :

- Demandez l'ajout d'un **mot de passe ou code confidentiel sur le compte client**, exigé pour toute opération sensible.
- Demandez, quand c'est proposé, le **verrouillage de la portabilité** et l'alerte en cas de changement de SIM ou d'activation d'eSIM.
- Vérifiez que votre espace client est protégé par une MFA solide.

**Chez vos services** :

- Retirez le SMS comme méthode de récupération partout où une autre option existe. C'est la mesure qui neutralise l'essentiel de l'impact du SIM swap.
- Préférez les [passkeys ou clés matérielles](#9-authentification-multifacteur-et-passkeys).
- Ne mettez pas de numéro de téléphone dans les profils publics.

**Segmenter ses numéros** :

| Numéro | Usage | Comment l'obtenir |
| --- | --- | --- |
| Principal | Banque, administration, proches | Votre ligne habituelle |
| Secondaire | Inscriptions, commerces, livraisons, petites annonces | Seconde SIM prépayée, eSIM secondaire, ou double SIM sur un téléphone récent |
| Jetable | Vérification ponctuelle d'un service peu fiable | Services de numéros temporaires (fiabilité faible, ne jamais y rattacher un compte à conserver) |

En France, l'achat d'une carte SIM prépayée nécessite une identification : un numéro « anonyme » n'existe pas légalement. Une SIM secondaire réduit la corrélation, elle ne procure pas l'anonymat.

### Ce que cela ne protège pas

Ni le contenu de vos appels et SMS classiques (non chiffrés de bout en bout, accessibles à l'opérateur et sur réquisition), ni votre localisation vis-à-vis de l'opérateur.

### Pièges à éviter

- Utiliser le même numéro comme second facteur pour tous les comptes et comme moyen de récupération de l'email principal : c'est un point de défaillance unique parfait.
- Publier une capture d'écran contenant un numéro, y compris flouté partiellement.
- Synchroniser son carnet d'adresses avec une application sociale : vous exposez les numéros de tous vos contacts, pas seulement le vôtre.
- Croire qu'une eSIM est plus sûre par nature. Elle supprime l'accès physique, ce qui coupe certains vols mais facilite les transferts à distance.

---

# Partie IV. Communiquer

## 13. Messageries chiffrées

🟢 **Base pour Signal, 🟡 au-delà.**

### Pourquoi

Une messagerie **chiffrée de bout en bout** garantit que seuls vous et votre correspondant pouvez lire les messages : ni le fournisseur, ni l'opérateur, ni un intercepteur réseau. Sans cela, votre conversation est lisible par au moins une entreprise, et donc communicable sur réquisition ou exposée en cas de piratage.

Mais le chiffrement du contenu n'est que la moitié du problème. La vraie question de 2026 est : **quelles métadonnées le service conserve-t-il ?** Qui parle à qui, quand, à quelle fréquence, depuis quelle adresse IP.

### Comparatif

| Application | Identifiant requis | Chiffrement | Métadonnées | Décentralisation | Audits | Pour qui |
| --- | --- | --- | --- | --- | --- | --- |
| **Signal** | Numéro de téléphone (pseudo affichable) | Protocole Signal, résistance post-quantique déployée | Minimales, expéditeur scellé, réponses aux réquisitions publiées et quasi vides | Non, serveurs centralisés | Protocole et applications audités | Référence pour presque tout le monde |
| **SimpleX Chat** | **Aucun** | Double ratchet avec composante post-quantique | Conception sans identifiant d'utilisateur, files de messages séparées par contact | Oui, serveurs interchangeables et auto-hébergeables | Audits en 2022 et 2024 | Meilleur choix quand il faut éviter tout identifiant |
| **Briar** | Aucun | Chiffré, transport par Tor | Pas de serveur central, très peu de métadonnées | Pair à pair | Audité | Contextes de censure ou de coupure réseau, fonctionne en Bluetooth et Wi-Fi local |
| **Molly** | Comme Signal | Client Signal alternatif | Idem Signal | Non | Client indépendant | Utilisateurs Signal sur Android voulant chiffrer la base locale et passer par Tor |
| **Session** | Aucun | Chiffré, routage en oignon ; confidentialité persistante et échange post-quantique ajoutés fin 2025 | Faibles | Réseau adossé à une cryptomonnaie | Historiquement critiqué pour l'absence de confidentialité persistante | Option à réévaluer, longtemps déconseillée |
| **WhatsApp** | Numéro | Protocole Signal pour le contenu | **Importantes** : carnet d'adresses, graphe social, horaires, appartenance aux groupes | Non | Protocole solide, écosystème fermé | Acceptable pour le grand public faute de mieux, jamais pour un usage sensible |
| **Telegram** | Numéro | **Pas de chiffrement de bout en bout par défaut** ; uniquement dans les « discussions secrètes » individuelles | Serveur voit presque tout | Non | Cryptographie maison critiquée | À ne pas considérer comme une messagerie confidentielle |
| **Matrix / Element** | Compte sur un serveur | Chiffrement de bout en bout activable | Métadonnées visibles du serveur d'accueil, historique fédéré | Oui, fédéré | Audité | Communautés, entreprises, auto-hébergement |
| **Threema** | Aucun (identifiant aléatoire) | De bout en bout | Faibles | Non | Audité | Alternative payante sans numéro, juridiction suisse |
| **iMessage** | Identifiant Apple | De bout en bout entre appareils Apple | Métadonnées chez Apple, sauvegardes iCloud à surveiller | Non | Fermé | Entre appareils Apple uniquement, revient en SMS avec les autres |

### Recommandation pratique

- **Pour presque tout le monde** : Signal. Il concilie une sécurité de premier plan, une base d'utilisateurs suffisante pour être utile, et une politique de rétention minimale démontrée par ses réponses publiées à des réquisitions judiciaires. Le principal reproche, l'obligation d'un numéro de téléphone à l'inscription, est atténué par les noms d'utilisateur qui évitent de divulguer le numéro à vos contacts.
- **Quand aucun identifiant ne doit exister** : SimpleX Chat.
- **En contexte de censure ou de coupure réseau** : Briar.
- **Pour un groupe ou une organisation** : Matrix, ou Signal avec des groupes.

### Bien configurer Signal

1. Réglages, Confidentialité : activez le **verrou d'écran**, le blocage des captures d'écran (Android), les **messages éphémères par défaut**.
2. Définissez un **nom d'utilisateur** et passez le numéro de téléphone en non découvrable, pour ne plus le divulguer à vos contacts.
3. Activez le **verrou du registre** (*registration lock*) avec un code PIN : il empêche qu'un attaquant réenregistre votre numéro sur son appareil après un SIM swap. Mesure fortement recommandée.
4. Vérifiez le **numéro de sécurité** de vos contacts importants en personne ou par un autre canal : c'est ce qui garantit l'absence d'interception à la mise en relation.
5. Appels : activez « toujours relayer les appels » si vous ne voulez pas divulguer votre adresse IP à votre correspondant.
6. Sauvegardes : chiffrées, avec la phrase de récupération conservée hors ligne.

### Ce que cela ne protège pas

- **L'appareil.** Un téléphone compromis lit vos messages après déchiffrement. Aucune messagerie ne corrige cela.
- **Le destinataire.** Il peut faire une capture d'écran, transférer, laisser son téléphone ouvert ou sauvegarder la conversation ailleurs.
- **Le fait que vous communiquiez.** Le contenu est protégé, l'existence de l'échange l'est beaucoup moins selon les services.
- **Les sauvegardes cloud.** Sur WhatsApp, une sauvegarde non chiffrée annule le bénéfice du chiffrement pour l'ensemble de la conversation, y compris pour votre interlocuteur.

### Pièges à éviter

- Utiliser une messagerie chiffrée pour du contenu sensible, mais avec un compte relié à votre identité civile et un numéro connu de tous.
- Négliger les **groupes** : un groupe de 200 personnes n'est pas un canal confidentiel, quelle que soit la technologie.
- Ne pas vérifier les numéros de sécurité, puis considérer la conversation comme certaine.
- Oublier que les notifications affichent le contenu sur l'écran verrouillé.
- Croire que les messages éphémères empêchent la conservation. Ils réduisent la surface en cas de saisie ultérieure, ils n'empêchent ni la capture d'écran ni la photo de l'écran.

*Vérifié : août 2026.*

---

## 14. Email chiffré et PGP

🟡 **Intermédiaire, avec une recommandation nette : évitez PGP si vous pouvez utiliser autre chose.**

### Pourquoi PGP existe

**PGP** (*Pretty Good Privacy*, aujourd'hui surtout implémenté par le logiciel libre GnuPG) permet de chiffrer un message pour un destinataire et de signer un contenu pour prouver son origine. C'est la seule solution interopérable pour chiffrer un email entre deux fournisseurs différents.

### Les limites, à connaître avant de commencer

- **Aucune confidentialité persistante.** Si votre clé privée est compromise un jour, **tous** les messages passés chiffrés avec elle deviennent lisibles. Les messageries modernes renouvellent leurs clés en permanence et n'ont pas ce défaut.
- **Les métadonnées restent en clair** : expéditeur, destinataire, date et, dans la plupart des cas, le sujet.
- **La gestion des clés est difficile** et les erreurs sont silencieuses : envoyer à la mauvaise clé, utiliser une clé expirée, ne pas savoir révoquer.
- **L'écosystème est ancien** et les implémentations ont connu des failles notables (par exemple la famille EFAIL en 2018, liée au rendu HTML des messages).

**En résumé** : pour une conversation privée, une messagerie chiffrée moderne est supérieure sur tous les plans. PGP garde une utilité réelle dans trois cas : recevoir des messages d'inconnus sur une adresse publique (rédactions, chercheurs en sécurité), signer des publications ou des paquets logiciels, et chiffrer des fichiers pour archivage.

### Comment faire, si c'est nécessaire

1. Installez [GnuPG](https://gnupg.org/), avec [Kleopatra](https://www.openpgp.org/software/kleopatra/) sur Windows ou [GPG Suite](https://gpgtools.org/) sur macOS. Dans Thunderbird, OpenPGP est intégré nativement.
2. Générez une paire de clés : algorithme moderne (Ed25519 ou RSA 4096), date d'expiration fixée (deux ans, prolongeable), phrase de passe forte.
3. Générez immédiatement un **certificat de révocation** et rangez-le hors ligne : sans lui, vous ne pourrez pas annoncer qu'une clé est compromise.
4. Sauvegardez la clé privée hors ligne, chiffrée, en deux exemplaires.
5. Publiez la clé publique : sur [keys.openpgp.org](https://keys.openpgp.org/), sur votre site, dans votre signature.
6. Vérifiez l'empreinte d'une clé reçue par un canal différent avant de l'utiliser.

Alternative moderne pour chiffrer des fichiers : [age](https://github.com/FiloSottile/age), beaucoup plus simple et sans l'héritage de PGP, mais non interopérable avec l'écosystème email.

### Chiffrement propriétaire des fournisseurs

Proton Mail et Tuta chiffrent automatiquement entre leurs propres utilisateurs. C'est simple et efficace, avec deux réserves : cela ne fonctionne que dans le même écosystème, et un message venant de l'extérieur arrive en clair chez le fournisseur avant d'être chiffré au repos. Les fonctions de « message protégé par mot de passe » vers un destinataire externe sont une solution intermédiaire correcte, à condition de transmettre le mot de passe par un autre canal.

### Pièges à éviter

- Chiffrer le corps du message et mettre l'information sensible dans le sujet.
- Répondre en citant l'intégralité d'un message chiffré dans un message non chiffré.
- Utiliser PGP pour des échanges en temps réel : la lourdeur pousse à des raccourcis, et les raccourcis sont l'origine de la plupart des fuites.
- Publier une clé avec votre nom réel sur un serveur de clés pour une identité qui doit rester séparée : les serveurs de clés sont archivés et difficiles à purger.

---
# Partie V. Réseau et navigation

## 15. DNS

🟢 **Base.** Mesure simple, rapide, à effet immédiat sur la publicité et le pistage.

### Pourquoi

Le **DNS** (*Domain Name System*) traduit les noms de domaine en adresses IP. Chaque fois que vous ouvrez un site, votre appareil interroge un résolveur DNS. Par défaut, c'est celui de votre fournisseur d'accès, et vos requêtes circulent le plus souvent en clair.

Conséquences : votre fournisseur d'accès dispose de la liste complète des domaines que vous consultez, cette liste est conservée un temps, et n'importe qui sur le réseau local peut l'observer si le trafic n'est pas chiffré.

Changer de résolveur apporte trois bénéfices : chiffrer la requête, choisir à qui on la confie, et **filtrer** les domaines publicitaires ou malveillants au niveau du réseau, ce qui protège aussi les appareils sur lesquels on ne peut pas installer de bloqueur (téléviseur, console, objets connectés).

### Les protocoles

| Sigle | Nom | Fonctionnement |
| --- | --- | --- |
| **DoH** | DNS over HTTPS | Requêtes DNS dans du trafic HTTPS, difficile à distinguer du web |
| **DoT** | DNS over TLS | Requêtes DNS dans un tunnel TLS sur un port dédié, plus facile à bloquer |
| **DoQ** | DNS over QUIC | Variante sur QUIC, plus rapide |
| **DNSSEC** | Signatures DNS | Garantit l'**intégrité** de la réponse, mais **ne chiffre rien** |

DNSSEC et DoH répondent à deux problèmes différents : l'un empêche la falsification, l'autre l'observation.

### Résolveurs recommandés

| Résolveur | Filtrage | Journalisation annoncée | Notes |
| --- | --- | --- | --- |
| **Quad9** (`9.9.9.9`) | Blocage des domaines malveillants | Pas d'adresse IP conservée | Fondation suisse, bon choix par défaut orienté sécurité |
| **Mullvad DNS** | Plusieurs profils, dont publicité et traqueurs | Aucune journalisation annoncée | Gratuit et ouvert à tous, même sans abonnement VPN |
| **dns0.eu** | Profils, dont une variante pour enfants | Journalisation minimale | Infrastructure européenne, à but non lucratif |
| **NextDNS** | Filtrage très configurable, par appareil | Journalisation optionnelle et paramétrable, à désactiver si non souhaitée | Gratuit jusqu'à un quota, très pratique pour un foyer |
| **Cloudflare** (`1.1.1.1`) | Variante `1.1.1.2` filtrant les malwares | Journaux courts annoncés | Rapide, mais grande société américaine |
| **FDN, LDN** | Aucun | Associatif | Résolveurs associatifs français, pour ceux qui préfèrent un acteur non commercial |

### Comment le mettre en place

- **Sur le routeur** (idéal) : tous les appareils du foyer en bénéficient, y compris ceux qu'on ne maîtrise pas. Attention, beaucoup de box opérateur ne le permettent pas.
- **Sur le système** : Android propose « DNS privé » (DoT) dans les réglages réseau ; iOS et macOS acceptent un profil de configuration fourni par le résolveur ; Windows 11 et les distributions Linux récentes gèrent DoH nativement.
- **Dans le navigateur** : Firefox et les navigateurs dérivés de Chromium proposent DoH. Ne configurer que le navigateur laisse le reste du système sur le DNS par défaut.
- **Auto-hébergé** : [Pi-hole](https://pi-hole.net/) ou [AdGuard Home](https://adguard.com/adguard-home/overview.html) sur un petit ordinateur du réseau local, avec en amont un résolveur chiffré. Le filtrage reste chez vous, et vous voyez précisément ce que vos objets connectés contactent.

### Ce que cela ne protège pas

- **Le contenu de votre navigation.** Le DNS ne concerne que la résolution du nom. Le reste du trafic est indépendant.
- **Votre adresse IP**, toujours visible des sites visités.
- **Le fingerprinting**, les cookies, les traqueurs de première partie ni ceux servis depuis le domaine du site (CNAME cloaking).
- **La confidentialité vis-à-vis du nouveau résolveur.** Vous déplacez la confiance, vous ne la supprimez pas. Le SNI des connexions TLS révèle également le domaine visité à votre fournisseur d'accès, sauf déploiement d'ECH par le site.

### Pièges à éviter

- Configurer un DNS filtrant et un VPN, puis s'étonner que le filtrage ne s'applique plus : le VPN impose généralement son propre résolveur.
- Utiliser un résolveur gratuit inconnu. Un résolveur voit toute votre navigation par nom de domaine, c'est un poste d'observation privilégié.
- Casser des services locaux (imprimante, NAS, intranet d'entreprise) en filtrant trop agressivement, puis tout désactiver par lassitude.

---

## 16. VPN

🟡 **Intermédiaire.** L'outil le plus survendu du domaine.

### Ce qu'un VPN fait réellement

Un **VPN** (*virtual private network*) crée un tunnel chiffré entre votre appareil et un serveur du fournisseur. Les sites voient l'adresse IP de ce serveur, pas la vôtre ; votre fournisseur d'accès voit un flux chiffré vers ce serveur, sans son contenu.

C'est utile pour :

- **empêcher votre fournisseur d'accès ou l'administrateur d'un réseau** (employeur, hôtel, université) de voir quels sites vous consultez ;
- **masquer votre adresse IP** aux sites visités, ce qui gêne une partie du pistage et empêche un correspondant hostile de la relever ;
- **se protéger sur un réseau non maîtrisé** (l'argument du « Wi-Fi public » est largement dépassé depuis la généralisation de HTTPS, mais reste marginalement valable) ;
- **contourner une restriction géographique ou une censure locale**.

### Ce qu'un VPN ne fait pas

C'est la partie que le marketing omet.

- Il **ne rend pas anonyme**. Vous restez connecté à vos comptes, votre navigateur garde son empreinte, vos cookies vous suivent.
- Il **ne bloque ni les traqueurs ni les publicités** (sauf option de filtrage DNS incluse).
- Il **ne protège pas contre les malwares ni le phishing**.
- Il **déplace la confiance** : le fournisseur de VPN voit ce que voyait votre fournisseur d'accès. La question n'est pas « suis-je protégé », mais « à qui est-ce que je préfère faire confiance, et pourquoi ».
- Il **ne protège pas contre une analyse de trafic** poussée par corrélation des volumes et des horaires, pour un adversaire qui observe les deux extrémités.

### Quand un VPN est utile, quand il ne l'est pas

| Situation | Utile |
| --- | --- |
| Réseau d'entreprise, d'école ou d'hôtel que vous ne voulez pas informer de votre navigation | Oui |
| Cacher son adresse IP à un site ou à un correspondant | Oui |
| Contourner un blocage géographique | Oui |
| Se protéger d'un adversaire étatique déterminé | Non, insuffisant, voir [Tor](#17-tor) |
| Empêcher Google ou Meta de vous reconnaître alors que vous êtes connecté | Non, sans effet |
| Éviter les malwares | Non |

### Critères de choix

Par ordre d'importance réelle :

1. **Modèle économique clair.** Un VPN gratuit se rémunère par vos données, la publicité ou la revente de bande passante. Évitez.
2. **Audits indépendants récents et publics**, portant sur les applications, l'infrastructure et la politique de journalisation, pas seulement une attestation vague.
3. **Journalisation minimale, démontrée** par un audit, une architecture sans disque, ou l'historique de réponses à des réquisitions.
4. **Inscription et paiement peu identifiants** : compte sans email, paiement en espèces ou par cryptomonnaie si votre modèle de menace l'exige.
5. **Protocoles modernes** : WireGuard, avec échange de clés résistant au quantique lorsque disponible.
6. **Applications libres** et fonctions de sûreté correctes : coupe-circuit (*kill switch*), protection contre les fuites DNS et IPv6.
7. **Propriété et transparence** : de nombreuses marques appartiennent à quelques groupes, ce que le nom ne révèle pas.

### Fournisseurs de référence

| Fournisseur | Points forts | Points d'attention |
| --- | --- | --- |
| **Mullvad** | Compte anonyme par numéro généré, sans email, paiement en espèces accepté, tarif unique, très nombreux audits publics, WireGuard résistant au quantique par défaut, DAITA contre l'analyse de trafic, OpenVPN abandonné début 2026 au profit d'une implémentation WireGuard réécrite en Rust | Pas de redirection de port, moins de fonctions grand public, choix de pays plus restreint que certains concurrents |
| **IVPN** | Politique de confidentialité stricte, audits réguliers, options anti-traqueurs, discours honnête sur les limites du VPN | Petite structure, prix élevé |
| **Proton VPN** | Offre gratuite utilisable sans publicité, applications libres, intégration Tor et fonctions avancées | Écosystème unique concentrant plusieurs services, chiffrement post-quantique en retard sur certains concurrents |

Ces trois fournisseurs partagent une caractéristique décisive : ils communiquent aussi sur ce que leur produit **ne** fait **pas**.

### Auto-hébergement et réseaux privés

Monter son propre serveur VPN (WireGuard sur un serveur loué) n'apporte **pas** d'anonymat : le serveur est loué à votre nom, et vous êtes probablement le seul utilisateur de cette adresse IP, ce qui vous rend plus identifiable qu'avec une IP partagée. C'est en revanche excellent pour un autre usage : accéder à distance à son réseau domestique.

Pour cela, [Tailscale](https://tailscale.com/) (facile, mais un tiers gère la coordination) ou [Headscale](https://github.com/juanfont/headscale) (équivalent libre à héberger soi-même), tous deux fondés sur WireGuard, relient vos appareils entre eux sans les exposer sur Internet.

### Pièges à éviter

- Croire qu'un VPN suffit pour une activité qui exige l'anonymat. Il ne suffit pas.
- Payer un abonnement de trois ans à un fournisseur choisi via un lien affilié dans une vidéo sponsorisée.
- Laisser le VPN actif pour se connecter à des comptes nominatifs tout en pensant être « caché ».
- Oublier le coupe-circuit : à chaque coupure du tunnel, votre trafic repart en clair avec votre vraie adresse IP.
- Utiliser un VPN sur le réseau de son employeur en pensant que cela dissimule tout : sur un poste géré par l'entreprise, l'agent de sécurité installé voit ce qui se passe avant le tunnel.

*Vérifié : août 2026.*

---

## 17. Tor

🟡 **Intermédiaire pour un usage ponctuel, 🔴 avancé pour un usage sérieux.**

### Pourquoi

**Tor** (*The Onion Router*) fait transiter votre trafic par trois relais successifs tenus par des bénévoles, chacun ne connaissant qu'une partie du chemin :

```
Vous ──► Garde ──────► Relais ──────► Sortie ──► Site
        (voit votre   (ne voit ni    (voit le site,
         IP, pas la    l'un ni        pas votre IP)
         destination)  l'autre)
```

Aucun point unique ne connaît à la fois qui vous êtes et ce que vous consultez. C'est aujourd'hui le meilleur outil grand public pour dissocier une activité de son origine réseau.

Tor sert aussi à accéder aux **services onion** (adresses en `.onion`), qui restent entièrement dans le réseau, sans nœud de sortie : c'est ainsi que fonctionnent les plateformes de dépôt sécurisé de documents utilisées par les rédactions (SecureDrop), ou les miroirs de sites bloqués.

### Comment l'utiliser correctement

**Utilisez le Tor Browser**, pas un navigateur ordinaire configuré avec un proxy. Le navigateur fait bien plus que router le trafic : il uniformise l'empreinte de tous les utilisateurs, désactive ce qui trahit, cloisonne par site et efface l'état à la fermeture.

Règles de base :

1. **Ne modifiez rien** : ni taille de fenêtre, ni extensions, ni polices, ni thème. Chaque personnalisation vous distingue de la foule et détruit l'anonymat par uniformité.
2. **Ne vous connectez à aucun compte** rattaché à votre identité civile.
3. **Utilisez les niveaux de sécurité** intégrés. Le niveau « le plus sûr » désactive JavaScript, principale source de vulnérabilités et de fingerprinting.
4. **Ne téléchargez pas de documents pour les ouvrir hors ligne** : un PDF ou un fichier bureautique peut contacter Internet à l'ouverture hors du navigateur, et révéler votre adresse IP réelle. Ouvrez-les dans un environnement isolé ou sous Tails.
5. **N'utilisez pas BitTorrent** sur Tor : le protocole divulgue l'adresse IP réelle et sature le réseau.

Si Tor est bloqué par votre réseau ou votre pays, utilisez les **ponts** (*bridges*), notamment le transport enfichable Snowflake ou obfs4, configurables au premier lancement.

### Ce que Tor ne protège pas

- **Ce que vous racontez.** Se connecter à son compte Facebook via Tor identifie l'utilisateur, quel que soit le circuit.
- **Le nœud de sortie**, qui voit le trafic non chiffré. Utilisez toujours HTTPS, ou des services onion qui évitent complètement la sortie.
- **La corrélation de bout en bout.** Un adversaire capable d'observer simultanément votre entrée dans le réseau et la sortie peut relier les deux par les volumes et les horaires. C'est le point faible reconnu du modèle.
- **Le fait que vous utilisiez Tor.** Votre fournisseur d'accès le voit, sauf usage de ponts. Dans certains contextes, cela suffit à attirer l'attention.
- **Votre système.** Une faille du navigateur ou du système d'exploitation contourne tout. Voir [Tails et Whonix](#22-systèmes-spécialisés-pour-usages-sensibles).

### VPN et Tor, faut-il combiner

Question fréquente, réponse simple : **par défaut, non**.

| Montage | Ce que cela change | Verdict |
| --- | --- | --- |
| **Vous → VPN → Tor** | Votre fournisseur d'accès ne voit pas que vous utilisez Tor ; le fournisseur de VPN le voit | Utile uniquement si l'usage de Tor est dangereux localement. Vous devez alors faire une confiance totale au VPN |
| **Vous → Tor → VPN** | Le site voit l'IP du VPN au lieu d'un nœud de sortie | Déconseillé : le VPN devient un identifiant permanent qui traverse tous vos circuits |

Dans presque tous les cas, Tor Browser seul est le meilleur choix. Ajouter des couches sans comprendre le modèle dégrade souvent l'anonymat au lieu de l'améliorer.

### Pièges à éviter

- Ouvrir une session personnelle « juste une minute » dans le Tor Browser.
- Agrandir la fenêtre en plein écran : la taille de la zone d'affichage est un élément d'empreinte.
- Installer uBlock Origin ou une autre extension dans le Tor Browser, ce qui vous rend distinguable.
- Mélanger dans le même circuit une identité pseudonyme et une activité liée à votre vie réelle (par exemple consulter la météo de votre commune).
- Croire que Tor rend impunissable. Les affaires documentées en [section 38](#38-études-de-cas-déchecs-opsec) montrent que les échecs viennent presque toujours du comportement, pas du réseau.

---

## 18. Navigateurs et empreinte numérique

🟢 **Base pour la configuration, 🟡 pour le cloisonnement.**

### Pourquoi le navigateur est le point central

C'est par lui que passe l'essentiel de votre exposition quotidienne. Il divulgue en permanence des dizaines d'éléments techniques et exécute du code fourni par des tiers.

### Comprendre le fingerprinting

Le **fingerprinting** (empreinte de navigateur) consiste à identifier un visiteur par la combinaison de ses caractéristiques : rendu d'une image par la carte graphique (canvas, WebGL), liste des polices, résolution et taille de fenêtre, fuseau horaire, langues, version du système, traitement audio, périphériques déclarés. Chaque élément est banal ; leur combinaison est souvent unique.

C'est aujourd'hui la technique dominante, parce qu'elle **ne stocke rien chez vous** : effacer les cookies, changer d'adresse IP ou passer en navigation privée n'y change rien.

Deux stratégies opposées pour s'en défendre :

| Stratégie | Principe | Exemples | Limite |
| --- | --- | --- | --- |
| **Uniformisation** | Ressembler exactement à tous les autres utilisateurs du même navigateur | Tor Browser, Mullvad Browser | Impose de ne rien personnaliser |
| **Randomisation** | Renvoyer des valeurs légèrement différentes à chaque site et à chaque session | Brave | Un bruit mal maîtrisé peut lui-même devenir un signal |

Ce qui ne marche pas : empiler dix extensions « anti-fingerprint ». Chaque extension ajoute des caractéristiques détectables et vous rend **plus** unique.

### Choisir son navigateur

| Navigateur | Base | Points forts | Points d'attention |
| --- | --- | --- | --- |
| **Mullvad Browser** | Firefox, développé avec le Tor Project | Anti-fingerprinting de Tor Browser sans le réseau Tor, uniformisation, aucune télémétrie, pensé pour être associé à un VPN | Pas de synchronisation, usage volontairement dépouillé |
| **Tor Browser** | Firefox | Meilleur anonymat disponible pour le grand public | Lenteur, sites qui bloquent Tor, inadapté au quotidien |
| **Firefox** durci | Moteur Gecko indépendant | Isolation totale des cookies par site, conteneurs, extensions puissantes, moteur alternatif à Chromium | Nécessite un réglage manuel, choix par défaut discutables |
| **LibreWolf** | Firefox | Firefox préconfiguré sans télémétrie, avec `resistFingerprinting` | Mises à jour parfois décalées, quelques sites cassés |
| **Brave** | Chromium | Blocage intégré efficace, randomisation d'empreinte, bon compromis pour un usage quotidien | Éditeur au modèle économique publicitaire propre, à désactiver ; base Chromium |
| **Chrome** | Chromium | Compatibilité | Vie privée faible par conception, restrictions imposées aux bloqueurs de contenu |
| **Safari** | WebKit | Protections intégrées correctes sur Apple | Écosystème fermé, peu configurable |

**Recommandation pragmatique** : deux navigateurs, l'un pour les comptes connectés (banque, travail, achats), l'autre pour la navigation générale. Cette seule mesure casse une grande partie de la corrélation, gratuitement.

### Extensions, le minimum efficace

- **uBlock Origin** : bloqueur de référence, léger et puissant. C'est le seul indispensable. Sur les navigateurs Chromium récents, ses capacités sont réduites par les nouvelles règles d'extensions ; c'est un argument fort en faveur de Firefox.
- Éventuellement un gestionnaire de mots de passe.
- Rien d'autre par défaut. Chaque extension supplémentaire élargit la surface d'attaque (rachats malveillants, mises à jour vérolées) et l'empreinte.

À éviter : les extensions « VPN gratuit », les nettoyeurs, les collections d'anti-traqueurs redondants.

### Réglages utiles dans Firefox

1. Paramètres, Vie privée : protection renforcée en mode **strict**.
2. Cookies effacés à la fermeture, sauf exceptions déclarées pour les sites où vous restez connecté.
3. Désactiver la télémétrie et les recommandations.
4. Activer **DNS over HTTPS** avec le résolveur de votre choix.
5. Installer **Firefox Multi-Account Containers** pour isoler dans des conteneurs distincts les activités qui ne doivent pas se croiser (un conteneur pour les réseaux sociaux, un pour les achats, un pour le travail).
6. Pour aller plus loin, le projet [arkenfox/user.js](https://github.com/arkenfox/user.js) documente un durcissement complet. À lire avant d'appliquer : certains réglages cassent des sites.

### Ce que cela ne protège pas

- Votre identité une fois connecté à un compte.
- Le suivi côté serveur et les traqueurs de première partie.
- Les données que vous envoyez volontairement dans un formulaire.
- Le suivi par adresse IP, qui relève du [VPN](#16-vpn) ou de [Tor](#17-tor).

### Pièges à éviter

- Se connecter à son compte Google dans le navigateur « privé ».
- Tester son empreinte sur un site dédié, obtenir « unique », et en conclure que rien ne sert. Le bon objectif n'est pas d'être introuvable, mais de réduire la corrélation entre vos activités.
- Multiplier les extensions de confidentialité, qui produisent l'effet inverse.
- Se fier au mode privé pour autre chose que ne pas laisser de traces locales.

*Vérifié : août 2026.*

---

## 19. Moteurs de recherche

🟢 **Base.** Changement peu coûteux, effet réel sur le profilage.

### Pourquoi

Vos requêtes constituent l'une des données les plus intimes qui soient : santé, finances, opinions, relations, projets. Reliées à un compte ou à une adresse IP, elles alimentent un profil publicitaire et sont conservées.

### Options

| Moteur | Index | Modèle | Remarques |
| --- | --- | --- | --- |
| **DuckDuckGo** | Bing, plus des sources propres | Publicité contextuelle, sans profilage annoncé | Bon compromis grand public, société américaine |
| **Startpage** | Google | Intermédiaire qui interroge Google à votre place | Résultats Google sans lien direct, propriété partiellement détenue par un acteur publicitaire, à savoir |
| **Brave Search** | Index propre | Indépendant | Rare index alternatif réellement autonome |
| **Mojeek** | Index propre | Indépendant, britannique | Index plus petit, utile pour la diversité |
| **Qwant** | Index propre partiel et Bing | Français, hébergement européen | Qualité variable selon les requêtes |
| **SearXNG** | Métamoteur agrégeant plusieurs sources | Auto-hébergeable | Excellent si vous hébergez votre instance ; sur une instance publique, vous faites confiance à son administrateur |

**Recommandation** : DuckDuckGo ou Brave Search par défaut, une instance SearXNG personnelle si vous savez héberger.

### Ce que cela ne protège pas

Le moteur voit toujours votre adresse IP et votre empreinte de navigateur. Si vous cherchez une adresse depuis votre ligne domestique, la protection est faible. Pour une recherche réellement sensible, combinez avec [Tor](#17-tor).

### Pièges à éviter

- Utiliser un moteur respectueux de la vie privée tout en étant connecté à un compte du même groupe.
- Taper dans la barre d'adresse d'un navigateur qui envoie les frappes au moteur par défaut pour l'autocomplétion.
- Oublier que les cartes en ligne, les magasins d'applications et les plateformes vidéo sont aussi des moteurs de recherche, avec le même effet de profilage.

---
# Partie VI. Appareils

Un principe domine cette partie : **la sécurité de l'appareil prime sur le choix des applications**. Un téléphone compromis annule Signal, Tor, votre VPN et votre gestionnaire de mots de passe simultanément.

## 20. Smartphones

🟢 **Base pour la configuration, 🔴 avancé pour GrapheneOS.**

### Pourquoi c'est le maillon décisif

Votre téléphone contient vos messages, vos photos, vos codes d'authentification, vos moyens de paiement, et il connaît votre position en permanence. Il est aussi allumé 24 heures sur 24, transporté partout et rempli d'applications tierces.

### Le socle, quel que soit l'appareil

1. **Code de déverrouillage d'au moins six chiffres**, idéalement une phrase de passe. La biométrie est un confort, pas un facteur de sécurité : elle est plus facile à contraindre physiquement et, dans plusieurs juridictions, juridiquement plus faible qu'un code mémorisé.
2. **Mises à jour automatiques activées**, système et applications.
3. **Chiffrement actif** (par défaut sur les versions récentes d'Android et d'iOS, à condition d'avoir un code).
4. **Permissions révisées** : localisation en « seulement pendant l'utilisation » ou jamais, micro, caméra, contacts, photos. Sur Android comme sur iOS, accordez l'accès à une sélection de photos plutôt qu'à toute la photothèque.
5. **Identifiant publicitaire désactivé ou réinitialisé** régulièrement.
6. **Notifications masquées sur l'écran verrouillé** pour les applications sensibles.
7. **Désinstaller ce qui ne sert pas.** Chaque application est un canal de collecte et une surface d'attaque.
8. **Sauvegardes chiffrées** : sur iOS, activer la protection avancée des données iCloud, qui met les sauvegardes en chiffrement de bout en bout ; sur Android, vérifier le chiffrement de la sauvegarde.

### iOS

Avantages : mises à jour longues et uniformes, bac à sable applicatif solide, contrôle strict du magasin d'applications, **mode Isolement** (*Lockdown Mode*) qui réduit fortement la surface d'attaque pour les personnes visées par des logiciels espions commerciaux.

Limites : écosystème fermé, forte incitation à utiliser iCloud, impossible de retirer les services du constructeur, transparence limitée.

Réglages à faire : protection avancée des données iCloud, désactiver « Partager ma position » et l'historique des lieux significatifs, limiter le suivi publicitaire, mode Isolement si votre profil le justifie, vérifier les partages de localisation actifs (fréquemment oubliés après une séparation).

### Android standard

Avantages : ouverture, choix des applications, contrôle plus fin.

Limites : la durée de support varie énormément selon le constructeur, et les surcouches ajoutent leur propre collecte. Vérifiez la politique de mises à jour **avant** d'acheter : un téléphone qui ne reçoit plus de correctifs est un risque permanent.

Réglages à faire : désactiver la personnalisation publicitaire, révoquer les permissions en arrière-plan, activer « DNS privé », désactiver l'historique des positions et des activités du compte Google, utiliser un magasin alternatif comme [F-Droid](https://f-droid.org/) ou [Obtainium](https://github.com/ImranR98/Obtainium) pour les applications libres.

### GrapheneOS

🔴 **Avancé, mais accessible.** [GrapheneOS](https://grapheneos.org/) est un système Android durci, libre, sans services Google installés par défaut.

Ce qu'il apporte concrètement :

- durcissement mémoire et système bien au-delà d'Android standard, réduction documentée de l'efficacité des outils d'extraction forensique du commerce ;
- **services Google Play optionnels, exécutés dans le bac à sable applicatif ordinaire**, sans privilèges système : vous gardez la compatibilité applicative sans donner les clés du système à Google ;
- **profils utilisateurs multiples** réellement isolés, outil de compartimentation le plus pratique qui existe sur téléphone ;
- permissions supplémentaires, dont la coupure de l'accès réseau et des capteurs par application ;
- redémarrage automatique après une période d'inactivité, qui remet l'appareil dans son état le plus protégé (données chiffrées, non déverrouillées).

Contraintes :

- **matériel limité aux Google Pixel**, pour des raisons de sécurité matérielle (démarrage vérifié avec clés utilisateur, composant sécurisé) ;
- l'installation demande une heure et un ordinateur, mais se fait via un [installeur web](https://grapheneos.org/install/web) plutôt accessible ;
- quelques applications refusent de fonctionner (certaines applications bancaires ou de billetterie contrôlant l'intégrité de l'appareil), à vérifier avant migration ;
- contexte 2026 : Google ne publie plus les sources Android qu'à un rythme semestriel, ce qui complique le travail des systèmes dérivés ; GrapheneOS a néanmoins livré son portage d'Android 17 le jour même de sa publication en juin 2026, et prend en charge les Pixel jusqu'aux modèles récents.

**Pour qui** : journalistes, militants, personnes visées, et toute personne prête à un peu de complexité pour un gain de sécurité important. Pour un usage familial ordinaire, un iPhone à jour est un excellent choix, plus simple.

### Logiciels espions et stalkerware

Deux catégories distinctes :

- **Le stalkerware**, applications de surveillance grand public installées par un proche ayant eu un accès physique. Signes : batterie qui chute, appareil chaud au repos, application inconnue avec des droits d'accessibilité ou d'administrateur, profil de configuration inconnu sur iOS. Réflexe : vérifier les droits d'administrateur et d'accessibilité, les profils installés, les comptes ajoutés au téléphone. En cas de suspicion dans un contexte de violences, sauvegarder les preuves **avant** de supprimer, et se faire accompagner (voir [section 35](#35-réagir-à-un-incident)).
- **Les logiciels espions commerciaux** de niveau étatique, qui exploitent des failles sans interaction. Contre eux : système à jour, mode Isolement sur iOS ou GrapheneOS, redémarrage régulier (certaines infections ne survivent pas au redémarrage), réduction du nombre de canaux entrants, et pour les profils très exposés, un examen par une structure spécialisée telle qu'[Access Now Digital Security Helpline](https://www.accessnow.org/help/) ou le Security Lab d'Amnesty International.

### Pièges à éviter

- Installer un fichier APK trouvé sur un site quelconque.
- Accorder les droits d'accessibilité à une application qui ne relève pas de l'accessibilité : c'est le sésame pour lire l'écran et simuler des touches.
- Croire qu'un téléphone « rooté » ou jailbreaké est plus sûr. C'est presque toujours l'inverse : le démarrage vérifié saute et le modèle de sécurité s'effondre.
- Utiliser un téléphone qui ne reçoit plus de mises à jour de sécurité pour des usages sensibles.

*Vérifié : août 2026.*

---

## 21. Ordinateurs et systèmes d'exploitation

🟢 **Base.**

### Le socle commun

1. **Système à jour**, redémarrages faits.
2. **Chiffrement du disque** activé, avec clé de récupération conservée hors ligne (voir [section 10](#10-sauvegardes-et-chiffrement-des-supports)).
3. **Compte utilisateur sans droits d'administrateur** pour l'usage quotidien, élévation ponctuelle uniquement.
4. **Pare-feu activé.**
5. **Verrouillage automatique** et mot de passe à la sortie de veille.
6. **Sauvegardes** testées.
7. **Installer des logiciels depuis les sources officielles** uniquement. Le téléchargement d'installateurs via un moteur de recherche, avec des liens sponsorisés menant à des copies vérolées, est un vecteur majeur d'infostealer.

### Windows

Le plus exposé, parce que le plus répandu, et le plus bavard par défaut.

- Édition Pro recommandée pour BitLocker (l'édition Famille propose un chiffrement plus limité et lié au compte Microsoft).
- Créer un **compte local** plutôt qu'un compte Microsoft si vous ne voulez pas synchroniser vos données et votre clé de chiffrement.
- Désactiver dans Confidentialité : identifiant publicitaire, suivi de l'historique d'activité, données de diagnostic facultatives, contenus suggérés.
- Désactiver ou paramétrer strictement les fonctions qui capturent l'activité de l'écran, présentes sur les machines récentes.
- Microsoft Defender à jour suffit dans la plupart des cas ; les suites tierces ajoutent surtout de la surface d'attaque et de la collecte.
- Attention aux dossiers synchronisés automatiquement vers le cloud à votre insu.

### macOS

Bon niveau par défaut, avec un écosystème fermé.

- Activer FileVault avec clé de récupération locale, sans dépôt chez le fournisseur.
- Réviser Réglages, Confidentialité et sécurité : services de localisation, analyses, publicité personnalisée.
- Limiter iCloud aux données que vous acceptez de confier, et activer la protection avancée des données.
- Gatekeeper actif, installations hors magasin uniquement depuis des sources vérifiées.

### Linux

Le meilleur contrôle, un effort d'apprentissage réel.

- Distributions grand public solides : **Fedora Workstation**, **Debian stable**, **Linux Mint**, **Ubuntu LTS**.
- Chiffrement LUKS du disque entier à l'installation.
- Mises à jour automatiques configurées, y compris pour les paquets Flatpak.
- Vigilance sur les dépôts tiers, PPA et scripts d'installation trouvés en ligne : ils s'exécutent avec des privilèges élevés.
- Pour aller plus loin : [Fedora Silverblue](https://fedoraproject.org/silverblue/) ou une distribution immuable, sandbox Flatpak avec [Flatseal](https://github.com/tchx84/Flatseal) pour restreindre les permissions, [AppArmor](https://apparmor.net/) ou SELinux, [Firejail](https://firejail.wordpress.com/) pour isoler un logiciel donné.

Linux n'est pas magiquement sûr : sans configuration, un poste Linux peut être moins bien protégé qu'un macOS récent. Son intérêt principal est l'absence de collecte imposée et la possibilité de vérifier.

### Applications installées

C'est le point aveugle habituel. Chaque logiciel installé peut lire vos fichiers, observer votre réseau et se mettre à jour depuis un serveur distant. Faites l'inventaire une fois par an, désinstallez, et privilégiez les versions web isolées dans le navigateur pour les services dont vous vous méfiez.

### Pièges à éviter

- Utiliser quotidiennement un compte administrateur.
- Exécuter des logiciels piratés : c'est le premier vecteur d'infostealer chez les particuliers.
- Coller dans un terminal une commande copiée depuis un site sans la comprendre, y compris quand une page vous demande de « prouver que vous êtes humain ».
- Laisser un ordinateur en veille en croyant que le disque chiffré protège. Éteignez.

---

## 22. Systèmes spécialisés pour usages sensibles

🔴 **Avancé.** Ces systèmes répondent à des besoins précis. Ils ne sont pas « plus sûrs » dans l'absolu, ils sont conçus pour d'autres compromis.

| Système | Principe | Idéal pour | Ne convient pas à |
| --- | --- | --- | --- |
| **[Tails](https://tails.net/)** | Système live sur clé USB, amnésique, tout le trafic passe par Tor | Travail ponctuel sensible, contact avec une source, poste emprunté, ne rien laisser sur la machine | Un usage quotidien, ou un besoin de persistance riche |
| **[Whonix](https://www.whonix.org/)** | Deux machines virtuelles : une passerelle Tor et un poste de travail sans accès réseau direct | Isolation forte contre les fuites d'IP, y compris si une application est compromise | Machines peu puissantes, mobilité |
| **[Qubes OS](https://www.qubes-os.org/)** | Compartimentation par virtualisation : chaque activité vit dans son propre domaine isolé | Modèle de menace élevé, besoin de séparer durablement plusieurs identités sur une même machine | Débutants, ordinateurs récents mal pris en charge, autonomie sur batterie |

### Tails, l'essentiel

Vous démarrez l'ordinateur sur une clé USB. Le système fonctionne en mémoire vive et ne touche pas au disque de la machine. À l'extinction, la mémoire est effacée et il ne reste rien. Tout le trafic sortant passe par Tor. Un **stockage persistant chiffré** optionnel permet de conserver des documents et une configuration.

Points d'attention : Tails ne protège pas d'un micrologiciel compromis (BIOS/UEFI) ni d'un enregistreur de frappe matériel ; l'usage de Tails est visible sur le réseau local ; et si vous vous connectez à un compte personnel, l'anonymat est perdu comme avec n'importe quel autre outil.

### Qubes OS, l'essentiel

Chaque activité tourne dans une machine virtuelle distincte, avec un code couleur visible à l'écran. Un domaine « travail », un domaine « personnel », un domaine « bancaire », un domaine jetable pour ouvrir une pièce jointe douteuse. Une compromission reste enfermée dans son domaine. Qubes intègre officiellement des modèles Whonix pour router un domaine entier via Tor.

Contraintes réelles : matériel compatible obligatoire (vérifiez la liste de compatibilité avant d'acheter), 16 Go de mémoire minimum en pratique, courbe d'apprentissage de plusieurs semaines, ergonomie exigeante.

### Comment choisir

```
Besoin ponctuel, ne rien laisser sur la machine ........... Tails
Séparer durablement plusieurs identités sur un poste ...... Qubes OS
Empêcher toute fuite d'IP hors de Tor ..................... Whonix (ou Qubes + Whonix)
Sécurité quotidienne raisonnable .......................... Linux durci ou macOS à jour
```

### Piège principal

Adopter un de ces systèmes sans en avoir besoin. Ils imposent des contraintes fortes ; s'ils ne correspondent pas à votre modèle de menace, vous les abandonnerez dans le mois, souvent après avoir négligé les mesures de base qui, elles, comptaient vraiment.

---

## 23. Objets connectés et domicile

🟡 **Intermédiaire.**

### Pourquoi

Les objets connectés grand public sont souvent mal sécurisés, rarement mis à jour, et conçus pour envoyer des données au constructeur. Ils sont installés au cœur de l'espace le plus privé qui soit, et beaucoup contiennent micro, caméra ou capteurs de présence.

### Mesures utiles

1. **Se demander si l'objet a besoin d'Internet.** Une prise, un thermostat ou une ampoule fonctionnent souvent très bien en local.
2. **Réseau invité ou VLAN séparé** pour les objets connectés, afin qu'ils ne voient ni votre ordinateur, ni votre NAS, ni vos sauvegardes. La plupart des box récentes proposent un réseau invité en quelques clics.
3. **Changer les identifiants par défaut**, désactiver l'UPnP sur la box, ne jamais exposer une caméra directement sur Internet.
4. **Bloquer au niveau DNS** les domaines de télémétrie, en observant d'abord ce que l'objet contacte avec Pi-hole ou AdGuard Home.
5. **Caméras et assistants vocaux** : privilégier ceux qui stockent en local, ou une solution ouverte comme [Home Assistant](https://www.home-assistant.io/) qui fonctionne sans cloud. Une caméra intérieure filmant en permanence vers un service tiers est un compromis à décider consciemment.
6. **Vérifier la durée de support** avant achat. Un objet abandonné par son fabricant devient une porte ouverte permanente sur votre réseau.

### Cas particuliers

- **Téléviseurs connectés** : la reconnaissance automatique de contenu analyse ce qui est affiché à l'écran, y compris depuis une source externe. Le remède le plus simple est de ne pas connecter le téléviseur au réseau et d'utiliser un boîtier séparé.
- **Voitures connectées** : elles collectent trajets, contacts synchronisés depuis le téléphone et parfois habitudes de conduite revendues. Pensez à effacer vos données appairées avant revente ou restitution d'un véhicule de location.
- **Traceurs Bluetooth** : utiles, mais aussi utilisés pour du pistage de personnes. Android et iOS alertent désormais en cas de traceur inconnu qui vous suit ; ne désactivez pas ces notifications.

---

## 24. Sécurité physique et voyages

🟡 **Intermédiaire, 🔴 en contexte de franchissement de frontière sensible.**

### Le principe

Un accès physique à un appareil déverrouillé rend inutile presque tout le reste. La sécurité physique n'est pas un supplément, c'est une condition.

### Au quotidien

- Verrouillez l'écran systématiquement, même pour cinq minutes.
- **Éteignez** plutôt que mettre en veille en cas d'absence prolongée : hors tension, la clé de chiffrement n'est plus en mémoire.
- Protégez le démarrage : mot de passe UEFI, démarrage sécurisé, désactivation du démarrage sur périphérique externe.
- Filtre de confidentialité sur l'écran en espace public, et attention aux caméras et aux regards lors de la saisie d'un code.
- Ne branchez jamais une clé USB trouvée, ni un câble prêté. Pour recharger sur une borne publique, utilisez un adaptateur bloquant les données ou votre propre batterie.
- Rangez les documents papier sensibles ; détruisez-les au broyeur coupe croisée plutôt qu'à la poubelle.

### Voyages et frontières

Les règles diffèrent énormément selon les pays. Dans plusieurs juridictions, les agents peuvent inspecter un appareil à la frontière, et parfois exiger le déverrouillage.

Approche recommandée si le sujet vous concerne :

1. **Voyagez avec le minimum.** L'appareil idéal en frontière sensible est un appareil propre, avec peu de données, et non votre téléphone habituel.
2. **Sauvegardez avant le départ** et retirez ce qui n'est pas nécessaire au voyage ; récupérez les données à l'arrivée depuis une source distante chiffrée.
3. **Éteignez complètement** les appareils avant un passage de frontière : c'est l'état le plus résistant à l'extraction.
4. **Désactivez la biométrie**, utilisez un code. Dans plusieurs pays, forcer une empreinte est juridiquement plus simple que d'obtenir un code.
5. **Déconnectez-vous** des comptes sensibles et supprimez les sessions actives avant le passage.
6. Sachez à l'avance ce que vous ferez si l'on vous demande vos codes, y compris les conséquences d'un refus, qui varient selon les pays. Renseignez-vous auprès d'une organisation spécialisée si votre profil est exposé.

Note sur les volumes cachés et les systèmes à double mot de passe : ils sont fragiles en pratique, faciles à suspecter, et peuvent aggraver votre situation juridique dans certains pays. Ne les envisagez pas comme une solution simple.

### Vol ou perte

Préparez **avant** : localisation et effacement à distance activés, sauvegardes à jour, inventaire des comptes connectés sur l'appareil, numéros d'urgence de l'opérateur et de la banque notés ailleurs. Voir la marche à suivre en [section 35](#35-réagir-à-un-incident).

---

# Partie VII. Données

## 25. Fichiers et métadonnées

🟡 **Intermédiaire.** Cause classique de désanonymisation.

### Pourquoi

Un fichier contient bien plus que son contenu apparent :

| Type de fichier | Métadonnées fréquentes |
| --- | --- |
| Photo | Modèle et numéro de série de l'appareil, date et heure, **coordonnées GPS**, réglages, parfois miniature de l'image originale avant recadrage |
| Document bureautique | Auteur, organisation, historique des révisions, commentaires masqués, chemins de fichiers locaux |
| PDF | Logiciel producteur, auteur, dates, contenu masqué mais présent sous un cache noir mal appliqué |
| Audio et vidéo | Appareil, date, position, parfois identifiants d'encodage |
| Fichier scanné ou imprimé | Points de traçage jaunes ajoutés par certaines imprimantes couleur, identifiant le modèle et la date |

Des affaires réelles ont été résolues grâce aux coordonnées GPS d'une photo, au champ « auteur » d'un document, ou à un caviardage effectué avec un rectangle noir posé sur un texte resté sélectionnable.

### Comment nettoyer

- **[MAT2](https://0xacab.org/jvoisin/mat2)** : outil libre de référence, en ligne de commande ou intégré au gestionnaire de fichiers sur Linux (`mat2 photo.jpg`). Traite images, PDF, documents bureautiques, audio.
- **[ExifTool](https://exiftool.org/)** : le plus complet pour inspecter et modifier (`exiftool -all= fichier.jpg` supprime tout). Sert aussi à **vérifier** ce qui reste après nettoyage.
- **Windows** : clic droit, Propriétés, Détails, « Supprimer les propriétés et les informations personnelles ». Suffisant pour les cas simples.
- **Caviardage** : n'utilisez jamais un rectangle noir dans un logiciel de dessin ou un surligneur. Exportez la zone en image aplatie, ou utilisez un outil de rédaction qui supprime réellement le texte sous-jacent.
- **Capture d'écran** : la solution la plus fiable pour publier un extrait de document. Elle supprime tout le contenu structurel, à condition de vérifier ce qui apparaît autour (barre de tâches, notifications, onglets ouverts, nom d'utilisateur, fond d'écran).

### Réflexe avant toute publication

```
1. Le fichier est-il nettoyé de ses métadonnées
2. Que voit-on à l'arrière-plan de l'image (courrier, plaque, vue par la fenêtre, reflet)
3. Le nom du fichier révèle-t-il quelque chose
4. Le contenu permet-il une géolocalisation (enseigne, transport, végétation, ombres)
5. La plateforme de destination va-t-elle recompresser (souvent oui, ce qui supprime l'EXIF, mais ne comptez pas dessus)
```

### Pièges à éviter

- Envoyer une photo « brute » par un canal qui conserve l'EXIF (email, transfert de fichiers, certaines messageries en mode document).
- Publier une capture d'écran d'un document nettoyé, mais dont le chemin de fichier visible contient votre nom.
- Oublier les métadonnées des fichiers **reçus** : elles renseignent aussi sur votre correspondant, ce qui est un enjeu quand vous protégez une source.

---

## 26. Chiffrement des données et coffres

🟡 **Intermédiaire.**

### Trois besoins, trois outils

| Besoin | Outil | Remarques |
| --- | --- | --- |
| Chiffrer un disque entier ou une clé USB | **[VeraCrypt](https://www.veracrypt.fr/)** | Successeur de TrueCrypt, multiplateforme, volumes conteneurs ou disques complets |
| Chiffrer des fichiers avant de les envoyer dans un cloud | **[Cryptomator](https://cryptomator.org/)** | Crée un coffre qui se synchronise fichier par fichier, compatible avec tous les clouds, chiffre aussi les noms de fichiers |
| Chiffrer un fichier ponctuellement pour l'envoyer | **[age](https://github.com/FiloSottile/age)** ou 7-Zip en AES-256 | age est simple et moderne ; 7-Zip est universel, à condition de choisir le format 7z et de cocher le chiffrement des noms de fichiers |

Les outils intégrés (BitLocker, FileVault, LUKS) couvrent le disque système, voir [section 10](#10-sauvegardes-et-chiffrement-des-supports).

### Bonnes pratiques

- Phrase de passe longue et unique, générée par votre gestionnaire, et **sauvegardée séparément**. Un coffre dont on a perdu la clé est un fichier perdu.
- Vérifiez les signatures des logiciels téléchargés.
- Chiffrez **avant** d'envoyer dans un cloud, pas après.
- Pensez à la mémoire : un volume monté est déchiffré. Démontez-le après usage.

### Ce que cela ne protège pas

Un fichier déchiffré en cours d'utilisation, les copies temporaires créées par les logiciels, les aperçus générés par le système, et les traces dans les fichiers récents.

### Suppression réelle

Sur un disque SSD ou une mémoire flash (donc sur tous les appareils récents), l'effacement « sécurisé » par réécriture ne fonctionne pas de façon fiable, à cause de la répartition d'usure. La méthode correcte : **chiffrer dès le départ**, puis détruire la clé (réinitialisation d'usine sur un appareil chiffré, ou commande de suppression sécurisée du micrologiciel). Pour un disque contenant des données critiques en fin de vie, la destruction physique reste la seule certitude.

---

## 27. Cloud et auto-hébergement

🟡 **Intermédiaire.**

### La question à se poser

Pour tout service en ligne : **qui détient les clés de déchiffrement ?**

| Modèle | Qui peut lire | Exemples |
| --- | --- | --- |
| Chiffré en transit uniquement | Le fournisseur, ses sous-traitants, la justice sur réquisition | Beaucoup de services web |
| Chiffré au repos, clés chez le fournisseur | Idem, mais protection en cas de vol de disques | Google Drive, OneDrive, Dropbox par défaut |
| **Chiffré de bout en bout, clés chez vous** | Vous seul | Proton Drive, Tresorit, Filen, ou n'importe quel cloud + Cryptomator |

### Recommandations

- Pour des documents personnels ordinaires, un grand cloud avec **Cryptomator** par-dessus est une solution excellente et peu coûteuse : vous gardez la fiabilité et la synchronisation, sans confier le contenu.
- Pour un chiffrement de bout en bout intégré, Proton Drive ou une solution équivalente, en acceptant la dépendance à un fournisseur.
- Vérifiez toujours ce qui est **partagé par lien**. Un lien de partage « secret » est public pour quiconque l'obtient, et il survit à l'oubli. Faites le ménage périodiquement.
- Surveillez les **synchronisations automatiques** activées à votre insu (dossier Documents envoyé dans le cloud, photothèque, sauvegarde de messagerie).

### Auto-hébergement

Héberger soi-même (Nextcloud, Immich pour les photos, Vaultwarden, Home Assistant, un serveur de fichiers) donne le contrôle total et supprime le tiers. En contrepartie, **vous devenez responsable** des mises à jour, des sauvegardes, de la disponibilité et de la sécurité. Un Nextcloud non mis à jour, exposé sur Internet, est plus dangereux qu'un cloud commercial.

Recommandations si vous vous lancez :

- Commencez petit, sur un seul service, chez vous plutôt que sur un serveur exposé.
- N'exposez rien directement : passez par un réseau privé ([Tailscale ou Headscale](#16-vpn)) pour l'accès distant.
- Mises à jour automatiques et sauvegardes hors site chiffrées, testées.
- Journaux et supervision minimale, pour savoir si quelque chose ne va pas.

### Piège classique

Confondre « auto-hébergé » et « privé ». Un service auto-hébergé mais exposé publiquement, mal configuré, sans sauvegarde, offre une confidentialité inférieure à un service commercial sérieux. Le contrôle n'a de valeur que s'il s'accompagne de compétence et de régularité.

---
# Partie VIII. Identité et exposition

## 28. Compartimentation et identités

🟡 **Intermédiaire, 🔴 pour une séparation stricte.**

### Pourquoi

La compartimentation est ce qui transforme une collection d'outils en véritable OPSEC. Sans elle, une seule erreur relie tout. Avec elle, une compromission reste locale.

### Concevoir ses compartiments

Commencez par lister vos activités, puis regroupez-les par **niveau de sensibilité** et par **public**. Trois à quatre compartiments suffisent à la plupart des gens.

Exemple de matrice à remplir :

| Élément | Identité civile | Professionnel | Pseudonyme public | Pseudonyme sensible |
| --- | --- | --- | --- | --- |
| Adresse email | perso@... | pro@... | alias dédié | compte distinct, sans lien |
| Numéro de téléphone | Ligne principale | Ligne pro | Aucun | Aucun |
| Navigateur ou profil | Profil A | Profil B | Profil C | Tor Browser |
| Appareil | Téléphone principal | Ordinateur de travail | Idem principal | Appareil ou système dédié |
| Moyen de paiement | Carte bancaire | Carte pro | Carte virtuelle | Aucun paiement |
| Photo de profil | Photo réelle | Photo réelle | Image générée, jamais réutilisée | Aucune |
| Style d'écriture | Naturel | Formel | Neutre | Volontairement différent |

**Règle de fer** : dès que deux colonnes partagent un élément, considérez-les comme fusionnées. Il n'existe pas de « à moitié séparé ».

### Créer un pseudonyme qui tient

1. **Nom** : jamais dérivé d'un pseudo déjà utilisé, ni d'un ancien pseudo, ni d'une variation (`kirin92`, `kirin_92`, `kirin.92` sont le même identifiant pour un moteur de recherche). Vérifiez qu'il n'existe nulle part avant de l'adopter.
2. **Email** : créé depuis le compartiment concerné, jamais depuis votre navigateur habituel, jamais avec votre numéro en récupération.
3. **Photo** : aucune photo personnelle, aucune image trouvée en ligne (la recherche inversée la retrouve), éventuellement une image générée et utilisée une seule fois.
4. **Comportement** : horaires de publication, tournures de phrase, fautes récurrentes, emoji favoris, sujets de conversation. La stylométrie automatisée est efficace, en particulier depuis la généralisation des modèles de langage.
5. **Détails autobiographiques** : la fuite la plus fréquente. « Il pleut encore chez nous », « le TER avait du retard », une référence à un événement local, un match, une école. Quelques miettes suffisent à réduire le champ à une ville.
6. **Réseau** : ne suivez pas vos propres comptes, n'interagissez pas avec vos proches, ne rejoignez pas les mêmes communautés. Le graphe social identifie mieux que le contenu.

### Erreurs qui font tomber une compartimentation

- Se connecter au mauvais compte parce que le navigateur a proposé le remplissage automatique.
- Utiliser le même appareil sans isolation (même empreinte, même IP, même heure).
- Payer un service avec sa vraie carte pour l'identité pseudonyme.
- Réutiliser une image, un texte, une phrase de présentation.
- Publier une photo prise avec le même appareil (le numéro de série de l'appareil photo est dans l'EXIF).
- Céder à la fatigue : la compartimentation tombe presque toujours après des semaines, par lassitude, pas par erreur technique.

### Outils qui aident

- Profils de navigateur séparés, ou conteneurs Firefox.
- Machines virtuelles, ou [Qubes OS](#22-systèmes-spécialisés-pour-usages-sensibles) pour une séparation forte.
- Profils utilisateurs multiples sur [GrapheneOS](#20-smartphones).
- Appareil physiquement dédié, la solution la plus robuste quand le modèle de menace le justifie.
- Un document écrit qui dit, pour chaque compartiment, ce qui est autorisé et ce qui ne l'est pas. Cela paraît excessif jusqu'au jour où cela évite l'erreur.

---

## 29. Réseaux sociaux et exposition publique

🟢 **Base.**

### Ce que vous publiez sans le vouloir

- **Géolocalisation implicite** : arrière-plan, enseigne, plaque de rue, numéro de bus, vue depuis la fenêtre, ombre indiquant l'heure et l'orientation. Les communautés de géolocalisation retrouvent un lieu à partir d'une photo en quelques minutes.
- **Rythme de vie** : horaires de publication, absences, vacances annoncées en direct (utile aux cambrioleurs, publiez après le retour).
- **Entourage** : identifications, commentaires, listes d'amis publiques. Vous pouvez être discret et être exposé par les publications de vos proches.
- **Documents** : billets d'avion et de concert (les codes-barres contiennent nom et numéro de réservation), colis, ordonnances, chèques, badges d'accès.
- **Enfants** : photos, école, prénom, habitudes. Cette exposition ne leur laisse aucun choix et dure des années.
- **Contexte professionnel** : organigramme reconstituable via LinkedIn, très utilisé pour le phishing ciblé et la fraude au président.

### Configuration minimale

1. Passez en revue les paramètres de confidentialité de chaque plateforme, en repartant des valeurs par défaut, qui changent régulièrement après les mises à jour.
2. Désactivez l'indexation de votre profil par les moteurs de recherche là où c'est proposé.
3. Limitez la recherche par numéro de téléphone et par adresse email.
4. Désactivez la synchronisation du carnet d'adresses. Elle expose vos contacts.
5. Nettoyez l'historique : anciennes publications, anciennes photos, anciens commentaires. Des outils d'effacement de masse existent selon les plateformes.
6. Retirez les applications tierces connectées à vos comptes sociaux.
7. Désactivez la reconnaissance faciale et les suggestions d'identification.

### Réduire l'exposition sans disparaître

Vous n'êtes pas obligé de tout quitter. Une exposition maîtrisée consiste à décider **ce qui est public, pour qui, et pour combien de temps** :

- séparer un compte public professionnel d'un compte privé restreint ;
- publier en différé plutôt qu'en direct ;
- flouter ou recadrer systématiquement, en vérifiant que le floutage n'est pas réversible (le pixellisé peut parfois être inversé ; préférez un aplat opaque) ;
- ne jamais publier de document contenant un code-barres ou un QR code lisible ;
- se relire avec la question : « qu'est-ce que quelqu'un qui me veut du mal apprend de cette publication ».

---

## 30. Courtiers en données et effacement

🟡 **Intermédiaire.** Travail répétitif, effet durable.

### Le problème

Les **courtiers en données** constituent et revendent des profils sans que vous ayez jamais eu de relation avec eux. Ils s'alimentent aux sources publiques, aux fuites, aux applications mobiles et aux programmes de fidélité. En France s'y ajoutent des sources ouvertes légales : annuaires, registres d'entreprises, listes électorales, avis publiés, cadastre, base des décès.

### Méthode de nettoyage

1. **Faire l'inventaire.** Cherchez votre nom, vos anciens pseudonymes, vos adresses email et votre numéro de téléphone (entre guillemets) sur plusieurs moteurs, et notez ce qui remonte. Voir [section 31](#31-auto-audit-osint).
2. **Demander l'effacement.** En Europe, le RGPD vous donne un droit à l'effacement opposable à ces sociétés, y compris quand elles sont établies hors UE mais ciblent le marché européen. Un courriel type suffit :

```
Objet : Demande d'effacement de données personnelles (article 17 du RGPD)

Madame, Monsieur,

Conformément à l'article 17 du règlement (UE) 2016/679, je demande
l'effacement de l'ensemble des données personnelles me concernant que
vous détenez, ainsi que la cessation de toute communication de ces
données à des tiers (article 21).

Je vous demande également, au titre de l'article 15, de me préciser
l'origine des données vous concernant me concernant et la liste des
destinataires auxquels elles ont été transmises.

Données permettant de m'identifier dans vos fichiers : [nom, adresse
email concernée].

Vous disposez d'un délai d'un mois pour répondre. À défaut, je saisirai
la CNIL.

[Nom]
```

3. **Suivre.** Tenez un tableau : société, date de demande, date de réponse, résultat, date de la prochaine vérification. Les fiches réapparaissent, il faut recommencer une à deux fois par an.
4. **Déréférencer.** Si un contenu subsiste, demandez le déréférencement aux moteurs de recherche (formulaires « droit à l'oubli » de Google et Bing). Le contenu reste en ligne, il devient beaucoup moins trouvable.
5. **En cas de refus ou de silence** : plainte en ligne auprès de la [CNIL](https://www.cnil.fr/fr/plaintes).

### Sources françaises spécifiques à traiter

- **Pages Blanches et annuaires** : demande de mise en liste rouge auprès de l'opérateur, et retrait sur les sites d'annuaires inversés.
- **Registres d'entreprises** : si vous êtes dirigeant ou auto-entrepreneur, votre adresse peut être publique. Une adresse de domiciliation évite d'exposer votre domicile.
- **Listes électorales, annonces légales, avis de décès, généalogie** : sources publiques légitimes, difficiles à faire retirer, à connaître pour évaluer votre exposition.
- **Sites d'avis, forums anciens, archives** : demander au site, puis au moteur.

### Services payants de suppression

Ils automatisent les demandes. Utiles pour gagner du temps, avec deux réserves : ils sont surtout adaptés au marché américain, et vous devez leur confier vos données personnelles pour qu'ils travaillent. À évaluer selon votre modèle de menace.

### Ce que cela ne protège pas

L'effacement est un travail d'entretien, pas une opération unique. Il ne supprime pas les copies déjà vendues, ni les jeux de données fuités qui circulent hors de tout cadre légal.

---

## 31. Auto-audit OSINT

🟡 **Intermédiaire.** L'exercice le plus instructif du guide.

### Principe

L'**OSINT** (*open source intelligence*) est la collecte d'informations à partir de sources ouvertes. Faites-le sur vous-même : vous verrez exactement ce qu'un adversaire voit, et vous saurez quoi corriger en priorité.

### Méthode, environ deux heures

Travaillez dans un navigateur propre, déconnecté de vos comptes, et notez tout dans un fichier.

**1. Identité**

- Recherchez `"prénom nom"` entre guillemets, avec et sans votre ville, sur au moins deux moteurs.
- Ajoutez des variantes : nom de jeune fille, nom d'usage, orthographes fautives.

**2. Identifiants**

- Chaque adresse email : recherche directe, puis sur [Have I Been Pwned](https://haveibeenpwned.com/).
- Chaque pseudonyme, actuel et ancien, y compris ceux de l'adolescence. Des outils comme [WhatsMyName](https://whatsmyname.app/) recherchent un pseudonyme sur des centaines de plateformes.
- Votre numéro de téléphone, entre guillemets.

**3. Images**

- Recherche d'image inversée sur vos photos de profil (Google Images, Yandex, Bing, TinEye).
- Vérifiez si une photo utilisée sur un compte pseudonyme apparaît ailleurs.

**4. Réseaux sociaux**

- Consultez chacun de vos profils en mode déconnecté, dans une fenêtre privée : c'est la vue publique réelle, souvent différente de ce que vous croyez.
- Regardez les publications de vos proches dans lesquelles vous apparaissez.

**5. Sources professionnelles et légales**

- Registres d'entreprises, annuaires professionnels, publications, dépôts de code (les commits Git contiennent souvent l'adresse email réelle), présentations, comptes rendus d'associations.

**6. Techniques**

- Vos dépôts publics : clés, jetons d'API, adresses email dans l'historique des commits.
- Vos anciens sites et domaines : WHOIS historique, archives.
- Si vous hébergez un service, vérifiez ce qu'il expose (bannières, certificats, pages d'erreur bavardes).

**7. Archives**

- [Wayback Machine](https://web.archive.org/) sur vos anciens sites et profils. Ce que vous avez supprimé y est souvent encore.

### Que faire des résultats

Classez ce que vous trouvez en trois catégories : **à supprimer** (demande directe, puis RGPD), **à déréférencer** (le contenu reste mais devient difficile à trouver), **à accepter** (source légale non modifiable, dont vous tenez compte dans votre modèle de menace).

Refaites l'exercice une à deux fois par an, et systématiquement avant une prise de parole publique, un changement de poste ou une situation conflictuelle.

---

## 32. Confidentialité financière

🟡 **Intermédiaire.**

### Pourquoi

Les données de paiement racontent tout : lieux fréquentés, santé, convictions, habitudes, relations. Elles sont conservées longtemps, analysées et parfois revendues sous forme agrégée.

### Mesures légales et accessibles

- **Cartes virtuelles à usage unique ou plafonnées**, proposées par de nombreuses banques : limitent la fuite en cas de compromission d'un commerçant et empêchent les prélèvements abusifs.
- **Espèces** pour les achats du quotidien que vous ne souhaitez pas voir profilés. C'est le moyen le plus simple et le plus efficace, tant qu'il existe.
- **Cartes prépayées**, dans les limites légales d'identification.
- **Compte séparé** pour les achats en ligne, alimenté au besoin : limite l'exposition du compte principal.
- **Refuser les programmes de fidélité** ou les alimenter avec un alias email et un numéro secondaire.
- **Surveiller** : alertes sur les opérations, vérification mensuelle des relevés, contrôle des mandats de prélèvement.

### Cryptomonnaies, à comprendre correctement

Bitcoin n'est **pas anonyme**. Son registre est public et permanent, et l'analyse de chaîne est une industrie mature. Un achat sur une plateforme réglementée relie votre identité à vos adresses, définitivement. Les cryptomonnaies dites confidentielles offrent des propriétés différentes, avec en contrepartie un accès de plus en plus restreint et une attention réglementaire soutenue.

En pratique, pour un particulier européen, les cryptomonnaies apportent rarement un gain de confidentialité et introduisent un risque de perte, d'erreur et de fraude. Elles ne sont pertinentes que pour des cas d'usage précis et documentés.

### Fraude bancaire

Réflexes : ne jamais valider dans l'application bancaire une opération que vous n'avez pas initiée, ne jamais communiquer un code reçu par SMS, raccrocher et rappeler le numéro figurant au dos de la carte en cas d'appel d'un « conseiller ». En cas de débit frauduleux, la banque doit rembourser sauf négligence grave démontrée ; faites opposition, déposez plainte et contestez par écrit.

---

## 33. Intelligence artificielle

🟡 **Intermédiaire.**

### Ce que vous confiez à un assistant en ligne

Une conversation avec un assistant IA en ligne est un envoi de données à une entreprise. Selon le service et l'offre, ces données peuvent servir à l'entraînement, être consultées par des humains pour évaluer la qualité, être conservées longtemps, et être exigées par la justice. Un litige américain a conduit en 2025 à une obligation de conservation étendue des journaux de conversation d'un grand fournisseur, y compris de conversations supprimées, et des décisions ultérieures ont confirmé qu'aucun secret professionnel ne protège ces échanges.

Conclusion pratique : **un assistant IA n'est pas un confident, ni un avocat, ni un médecin**. Traitez chaque message comme une publication potentielle.

### Règles d'usage

1. **Ne collez jamais** : identifiants, clés d'API, données de santé, éléments d'un dossier juridique, informations concernant des tiers, code source confidentiel, documents d'entreprise sous accord de confidentialité.
2. **Anonymisez avant** : remplacez noms, dates, montants et lieux par des variables. Le raisonnement demandé reste le même.
3. **Désactivez** l'utilisation de vos conversations pour l'entraînement quand l'option existe, et vérifiez-la après chaque mise à jour de l'interface.
4. **Attention aux intégrations** : un assistant branché sur votre messagerie, votre disque ou votre calendrier lit tout ce à quoi il a accès. Accordez le minimum.
5. **En entreprise**, préférez une offre contractuelle avec engagement de non-entraînement, ou un déploiement interne.

### L'IA locale

Faire tourner un modèle sur votre propre machine résout la question à la racine : rien ne sort.

| Outil | Public | Remarques |
| --- | --- | --- |
| **[Ollama](https://ollama.com/)** | Simple, ligne de commande et API locale | Le plus répandu, très bonne prise en main ; vérifiez si votre version propose des fonctions en ligne et désactivez-les si vous voulez rester strictement local |
| **[LM Studio](https://lmstudio.ai/)** | Interface graphique | Pratique pour tester des modèles, application propriétaire |
| **[llama.cpp](https://github.com/ggml-org/llama.cpp)** | Technique | Le moteur sous-jacent de nombreux outils, sans dépendances, fonctionne sur du matériel modeste |
| **[Jan](https://jan.ai/)** | Interface graphique libre | Alternative ouverte à LM Studio |
| **[Open WebUI](https://github.com/open-webui/open-webui)** | Interface web à héberger | Se branche sur Ollama, pratique pour un usage familial ou en équipe |

Réalité matérielle : un modèle de 7 à 14 milliards de paramètres quantifié tourne correctement sur un ordinateur récent avec 16 Go de mémoire, et les résultats restent en deçà des grands modèles en ligne. Pour du résumé de document, de la reformulation et du traitement de texte sensible, c'est largement suffisant.

**Vérification utile** : coupez le réseau et confirmez que l'outil fonctionne toujours. C'est la seule preuve que rien ne part.

### L'IA comme menace

- **Clonage vocal** à partir de quelques secondes d'audio public, utilisé pour l'arnaque au proche en détresse et la fraude au dirigeant. Contre-mesure simple et efficace : convenir en famille d'un **mot de passe oral** à demander en cas d'appel inattendu réclamant de l'argent ou une action urgente.
- **Deepfakes vidéo**, y compris en visioconférence. Pour toute demande sensible, revalidez par un canal différent.
- **Phishing personnalisé** rédigé sans faute à partir de vos données publiques.
- **Corrélation** : recherche de visage, analyse stylométrique, géolocalisation d'image assistée. Ces capacités, autrefois réservées à des spécialistes, sont désormais accessibles à tous, ce qui doit vous rendre plus prudent sur ce que vous publiez.

---

# Partie IX. Réagir

## 34. Que faire en cas de fuite de données

🟢 **À lire avant d'en avoir besoin.**

Vous apprenez qu'une entreprise chez qui vous êtes client a été victime d'une compromission, ou vous recevez une notification. Voici la marche à suivre, dans l'ordre.

### Étape 1. Déterminer ce qui a fuité

C'est ce qui détermine tout le reste. Lisez la notification et cherchez la liste exacte des catégories de données.

| Donnée exposée | Risque principal | Action |
| --- | --- | --- |
| Adresse email | Phishing ciblé, spam | Vigilance accrue, alias si possible |
| Mot de passe | Prise de contrôle de ce compte et de tous ceux qui partagent ce mot de passe | Changement immédiat partout où il était réutilisé |
| Nom, adresse postale, date de naissance | Usurpation d'identité, crédibilité du phishing | Ces données ne se changent pas : adaptez votre vigilance durablement |
| Numéro de téléphone | SIM swap, smishing, vishing | Sécuriser le compte opérateur, retirer le SMS comme second facteur |
| IBAN | Prélèvements frauduleux | Surveiller les prélèvements, contester sous 13 mois, demander une liste blanche à la banque |
| Numéro de carte bancaire | Fraude | Opposition et refabrication |
| Numéro de sécurité sociale, pièce d'identité | Usurpation lourde, ouverture de comptes à votre nom | Signalement, vigilance longue durée, garder les preuves de la notification |
| Données de santé | Chantage, discrimination, phishing très ciblé | Vigilance élevée, signalement CNIL |
| Réponses aux questions secrètes | Contournement de la récupération de compte | Changer ces réponses partout |

### Étape 2. Sécuriser, dans le bon ordre

1. Changer le mot de passe du service concerné.
2. **Changer le mot de passe partout où il a été réutilisé.** C'est la vraie urgence.
3. Activer la MFA sur ce service et sur les comptes liés.
4. **Révoquer les sessions actives** et les appareils connectés sur les comptes importants : sans cela, un attaquant déjà connecté reste connecté malgré le changement de mot de passe.
5. Vérifier l'absence de **règles de transfert**, d'adresses de récupération ou d'applications tierces ajoutées sur votre messagerie.

### Étape 3. Anticiper l'attaque secondaire

C'est le point le plus souvent négligé, et le plus dangereux. Dans les semaines qui suivent, attendez-vous à :

- des courriels et SMS qui **citent vos vraies données** (numéro de commande, montant, nom du service) pour être crédibles ;
- des appels se présentant comme votre banque, votre opérateur, un service public, l'assurance maladie, ou le service client de l'entreprise victime ;
- des demandes de « sécurisation » ou de « remboursement » vous incitant à valider une opération.

Règle unique et suffisante : **ne jamais agir sur sollicitation entrante**. Raccrochez, n'utilisez aucun lien reçu, et reprenez contact par un canal que vous connaissez déjà.

### Étape 4. Surveiller

- Relevés bancaires, chaque mois, y compris les petits montants (les tests de carte volée commencent souvent par quelques euros).
- Comptes importants : alertes de connexion activées.
- Inscription aux alertes de [Have I Been Pwned](https://haveibeenpwned.com/NotifyMe) pour être prévenu des prochaines fuites.
- Si des documents d'identité ont fuité, surveillez les traces d'usurpation : courriers d'organismes inconnus, refus de crédit inexpliqué, changement d'adresse non demandé.

### Étape 5. Faire valoir ses droits

- Demander à l'entreprise le détail précis des données vous concernant (article 15 du RGPD).
- Signaler la fuite à la [CNIL](https://www.cnil.fr/fr/plaintes) si l'entreprise n'a pas notifié correctement.
- En cas de préjudice : plainte, et éventuellement action collective.
- Ressources publiques françaises : [cybermalveillance.gouv.fr](https://www.cybermalveillance.gouv.fr/) pour le diagnostic et l'assistance, [service-public.fr](https://www.service-public.fr/) pour les démarches d'usurpation d'identité.

### Pourquoi une fuite ancienne reste dangereuse

- Les données d'état civil ne changent pas. Une date de naissance divulguée en 2018 sert encore aujourd'hui.
- Les jeux de données sont **agrégés** : trois fuites partielles combinées produisent un profil complet.
- Les mots de passe divulgués alimentent les dictionnaires d'attaque, y compris dans leurs variantes prévisibles (`MonMotDePasse2019` devient `MonMotDePasse2026`).
- Un compte oublié, resté avec un ancien mot de passe, reste une porte d'entrée des années plus tard. Fermez les comptes inutilisés.

---

## 35. Réagir à un incident

Procédures courtes, à appliquer dans l'ordre.

### Compte compromis

1. Depuis un **appareil sain** (pas celui suspecté d'être infecté), changez le mot de passe.
2. Révoquez toutes les sessions et appareils connectés.
3. Vérifiez et supprimez : règles de transfert, adresses de récupération, numéros de téléphone, applications tierces, clés d'API, délégations d'accès.
4. Activez ou reconfigurez la MFA, régénérez les codes de secours.
5. Vérifiez les comptes qui utilisaient cette adresse comme moyen de récupération.
6. Prévenez vos contacts si le compte a pu servir à les démarcher.
7. Cherchez la cause : mot de passe réutilisé, phishing, infostealer sur la machine. Si l'infection est probable, traitez l'appareil avant de vous reconnecter, sinon vous perdrez à nouveau le compte immédiatement.

### Appareil probablement infecté

1. Déconnectez-le du réseau.
2. Depuis un autre appareil, changez les mots de passe des comptes critiques et révoquez les sessions.
3. Sauvegardez vos **documents** (pas les exécutables ni les fichiers de configuration).
4. **Réinstallez le système.** Le nettoyage antivirus d'une machine réellement compromise n'offre aucune garantie sérieuse.
5. Restaurez vos documents, réinstallez les logiciels depuis les sources officielles.
6. Faites tourner à nouveau vos comptes critiques, en supposant que tout ce qui se trouvait dans le navigateur a fuité.

### Appareil perdu ou volé

1. Localisation et verrouillage à distance, puis effacement si la récupération semble improbable.
2. Appelez l'opérateur pour bloquer la ligne et la carte SIM.
3. Changez les mots de passe des comptes dont la session était ouverte, révoquez les sessions.
4. Si l'appareil contenait des codes 2FA, reconfigurez-les avec vos sauvegardes.
5. Déposez plainte, notez l'IMEI (à conserver quelque part par avance).

### Harcèlement, doxing, menaces

1. **Documentez avant tout** : captures d'écran horodatées avec l'URL visible, sauvegarde des messages, éventuellement constat d'huissier pour les cas graves.
2. Ne répondez pas, ne négociez pas.
3. Signalez aux plateformes, puis demandez le retrait et le déréférencement.
4. Verrouillez vos comptes : profils en privé, filtres de messages, désactivation temporaire des mentions.
5. Prévenez votre entourage et, si nécessaire, votre employeur, avant qu'ils ne soient contactés.
6. Déposez plainte. En France : [cybermalveillance.gouv.fr](https://www.cybermalveillance.gouv.fr/), le **3018** pour les mineurs et les victimes de violences numériques, [Pharos](https://www.internet-signalement.gouv.fr/) pour les contenus illicites.

### Violences dans le cadre domestique

Situation particulière, où l'adversaire connaît vos mots de passe, a eu accès à vos appareils et figure sur vos comptes partagés.

- **Ne modifiez rien précipitamment** si cela peut alerter la personne et provoquer une escalade. Évaluez d'abord votre sécurité physique.
- Cherchez : partages de localisation, comptes familiaux, appareils enregistrés, applications de suivi, traceurs Bluetooth dans les affaires et le véhicule, comptes cloud partagés.
- Utilisez un appareil auquel la personne n'a pas eu accès pour préparer les démarches.
- Faites-vous accompagner : **3919** (violences faites aux femmes), associations spécialisées, et ressources dédiées à la sécurité numérique des victimes.

---

## 36. Phishing et ingénierie sociale

🟢 **Base.**

### Le principe à retenir

L'ingénierie sociale exploite le contexte et l'urgence, pas la technique. Les indices classiques (fautes, adresse bizarre) ont largement disparu. Un message de phishing en 2026 peut être parfaitement rédigé, citer vos vraies données, et provenir d'un domaine crédible.

### Les signaux qui restent fiables

1. **L'urgence.** « Votre compte sera suspendu sous 24 heures », « une commande de 890 euros vient d'être validée ». L'urgence artificielle est le marqueur le plus constant.
2. **La sollicitation entrante.** Vous n'avez rien demandé, et pourtant on vous contacte.
3. **Le canal détourné.** Une administration ou une banque qui vous demande de cliquer sur un lien, d'installer une application, ou de communiquer un code.
4. **La demande d'action inhabituelle** : virement de « mise en sécurité », lecture d'un code à voix haute, installation d'un outil de prise en main à distance, exécution d'une commande dans un terminal.

### Le réflexe unique

**N'utilisez jamais le canal entrant pour vérifier.** Raccrochez, n'ouvrez pas le lien reçu, et reprenez contact par un moyen que vous possédez déjà : l'application officielle installée par vos soins, le numéro au dos de votre carte bancaire, l'adresse du site tapée à la main.

### Techniques courantes en 2026

- **AiTM** (*adversary in the middle*) : la page de connexion est un relais transparent vers le vrai site, qui capture mot de passe, code MFA et session. Seules les passkeys et clés FIDO2 y résistent structurellement.
- **ClickFix** : une page affiche une fausse vérification et vous demande de coller une commande dans une fenêtre système. Cela installe un infostealer. Aucune vérification humaine légitime ne demande cela.
- **Quishing** : QR code menant à un faux site, y compris collé sur un vrai support (parcmètre, borne, affiche).
- **Fraude au support technique** et **arnaque au faux conseiller bancaire**, en forte hausse, appuyées sur des données réelles issues de fuites.
- **Rançon fictive** : mail affirmant détenir des images compromettantes, souvent accompagné d'un mot de passe issu d'une vieille fuite pour faire vrai. Ne payez pas, changez le mot de passe concerné s'il est encore utilisé.
- **Fausse offre d'emploi ou faux recruteur**, avec un fichier « test technique » piégé.

### Bonnes habitudes

- Utilisez un gestionnaire de mots de passe : il refuse de remplir sur un domaine qui ne correspond pas, ce qui constitue une alerte fiable.
- Déployez des passkeys sur les comptes critiques.
- Vérifiez toujours l'expéditeur réel, pas le nom affiché.
- Instaurez un **mot de passe familial** oral pour les demandes urgentes d'argent ou d'informations, désormais indispensable face au clonage vocal.
- En entreprise, exigez une double validation hors bande pour tout changement de coordonnées bancaires.

---
# Partie X. Aller plus loin

## 37. OPSEC avancée pour profils exposés

🔴 **Avancé.** Cette section s'adresse aux personnes dont l'échec a des conséquences graves : journalistes et leurs sources, lanceurs d'alerte, militants, avocats, chercheurs en sécurité, enquêteurs OSINT, personnes visées par des violences.

### Le principe directeur

Aux niveaux de menace élevés, la sécurité ne vient plus des outils mais des **procédures écrites, répétées et respectées même quand on est fatigué ou pressé**. Les échecs documentés viennent presque tous d'une exception ponctuelle à une règle par ailleurs correcte.

### Séparation matérielle

Le cloisonnement logiciel a des limites. Quand l'enjeu est élevé :

- **appareil dédié** à l'activité sensible, jamais utilisé pour autre chose, jamais connecté au même réseau que vos appareils personnels ;
- **réseau distinct** : forfait de données dédié, ou usage depuis des lieux variés et non habituels, sans jamais retomber sur le domicile ni sur le lieu de travail ;
- **systèmes amnésiques** ([Tails](#22-systèmes-spécialisés-pour-usages-sensibles)) pour ne rien laisser derrière ;
- pas de compte, d'application ni de fichier partagés entre les compartiments.

### Protection des sources

Pour une rédaction ou un chercheur :

- **Ne collectez pas ce que vous n'avez pas besoin de connaître.** L'information que vous ne détenez pas ne peut ni fuir, ni être saisie, ni être exigée.
- Mettez en place un canal de dépôt conçu pour cela : [SecureDrop](https://securedrop.org/) sur un service onion, ou à défaut Signal avec messages éphémères et vérification du numéro de sécurité.
- Minimisez les métadonnées : évitez les échanges par email et par téléphone, qui laissent des traces chez des tiers hors de votre contrôle.
- Séparez physiquement l'appareil de contact et l'appareil d'analyse des documents ; ouvrez les fichiers reçus dans un environnement isolé et hors ligne.
- Nettoyez les documents avant publication : [métadonnées](#25-fichiers-et-métadonnées), marqueurs invisibles, particularités de mise en page permettant d'identifier la copie transmise (attention aux documents individualisés par le détenteur).
- Établissez et écrivez à l'avance une politique de conservation et de destruction. Décidez froidement, pas dans l'urgence.

### OPSEC pour l'enquêteur OSINT

Le risque est le retour de flamme : votre cible apprend qui vous êtes.

- **Comptes de recherche dédiés** (*sock puppets*), créés depuis un environnement propre, avec une histoire crédible et une ancienneté suffisante. Un compte créé la veille attire l'attention.
- Ne consultez jamais un profil sensible depuis un compte relié à vous : certaines plateformes notifient les visites ou les suggèrent dans les recommandations de contacts.
- Attention aux **suggestions d'amis** : elles se nourrissent du carnet d'adresses, de l'adresse IP et de l'historique. Ne mélangez jamais les appareils.
- Adresse IP différente de votre lieu de travail ; attention aussi au fait qu'un accès depuis un réseau d'entreprise identifie l'employeur dans les journaux de la cible.
- Journalisez votre travail (horodatage, méthode, captures) : c'est nécessaire pour la valeur probante, et cela évite de refaire deux fois la même recherche depuis deux identités.
- Respectez le cadre légal : la collecte en sources ouvertes n'autorise ni l'intrusion, ni l'usurpation d'identité, ni le traitement de données personnelles hors des règles applicables.

### Répétition et plan de secours

- Écrivez vos procédures, y compris la procédure de **destruction** et celle de **compromission** (que faire, dans quel ordre, qui prévenir, en combien de temps).
- Répétez-les à froid, au moins une fois. Une procédure jamais testée échoue au premier usage réel.
- Prévoyez un canal de secours convenu à l'avance avec vos correspondants, ainsi qu'un signal de sécurité (mot convenu indiquant que vous écrivez sous contrainte, ou son absence indiquant un problème).
- Prévoyez l'accès à vos comptes en cas d'indisponibilité prolongée, et une procédure de mise en sécurité de vos données pour vos proches.

### Se faire aider

- [Access Now Digital Security Helpline](https://www.accessnow.org/help/) : assistance gratuite, 24 h/24, multilingue, pour les personnes de la société civile.
- [Freedom of the Press Foundation](https://freedom.press/) : guides et formations pour les journalistes.
- [Citizen Lab](https://citizenlab.ca/) et le Security Lab d'[Amnesty International](https://securitylab.amnesty.org/) : analyse de compromissions par logiciels espions.
- En France : [Nothing2Hide](https://nothing2hide.org/), [La Quadrature du Net](https://www.laquadrature.net/), [Reporters sans frontières](https://rsf.org/).

---

## 38. Études de cas d'échecs OPSEC

Ces affaires sont documentées publiquement. Elles sont utiles parce qu'elles montrent une constante : **la technique tient, c'est le comportement qui cède**.

### Un identifiant réutilisé, des années plus tôt

Ross Ulbricht, fondateur de la place de marché Silk Road, opérait derrière Tor. L'enquête a notamment exploité des messages publiés très tôt sur des forums publics pour faire connaître le site, dont l'un mentionnait une adresse email personnelle contenant son nom réel. Un message vieux de plusieurs mois, publié avant que le projet ne devienne sensible, a suffi à établir un lien.

**Leçon** : votre OPSEC commence **avant** que l'activité ne devienne sensible. Les archives et les moteurs conservent ce que vous avez supprimé.

### Une métadonnée d'email

Alexandre Cazes, administrateur d'AlphaBay, a été identifié à partir d'un en-tête d'un email automatique envoyé aux nouveaux utilisateurs, qui contenait une adresse personnelle utilisée depuis des années et reliée à ses comptes réels.

**Leçon** : les systèmes automatisés fuient à votre place. Vérifiez ce que produisent vos scripts, vos formulaires, vos serveurs et vos messages automatiques.

### Être le seul à utiliser Tor

En 2013, un étudiant de Harvard a envoyé une fausse alerte à la bombe via Tor et un service d'email anonyme pour éviter un examen. Il n'a pas été démasqué par une faille de Tor, mais par les journaux du réseau universitaire : il était, à ce moment précis, l'un des très rares utilisateurs de Tor sur le réseau du campus.

**Leçon** : l'anonymat dépend de la taille de la foule dans laquelle vous vous fondez. Utiliser un outil rare dans un contexte restreint vous désigne au lieu de vous protéger.

### Une seule connexion sans protection

Hector Monsegur, figure du groupe LulzSec, s'est connecté une fois à un canal IRC sans passer par Tor, ce qui a révélé son adresse IP réelle.

**Leçon** : une exception unique annule des mois de discipline. Les protections doivent être automatiques (routage forcé au niveau du système, comme avec Whonix ou Tails), pas laissées à la vigilance humaine.

### Des métadonnées d'image

En 2012, la localisation approximative de John McAfee, alors en fuite, a été divulguée par une photo publiée par un média, dont les données EXIF contenaient des coordonnées GPS.

**Leçon** : la [section 25](#25-fichiers-et-métadonnées) n'est pas théorique. Le nettoyage doit être systématique, y compris pour les fichiers transmis à des tiers qui les publieront.

### Des marqueurs sur un document imprimé

En 2017, une analyste américaine a transmis à un média un document classifié imprimé. Le document publié contenait les micropoints jaunes ajoutés automatiquement par de nombreuses imprimantes couleur, identifiant l'imprimante et l'horodatage. Le nombre restreint de personnes ayant imprimé ce document a fait le reste.

**Leçon** : le support physique porte des identifiants invisibles, et les journaux d'accès internes réduisent la liste des suspects. Retranscrire plutôt que transmettre l'original est parfois la seule option sûre.

### Faire confiance à une plateforme fournie par l'adversaire

Les opérations autour des réseaux Encrochat et Anom ont montré que des milliers d'utilisateurs communiquaient sur des téléphones dits sécurisés, dont l'infrastructure était en réalité compromise ou directement exploitée par des services d'enquête.

**Leçon** : préférez les protocoles ouverts, audités et vérifiables aux « solutions sécurisées » fermées vendues clés en main. Ne pas pouvoir vérifier signifie devoir faire confiance, et la confiance est exactement ce que l'OPSEC cherche à minimiser.

### Le point commun

| Cause de l'échec | Fréquence | Contre-mesure |
| --- | --- | --- |
| Réutilisation d'un identifiant ou d'un pseudonyme | Très fréquente | [Compartimentation](#28-compartimentation-et-identités) stricte dès le premier jour |
| Une exception ponctuelle à la règle | Très fréquente | Automatiser le routage et l'isolation |
| Métadonnées oubliées | Fréquente | Procédure de nettoyage systématique |
| Confiance dans un tiers fermé | Fréquente | Outils ouverts et audités |
| Erreur commise avant que l'activité ne devienne sensible | Fréquente | Considérer l'archivage comme permanent |

---

# Partie XI. Références

## 39. Checklists

### 39.1 Niveau base, environ 3 heures

- [ ] Gestionnaire de mots de passe installé, mot de passe maître mémorisé, clé de récupération rangée hors ligne
- [ ] Email principal : mot de passe unique, MFA, règles de transfert vérifiées, adresses de récupération à jour
- [ ] Mots de passe uniques sur les comptes critiques (banque, opérateur, cloud, achats, travail)
- [ ] MFA activée partout où c'est possible, en évitant le SMS quand une autre option existe
- [ ] Codes de secours imprimés et rangés
- [ ] Chiffrement du disque activé sur ordinateur et téléphone, clé de récupération conservée hors ligne
- [ ] Mises à jour automatiques activées partout
- [ ] Sauvegarde en place, et **restauration testée**
- [ ] Vérification des adresses email sur Have I Been Pwned, mots de passe concernés changés
- [ ] Applications mobiles inutilisées désinstallées, permissions révisées
- [ ] Extensions de navigateur réduites à l'essentiel, uBlock Origin installé
- [ ] DNS chiffré et filtrant configuré
- [ ] Comptes en ligne inutilisés fermés

### 39.2 Niveau intermédiaire

- [ ] Alias email en place, un par service pour les nouvelles inscriptions
- [ ] Deux navigateurs ou profils séparés, l'un connecté, l'autre non
- [ ] Signal installé et configuré (verrou du registre, nom d'utilisateur, messages éphémères)
- [ ] Numéro de téléphone retiré des méthodes de récupération critiques
- [ ] Code confidentiel activé chez l'opérateur téléphonique
- [ ] Réseaux sociaux : paramètres revus, historique nettoyé, synchronisation des contacts désactivée
- [ ] Auto-audit OSINT réalisé, résultats classés et traités
- [ ] Demandes d'effacement envoyées aux principaux courtiers en données
- [ ] Cloud personnel chiffré côté client (Cryptomator ou équivalent)
- [ ] Objets connectés sur un réseau séparé
- [ ] Métadonnées nettoyées avant toute publication de fichier
- [ ] VPN choisi en connaissance de cause, ou décision assumée de ne pas en utiliser
- [ ] Deux clés de sécurité matérielles achetées et enregistrées sur les comptes critiques
- [ ] Mot de passe familial oral convenu contre le clonage vocal

### 39.3 Niveau avancé

- [ ] Modèle de menace écrit, daté, relu tous les six mois
- [ ] Compartiments définis et documentés, avec règles explicites
- [ ] Appareil dédié pour l'activité sensible, jamais mélangé
- [ ] Tails ou Qubes OS maîtrisé et réellement utilisé pour les tâches concernées
- [ ] GrapheneOS ou iOS en mode Isolement selon le profil
- [ ] Procédures écrites : compromission, destruction, contact d'urgence, canal de secours
- [ ] Procédures testées au moins une fois à froid
- [ ] Contacts établis avec une structure d'assistance avant d'en avoir besoin
- [ ] Politique de conservation et de destruction des données définie et appliquée
- [ ] Revue annuelle complète : outils, comptes, appareils, exposition publique

### 39.4 Réaction rapide en cas de fuite

- [ ] Identifier les catégories de données concernées
- [ ] Changer le mot de passe du service, puis partout où il était réutilisé
- [ ] Révoquer les sessions actives et les appareils connectés
- [ ] Vérifier les règles de transfert et les accès tiers sur la messagerie
- [ ] Renforcer la MFA sur les comptes liés
- [ ] Se préparer aux tentatives de phishing citant vos vraies données
- [ ] Surveiller les relevés bancaires pendant plusieurs mois
- [ ] Exercer ses droits RGPD, signaler à la CNIL si nécessaire

### 39.5 Avant un voyage sensible

- [ ] Sauvegarde complète effectuée et vérifiée
- [ ] Données inutiles retirées des appareils emportés
- [ ] Appareils éteints avant le passage de frontière
- [ ] Biométrie désactivée, code long activé
- [ ] Sessions sensibles fermées, comptes déconnectés
- [ ] Comportement décidé à l'avance en cas de demande de déverrouillage
- [ ] Contacts d'urgence et numéros importants notés hors des appareils

### 39.6 Revue périodique, deux fois par an

- [ ] Modèle de menace toujours valable
- [ ] Rapport du gestionnaire de mots de passe traité (réutilisations, fuites, mots de passe faibles)
- [ ] Sessions actives et appareils connectés purgés sur les comptes principaux
- [ ] Applications tierces autorisées révisées
- [ ] Restauration de sauvegarde testée
- [ ] Auto-audit OSINT refait
- [ ] Fiches chez les courtiers en données revérifiées
- [ ] Outils utilisés toujours maintenus, audités et recommandés

---

## 40. Glossaire

**AiTM** (*adversary in the middle*) : attaque où un serveur intermédiaire relaie en temps réel la connexion vers le vrai site, capturant identifiants, code MFA et session.

**Alias** : adresse email de redirection, unique par service, qui masque l'adresse réelle et permet de couper une source de spam ou de fuite.

**Bac à sable** (*sandbox*) : mécanisme d'isolation qui empêche un programme d'accéder au reste du système.

**Chiffrement au repos** : les données sont chiffrées sur le disque du serveur, mais le fournisseur détient généralement la clé.

**Chiffrement de bout en bout** : seuls l'expéditeur et le destinataire peuvent déchiffrer. Ni le fournisseur ni un intercepteur n'ont accès au contenu.

**Chiffrement en transit** : les données sont chiffrées entre vous et le serveur, qui les déchiffre à l'arrivée.

**Client-side scanning** : analyse des contenus sur l'appareil de l'utilisateur, avant chiffrement. Seule méthode permettant d'inspecter des communications chiffrées de bout en bout, au prix d'un affaiblissement du modèle de sécurité.

**Compartimentation** : séparation volontaire des activités et des identités, pour qu'une compromission ne se propage pas.

**Confidentialité persistante** (*forward secrecy*) : propriété garantissant que la compromission future d'une clé ne permet pas de déchiffrer les échanges passés.

**Corrélation** : recoupement d'éléments individuellement anodins permettant d'identifier une personne ou de relier deux identités.

**Courtier en données** (*data broker*) : entreprise qui collecte, agrège et revend des profils de personnes.

**Credential stuffing** : essai automatisé d'identifiants issus de fuites sur de nombreux services, exploitant la réutilisation des mots de passe.

**Diceware** : méthode de génération de phrases de passe par tirage aléatoire de mots dans une liste.

**DNS** : annuaire traduisant les noms de domaine en adresses IP. **DoH** et **DoT** en sont les versions chiffrées.

**Doxing** : publication d'informations personnelles dans le but de nuire.

**EXIF** : métadonnées intégrées aux images (appareil, date, coordonnées GPS).

**FIDO2 / WebAuthn** : standards d'authentification par clé cryptographique, résistants au phishing car liés au domaine.

**Fingerprinting** : identification d'un visiteur par la combinaison des caractéristiques techniques de son navigateur et de son appareil.

**Infostealer** : logiciel malveillant spécialisé dans le vol d'identifiants, de cookies de session et de fichiers.

**Métadonnées** : données décrivant une communication ou un fichier (qui, quand, où, avec qui) par opposition au contenu.

**MFA / 2FA** : authentification exigeant plusieurs preuves d'identité.

**Modèle de menace** : description explicite de ce que vous protégez, contre qui, avec quelles conséquences et quels moyens.

**OPSEC** : sécurité opérationnelle, démarche consistant à identifier les informations sensibles, les menaces, les vulnérabilités, et à y répondre de façon proportionnée.

**OSINT** : renseignement en sources ouvertes, collecte d'informations publiquement accessibles.

**Passkey** : justificatif d'authentification fondé sur WebAuthn, remplaçant le mot de passe, résistant au phishing.

**PGP / GnuPG** : chiffrement et signature de messages et de fichiers, interopérable, sans confidentialité persistante.

**Post-quantique** : algorithmes conçus pour résister à un futur ordinateur quantique. Pertinent contre la stratégie « capter maintenant, déchiffrer plus tard ».

**Rançongiciel** : logiciel qui chiffre vos données pour exiger un paiement. Réponse principale : la sauvegarde hors ligne.

**SIM swapping** : détournement d'un numéro de téléphone auprès de l'opérateur, permettant d'intercepter les SMS d'authentification.

**Stalkerware** : logiciel de surveillance installé sur l'appareil d'un proche, souvent dans un contexte de violences.

**Stylométrie** : analyse du style d'écriture permettant de relier des textes à un même auteur.

**Surface d'exposition** : ensemble des points par lesquels des informations vous concernant sont accessibles.

**TOTP** : code à usage unique calculé à partir d'un secret partagé et de l'heure.

**Tor** : réseau d'anonymisation faisant transiter le trafic par trois relais successifs.

**VPN** : tunnel chiffré vers un serveur tiers, qui masque l'adresse IP aux sites visités et le trafic au fournisseur d'accès.

**Zero-knowledge** : architecture dans laquelle le fournisseur ne peut techniquement pas accéder aux données de l'utilisateur.

---

## 41. Ressources

### Francophones

| Ressource | Type | Utilité |
| --- | --- | --- |
| [CNIL](https://www.cnil.fr/) | Autorité de protection des données | Guides pratiques, modèles de courriers, dépôt de plainte |
| [ANSSI](https://cyber.gouv.fr/) | Agence de cybersécurité | Guides d'hygiène informatique, recommandations techniques |
| [Cybermalveillance.gouv.fr](https://www.cybermalveillance.gouv.fr/) | Dispositif public d'assistance | Diagnostic, marche à suivre en cas d'incident, annuaire de prestataires |
| [La Quadrature du Net](https://www.laquadrature.net/) | Association | Suivi des textes touchant aux libertés numériques |
| [Nothing2Hide](https://nothing2hide.org/) | Association | Formations et guides pour journalistes et société civile |
| [Exodus Privacy](https://exodus-privacy.eu.org/) | Association | Analyse des pisteurs présents dans les applications Android |
| [Framasoft](https://framasoft.org/) et [Chatons](https://www.chatons.org/) | Associations | Services libres et hébergeurs alternatifs francophones |
| [Sécurité en soirée, guides RSF](https://rsf.org/) | ONG | Sécurité des journalistes |
| [3018](https://www.e-enfance.org/) | Numéro national | Violences numériques, en particulier pour les mineurs |
| [3919](https://www.solidaritefemmes.org/) | Numéro national | Violences faites aux femmes, y compris volet numérique |

### Anglophones

| Ressource | Type | Utilité |
| --- | --- | --- |
| [Privacy Guides](https://www.privacyguides.org/) | Guide communautaire | Recommandations d'outils argumentées, sans sponsors |
| [EFF Surveillance Self-Defense](https://ssd.eff.org/) | Guide | Pédagogie du modèle de menace, plusieurs langues dont le français |
| [Freedom of the Press Foundation](https://freedom.press/) | ONG | Sécurité des journalistes et des sources, SecureDrop |
| [Access Now Helpline](https://www.accessnow.org/help/) | Assistance | Aide gratuite pour la société civile, 24 h/24 |
| [Citizen Lab](https://citizenlab.ca/) | Recherche | Enquêtes sur les logiciels espions et la surveillance |
| [Amnesty Security Lab](https://securitylab.amnesty.org/) | Recherche | Analyse forensique de compromissions |
| [Tor Project](https://www.torproject.org/) | Projet | Documentation officielle de Tor |
| [GrapheneOS](https://grapheneos.org/) | Projet | Documentation et forum techniques de référence sur la sécurité Android |
| [Have I Been Pwned](https://haveibeenpwned.com/) | Service | Vérification et alertes de fuites |
| [NIST SP 800-63](https://pages.nist.gov/800-63-3/) | Standard | Référentiel d'authentification, base des recommandations modernes sur les mots de passe |

### Veille

- Blogs : [Schneier on Security](https://www.schneier.com/), [Krebs on Security](https://krebsonsecurity.com/), [Soatok](https://soatok.blog/) (cryptographie appliquée), [A Few Thoughts on Cryptographic Engineering](https://blog.cryptographyengineering.com/).
- Actualité francophone : [LeMagIT](https://www.lemagit.fr/), [Next](https://next.ink/), [Zataz](https://www.zataz.com/).
- Suivi réglementaire européen : [EDRi](https://edri.org/), [Patrick Breyer](https://www.patrick-breyer.de/), [exitchatcontrol.eu](https://exitchatcontrol.eu/).
- Communautés : forum de [Privacy Guides](https://discuss.privacyguides.net/), forum [GrapheneOS](https://discuss.grapheneos.org/).

### Livres

- *Extreme Privacy*, Michael Bazzell : très complet sur l'effacement et la vie privée opérationnelle, orienté États-Unis, à adapter au contexte européen.
- *L'Art de l'invisibilité*, Kevin Mitnick : bonne vulgarisation de l'ingénierie sociale, quelques éléments techniques datés.
- *Sandworm*, Andy Greenberg : compréhension des opérations étatiques.
- *Permanent Record*, Edward Snowden : contexte de la surveillance de masse.

### Outils cités dans ce guide

Gestionnaires de mots de passe : [Bitwarden](https://bitwarden.com/), [KeePassXC](https://keepassxc.org/), [Proton Pass](https://proton.me/pass), [Vaultwarden](https://github.com/dani-garcia/vaultwarden).
Authentification : [Aegis](https://getaegis.app/), [Ente Auth](https://ente.io/auth/), [2FAS](https://2fas.com/), [YubiKey](https://www.yubico.com/), [Nitrokey](https://www.nitrokey.com/).
Messageries : [Signal](https://signal.org/), [SimpleX](https://simplex.chat/), [Briar](https://briarproject.org/), [Molly](https://molly.im/), [Element](https://element.io/), [Threema](https://threema.ch/).
Email et alias : [Proton Mail](https://proton.me/mail), [Tuta](https://tuta.com/), [Posteo](https://posteo.de/), [mailbox.org](https://mailbox.org/), [SimpleLogin](https://simplelogin.io/), [addy.io](https://addy.io/).
Réseau : [Mullvad](https://mullvad.net/), [IVPN](https://www.ivpn.net/), [Proton VPN](https://protonvpn.com/), [Quad9](https://www.quad9.net/), [dns0.eu](https://www.dns0.eu/), [NextDNS](https://nextdns.io/), [Tailscale](https://tailscale.com/), [Headscale](https://github.com/juanfont/headscale), [Pi-hole](https://pi-hole.net/), [AdGuard Home](https://adguard.com/adguard-home/overview.html).
Navigateurs : [Mullvad Browser](https://mullvad.net/browser), [Tor Browser](https://www.torproject.org/download/), [LibreWolf](https://librewolf.net/), [Brave](https://brave.com/), [arkenfox](https://github.com/arkenfox/user.js), [uBlock Origin](https://github.com/gorhill/uBlock).
Systèmes : [GrapheneOS](https://grapheneos.org/), [Tails](https://tails.net/), [Whonix](https://www.whonix.org/), [Qubes OS](https://www.qubes-os.org/), [F-Droid](https://f-droid.org/), [Obtainium](https://github.com/ImranR98/Obtainium).
Fichiers et chiffrement : [VeraCrypt](https://www.veracrypt.fr/), [Cryptomator](https://cryptomator.org/), [age](https://github.com/FiloSottile/age), [MAT2](https://0xacab.org/jvoisin/mat2), [ExifTool](https://exiftool.org/), [Restic](https://restic.net/), [BorgBackup](https://www.borgbackup.org/).
IA locale : [Ollama](https://ollama.com/), [llama.cpp](https://github.com/ggml-org/llama.cpp), [Jan](https://jan.ai/), [Open WebUI](https://github.com/open-webui/open-webui).

---

## 42. Sources

Sources consultées pour la rédaction et la vérification de ce document. Date de consultation : **août 2026**. Les liens pointent en priorité vers les sources primaires. Les affirmations chiffrées issues de la presse ou d'entreprises privées sont signalées comme telles dans le texte.

### Institutions, autorités et textes

- CNIL, [cnil.fr](https://www.cnil.fr/) : violations de données, droits RGPD, doctrine sur la vérification d'âge et le double anonymat.
- ANSSI, [cyber.gouv.fr](https://cyber.gouv.fr/) : guide d'hygiène informatique, référentiels et recommandations.
- Cybermalveillance.gouv.fr, [cybermalveillance.gouv.fr](https://www.cybermalveillance.gouv.fr/) : conduite à tenir en cas d'incident.
- Règlement (UE) 2016/679 (RGPD), articles 15 à 21.
- Parlement européen et Conseil de l'Union européenne : proposition de règlement CSAR (2022/0155), positions et calendrier des trilogues.
- Assemblée nationale et Sénat : proposition de loi contre le narcotrafic, article 8 ter et son retrait en commission des lois, mars 2025.
- Conseil fédéral suisse : révision de l'ordonnance sur la surveillance de la correspondance par poste et télécommunication, consultation 2025 et réexamen annoncé en février 2026.

### Suivi de Chat Control et des libertés numériques

- Patrick Breyer, [Chat Control, dossier de suivi](https://www.patrick-breyer.de/en/posts/chat-control/).
- [exitchatcontrol.eu](https://exitchatcontrol.eu/).
- [EDRi](https://edri.org/) et [Center for Democracy and Technology Europe](https://cdt.org/).
- Euronews, [Why is Chat Control one of the EU's biggest digital rights fights](https://www.euronews.com/my-europe/2026/07/28/why-is-chat-control-one-of-the-eus-biggest-digital-rights-fights), 28 juillet 2026 : vote du Parlement du 9 juillet 2026 et confirmation par le Conseil le 23 juillet 2026 du régime intérimaire jusqu'au 3 avril 2028.
- La Quadrature du Net, [Le Parlement vote l'interdiction des réseaux sociaux aux jeunes de moins de 15 ans](https://www.laquadrature.net/2026/07/22/le-parlement-vote-linterdiction-des-reseaux-sociaux-aux-jeunes-de-moins-de-15-ans/), 22 juillet 2026.
- La Quadrature du Net, [Le gouvernement prêt à tout pour casser le droit au chiffrement](https://www.laquadrature.net/2025/03/18/le-gouvernement-pret-a-tout-pour-casser-le-droit-au-chiffrement/), mars 2025.

### Fuites de données et menaces

- Chiffres CNIL relayés par la presse spécialisée : 6 167 notifications de violations en 2025 (hausse d'environ 10 % sur un an), plus de 2 700 notifications au premier trimestre 2026, et progression des incidents touchant plus d'un million de personnes.
- [Have I Been Pwned](https://haveibeenpwned.com/) : base de référence sur les fuites publiques.
- Rapports d'éditeurs et de CERT sur les infostealers et le vol de sessions (2025 et 2026). Les volumes annoncés varient selon les méthodologies ; seuls les ordres de grandeur et les tendances sont repris ici.
- Verizon Data Breach Investigations Report, éditions récentes, sur la part de l'abus d'identifiants dans les compromissions.

### Outils et projets

- [Privacy Guides](https://www.privacyguides.org/) : recommandations et critères, notamment sur les messageries (Signal, SimpleX, Briar, Molly) et les VPN.
- [Signal](https://signal.org/blog/) : documentation du protocole, chiffrement post-quantique, réponses publiées aux réquisitions.
- [SimpleX Chat](https://simplex.chat/blog/) : architecture sans identifiant, rapports d'audit 2022 et 2024.
- Privacy Guides, [Session messenger adds PFS, PQE and other improvements](https://www.privacyguides.org/news/2025/12/03/session-messenger-adds-pfs-pqe-and-other-improvements/), décembre 2025.
- [Mullvad](https://mullvad.net/fr/blog) : abandon d'OpenVPN en janvier 2026, implémentation WireGuard en Rust, audit de janvier et février 2026, DAITA, échange de clés résistant au quantique.
- [IVPN](https://www.ivpn.net/blog/) et [Proton](https://proton.me/blog) : audits et évolutions d'infrastructure, déplacement partiel hors de Suisse.
- [GrapheneOS](https://grapheneos.org/releases) et [forum GrapheneOS](https://discuss.grapheneos.org/) : portage d'Android 17 en juin 2026, appareils pris en charge, conséquences du passage d'AOSP à deux publications de sources par an.
- [Tails](https://tails.net/news/), [Whonix](https://www.whonix.org/), [Qubes OS](https://www.qubes-os.org/doc/) : documentation officielle et notes de version.
- [FIDO Alliance](https://fidoalliance.org/) : état de l'adoption des passkeys, travaux sur le Credential Exchange Protocol.
- [NIST SP 800-63B](https://pages.nist.gov/800-63-3/sp800-63b.html) : recommandations d'authentification, y compris sur le renouvellement des mots de passe.

### Pistage et publicité

- Communications de Google sur l'abandon de la suppression des cookies tiers dans Chrome (2025) et sur l'évolution de sa politique publicitaire relative aux identifiants d'appareil (février 2025).
- Travaux académiques et rapports sur le fingerprinting, le CNAME cloaking et le suivi côté serveur.
- [Exodus Privacy](https://exodus-privacy.eu.org/) : pisteurs présents dans les applications mobiles.

### Intelligence artificielle

- Décisions et ordonnances rendues dans le litige opposant des médias américains à OpenAI, sur la conservation des journaux de conversation, à partir de mai 2025, et décisions ultérieures sur l'absence de secret applicable à ces échanges.
- Documentation des projets [Ollama](https://ollama.com/), [llama.cpp](https://github.com/ggml-org/llama.cpp), [Jan](https://jan.ai/).

**Note de méthode.** Certaines informations de ce guide proviennent de sources secondaires (presse spécialisée, blogs d'éditeurs) faute de source primaire accessible. Elles sont formulées avec les précautions correspondantes. Si vous constatez une erreur ou une information devenue obsolète, ouvrez une issue : voir [section 43](#43-contribuer-et-maintenir-ce-projet).

---

## 43. Contribuer et maintenir ce projet

### Ce qu'est ce projet

Une ressource francophone unique, en Markdown, pensée pour rester lisible, vérifiable et facile à maintenir par une seule personne ou par une petite communauté. Un site web pourra venir plus tard ; le contenu restera la source de vérité.

### Structure du dépôt

```
french-opsec/
├── README.md          Le guide complet, source unique du contenu
├── CONTRIBUTING.md    Comment contribuer, critères d'inclusion d'un outil
└── LICENSE            CC BY-SA 4.0 pour le contenu
```

Le guide tient volontairement dans un seul fichier : c'est ce qui le rend consultable hors ligne, imprimable, recherchable avec un simple `Ctrl+F`, et facile à relire dans une pull request. Si le volume l'impose un jour, la découpe se fera par partie, en conservant les ancres.

### Comment contribuer

Toutes les contributions passent par une issue ou une pull request.

| Vous voulez | Faites |
| --- | --- |
| Signaler une erreur | Ouvrez une issue avec la section concernée et la source qui contredit le texte |
| Signaler une information obsolète | Ouvrez une issue avec la date et la source du changement |
| Proposer un outil | Ouvrez une issue en répondant aux critères ci-dessous |
| Proposer une correction de forme | Pull request directe |
| Proposer une nouvelle section | Ouvrez d'abord une issue pour discuter du périmètre |

### Critères d'inclusion d'un outil

Un outil n'est pas ajouté parce qu'il est populaire. Il doit satisfaire l'essentiel de ces critères, et la proposition doit l'argumenter :

1. **Utilité** : il résout un problème identifié dans le guide, pour un modèle de menace explicite.
2. **Transparence** : code ouvert de préférence, ou à défaut documentation technique sérieuse sur le fonctionnement et les limites.
3. **Audits** : audit indépendant public, ou justification de son absence.
4. **Maintenance** : projet actif, correctifs de sécurité livrés, publication des vulnérabilités.
5. **Modèle économique clair** : on sait qui paie et comment.
6. **Limites documentées** : la proposition doit indiquer ce que l'outil **ne** protège **pas**.
7. **Alternatives** : au moins une alternative crédible mentionnée.

Sont refusés : les outils sans limites explicitées, les liens affiliés, les produits promettant l'anonymat total, les recommandations sans source.

### Règles de rédaction

- Français clair, phrases courtes, ton neutre et professionnel.
- Chaque terme technique est défini à sa première apparition et ajouté au [glossaire](#40-glossaire).
- Aucune affirmation absolue : pas de « 100 % sécurisé », « impossible à tracer », « totalement anonyme ».
- Toute affirmation factuelle vérifiable doit pouvoir être rattachée à une source listée en [section 42](#42-sources).
- Structure des fiches outils : pourquoi, comment, ce que cela ne protège pas, pièges, alternatives.
- Pas de style sensationnaliste, pas d'accumulation d'emojis, pas de marketing.

### Maintenance

- Les sections sensibles au temps portent la mention `*Vérifié : mois année.*` Mettez-la à jour lorsque vous vérifiez le contenu, même si rien ne change.
- Une revue complète est souhaitable deux fois par an, ainsi qu'après tout changement réglementaire majeur.
- Les changements notables sont décrits dans le message de commit et dans l'issue correspondante, afin que l'historique reste consultable via Git.
- Un outil retiré doit l'être avec une justification en issue, afin que la décision reste traçable.

### Licence

Le contenu est publié sous **Creative Commons Attribution - Partage dans les mêmes conditions 4.0 International (CC BY-SA 4.0)**.

Pourquoi ce choix plutôt que MIT : la licence MIT est conçue pour du code, pas pour de la documentation, et n'impose pas le partage à l'identique. CC BY-SA garantit trois choses utiles à une ressource documentaire : la réutilisation libre, y compris commerciale ; l'attribution, qui permet de remonter à la source et donc de vérifier les informations ; et le partage dans les mêmes conditions, qui empêche qu'une version dérivée soit refermée. Les éventuels extraits de code et scripts fournis dans le dépôt sont, eux, placés sous licence MIT.

### Avant de contribuer

Lisez [CONTRIBUTING.md](CONTRIBUTING.md). Merci de citer vos sources : c'est ce qui distingue ce guide d'une liste d'opinions.

---

*Ce document est un travail collectif et perfectible. Il ne remplace ni une analyse de risque personnalisée, ni l'accompagnement d'une structure spécialisée si votre situation le justifie.*

*Dernière vérification générale : août 2026.*
