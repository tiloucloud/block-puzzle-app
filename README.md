# Block Puzzle — Android App (Capacitor)

This folder contains a complete Android app project, built on top of your
Block Puzzle game (HTML/JS). It already has the AdMob plugin wired in, and
is currently using Google's **official public test Ad IDs** so you can try
everything out before you have your own AdMob account approved.

## 1) What to do before building the app

### a) Change the package name (appId)
Open `capacitor.config.json` and change:
```
"appId": "com.yourname.blockpuzzle"
```
to your own real package name, e.g. `com.yourcompany.blockpuzzle`
(it must be unique on the Play Store, and **cannot be changed after you
publish**, so pick it carefully).

### b) Create an AdMob account (if you haven't yet)
1. Go to https://admob.google.com and sign up with your Google account
2. Click "Add app" → choose Android → name it (e.g. Block Puzzle)
3. You'll get an **App ID** (looks like: `ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY`)
4. Create 2 Ad Units: one "Banner" and one "Interstitial" — each will have
   its own ID

### c) Replace the test IDs with your real ones
Once you have your own IDs, update them in two places:

**1. `android/app/src/main/AndroidManifest.xml`** (the App ID):
```xml
<meta-data
    android:name="com.google.android.gms.ads.APPLICATION_ID"
    android:value="ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY"/>
```

**2. `www/index.html`** (the Ad Unit IDs, near the top of the script):
```js
const ADMOB_BANNER_ID = 'ca-app-pub-XXXXXXXXXXXXXXXX/AAAAAAAAAA';
const ADMOB_INTERSTITIAL_ID = 'ca-app-pub-XXXXXXXXXXXXXXXX/BBBBBBBBBB';
```

**IMPORTANT:** Keep the test IDs in place until you're confident the app
works correctly. If you switch to production IDs before the app is
actually published, Google may flag or suspend your AdMob account for
invalid traffic. Only switch to production IDs once the app is live on
the Play Store.

### d) App icon
The icon has already been added to `android/app/src/main/res/mipmap-*/`
at all required densities (including the adaptive icon foreground/background
for Android 8+). No action needed here unless you want to change it later.

## 2) How to build the APK/AAB

This step requires **Android Studio** (it can't be done in this
environment since there's no Android SDK here):

1. Send this whole folder to your computer (or push it to a Git repo and
   clone it there)
2. Open Android Studio → "Open" → select the `android/` folder
3. Let Gradle sync and download dependencies (needs internet)
4. From the menu: **Build → Generate Signed Bundle / APK**
   - Choose **Android App Bundle (.aab)** — this is what the Play Store
     requires now
   - Create a new **keystore** (save it somewhere safe — if you lose it,
     you won't be able to publish updates to this app ever again!)
5. Once built, you'll get an `.aab` file ready to upload

## 3) Publishing on the Play Store

1. Go to https://play.google.com/console (there's a one-time $25 fee)
2. Click "Create app" → give it a name, pick a category (Games > Puzzle)
3. Fill out "App content" (privacy policy URL, content rating,
   target audience, data safety form)
4. Add screenshots (at least 2), a feature graphic (1024x500), and the icon
5. Upload the `.aab` file under the "Production" track (or start with
   "Internal testing" first to try it out)
6. Submit for review (usually takes 1–7 days)

## 4) Important tips

- Start with **Internal/Closed testing** before going to Production, to
  make sure the ads work correctly and there are no crashes
- You need a live **Privacy Policy** URL (you can generate one for free
  at https://app-privacy-policy-generator.firebaseapp.com), since AdMob
  collects user data
- A new AdMob account can take a few days to get verified — be patient

---
If you run into any issue in Android Studio or during the build process,
just let me know and we'll go through it together.
