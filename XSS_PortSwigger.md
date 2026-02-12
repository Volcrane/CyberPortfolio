# Lab XSS PortSwigger – Alert(1)

## Objectif
Comprendre et exploiter une vulnérabilité XSS dans un blog, et analyser comment les cookies peuvent être interceptés

## Étapes
1. Identifier le champ vulnérable (champ commentaire)  
2. Injecter le script : <script>alert(1)</script>  
3. Observer le popup alert(1) pour vérifier la vulnérabilité 
4. Inspecter la requête HTTP pour comprendre le comportement du cookie

## Résultat
- XSS fonctionnel, popup alert(1) visible
- Cookie capturé dans la requête (test local uniquement)

## Leçons apprises
- Comment un script peut voler un cookie si le site ne filtre pas correctement les entrées
- Importance de la validation côté serveur et de l’encodage des entrées utilisateur
