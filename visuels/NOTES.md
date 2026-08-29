# Visuels — à produire

Contrairement à Vague Zéro et Gravity Flip (projets Godot, génération d'écrans
possible en headless), Calculatrice H/M est une app Android native (Compose) : il n'y a
pas de moyen de produire des captures sans un appareil ou un émulateur réel.

## Ce qu'il manque

| Fichier | Format | Usage |
|---|---|---|
| `icone_512.png` | 512×512 PNG | Icône de la fiche Play (obligatoire) |
| `banniere_1024x500.png` | 1024×500 PNG | Image mise en avant de la fiche |
| `capture-1.png` … | 1080×1920 ou 1080×2400 PNG (portrait — l'app est verrouillée en
portrait, voir `screenOrientation="portrait"` dans le manifeste) | Captures d'écran de
la fiche, deux minimum |

## Comment les produire

Appareil ou émulateur branché en débogage, avec l'app installée et une expression déjà
calculée à l'écran (ex. `2H30M+45M`) :

```bash
adb shell screencap -p /sdcard/capture.png
```

```bash
adb pull /sdcard/capture.png "D:/dev/CalculatriceHM/Play Store/visuels/capture-1.png"
```

Cette étape revient à Olivier — piloter un appareil réel pour capturer l'écran ne se
fait pas depuis Claude Code.

## Une fois produits

Copier `banniere_1024x500.png` et les captures dans
`site-github-pages/img/` et les référencer depuis `index.html` (actuellement une
maquette CSS tient lieu d'aperçu, en l'absence de vraies captures).
