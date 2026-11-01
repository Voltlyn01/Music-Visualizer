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

## Lyrics without a second upload
1. Lyrics you saved before load automatically (matched by file, then by artist + title).
2. Select the song and its .lrc file together in the same picker; they pair by file name.
3. Automatic and on by default (switch off in Settings > Find lyrics online). Sends only title, artist, album and length to lrclib.net (free, no key). Audio never leaves the device. Only time-synced lyrics are used.
4. Otherwise use the Lyrics button: paste, Stamp or Auto-time, Save. Saved lyrics are reused next time.
Tags are read from MP3 (ID3v2.3/2.4, ID3v1); other formats use the file name ("Artist - Title").

## Deploy on Vercel
Push these files to your repo and redeploy. vercel.json sets the security headers (it replaces _headers there). Bump `V` in service-worker.js so phones pick up the update.

## Roman letters for Indian-language lyrics
Lyrics in Devanagari (Hindi, Marathi, Nepali), Bengali/Assamese, Gurmukhi (Punjabi), Gujarati, Odia, Tamil, Telugu, Kannada and Malayalam are shown in English letters. This is transliteration (same words, same order), never translation. The `Aa` button or Settings > Roman letters switches back to the original script. Your saved lyrics always keep the original script. Rules are built in (no service, no cost) and are approximate: spelling follows common casual romanization and some words will differ from how you would write them. Urdu (Arabic script) is not converted and stays in the original script.
