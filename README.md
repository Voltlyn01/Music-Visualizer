# XY Music Visualizer (installable web app)
Plays audio files from your own device with constellation lyrics. No account, no server, nothing is uploaded. Works offline after the first visit.

## Host it free (needs HTTPS)
Upload this whole folder to a static host, e.g. GitHub Pages or Cloudflare Pages (check their current free terms). Open the https URL once while online.

## Install on Android
Open the URL in Chrome > menu > Install app (or tap the Install app button on the home screen). It then opens full screen like an app and works offline.

## Make a real APK (free)
Go to pwabuilder.com, enter your hosted URL, choose Android, and download the package. Follow its signing steps. You need the hosted HTTPS URL first.

## Notes
- Keep your music in your phone storage; the app asks you to pick files and never stores them.
- To update, change the files and bump `V` in service-worker.js (xy-v1 -> xy-v2).

## Security
No backend, keys, accounts or database. A Content-Security-Policy is set in index.html. `_headers` adds real HTTP headers on Cloudflare Pages/Netlify; GitHub Pages cannot set headers, so the meta policy is your protection there.
