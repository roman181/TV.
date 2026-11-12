# Android SDK / Build-Umgebung

## GitHub Actions (empfohlen, ohne PC)

Die Workflows installieren die Build-Umgebung automatisch:

- Eclipse Temurin JDK 17
- Android command-line tools über `android-actions/setup-android@v4`
- Android SDK Platform 36
- Android Build Tools 36.0.0
- Android Platform Tools (`adb`)
- Gradle 8.13

Android SDK-Lizenzen werden im Runner akzeptiert. Das SDK selbst wird nicht in Git eingecheckt: Es ist groß, plattformabhängig und wird vom Workflow reproduzierbar installiert.

## Lokal mit Android Studio

1. Android Studio installieren.
2. JDK 17 auswählen.
3. SDK Platform 36 und Build Tools 36.0.0 im SDK Manager installieren.
4. `local.properties.example` nach `local.properties` kopieren und `sdk.dir` anpassen.
5. Im Projektordner ausführen:

```bash
gradle --no-daemon :dashboard-app:assembleDebug
```

Die APK liegt danach unter `dashboard-app/build/outputs/apk/debug/`.

## APK-Signierung

Der CI-Build erzeugt eine debug-signierte APK für private Tests. Für eine öffentliche Play-Store-Veröffentlichung muss ein eigener Release-Keystore erstellt und sicher als GitHub Actions Secrets hinterlegt werden. Keystore-Dateien und Passwörter niemals ins Repository laden.
