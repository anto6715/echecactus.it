# echecactus.it

Website behind the QR codes on ECheCactus plant labels (`https://echecactus.it/p/<CODE>`). App repository and decisions: ECheCactus, ADR-0002.

## Files
- `index.html`: home page, Italian and English.
- `404.html`: GitHub Pages serves it for every path without a file, so it is the page a label link opens when the app isn't installed. It shows the code and explains the label. It never shows plant data: no server holds any.
- `.well-known/assetlinks.json`: Android App Links. It lists every app ID and signing-key fingerprint allowed to open `echecactus.it` links directly.
- `CNAME`: the custom domain for GitHub Pages.
- `.nojekyll`: publish files as they are. Without it, GitHub's Jekyll build would skip `.well-known/`.

## Publishing
GitHub Pages, deployed from the `main` branch, root folder. A push to `main` publishes within a minute or two.

## Rules for `assetlinks.json`
- Never remove the entry of an app version people have installed. Android rechecks the file when the app is installed or updated, and without its entry, labels open in the browser instead of the app.
- At release, add the fingerprint of Google Play's app signing key (Play Console → App integrity), next to the development key.
- Current entries: `io.github.anto6715.applinks_test`, the M0b App Links test app (debug key). It can be removed once the test is over.
