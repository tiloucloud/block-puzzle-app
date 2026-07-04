# How to Build the APK Without Android Studio (using GitHub)

You don't need to install anything on your computer. GitHub will build
the app for you in the cloud, for free. Here's exactly how:

## Step 1 — Create a GitHub account
Go to https://github.com and sign up (free) if you don't have an account.

## Step 2 — Create a new repository
1. Click the "+" icon (top right) → "New repository"
2. Name it something like `block-puzzle-app`
3. Set it to **Private** (recommended, so your project isn't public)
4. Click "Create repository"

## Step 3 — Upload your project
On the new repository page, click **"uploading an existing file"**
(a link shown on the empty repo page).

- Unzip `blockblast-app.zip` on your computer first
- Drag and drop **all the files and folders** into the GitHub upload
  page (yes, this works even for folders like `android/`, `www/`, and
  `.github/`)
- Scroll down, click "Commit changes"

## Step 4 — Watch it build
1. Click the **"Actions"** tab at the top of your repository
2. You'll see a workflow called **"Build Android APK"** running
   (it starts automatically after upload)
3. Wait about 3–5 minutes for it to finish (a green checkmark ✅ means
   success)

## Step 5 — Download your APK
1. Click on the finished workflow run
2. Scroll down to **"Artifacts"**
3. Click **"block-puzzle-debug-apk"** to download a `.zip` — inside
   it is your `app-debug.apk`

## Step 6 — Install it on your phone
1. Send the `.apk` file to your phone (WhatsApp to yourself, Google
   Drive, USB cable, email — whatever's easiest)
2. Open it on your phone. Android will probably warn "unknown app
   source" — that's normal for an app not yet on the Play Store.
   Tap "Install anyway" / allow the permission it asks for
3. Open the app — this is your real Android app, with real AdMob
   test ads showing (banner + interstitial)

## Notes
- This debug APK is for **testing only** — it's not signed for the
  Play Store. When you're ready to publish, we'll set up a signing
  key and build a **release AAB** instead (a few extra steps, but the
  same GitHub Actions approach works for that too — just ask).
- Every time you push a code change to GitHub, it automatically
  rebuilds — you never have to touch Android Studio.
- If the build fails (red ❌ instead of green ✅), click on it to see
  the error log, and send it to me — I'll help you fix it.
