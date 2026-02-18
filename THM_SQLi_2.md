# Lab TryHackMe – SQL Injection Advanced Basics

## Contexte

Ce lab TryHackMe présente une application web vulnérable à l’injection SQL avancée
L’objectif est de comprendre comment manipuler des requêtes SQL avec différentes techniques et d’évaluer l’impact potentiel sur la base de données et les utilisateurs

---

## Identification de la vulnérabilité

* Le formulaire d’authentification et certains paramètres URL acceptent des entrées utilisateur sans filtrage
* Les requêtes SQL sont construites dynamiquement à partir de ces entrées, sans requêtes préparées
* La vulnérabilité identifiée est une **SQL Injection de type Union-Based et Boolean-Based**, permettant d’extraire et manipuler des données sensibles

---

## Exploitation

### 1. Bypass d’authentification (Boolean-Based)

Payload injecté dans le champ `username` :

```
' OR 1=1 --
```

* La condition retourne toujours vrai → contournement du login
* Accès à un compte sans connaître le mot de passe

### 2. Extraction de données (Union-Based)

Payload injecté pour extraire le nom et l’e-mail des utilisateurs via `UNION SELECT` :

```
' UNION SELECT username, email FROM users --
```

* Permet de lister les utilisateurs existants
* Démonstration de l’accès non autorisé à la base de données

---

## Impact

Une injection SQL permet à un attaquant de :

* Contourner l’authentification
* Accéder aux comptes administrateurs
* Lire, modifier ou supprimer les données
* Compromettre l’intégrité et la confidentialité de la base de données

Dans un contexte réel, ces vulnérabilités sont considérées **critiques pour la sécurité de l’application**

---

## Remédiation

Pour corriger ces vulnérabilités :

* Utiliser des requêtes préparées (Prepared Statements) ou ORM sécurisé
* Valider et filtrer toutes les entrées utilisateur côté serveur
* Limiter les privilèges des comptes de base de données
* Mettre en place des logs et alertes pour détecter les tentatives d’injection

---

## Compétences mises en pratique

* Identification et exploitation d’injections SQL avancées
* Compréhension des techniques Union-Based et Boolean-Based
* Analyse des requêtes SQL et de l’impact sur la base de données
* Rédaction de rapports clairs et structurés pour un contexte professionnel
