# Fiche Google Play — Calculatrice H/M

⚠️ **Différence importante avec les dossiers Play Store de Vague Zéro / Gravity Flip** :
cette application est **déjà publiée** (fiche existante « Hours minute sec. Calculator »,
`com.masociete.calc_heure`, dernière version en production : code 48 / nom 24.10.16.0 —
voir `app/build.gradle.kts` dans le dépôt de code
[olivier3dprint/CalculatriceHM](https://github.com/olivier3dprint/CalculatriceHM)).
Les textes ci-dessous sont un
**brouillon de travail**, à comparer avec ce qui est réellement en ligne dans la Play
Console avant de coller quoi que ce soit — contrairement aux deux autres projets, il
existe déjà une fiche à ne pas écraser par erreur.

---

## Nom de l'application

**Ne pas changer** : l'upload est refusé comme nouvelle application si le nom ne
correspond pas exactement à la fiche existante (voir commentaire dans
`app/build.gradle.kts`).

```
Hours minute sec. Calculator
```

## Description courte

*(80 caractères max — 72 utilisés, brouillon)*

```
Additionne des durées H/M/S, résultat en minutes et heures décimales.
```

## Description complète

*(4000 caractères max — environ 1050 utilisés, brouillon)*

```
Calculatrice H/M additionne, soustrait, multiplie et divise des durées exprimées en heures, minutes et secondes — pratique pour les feuilles de temps, la facturation à l'heure, ou simplement additionner des durées de trajet.

■ SAISIE NATURELLE
Tapez vos durées avec les suffixes H (heures), M (minutes) et S (secondes), combinez-les avec + - * / et des parenthèses : "5H25+2H30M+25M+5" ou "2H30M15S" sont compris directement, sans écran de saisie séparé pour chaque unité.

■ TROIS RÉSULTATS EN MÊME TEMPS
• Le total en minutes
• Le total en heures et minutes ("X heures Y")
• Le total en heures décimales (heures centièmes), le format attendu par la plupart des logiciels de paie et de facturation

■ SANS COMPTE, SANS CONNEXION
La calculatrice fonctionne entièrement hors ligne. Aucune inscription, aucune donnée personnelle demandée.

■ LÉGÈRE
Une seule fonction, un seul écran, aucun menu à apprendre.

L'application affiche une bannière publicitaire discrète (Google AdMob) pour rester gratuite. Aucun achat intégré.
```

---

## Fiche anglaise (English store listing)

Le nom existant sur la fiche étant déjà en anglais, il est probable qu'une fiche
anglaise existe déjà en Play Console. À vérifier (Accroître le nombre d'utilisateurs →
Traductions) avant de coller ce brouillon.

### Short description

*(80 characters max — 65 used, draft)*

```
Add H/M/S durations, get the result in minutes and decimal hours.
```

### Full description

```
Hours Minutes Calculator adds, subtracts, multiplies and divides durations expressed in hours, minutes and seconds — useful for timesheets, hourly billing, or simply adding up travel times.

■ NATURAL INPUT
Type your durations with the suffixes H (hours), M (minutes) and S (seconds), combine them with + - * / and parentheses: "5H25+2H30M+25M+5" or "2H30M15S" are understood directly, no separate entry screen per unit.

■ THREE RESULTS AT ONCE
• The total in minutes
• The total in hours and minutes ("X hours Y")
• The total in decimal hours, the format expected by most payroll and invoicing software

■ NO ACCOUNT, NO CONNECTION
The calculator works entirely offline. No sign-up, no personal data requested.

■ LIGHTWEIGHT
One function, one screen, nothing to learn.

The app shows a small banner ad (Google AdMob) to stay free. No in-app purchases.
```

---

## Classification et catégorie

| Champ | Valeur |
|---|---|
| Type | Application |
| Catégorie | Outils |
| Public cible | Tout public |
| Contient des annonces | **Oui** (bannière AdMob) |
| Achats via l'application | Non |

## Questionnaire de classification du contenu (IARC)

Aucun contenu sensible : pas de violence, contenu sexuel, langage grossier, drogues,
jeux d'argent, partage de position ni interaction entre utilisateurs (pas de compte, pas
de classement).

## Sécurité des données

| Donnée | Collectée | Partagée | Pourquoi |
|---|---|---|---|
| Identifiant publicitaire | Oui | Oui | Publicité (SDK AdMob) |

Aucune autre donnée n'est collectée : pas de compte, pas de position, pas de contacts,
pas de fichiers. Le SDK AdMob ajoute lui-même la permission
`com.google.android.gms.permission.AD_ID` au manifeste : Play rejette une application
qui la déclare sans déclarer l'usage correspondant ci-dessus.

Données chiffrées en transit ? **Oui** (AdMob en HTTPS). Le calcul lui-même ne fait
aucun appel réseau — seule la bannière publicitaire en fait.

---

## Identifiants AdMob — résolu le 29/08/2026

Le code utilisait encore les identifiants de **test** fournis par Google. Depuis la
version 51 / 2026.08.29.1, les vrais identifiants du compte AdMob sont en place :

- `AndroidManifest.xml` : `com.google.android.gms.ads.APPLICATION_ID` =
  `ca-app-pub-7930855717646694~3359334936` (App ID réel)
- `MainActivity.kt` (`AdBanner`) : `adUnitId` =
  `ca-app-pub-7930855717646694/4932271050` (bloc réel — repris du bloc déjà utilisé
  côté WinDev)

La bannière **bascule automatiquement** entre bloc de test et bloc réel selon
`BuildConfig.DEBUG` (`buildConfig = true` ajouté dans `app/build.gradle.kts`) : un
build de debug lancé depuis Android Studio continue de servir le bloc de test, un
build release (comme l'AAB envoyé à Play) sert le bloc réel. Plus besoin de basculer
la valeur à la main avant chaque envoi — l'oubli dans un sens coûtait un revenu nul,
l'oubli dans l'autre risquait une suspension du compte pour trafic non valide.

---

## Visuels

Dans `visuels/` — voir [visuels/NOTES.md](visuels/NOTES.md) : rien n'est encore produit
(icône 512×512, bannière 1024×500, captures d'écran), contrairement aux deux autres
projets où ces fichiers existaient déjà. Cette calculatrice tourne sur un vrai
appareil Android natif (pas Godot), donc pas de génération headless possible ; les
captures doivent venir d'un appareil ou de l'émulateur, via ADB (commande dans
`visuels/NOTES.md`).

## Site — page d'accueil et politique de confidentialité

`index.html` et `confidentialite.html`, sur le même principe bilingue que Vague Zéro /
Gravity Flip, vivent **à la racine** de ce dépôt (pas dans un sous-dossier
`site-github-pages/`) : GitHub Pages en mode `main` / `/ (root)` ne sert `index.html`
qu'à la racine, un sous-dossier y donnerait un 404 sur l'URL racine — erreur commise et
corrigée le 29/08/2026.

Contrairement à ce que suggérait la première version de cette fiche, ce contenu ne vit
**pas** dans le dépôt de code (`olivier3dprint/CalculatriceHM`) mais dans un dépôt
dédié — `olivier3dprint/Calculatrice` — exactement comme pour Gravity Flip.

GitHub Pages : Settings → Pages → Source = `main` / `/ (root)`. URL résultante :

```
https://olivier3dprint.github.io/Calculatrice/
https://olivier3dprint.github.io/Calculatrice/confidentialite.html
```

Cela suppose le dépôt public (GitHub Pages sur dépôt privé exige un plan payant) —
à vérifier dans Settings → General → Danger Zone / Visibility.

## Champs restant à remplir

- **Politique de confidentialité** (champ unique pour toute l'application, pas par
  langue — Surveiller et améliorer → Règles et programmes → Contenu de l'application →
  Règles de confidentialité) : coller l'URL `confidentialite.html` ci-dessus une fois
  Pages activé.
- **Site web** (facultatif) : `https://olivier3dprint.github.io/Calculatrice/`.
- **Adresse e-mail de contact** : `olivier3dprint@gmail.com`.
