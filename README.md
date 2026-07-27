# pickleball95.com — Pickleball Vexin Centre

Site statique du club, sans dépendance ni étape de build. Du HTML, du CSS, rien d'autre.

## Pages

| Fichier | Adresse | État |
|---|---|---|
| `index.html` | `/` | publiée |
| `ou-jouer.html` | `/ou-jouer.html` | publiée |
| `adherer.html` | `/adherer.html` | publiée |
| `le-club.html` | `/le-club.html` | publiée |
| `tournoi-k100.html` | `/tournoi-k100.html` | **non publiée** — absente des menus, `noindex`, exclue de `robots.txt` |

## Modifier le site

Tout est éditable directement sur github.com : ouvrir le fichier, cliquer sur le crayon, valider. Le site se redéploie tout seul en une minute.

Les informations qui changent le plus souvent :

- **créneaux et gymnases** → `ou-jouer.html`, plus le bloc « la semaine » en haut de `index.html`
- **procédure d'inscription** → `adherer.html`
- **adresse de contact** → `le-club.html`, chercher `contact@pickleball95.com`

## Publier la page tournoi

1. `tournoi-k100.html` : supprimer la balise `<meta name="robots" content="noindex, nofollow">`
2. `tournoi-k100.html` : supprimer le bloc `<div class="brouillon">…</div>`
3. Ajouter `<li><a href="tournoi-k100.html">Tournoi</a></li>` dans le `<nav>` des quatre autres pages
4. `robots.txt` : supprimer la ligne `Disallow: /tournoi-k100.html`
5. `sitemap.xml` : ajouter l'URL

## Reste à compléter

Chercher `TODO` dans les fichiers. Points ouverts :

- adresse e-mail de contact réellement créée dans Google Workspace
- adresse exacte et nom officiel du site du comité à Cergy
- tableaux, tarif d'engagement et lien d'inscription du K100
- formulation du format K100 à recaler sur le règlement FFT
- vérifier que les créneaux et les règles d'accès aux gymnases sont toujours exacts

## Fichiers techniques

- `CNAME` — domaine personnalisé, ne pas supprimer
- `.nojekyll` — désactive le traitement Jekyll de GitHub Pages
- `404.html` — page d'erreur
- `robots.txt`, `sitemap.xml` — référencement
