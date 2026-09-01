# cahier-de-revisions

Application de révision de Bérénice (CM1-CM2). Une seule page HTML, aucune dépendance,
aucun serveur, rien qui sorte de l'appareil.

## Les trois exercices

Tous les trois marchent sur le même principe : **un item raté retourne dans la file
et revient plus loin ; la série ne se termine que lorsque tout a été réussi.**

1. **Mes mots** — les 41 mots de la fiche « Mots à apprendre » du jeudi 10 septembre 2026.
   L'app dit le mot à voix haute, l'élève l'écrit en entier (article compris), l'app
   compare lettre par lettre et montre où est la faute. Trois aides : réécouter plus
   lentement, voir le mot **découpé en syllabes**, ou afficher le mot quelques secondes.
2. **Mes tables** — tables de 2 à 10, × 1 à 10. Un calcul faux revient plus tard.
3. **et / est** — le « Revoir et / est » de la fiche, 8 phrases à trou avec le truc de
   substitution (*était* → est, *et puis* → et).

## Contrainte : iPad Air 1 sous iOS 12.5.8 (Safari 12)

La page est écrite pour ce navigateur précis. À ne pas casser lors d'une modification :

- pas de `clamp()`, `min()`, `max()` en CSS (Safari 13.1+) ;
- pas de `gap` en **flexbox** (Safari 14.1+) — le `gap` de **grid** est autorisé, doublé
  de `grid-gap` ; ailleurs, espacement par marges ;
- pas de `inset`, pas de `:is()`, pas de `?.` ni `??` en JavaScript ;
- `prefers-color-scheme` n'existe pas sur iOS 12 : le thème clair est le thème complet
  par défaut, et le bouton « Thème » du bas force clair ou sombre ;
- champs de saisie en 26 px minimum, pour que Safari ne zoome pas au focus ;
- `autocorrect="off"`, `autocapitalize="none"`, `spellcheck="false"` sur le champ des
  mots : sans cela le clavier iOS corrige les fautes à la place de l'élève ;
- clavier numérique via `type="tel"` + `pattern="[0-9]*"` (`inputmode` n'est pas suivi) ;
- une rangée de lettres accentuées (é è ê à â î ô û ç ï) évite l'appui long sur iPad ;
- la synthèse vocale iOS exige un appui pour démarrer : chaque lecture part d'un bouton.

## Mettre la page sur l'iPad

1. Fusionner cette branche dans `main`.
2. Settings → Pages → *Deploy from a branch*, branche `main`, dossier `/root`.
3. Ouvrir `https://geoffroy-b-d-c.github.io/cahier-de-revisions/` dans Safari sur l'iPad,
   puis Partager → **Sur l'écran d'accueil** : la page s'ouvre alors en plein écran,
   comme une application.

Sans réseau, l'autre solution est de copier `index.html` sur l'iPad (AirDrop, Fichiers)
et de l'ouvrir depuis l'app Fichiers.

## Ce qui est gardé en mémoire

Le prénom, le thème, les catégories et les tables choisies, les mots qui ont demandé
plusieurs essais et le résultat de la dernière série — dans le `localStorage` du
navigateur, sur l'appareil uniquement.
