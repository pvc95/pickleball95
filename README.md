# pickleball95.com — Pickleball Vexin Centre

Site statique bilingue français / anglais. Pas de build, pas de dépendance : du HTML et une feuille de style.

## Arborescence

| Français (racine) | Anglais (`/en/`) | État |
|---|---|---|
| `index.html` | `en/index.html` | publiée |
| `ou-jouer.html` | `en/where-to-play.html` | publiée |
| `adherer.html` | `en/join.html` | publiée |
| `le-club.html` | `en/the-club.html` | publiée |
| `qui-sommes-nous.html` | `en/about-us.html` | publiée — identité juridique et mentions légales |
| `tournoi-k100.html` | `en/k100-tournament.html` | publiée — inscriptions ouvertes sur HelloAsso |

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

## Le tournoi K100

Les deux pages sont publiées depuis l'ouverture de la billetterie. Informations à tenir à jour si elles changent :

- lien HelloAsso, présent sur les deux pages tournoi **et** sur les deux pages d'accueil
- tableaux et tarifs : le tableau « Tableaux et tarifs »
- la règle FFT du tableau unique par jour, et le lien de création DUPR

Après le 4 octobre 2026, il faudra soit archiver ces pages, soit les remplacer par un compte rendu. Ne pas les laisser annoncer des inscriptions closes.

## Reste à compléter

Chercher `TODO` dans les fichiers. Points ouverts :

- adresse e-mail de contact réellement créée dans Google Workspace
- vérifier que les créneaux et les règles d'accès aux gymnases sont toujours exacts
- les deux vidéos de la page d'accueil sont en français : la version anglaise le signale, mais une vidéo anglophone serait mieux

## Fichiers techniques

- `CNAME` — domaine personnalisé, ne pas supprimer
- `.nojekyll` — désactive le traitement Jekyll de GitHub Pages
- `404.html` — page d'erreur, bilingue
- `robots.txt`, `sitemap.xml` — référencement, avec les correspondances de langue

## Mentions légales et transparence

La page « Qui sommes-nous » porte l'énoncé de mission, la composition du bureau, l'identité juridique (RNA W953012473, siège 21 rue du Général Leclerc, 95750 Chars) et les mentions légales exigées par la LCEN.

Le pied de page de **toutes** les pages répète la raison sociale, l'adresse du siège et le numéro RNA. C'est ce que contrôlent les évaluateurs de Google pour les programmes destinés aux associations.

Ne sont volontairement **pas** publiés : les adresses personnelles, professions et nationalités des dirigeants, qui figurent dans la déclaration en préfecture mais n'ont pas à être exposées en ligne. Le site ne mentionne que nom et fonction.

À mettre à jour après chaque assemblée générale : la composition du bureau et la liste des administrateurs, dans les deux langues.

## Le bandeau d'annonce du tournoi

Un bandeau sarcelle est affiché au-dessus de l'en-tête sur `index.html` et `en/index.html`. Il annonce le K100 avec un compteur de jours et deux liens : la page du tournoi et la billetterie.

**Il s'efface tout seul le 5 octobre 2026 à minuit.** Aucune intervention n'est nécessaire après le tournoi : le petit script le masque au-delà de cette date, et il est masqué par défaut dans le HTML, donc rien ne s'affiche si le script ne s'exécute pas.

Pour le retirer définitivement, ou pour le réutiliser pour un autre évènement :

- le bloc à supprimer est délimité par le commentaire `BANDEAU TEMPORAIRE` : l'élément `<aside class="alerte">` et le `<script>` qui le suit
- à faire sur les **deux** pages d'accueil
- pour une autre date, changer les deux `new Date(2026, 9, ...)` du script — attention, les mois commencent à 0 en JavaScript, donc `9` signifie octobre
- les styles `.alerte` restent dans `styles.css` et peuvent servir à nouveau

Après le tournoi, il reste à traiter séparément les deux pages `tournoi-k100.html` et `en/k100-tournament.html`, qui continueront d'annoncer des inscriptions ouvertes.
