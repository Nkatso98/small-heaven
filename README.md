# Small Heaven — Luxury Sensual Spa Website

This is a minimal, tasteful static site scaffold for Small Heaven, a sensual massage spa. It is intentionally non-explicit and focuses on luxury, discretion, and presence.

Quick start

1. Open `index.html` in your browser (double-click or use a dev server).

2. To test WhatsApp booking locally, use the `booking.html` page and click "Message on WhatsApp" (opens WhatsApp web or the app).

Deployment

- Host as a static site (Netlify, Vercel, GitHub Pages) or drop into any web host.

Deploying as a static site

- Netlify: Connect the repository, set the publish directory to the repository root (or the `small-heaven` folder if you place it inside a larger repo). `netlify.toml` is included.
- GitHub Pages: Push the `small-heaven` folder to a branch named `gh-pages` or put files in the repository root and enable Pages from `main`/`docs` as desired.

WordPress theme

- A minimal starter theme is included at `wp-theme/`. Copy the folder into `wp-content/themes/` on your WordPress install to test. It's a scaffold — you'll want to adapt templates and enqueue the static CSS if you want a pixel match.

Assets & visuals

- `assets/logo.svg` and `assets/hero-placeholder.svg` are included as placeholders. Replace with your photography and logo for a polished look.

Files

- `index.html`, `rituals.html`, `about.html`, `discretion.html`, `booking.html`
- `css/styles.css`

Local WordPress testing (quick)

1. Ensure Docker and Docker Compose are installed.
2. From the project root run the PowerShell helper:

```powershell
./scripts/setup-wp.ps1
```

3. Visit http://localhost:8000 to complete the WordPress installer.
4. After install, activate the theme at Appearance → Themes (the theme is copied as `hands-of-a-goddess`).

CI / Deployment

- GitHub Pages: a workflow is provided at `.github/workflows/deploy.yml` that publishes the repository root on push to `main` or `master`.
- Netlify: `netlify.toml` is included for direct deploys; set publish directory to repository root.

Firebase Hosting

- This project includes `firebase.json` and `.firebaserc` to help deploy the static frontend to Firebase Hosting.
- To deploy:

1. Install the Firebase CLI:

```bash
npm install -g firebase-tools
```

2. Login and initialize (if you haven't):

```bash
firebase login
firebase init hosting
```

When `firebase init` asks for the public directory, choose `.` (repository root) or `public` depending on your preference. The provided `firebase.json` is configured to publish the repo root but ignores WordPress/theme files.

3. To deploy:

```bash
firebase deploy --only hosting
```

Replace `your-firebase-project-id` in `.firebaserc` with your Firebase project id, or select the project during `firebase init`.

Automatic Firebase Deployment via GitHub Actions

A GitHub Actions workflow is included at `.github/workflows/firebase-deploy.yml`. To enable automatic deployment:

1. Set up your Firebase project and get a service account JSON key.
2. In your GitHub repository, add two secrets:
   - `FIREBASE_SERVICE_ACCOUNT`: Paste your Firebase service account JSON (from Firebase Console → Project Settings → Service Accounts).
   - Update the `projectId` in the workflow file to match your Firebase project id.
3. Push to `main` or `master` and the workflow will automatically deploy to Firebase Hosting.

Quick local Firebase deploy

Once Firebase CLI is installed (`firebase --version` should show the version):

```bash
firebase login
firebase deploy --only hosting
```

Next steps I can do for you

- Provide a quick demo video or screenshot
- Add custom animations and polish
- Help connect a custom domain to Firebase
- Set up Firestore for booking confirmations
