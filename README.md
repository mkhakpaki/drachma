# drachma (product site)

Product website for **Drachma** — a warm, offline-first budget app for Android and iOS.
Served via GitHub Pages at <https://mkhakpaki.github.io/drachma/>.

Static HTML/CSS, no build step. The visual language mirrors the app's **Hearth** design
system: the Terracotta & Sage palette, Fraunces (display) + Inter (body) variable fonts,
Light / Dark / OLED themes, and reduced-motion support.

## Pages

- `index.html` — product page (features, privacy stance, FAQ, store links)
- `privacy.html` — plain-language privacy policy (version 2026-07)
- `terms.html` — plain-language terms of service (version 2026-07)
- `support.html` — help topics + contact
- `404.html`

## Notes

- Legal doc versions track `LegalDocuments.kt` in the app repo — bump both together,
  since a version bump triggers in-app re-consent.
- Store badge links: the Google Play URL is final; the App Store id is the real one
  (6801626534, same constant as the app's `ExternalLinks.ios.kt`).
- Fonts are the same variable TTFs the app ships (OFL-licensed Fraunces & Inter).
