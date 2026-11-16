# 729

A 2048-style puzzle game where tiles grow through intermediate blocks before reaching the next power. In base 3, two 3s make a 6 domino, and two 6s make a 9. Slam one block into two matching ones at once for a triple. Reach 729 to win.

Game modes:

- **Classic**: powers of 3 on 5×5, win at 729
- **2048**: the original, powers of 2 on 4×4
- **4's**: powers of 4 on 7×7, win at 1024
- **Custom**: pick the base (2–6), grid (4×4 to 8×8) and winning tile

Each mode keeps its own game in progress and best score. In base 4 and up, long blocks bend to fit when a straight one has no room.

## Install on Android

1. Open the [latest release](../../releases/tag/latest) on your phone and download `729.apk`.
2. Open the downloaded file. If Android asks, allow your browser to install unknown apps.
3. Later builds install as updates over the old one, so your saved game and best scores are kept.

## How it's built

- The game is a single offline page: `app/src/main/assets/index.html`.
- `app/` is a small Android app that shows that page in a full-screen WebView, with no internet permission.
- Every push to `main` runs the **Build APK** workflow (`.github/workflows/build-apk.yml`). It uploads the APK as a workflow artifact and replaces the `latest` release.
- To build locally, open the project in Android Studio, or run `./gradlew assembleRelease` with JDK 17 and the Android SDK installed.

The APK is signed with `app/sideload.keystore`, a key kept in the repo on purpose so every build can update the last one. It's fine for sideloading. Use a private key if you ever publish to the Play Store.
