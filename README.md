# Lakas

A free recomp tracker for Android: Filipino food logging, a home barbell
program with progression, and an adaptive calorie estimate. No account,
no ads, no paywall. Your data stays on your phone.

**App:** https://emski-glitch.github.io/lakas/

## Install on Android

**Option 1 – from Chrome (recommended, works offline)**
1. Open the app link above in Chrome.
2. Tap ⋮ → **Install app** (or **Add to Home screen**).

**Option 2 – APK file**
1. Go to [Releases](https://github.com/Emski-glitch/lakas/releases/latest) on your phone.
2. Download **Lakas.apk** and open it. Allow installs from that source if Android asks.

Both load the app from the website, so you install once and updates arrive on their own.

## AI food logging (optional)

Snap your plate (Food → + Add → Photo) or describe a meal in Taglish, and the AI lists each
food with an estimated weight for you to review. It uses Google Gemini with your own free key:

1. Get a key at https://aistudio.google.com/apikey.
2. Paste it in **More → AI food logging → Save and test**.

The key stays on your phone and is not included in backups. On Google's free tier, Google may
use what you send to improve its products. Weights from photos are rough, so check portions.

## How updates work

1. A change is pushed to `main`.
2. GitHub Pages republishes the site in about a minute.
3. Next time Lakas opens, a green **Update ready** pill appears. Tap it to reload.
   **More → App version → What's new** lists the changes.

The APK only needs rebuilding when the app name, icon or the `apk/` wrapper
changes. That happens automatically on push, or from **Actions → Build Android APK → Run workflow**.

## Release checklist

1. Bump `APP_VERSION` in `index.html` **and** `VERSION` in `sw.js` (same number).
2. Add an entry at the top of `WHATS_NEW` in `index.html`.
3. If stored data changes shape, bump `DATA_VERSION` and add a step to `migrate()`,
   so old logs convert instead of breaking.
4. Commit and push to `main`.

## Keeping your data safe

- Data lives in the browser storage for `emski-glitch.github.io/lakas`. Don't move the site
  to a different address, or the app starts empty.
- Before each update applies, the app keeps a copy of your previous data on the phone.
- Use **More → Your data → Save backup file** now and then (Google Drive works).
- Uninstalling the APK or clearing Chrome's site data erases your logs. Back up first.

## Reporting bugs

Open an [issue](https://github.com/Emski-glitch/lakas/issues/new) with a screenshot and what you tapped.

## Notes

- `apk/debug.keystore` is a throwaway debug signing key, kept in the repo so every APK build
  installs over the last one. It's fine for a personal app. Use a private key stored as a GitHub
  secret before publishing to the Play Store.
- Food values are approximate home-style portions.
