# Get a test APK in ~10 minutes (no Android Studio needed)

This project includes a GitHub Actions workflow that builds a debug APK for you
automatically, on GitHub's servers. You just need a free GitHub account.

## Steps

1. **Create a free GitHub account** at https://github.com/signup if you don't have one.

2. **Create a new repository:**
   - Go to https://github.com/new
   - Name it anything (e.g. `wonderland-waterpark-app`)
   - Keep it **Private** if you don't want the code public
   - Click **Create repository** (don't add a README — leave it empty)

3. **Upload this project to that repo.** Easiest way — on the new repo's page, click
   **"uploading an existing file"** and drag in everything from this `wonderland-app` folder.
   (If you're comfortable with git/command line instead: `git init`, `git add .`,
   `git commit -m "initial"`, `git remote add origin <your repo URL>`, `git push -u origin main`.)

4. **Watch it build:** Click the **Actions** tab at the top of your repo. You should see
   a workflow run start automatically (named "Build Android APK"). It takes about
   5–8 minutes. A green checkmark means it succeeded.

5. **Download the APK:** Click into that finished run, scroll to **Artifacts** at the
   bottom, and download **wonderland-waterpark-debug-apk**. It's a `.zip` — unzip it to
   get `app-debug.apk`.

6. **Install it on your Android phone:**
   - Transfer the APK to your phone (email it to yourself, use Google Drive, or a USB cable)
   - Tap the file on your phone — Android will ask permission to "install unknown apps"
     the first time; allow it for that app
   - It installs and opens like any normal app

That's it — you'll have the real app running on your phone, using the exact same code
that will later go to the Play Store.

## Notes
- This debug APK is **unsigned for release** — it's for testing only, not for the Play Store.
  When you're ready to submit to Play Store, follow the signing steps in the main `README.md`.
- If the Actions run fails, click into it to see the error — the most common cause is a typo
  introduced during upload. Feel free to paste the error back to me and I'll help fix it.
- Every time you push a change to the repo, this workflow re-runs and gives you a fresh APK.
