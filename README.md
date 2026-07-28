# Wonderland Waterpark — Mobile App

A native Android & iOS app wrapper around **wonderlandwaterpark.in**, built with
[Capacitor](https://capacitorjs.com). The app is a real native project (not a browser bookmark) —
it has its own icon, splash screen, offline screen, and native back-button/gesture handling —
and it always shows your live website, so any updates you make to the site appear in the app
automatically with no app update required.

---

## 1. What's in this project

```
wonderland-app/
├── www/index.html          ← local "shell": splash screen, connectivity check, then loads your live site
├── capacitor.config.json   ← app ID, name, allowed domains, splash/status bar settings
├── android/                ← full native Android Studio project (Gradle)
├── ios/                    ← full native Xcode project
├── assets-src/              ← source icon & splash artwork (1024px icon, 2732px splash)
```

The site URL is set in `www/index.html`:
```js
var SITE_URL = "https://wonderlandwaterpark.in";
```
Change this one line any time you move domains — no store resubmission needed for that change alone.

---

## 2. Before you touch Xcode/Android Studio

You'll need:
- A Mac (for iOS builds — Xcode only runs on macOS; there's no way around this, even for me)
- [Xcode](https://apps.apple.com/us/app/xcode/id497799835) (free, Mac App Store) for iOS
- [Android Studio](https://developer.android.com/studio) (free, any OS) for Android
- [Node.js](https://nodejs.org) 18+ installed locally
- [CocoaPods](https://cocoapods.org) for iOS: `sudo gem install cocoapods`

Copy this whole `wonderland-app` folder to your machine, then:

```bash
cd wonderland-app
npm install
npx cap sync
```

---

## 3. Running/testing locally

**Android:**
```bash
npx cap open android
```
This opens Android Studio. Press the ▶ Run button with an emulator or a USB-connected phone
(with Developer Mode + USB debugging on) selected.

**iOS:**
```bash
cd ios/App && pod install && cd ../..
npx cap open ios
```
This opens Xcode. Select a Simulator or your connected iPhone, then press ▶ Run.
(First run on a physical iPhone: in Xcode, go to your project target → **Signing & Capabilities**
→ select your Apple ID team — see step 5.)

---

## 4. Before submitting: things to double check

- [ ] **App name & bundle ID** — currently `in.wonderlandwaterpark.app` / "Wonderland Waterpark".
      Change in `capacitor.config.json` (`appId`, `appName`) then re-run `npx cap sync` if you want something different. Bundle IDs can't be changed after your first store submission, so lock this in first.
- [ ] **Icon/splash** — I generated these from your logo's color palette. If you'd like your literal
      logo mark used instead of the wave/droplet icon I designed, tell me and I'll regenerate.
- [ ] **Privacy Policy URL** — both stores require one if the app touches network data (yours does).
      If you don't already have one on your site, I can draft one for you.
- [ ] **Test on a real device with airplane mode on** — confirm the offline screen appears and the
      "Retry" button works once you reconnect.
- [ ] **Test all links inside your site** (tel:, mailto:, external map links) open correctly.

---

## 5. Apple Developer & Google Play accounts (you said you don't have these yet)

### Apple Developer Program — $99/year
1. Go to https://developer.apple.com/programs/enroll/
2. Sign in with (or create) an Apple ID, enroll as **Individual** or **Organization**
   (Organization requires a D-U-N-S number — takes longer; Individual is faster to start with).
3. Pay the $99/yr fee. Approval usually takes 24–48 hours.
4. Once approved, in Xcode: **Xcode → Settings → Accounts** → sign in with that Apple ID.
   Xcode will handle certificates/provisioning automatically if you enable
   "Automatically manage signing" on the App target.

### Google Play Console — $25 one-time
1. Go to https://play.google.com/console/signup
2. Sign in with a Google account, pay the one-time $25 registration fee.
3. Verification (ID + sometimes a short video) can take a few hours to a few days for new accounts.
4. Once verified, click **Create app** and fill in the store listing (see below).

---

## 6. Building the release files

### Android — signed `.aab` for Play Store
1. In Android Studio: **Build → Generate Signed Bundle / APK → Android App Bundle**.
2. Create a new keystore (first time only) — **save this file and its passwords somewhere safe**;
   losing it means you can never update the app again under the same listing.
3. Choose **release** build variant, finish — this produces `app-release.aab`.

### iOS — `.ipa` for App Store
1. In Xcode: select **Any iOS Device (arm64)** as the run destination (not a simulator).
2. **Product → Archive**.
3. Once archived, click **Distribute App → App Store Connect → Upload**.
4. Xcode handles signing automatically if you enabled automatic signing in step 4.

---

## 7. Store listing basics you'll need ready

Both stores ask for the same core assets:
- App name, short description, full description
- Screenshots (phone-size at minimum; Android also wants a feature graphic 1024×500)
- Privacy policy URL
- Category (Travel & Local, or Lifestyle)
- Content rating questionnaire (straightforward for a waterpark site — no mature content)
- Contact email & support URL

I'm happy to draft the store description text, privacy policy, or screenshots copy for you — just ask.

---

## 8. What this app does automatically

- **Splash screen** while checking connectivity
- **Offline screen with Retry button** if there's no internet or the site can't be reached
- **Native Android back button** navigates the site's history before exiting the app
- **iOS swipe-from-edge** gesture navigates back, matching standard iOS apps
- **tel:/ mailto: links** on your site open the phone/email app natively (handled by Capacitor automatically)
- Any future updates to your live website appear in the app instantly — you only need a new store
  submission if you change the native shell itself (icon, name, permissions, etc.)

---

## Questions / next steps I can help with right now
- Draft your Play Store & App Store listing copy
- Draft a privacy policy page
- Swap in your actual logo mark as the app icon instead of the generated one
- Add native push notifications for ride/weather alerts (would need a backend piece)
