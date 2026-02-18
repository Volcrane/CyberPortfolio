# Lab TryHackMe – Introduction to Web Hacking

## Contexte

Ce module TryHackMe introduit les concepts fondamentaux du web hacking en présentant les principales catégories de vulnérabilités rencontrées sur les applications web

L’objectif est de comprendre comment fonctionne une application web, d’identifier les points d’attaque potentiels et d’analyser les failles de sécurité courantes

---

## Compréhension de l’architecture Web

Avant toute exploitation, une analyse du fonctionnement d’une application web a été réalisée :

* Communication client ↔ serveur via HTTP
* Requêtes GET et POST
* Paramètres transmis dans l’URL ou le corps de la requête
* Interaction avec une base de données

Cette étape est essentielle pour comprendre où une vulnérabilité peut apparaître

---

## Vulnérabilités étudiées

### 1. Injection (SQL Injection)

Manipulation des entrées utilisateur pour modifier la requête SQL exécutée par le serveur

Impact potentiel :

* Contournement d’authentification
* Extraction de données
* Compromission de la base de données

---

### 2. Cross-Site Scripting (XSS)

Injection de JavaScript malveillant dans une application web

Impact potentiel :

* Vol de cookies
* Détournement de session
* Modification du contenu affiché
* Redirection vers un site malveillant

---

### 3. Broken Authentication

Mauvaise gestion des sessions ou des identifiants :

* Identifiants prévisibles
* Sessions non invalidées
* Absence de protection contre le brute force

Impact :

* Accès non autorisé à des comptes utilisateurs

---

### 4. Directory Enumeration

Recherche de fichiers et répertoires cachés via outils ou analyse manuelle

Objectif :

* Identifier des ressources sensibles exposées
* Découvrir des pages d’administration non protégées

---

## Méthodologie appliquée

Durant ce lab :

* Analyse des requêtes HTTP
* Manipulation des paramètres
* Test d’injections simples
* Observation du comportement du serveur

L’approche suivie repose sur :

1. Compréhension du fonctionnement normal
2. Identification d’un comportement anormal
3. Test contrôlé d’une hypothèse d’exploitation

---

## Impact global en contexte réel

Les vulnérabilités web sont parmi les plus exploitées en environnement réel

Une mauvaise sécurisation peut entraîner :

* Compromission de données sensibles
* Prise de contrôle de comptes
* Atteinte à la réputation de l’entreprise
* Non-conformité réglementaire (RGPD, etc.)

---

## Compétences mises en pratique

* Compréhension de l’architecture client/serveur
* Analyse de requêtes HTTP
* Identification des principales vulnérabilités web
* Approche méthodologique d’un test d’intrusion web
