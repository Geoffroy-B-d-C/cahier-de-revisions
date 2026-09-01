# cahier-de-revisions

Cahier de révisions en une seule page HTML : aucune dépendance, aucun serveur,
rien qui sorte de l'appareil.

## Les trois exercices

Même principe partout : **un item raté retourne dans la file et revient trois
questions plus loin ; la série ne se termine que lorsque tout a été réussi.**

1. **Dictée de mots** — l'app dit le mot, l'élève l'écrit en entier avec son article.
   La correction compare **lettre par lettre** (plus longue sous-suite commune) et
   montre les lettres en trop barrées et les lettres oubliées soulignées. Aides :
   réécouter moins vite, voir le mot **découpé en syllabes**, ou l'afficher un moment.
2. **Tables de multiplication** — tables de 2 à 10, dix multiplicateurs chacune.
3. **et / est** — le « Revoir » de la fiche : 8 phrases à trou, avec le test de
   substitution (*était* → est, *et puis* → et) donné à chaque erreur.

## Les listes de mots

La liste livrée est celle de la fiche du jeudi 10 septembre 2026 (41 mots), avec
pour chaque mot son **découpage en syllabes** et sa **catégorie** (noms, adjectifs,
verbes, mots invariables), saisis à la main.

En bas de l'accueil, la zone « Listes de mots » permet d'en ajouter, d'en modifier
et d'en supprimer sans toucher au code : un mot par ligne, écrit exactement comme
sur la fiche. Ces listes sont enregistrées dans le `localStorage` et survivent à la
fermeture de la page.

Une liste ajoutée par ce formulaire n'a ni syllabes ni catégories : le bouton
« Syllabes » et les puces de catégorie disparaissent alors, plutôt que d'inventer
un découpage qui pourrait être faux. Pour une liste avec syllabes, il faut
l'ajouter dans `LISTE_FICHE` (ou une liste sœur) dans `index.html`.

**« Envoyer sur l'iPad »** fabrique un lien `…/#l=<listes en base64>` : ouvert sur
un autre appareil, il y ajoute les listes qui n'y sont pas déjà (il n'écrase rien).

## Contrainte : iPad Air 1 sous iOS 12.5.8 (Safari 12)

À ne pas casser lors d'une modification :

- pas de `clamp()`, `min()`, `max()` en CSS (Safari 13.1+) ;
- pas de `gap` en **flexbox** (Safari 14.1+) — le `gap` de **grid** est autorisé,
  doublé de `grid-gap` ; ailleurs, espacement par marges ;
- pas de `inset`, pas de `:is()`, pas de `?.` ni `??` en JavaScript ;
- champs de saisie à 24 px minimum, sinon Safari zoome au focus ;
- `autocorrect="off"`, `autocapitalize="none"`, `spellcheck="false"` sur le champ
  des mots : sans cela le clavier iOS corrige les fautes à la place de l'élève ;
- clavier numérique via `type="tel"` + `pattern="[0-9]*"` (`inputmode` non suivi) ;
- une rangée de lettres accentuées évite l'appui long sur iPad ;
- la synthèse vocale iOS exige un appui : chaque lecture part d'un bouton ;
- page volontairement mono-thème (c'est une feuille de cahier), d'autant que
  `prefers-color-scheme` n'existe pas sur iOS 12.

## Mettre la page sur l'iPad

GitHub Pages est actif sur `main` : <https://geoffroy-b-d-c.github.io/cahier-de-revisions/>

Sur l'iPad, ouvrir cette adresse dans Safari puis **Partager → Sur l'écran d'accueil** :
la page s'ouvre ensuite en plein écran, comme une application.
