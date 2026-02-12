# Lab TryHackMe – SQL Injection Basique

## Objectif
Comprendre et exploiter une vulnérabilité SQLi simple sur un formulaire web

## Étapes
1. Identifier le champ de formulaire vulnérable 
2. Tester une injection simple : `' OR '1'='1`  
3. Observer le comportement de la page et les messages d’erreur SQL
4. Noter comment la base de données réagit aux différentes entrées

## Résultat
- Injection SQL fonctionnelle sur le champ de login
- Accès à des données fictives ou modification de la réponse du serveur

## Leçons apprises
- Importance de la **validation côté serveur** et des requêtes préparées
- Compréhension du fonctionnement basique d’une vulnérabilité SQLi
