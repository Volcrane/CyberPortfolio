# Lab XSS PortSwigger – Reflected XSS (Alert 1)

## Contexte

Ce lab PortSwigger simule une application de blog contenant un champ commentaire vulnérable.
L’objectif est d’identifier une vulnérabilité de type Cross-Site Scripting (XSS), de l’exploiter et d’analyser les implications en matière de sécurité des cookies

---

## Identification de la vulnérabilité

Le champ commentaire accepte des entrées utilisateur qui sont réaffichées dans la page sans filtrage ni encodage.

Le paramètre injecté est directement interprété par le navigateur, ce qui indique une absence de validation et d’échappement des caractères spéciaux côté serveur

La vulnérabilité identifiée est une **XSS de type Reflected**

---

## Exploitation

Injection du payload suivant dans le champ commentaire :

```html
<script>alert(1)</script>
```

Résultat :

* Exécution immédiate du script dans le navigateur
* Apparition de la fenêtre `alert(1)`
* Confirmation que du code JavaScript arbitraire peut être exécuté

Une analyse des requêtes HTTP montre que les cookies de session sont transmis dans les échanges.

---

## Impact

Cette vulnérabilité permettrait à un attaquant de :

* Exécuter du JavaScript malveillant dans le navigateur de la victime
* Intercepter ou exfiltrer des cookies de session (si non protégés par HttpOnly)
* Usurper une session utilisateur
* Modifier dynamiquement le contenu affiché
* Rediriger vers un site malveillant

L’impact principal concerne la **confidentialité des données utilisateur** et la **prise de contrôle de session**

---

## Remédiation

Pour corriger cette vulnérabilité :

* Mettre en place un encodage systématique des entrées utilisateur (HTML encoding)
* Valider les entrées côté serveur
* Implémenter une Content Security Policy (CSP)
* Marquer les cookies sensibles avec l’attribut `HttpOnly`

---

## Compétences mises en pratique

* Identification d’une faille XSS
* Exploitation via injection JavaScript
* Analyse du comportement HTTP et des cookies
* Compréhension de l’impact sécurité en contexte réel
