# Our IDFA 2026

A shared plan for who's seeing which IDFA films (12–22 Nov 2026). Anyone with the link and the group password can add screenings and people, and mark "thinking" or "bought".

The page is hosted on GitHub Pages. The plan itself is saved in a free Firebase (Google) database.

## 1. Create the database (about 5 minutes)

1. Go to https://console.firebase.google.com and sign in with your Google account.
2. **Create a project**. Any name works, e.g. `our-idfa`. You can turn Google Analytics off.
3. In the left menu open **Build → Firestore Database → Create database**.
   - Location: `eur3 (europe-west)` or any EU region.
   - Start in **production mode** (the rules below replace the defaults).
4. Open the **Rules** tab, delete what's there, paste the contents of `firestore.rules`, and click **Publish**.
5. Go to **Project settings** (gear icon) → **General** → **Your apps** → click the **</>** (Web) icon.
   Register an app (any nickname, no hosting needed). Firebase shows a `firebaseConfig` block.
6. Open `index.html`, search for `FIREBASE_CONFIG`, and replace the `PASTE_…` values with yours.
7. Open **Build → Authentication → Get started**, then **Sign-in method → Email/Password → Enable** (leave
   "Email link" off) and save.
8. In **Authentication → Users → Add user**, enter the email `plan@idfaplanner.firebaseapp.com` and the group
   password. This is the one shared account everyone signs in to; the page only asks for its password.
   The email must match `SHARED_EMAIL` in `index.html` and the email in `firestore.rules`.
9. In **Authentication → Settings → User actions**, untick **Enable create (sign-up)** and save, so nobody
   can make extra accounts.

The config values are meant to be public; the rules and the password are what protect the database.
To change the password later, open the user in **Authentication → Users** and reset it there. Devices
that are already signed in stay signed in until someone clicks **Lock this device** at the bottom of the page.

## 2. Put it on GitHub Pages

1. Create a new repository on GitHub, e.g. `our-idfa`.
2. Upload `index.html` (and this README and `firestore.rules` if you like) to the repository root.
3. In the repository go to **Settings → Pages**. Under **Build and deployment** pick
   **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. After a minute the site is live at `https://<your-username>.github.io/our-idfa/`. Share that link.

## Good to know

- Anyone who has the password can edit or delete anything, so share it only with your group.
- The page itself (code, no plan data) is public on GitHub; the plan is only readable after signing in.
- Firebase's free tier is far more than a small group will use; no card is needed.
- The `noindex` tag keeps search engines from listing the page.
