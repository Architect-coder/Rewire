# Deploying REWIRE as an installable app

A PWA only becomes "installable" (add to home screen, works offline, launches
full-screen) once it's served over **https** — a file opened directly from
your downloads folder won't offer an install prompt. The fastest path, since
you already have this working for SFC, is GitHub Pages.

## Steps

1. Create a new GitHub repo (e.g. `rewire-app`), or a new folder in an
   existing Pages-enabled repo.
2. Upload these four files to the repo root, keeping the same names:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
3. In the repo settings, enable **GitHub Pages** for the branch/folder you
   uploaded to (same as you did for `sfc-financial-platform`).
4. Visit the resulting URL
   (`https://<your-username>.github.io/rewire-app/`) on your phone.
5. In Chrome (Android) you'll get an "Install app" / "Add to Home screen"
   prompt automatically, or you can trigger it from the browser menu. In
   Safari (iPhone) use Share → **Add to Home Screen** — iOS doesn't show an
   automatic install banner for PWAs, so this manual step is normal.

## What you get once installed

- App icon on your home screen, opens full-screen with no browser chrome
- Works offline after the first load (service worker caches the app shell)
- Data still lives in the browser's local storage on that device — export a
  backup from Settings before switching phones or clearing browser data

## What you don't get (and why)

- **Guaranteed background reminders.** The in-app reminder only fires while
  REWIRE is open or backgrounded in the browser process. iOS in particular
  suspends web apps aggressively when fully closed, and there's no way
  around that without a push-notification server, which is a separate
  backend project. If a reminder absolutely needs to fire on time, use your
  phone's native alarm/reminders app instead — I can set one directly if
  you want.
