# Lab TryHackMe – SQL Injection Basics

## Contexte

Ce lab TryHackMe présente une application web vulnérable à l’injection SQL
L’objectif est d’identifier une faille dans un formulaire d’authentification et de comprendre comment une requête SQL mal sécurisée peut être manipulée

L’application interagit avec une base de données contenant des comptes utilisateurs

---

## Identification de la vulnérabilité

Le formulaire de connexion transmet les paramètres `username` et `password` à une requête SQL côté serveur

Les entrées utilisateur ne sont pas correctement filtrées ni sécurisées via des requêtes préparées

Cela permet d’injecter du code SQL directement dans la requête exécutée par la base de données

La vulnérabilité identifiée est une **SQL Injection de type Authentication Bypass (Boolean-based)**

---

## Exploitation

Injection du payload suivant dans le champ username :

```
' OR 1=1 --
```

Effet :

* La condition `1=1` est toujours vraie
* La requête retourne un utilisateur valide
* L’authentification est contournée sans connaître le mot de passe

Cela démontre qu’un attaquant peut manipuler la logique de la requête SQL pour obtenir un accès non autorisé

---

## Impact

Une injection SQL peut permettre à un attaquant de :

* Contourner l’authentification
* Accéder à des comptes administrateurs
* Lire, modifier ou supprimer des données
* Extraire l’intégralité de la base de données
* Compromettre l’intégrité du système

Dans un contexte réel, cela représente un risque critique pour la confidentialité et l’intégrité des données

---

## Remédiation

Pour prévenir ce type de vulnérabilité :

* Utiliser des requêtes préparées (Prepared Statements)
* Implémenter un ORM sécurisé
* Valider et filtrer les entrées utilisateur
* Appliquer le principe du moindre privilège sur la base de données
* Mettre en place une journalisation des tentatives d’injection

---

## Compétences mises en pratique

* Identification d’une faille SQL Injection
* Exploitation d’un bypass d’authentification
* Compréhension de la logique des requêtes SQL
* Analyse d’impact sécurité sur une base de données
