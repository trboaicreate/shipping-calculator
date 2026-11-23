# Shipping Manager Curaçao — free APK build via GitHub Actions

This is Android source code, **not yet a compiled APK**. The workflow in `.github/workflows/build-apk.yml` builds an unsigned-for-release, debug-signed APK that can be installed on your own Android device.

## Android-only setup

1. Create a free GitHub account at https://github.com and a new **private** repository, e.g. `shipping-manager-curacao` (no README).
2. Download this ZIP and extract it using Android Files or another unzip app.
3. In Chrome, open your repository on GitHub, turn on **Desktop site** if necessary, and use **Add file → Upload files**. Upload the extracted project files **with their directory structure**. GitHub's uploader may not reliably upload folders on mobile. If that happens, use the `github.dev` web editor (press `.` on your repository in desktop mode), create the same folders, and upload files there; do not upload the ZIP as a single file.
4. Verify the repository has `settings.gradle`, `app/build.gradle`, and `.github/workflows/build-apk.yml` in the correct locations. Commit to the `main` branch.
5. Open **Actions → Build Android APK → Run workflow** (or open the build triggered by your commit).
6. Wait for a green check, open that workflow run, and download the **ShippingManagerCuracao-APK** artifact. Unzip it to find `app-debug.apk`.
7. Open `app-debug.apk` on your Android phone. If Android asks, permit installation from the app you used to open the file. Only install APKs built from your own repository.

**Important:** No Google Play registration or Android Studio required. GitHub Actions usage is subject to GitHub's free-tier limits. GitHub-hosted runners may change their available Android SDK; this workflow installs Android 35 explicitly.

**Limitations:** This is a WebView wrapper of the local HTML app. Orders remain local to each device; AI scanning needs a separate deployed backend. Browser order history does not migrate automatically. Test PDF/PNG share, invoice saving, and file uploads on your device. For distribution to customers, a properly signed release build and updated Android target SDK/security review would be needed.

## Payments update
The Payments tab tracks partial payments, outstanding balances, payment history and WhatsApp reminders. Existing local paid/unpaid orders are migrated on first open. Data remains local to the app installation.
