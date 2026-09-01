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
- Store badge links: the Google Play URL is final; the App Store badge uses the full
  canonical listing URL (`/us/app/drachma-offline-budget-app/id6801626534`). The short
  `/app/id6801626534` form 301-redirects to it, picking the storefront by IP
  geolocation; linking the canonical URL directly skips that hop and the geo lookup.
  The `/us/` segment does not restrict anyone: on iOS the App Store app resolves the
  universal link against the signed-in account's storefront, and the listing is live in
  other storefronts (verified `/gb/` returns 200). Desktop web visitors outside the US
  do see the US page. Id 6801626534 is the same constant as the app's
  `ExternalLinks.ios.kt`.
- Fonts are the same variable TTFs the app ships (OFL-licensed Fraunces & Inter).
