# ci_cd

A new Flutter project.

## GitHub Actions CI/CD

This project includes `.github/workflows/flutter-ci.yml`.

The workflow runs on every push, pull request, and manual dispatch. It checks
formatting, runs `flutter analyze`, runs `flutter test`, builds an Android debug
APK, and uploads the APK as a workflow artifact.

To test it on GitHub:

```sh
git init
git add .
git commit -m "Add Flutter CI workflow"
git branch -M main
git remote add origin https://github.com/<your-user>/<your-repo>.git
git push -u origin main
```

After pushing, open the repository on GitHub and go to the **Actions** tab.

## Android Release Deploy

This project also includes `.github/workflows/deploy.yaml`.

The deploy workflow builds a signed release APK and AAB. Manual runs upload the
files as workflow artifacts. Tag pushes such as `v1.0.0` also create a GitHub
Release with both files attached.

Add these GitHub repository secrets before running the deploy workflow:

```text
ANDROID_KEYSTORE_BASE64
ANDROID_KEYSTORE_PASSWORD
ANDROID_KEY_ALIAS
ANDROID_KEY_PASSWORD
```

Create the keystore secret from your local keystore:

```sh
base64 -i android/app/upload-keystore.jks | tr -d '\n' | pbcopy
```

Then paste the clipboard value into `ANDROID_KEYSTORE_BASE64`.

To create a GitHub Release:

```sh
git tag v1.0.0
git push origin v1.0.0
```

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
