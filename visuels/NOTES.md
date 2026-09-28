# Visuels

Contrairement à Vague Zéro et Gravity Flip (projets Godot, génération d'écrans
possible en headless), Calculatrice H/M est une app Android native (Compose) : il n'y a
pas de moyen de produire des captures sans un appareil ou un émulateur réel.

## Captures d'écran (faites le 2026-09-28)

`capture-1.png` à `capture-3.png` : captures réelles prises sur l'Oppo A74 (version
2026.09.13.0) via `adb exec-out screencap`, recadrées en 1080×2160 (barre d'état et
barre de navigation retirées, ce qui ramène aussi le format à 2:1, le maximum accepté par
le Play Store). Copies réduites en 540×1080 WebP dans `../img/`, utilisées par
`index.html` (captures 1 et 3).

- capture-1 : `2H30M+45M` → 195 minutes, 3,25 heures, 3 heures 15
- capture-2 : `1H20M30S+45M15S` → 125.75 minutes, 2,10 heures, 2 heures 6
- capture-3 : `7H45M*5` → 2325 minutes, 38,75 heures, 38 heures 45

## Ce qu'il manque encore

| Fichier | Format | Usage |
|---|---|---|
| `icone_512.png` | 512×512 PNG | Icône de la fiche Play (obligatoire) |
| `banniere_1024x500.png` | 1024×500 PNG | Image mise en avant de la fiche |

## Refaire les captures

Téléphone connecté en débogage sans fil (`adb connect <ip>:<port>`), app ouverte avec
un calcul à l'écran :

```bash
adb exec-out screencap -p > capture.png
```

Puis recadrer en 1080×2160 (retirer les 88 px du haut et les 152 px du bas sur l'A74).
