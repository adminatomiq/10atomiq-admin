# Atomiq Admin

Admin dashboard for the Atomiq student app. It's a single static page (`index.html`), so it runs on GitHub Pages with no build step.

## What's inside

| File | Purpose |
|---|---|
| `index.html` | The whole admin dashboard (Overview, Students, Exams, Messages, Rankings) |
| `404.html` | Copy of `index.html`, so a wrong URL still opens the dashboard |
| `robots.txt` | Asks search engines not to list this site |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

## Put it on GitHub Pages

1. Create a new repository on GitHub named `atomiq-admin` (Public, or Private if your plan includes Pages for private repos).
2. Upload all the files in this folder to the repository's main branch, including `.nojekyll`.
3. Go to **Settings → Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, then click **Save**.
4. After a minute or two the site is live at `https://<your-github-username>.github.io/atomiq-admin/`.

## One-time Firebase setup

1. In the Firebase console, open **Authentication → Settings → Authorized domains** and add `<your-github-username>.github.io`. Without this, Google sign-in fails with "unauthorized domain".
2. Make sure your admin Google account is listed in two places, with the same email:
   - `ADMIN_EMAILS` near the top of the script in `index.html`
   - the admin check in your `firestore.rules`

The Firestore rules are what actually protect your data. `ADMIN_EMAILS` only decides what the page shows, so anyone who isn't an admin in the rules can't read students or messages even if they open this page.

## Run it on your computer

Google sign-in doesn't work from a `file://` address, so serve the folder locally:

```
python -m http.server 8000
```

Then open http://localhost:8000. (`localhost` is allowed in Firebase by default.)

## Updating

Edit `index.html` and commit. If you change it, copy it over `404.html` too. GitHub Pages redeploys automatically.
