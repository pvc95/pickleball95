# pickleball95.com — Pickleball Vexin Centre

Site statique bilingue français / anglais. Pas de build, pas de dépendance : du HTML et une feuille de style.

## Arborescence

| Français (racine) | Anglais (`/en/`) | État |
|---|---|---|
| `index.html` | `en/index.html` | publiée |
| `ou-jouer.html` | `en/where-to-play.html` | publiée |
| `adherer.html` | `en/join.html` | publiée |
| `le-club.html` | `en/the-club.html` | publiée |
| `tournoi-k100.html` | `en/k100-tournament.html` | **non publiées** — hors menus, `noindex`, exclues de `robots.txt` |

`styles.css` est partagé par les onze pages : une modification de style se répercute partout.

## Comment la langue est choisie

**Détection automatique.** Un script de quinze lignes, présent uniquement dans `index.html`, lit les préférences linguistiques du navigateur. Si l'anglais arrive avant le français, il redirige vers `/en/`. Sinon on reste en français, qui est la langue par défaut du site.

Le script ne redirige pas dans trois cas : quand l'URL porte un paramètre `?lang=`, quand la navigation vient du site lui-même, et quand le navigateur annonce une préférence française.

**Choix manuel.** Le sélecteur à drapeaux en haut à droite mène toujours à la page équivalente dans l'autre langue. Il fonctionne sans JavaScript (balise `<details>`) ; le script annexe ne sert qu'à refermer le menu au clic extérieur.

Les pages anglaises ne redirigent jamais : un francophone qui arrive sur `/en/join.html` depuis un moteur de recherche y reste, et peut basculer par le sélecteur.

## Modifier le site

Tout est éditable sur github.com : ouvrir le fichier, cliquer sur le crayon, valider. Le redéploiement prend environ une minute.

**Une modification de contenu doit être faite dans les deux langues.** Les informations qui bougent le plus :

- **créneaux et gymnases** → `ou-jouer.html` + `en/where-to-play.html`, et le bloc « la semaine » en haut des deux pages d'accueil
- **procédure d'inscription** → `adherer.html` + `en/join.html`
- **adresse de contact** → `le-club.html` + `en/the-club.html`, chercher `contact@pickleball95.com`

Si vous ajoutez une page, pensez aux trois balises `<link rel="alternate" hreflang="…">` dans le `<head>`, aux liens du sélecteur de langue, et à `sitemap.xml`.

## Publier les pages tournoi

Pour chacune des deux pages (`tournoi-k100.html` et `en/k100-tournament.html`) :

1. Supprimer `<meta name="robots" content="noindex, nofollow">`
2. Supprimer le bloc `<div class="brouillon">…</div>`
3. Ajouter les trois balises `hreflang` du couple de pages
4. Ajouter l'entrée dans le `<nav>` des quatre autres pages de la même langue
5. `robots.txt` : supprimer les deux lignes `Disallow`
6. `sitemap.xml` : ajouter les deux URL

## Reste à compléter

Chercher `TODO` dans les fichiers. Points ouverts :

- adresse e-mail de contact réellement créée dans Google Workspace
- adresse exacte et nom officiel du site du comité à Cergy
- tableaux, tarif d'engagement et lien d'inscription du K100
- formulation du format K100 à recaler sur le règlement FFT
- vérifier que les créneaux et les règles d'accès aux gymnases sont toujours exacts
- les deux vidéos de la page d'accueil sont en français : la version anglaise le signale, mais une vidéo anglophone serait mieux

## Fichiers techniques

- `CNAME` — domaine personnalisé, ne pas supprimer
- `.nojekyll` — désactive le traitement Jekyll de GitHub Pages
- `404.html` — page d'erreur, bilingue
- `robots.txt`, `sitemap.xml` — référencement, avec les correspondances de langue
