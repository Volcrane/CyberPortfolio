# Lab PortSwigger - DOM XSS Basique

## Objectif
Comprendre et exploiter une vulnérabilité XSS côté client (DOM-based XSS)

## Étapes
1. Identifier un paramètre dans l'URL ou un champ de formulaire qui reflète l'entrée utilisateur
2. Injecter un script simple : `<script>alert<('DOM XSS')</script>`
3. Observer le comportement dans le navigateur et vérifier l'apparition du popup
4. Analyser comment le DOM manipule les données par l'utilisateur

## Résultat
- Le popup `DOM XSS` apparaît → vulnérabilité confirmée côté client
- Pas besoin de toucher au serveur, tout se passe dans le navigateur

## Leçons apprises 
- Différence entre XSS côté serveur et côté client
- Importance de **sanitiser le DOM** pour protéger les utilisateurs
