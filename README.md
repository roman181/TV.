# KODi.Debil

Android-Dashboard und Profilpakete auf Basis des offiziellen Kodi-Projekts.

## Automatischer Android-Build

Der GitHub-Actions-Workflow **KODi.Debil Android – Dashboard + Profil** baut die Dashboard-APK und erstellt die Profilpakete.

- Bei Pushes auf `main` oder `master` wird der Build gestartet.
- Ein manueller Start ist unter **Actions → KODi.Debil Android – Dashboard + Profil → Run workflow** möglich.
- APK und Profilpakete werden als Workflow-Artefakt für 30 Tage bereitgestellt.
- Bei einem Versions-Tag im Format `v*` wird nach erfolgreichem Build automatisch ein GitHub Release mit APK, Profil-ZIPs und SHA-256-Prüfsummen veröffentlicht.

## Release erstellen

1. Öffne **Releases → Draft a new release** oder erstelle lokal einen Tag.
2. Verwende einen Versions-Tag, zum Beispiel `v1.0.1`.
3. Veröffentliche/pushe den Tag.
4. Öffne **Actions** und warte, bis der Android-Build erfolgreich abgeschlossen ist.
5. Das Release findest du anschließend unter **Releases**.

Beispiel für Git:

```bash
git tag v1.0.1
git push origin v1.0.1
```

## Release-Dateien

Ein erfolgreiches Tag-Build veröffentlicht:

- `KODi.Debil-Dashboard.apk`
- `KODi.Debil-Dashboard-debug.apk`
- `KODi.Debil-Profil.zip`
- `script.kodidebil.setup-1.0.0.zip`
- `SHA256SUMS.txt`

## Hinweise

- Der Workflow verwendet JDK 17, Gradle 8.13 und Android SDK / Build Tools 36.
- Die Dashboard-APK aus diesem Workflow ist eine Debug-signierte APK. Für eine Verteilung als reguläres Produktionsrelease sollte eine eigene Release-Signierung mit sicher hinterlegtem Keystore und GitHub Actions Secrets eingerichtet werden.
- Kodi ist ein eigenständiges Open-Source-Projekt. Marken- und Projektbestandteile bleiben ihren jeweiligen Rechteinhabern zugeordnet.

## Repository

https://github.com/roman181/TV.
