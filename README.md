# EnglishTutorApp Advanced (Compose)

Interactive English learning app with:
- 12 levels, flashcards with TTS, quizzes (MCQ)
- Progress saved via DataStore, Stats screen
- 100% offline (local assets)

## Build APK in the cloud (GitHub Actions)
Create `.github/workflows/build.yml` with:
```yaml
name: Android APK (Debug)
on: [push, workflow_dispatch]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-java@v4
        with:
          distribution: 'temurin'
          java-version: '17'
      - uses: android-actions/setup-android@v3
      - uses: gradle/gradle-build-action@v3
        with:
          arguments: |
            wrapper
            assembleDebug
      - uses: actions/upload-artifact@v4
        with:
          name: app-debug.apk
          path: app/build/outputs/apk/debug/app-debug.apk
```
APK appears in the run **Artifacts** as `app-debug.apk`.

## What’s new
- Arabic UI strings
- Daily streak + XP + badges
- XP rewards: TTS(+2), flip/next(+1), quiz correct(+5), quiz finish(+10)
- Richer lessons: 10 items/level
