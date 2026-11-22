# AGORA — Physique-Chimie (5 semaines)

## Contenu
- `docs/index.html` : site GitHub Pages interactif, correction immédiate et téléchargement du rapport.
- `docs/questions.json` : 200 QCM (40 par semaine, 5 propositions par question).
- `docs/config.js` : adresse du serveur de collecte.
- `apps-script/Code.gs` : programmation des envois et réception des rapports.

## Dates
24 novembre, 1er, 8, 15 et 22 décembre 2026. Envoi visé : 17 h (heure de Paris). Google Apps Script ne garantit pas l'exactitude à la minute près.

## Étape 1 : GitHub Pages
1. Créez un dépôt GitHub, par exemple `agora-physique`.
2. Ajoutez les fichiers de `docs/` à la racine du dépôt, **ou** gardez le dossier `docs/` et choisissez `/docs` comme source Pages.
3. GitHub > Settings > Pages > Deploy from a branch > main > `/docs` > Save.
4. Notez l'adresse publiée : `https://VOTRE_COMPTE.github.io/agora-physique/`.
5. Testez la page en ouvrant `?week=1`.

## Étape 2 : Apps Script
1. Ouvrez script.google.com et créez un projet.
2. Remplacez le contenu de `Code.gs` par celui du fichier fourni.
3. Dans Project Settings, définissez le fuseau horaire `Europe/Paris` et ajoutez les propriétés de script :
   - `STUDENT_EMAIL` : adresse de Cyril (destinataire des liens hebdomadaires).
   - `PARENT_EMAIL` : votre adresse (destinataire des rapports).
   - `GITHUB_PAGES_BASE_URL` : URL GitHub Pages, terminée par `/`.
   - `SPREADSHEET_ID` : facultatif, créé automatiquement par `initialiser()`.
4. Exécutez une fois `initialiser()` et autorisez Sheets et Mail.
5. Exécutez une fois `installerDeclencheur()` et autorisez les déclencheurs.
6. Déployez > Nouveau déploiement > Application Web > Exécuter en tant que **moi** > Accès **tout le monde**. Copiez l'URL `/exec`.
7. Collez cette URL dans `docs/config.js`, entre les apostrophes, puis republiez le fichier sur GitHub.
8. Faites un test complet avant le 24 novembre : ouvrez le questionnaire, répondez aux 40 questions, envoyez le rapport et vérifiez Google Sheets + la boîte mail du parent.

## Important
- GitHub Pages est public : **ne mettez pas d'adresse e-mail personnelle, de jeton ni de mot de passe dans le site**.
- Les questions et leurs corrections sont accessibles dans `questions.json` : il s'agit d'un outil de révision, pas d'une évaluation sécurisée.
- Le formulaire public de réception ne vérifie pas l'identité de l'expéditeur et peut recevoir des soumissions non authentifiées. Ne l'utilisez pas pour des données sensibles ni comme registre officiel de notes.
- L'interface confirme seulement la **soumission** du rapport, pas sa réception effective : contrôlez la feuille ou l'e-mail. Si le rapport n'arrive pas, consultez les exécutions Apps Script.
- Google Apps Script peut exécuter les déclencheurs autour de 17 h, sans garantie à 17 h 00 exactes.
- Les 40 questions d'une semaine sont des variantes de 10 situations (ou de jeux de valeurs) : vérifiez leur adéquation au cours de Cyril avant diffusion. Les semaines 3 et 5 privilégient le calcul.
- Le site ne conserve pas automatiquement la progression si l'onglet est fermé ; l'élève doit terminer la séance avant de quitter.
- Les envois du mardi ne sont pas activés par la fourniture de cette archive : vous devez installer et autoriser Apps Script.
