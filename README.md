# JIM Fitness – iPhone app (Capacitor)

This wraps the JIM PWA (`www/`, same files as the `jim-fitness-pwa` repo) in a real iOS app. It talks to your Apps Script JSON API (Code.v2), so it needs that pasted and deployed with **Who has access: Anyone**, plus your token (see the PWA README).

## One-time Mac setup (free)
1. Install **Xcode** from the Mac App Store (big download, ~1 hr). Open it once, accept the license, let it install components.
2. Install Node.js LTS from https://nodejs.org (if you don't have it).
3. Install CocoaPods: in Terminal run `sudo gem install cocoapods` (or `brew install cocoapods`).
4. Xcode → Settings → Accounts → **+** → Apple ID → sign in with your normal Apple ID (free, no $99).

## Build and put it on your iPhone
```bash
git clone https://github.com/Jaylennunnally/Jim-fitness-ios.git
cd jim-fitness-ios
npm install
npx cap sync ios        # copies www/ into the app and runs pod install
npx cap open ios        # opens Xcode
```
In Xcode:
1. Click **App** (blue icon, top left) → target **App** → **Signing & Capabilities** → tick *Automatically manage signing* → Team: *(your name) (Personal Team)*.
2. If it complains about the Bundle Identifier, change `com.jaylennunnally.jim` to something unique like `com.jaylennunnally.jim2`.
3. Plug your iPhone in with a cable, unlock it, tap **Trust**. Pick your iPhone at the top of Xcode and press **▶ Run**.
4. On the iPhone: Settings → Privacy & Security → **Developer Mode** → On (restarts the phone). Then Settings → General → **VPN & Device Management** → your Apple ID → **Trust**.
5. Open JIM, paste your `/exec` link and token on the setup screen once.

## The catch with a free Apple ID
- The app **stops opening after 7 days**. Plug into the Mac, open Xcode, press ▶ Run again to renew (your login stays).
- Only on your own devices; max 3 apps.

## Later: $99/yr Apple Developer Program
Signing lasts a year, you get **TestFlight** so your brothers can install it from a link (each would need their own sheet + Apps Script + token), and you can submit to the App Store.

## Updating the app
Edit files in `www/` (or copy them from `jim-fitness-pwa`), then `npx cap sync ios` and ▶ Run.
