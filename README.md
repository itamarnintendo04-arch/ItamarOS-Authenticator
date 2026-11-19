# ItamarOS Authenticator 1.2 🔐

ItamarOS's iPhone authenticator app. SwiftUI, 6-digit TOTP/HOTP codes, QR-code setup, Keychain storage, optional Face ID/passcode lock.

## Sign-in design

- Default: **Sign in with ItamarOS Authenticator**
- Sends an approval request to the user's linked iPhone
- Shows a 2-digit number that must match on the iPhone
- **Approve** or **Deny** (approval requires Face ID or device passcode)
- Secondary link: **Sign in with email instead** — 6-digit email code
- During the first launch of every ItamarOS app, recommend installing the Authenticator using **Install / Not Now**, once a signed release link is available

## Source package

The complete **v1.2 source ZIP** has been generated in the ChatGPT conversation. Extract it into this repository (including hidden `.github/` files), then run **Actions → Build iOS IPA (unsigned)**.

The package includes the iOS app, a Supabase Edge Function, SQL migration, a reusable web login, and first-launch install recommendation. **This GitHub repository is currently a starter: the source ZIP still needs to be imported.**

## Production checklist

1. Review the Edge Function and SQL migration against the ItamarOS Supabase project.
2. Deploy/test the broker before making it the default login method in existing apps.
3. Configure Apple Developer Push Notifications and APNs secrets server-side. No APNs key belongs in this repo.
4. Set a genuine App Store/TestFlight/signed installation link for the companion prompt.
5. Build a signed IPA and test on a real iPhone. The unsigned CI artifact is not directly installable.

Do not assert that automatic push sign-in works until these tests pass; an iPhone with the app closed cannot receive real push without APNs provisioning.

See `docs/AUTO_SIGN_IN.md` after importing the source ZIP.
