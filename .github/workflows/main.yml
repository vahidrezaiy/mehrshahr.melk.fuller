name: Build Android APK

on:
  push:
    branches:
      - main
      - master

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Java
        uses: actions/setup-java@v3
        with:
          distribution: temurin
          java-version: '17'

      - name: Setup Flutter
        uses: subosito/flutter-action@v3
        with:
          flutter-version: '3.22.0'

      - name: Enable Gradlew permission
        run: chmod +x android/gradlew || true

      - name: Get dependencies
        run: flutter pub get

      - name: Build release APK
        run: flutter build apk --release || flutter build apk

      - name: Upload APK artifact
        uses: actions/upload-artifact@v3
        with:
          name: MehrshahrMelk-release
          path: build/app/outputs/flutter-apk/app-release.apk
