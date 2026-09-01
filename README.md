# cahier-de-revisions

Application de révision en français, en une seule page HTML, sans dépendance ni serveur.
Deux exercices :

1. **Dictée** — la phrase est lue à voix haute par la synthèse vocale du navigateur
   (voix `fr-FR`, vitesse normale ou ralentie, réécoute illimitée). L'élève tape la
   phrase, puis la correction compare mot à mot et affiche, au-dessus de chaque erreur,
   le mot attendu. Quatre niveaux (CE1, CE2, CM1, CM2), séries de 5 phrases, note sur 20,
   relevé de fin de série et une astuce de grammaire par phrase.
2. **Tables de multiplication** — choix des tables (1 à 12), des multiplicateurs
   (jusqu'à 10 ou 12) et de la longueur de la série (10, 20 ou 30 calculs). Chrono,
   série sans faute, record enregistré par configuration, bilan avec la liste des
   calculs ratés et un bouton pour ne rejouer que ceux-là. Table de Pythagore en annexe.

Le prénom, le niveau, les réglages et les records sont conservés dans le navigateur
(`localStorage`). Aucune donnée ne quitte le poste.

## Consulter la page

- **En local** : cloner le dépôt et ouvrir `index.html` dans Chrome
  (`file:///chemin/vers/cahier-de-revisions/index.html`).
- **En ligne** : activer GitHub Pages (Settings → Pages → Deploy from a branch,
  branche `main`, dossier `/root`). L'adresse sera alors
  `https://geoffroy-b-d-c.github.io/cahier-de-revisions/`.

Si aucune voix française n'est installée sur le poste, la dictée reste utilisable :
le bouton « Montrer la phrase » la transforme en exercice de copie, et la correction
fonctionne à l'identique.
