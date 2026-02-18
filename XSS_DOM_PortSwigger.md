# Lab PortSwigger – DOM-Based XSS

## Contexte

Ce lab PortSwigger présente une application web vulnérable à une attaque **DOM-Based XSS**
L’objectif est de comprendre comment les entrées utilisateur peuvent manipuler le Document Object Model (DOM) côté client et provoquer l’exécution de scripts malveillants

---

## Identification de la vulnérabilité

* Le champ de saisie (`input` ou paramètre URL) est traité uniquement par JavaScript côté client
* Les entrées ne sont pas filtrées ou encodées avant d’être insérées dans le DOM via `innerHTML` ou un équivalent
* La vulnérabilité identifiée est une **DOM-Based Reflected XSS**, où la manipulation se produit uniquement dans le navigateur de la victime

---

## Exploitation

Payload injecté dans le champ vulnérable :

```html
<script>alert('DOM XSS')</script>
```

Résultat :

* Le script est exécuté immédiatement dans le navigateur
* Confirme qu’un attaquant peut injecter du code JavaScript arbitraire sans toucher le serveur

---

## Impact

Une DOM XSS permettrait à un attaquant de :

* Voler des cookies ou tokens de session accessibles côté client
* Modifier dynamiquement le contenu affiché sur la page
* Rediriger l’utilisateur vers un site externe
* Injecter des keyloggers ou autres scripts malveillants

Même si l’attaque se limite au navigateur de la victime, le risque reste **élevé pour la confidentialité et l’intégrité des données utilisateur**.

---

## Remédiation

Pour corriger cette vulnérabilité :

* Ne jamais insérer de données utilisateur dans le DOM avec `innerHTML`
* Utiliser `textContent` ou équivalent pour insérer du texte sûr
* Valider et encoder toutes les entrées côté client et côté serveur
* Mettre en place une Content Security Policy (CSP) adaptée

---

## Compétences mises en pratique

* Identification d’une XSS côté client (DOM)
* Compréhension des différences entre Reflected XSS classique et DOM-Based XSS
* Analyse du DOM et des comportements JavaScript
* Évaluation de l’impact sécurité pour l’utilisateur final
