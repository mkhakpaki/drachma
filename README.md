# drachma (product site)

Product website for **Drachma**, a private, offline-first budget app for Android and iOS.
Served via Cloudflare Pages at <https://trydrachma.com/>. During the domain move it is also
still served via GitHub Pages at <https://mkhakpaki.github.io/drachma/>; both deploy from `main`.

Static HTML/CSS, no build step. The visual language mirrors the app's **Hearth** design
system: the Terracotta & Sage palette, Fraunces (display) + Inter (body) variable fonts,
Light / Dark / OLED themes, and reduced-motion support.

## Pages

- `index.html`: product page (subscriptions & installments, features, Free vs Plus, privacy stance, FAQ, store links)
- `privacy.html`: plain-language privacy policy (version 2026-10)
- `terms.html`: plain-language terms of service (version 2026-10)
- `support.html`: help topics + contact
- `get/index.html`: store smart-link: sniffs the UA, redirects to Play/App Store, forwards query params
- `404.html`
- `tr/`: Turkish versions of `index`, `privacy`, `terms` and `support` (same markup, translated)

## Notes

- Legal doc versions track `LegalDocuments.kt` in the app repo. Bump both together,
  since a version bump triggers in-app re-consent.
- Store badge links: the Google Play URL is final; the App Store id is the real one
  (6801626534, same constant as the app's `ExternalLinks.ios.kt`).
  These live in `index.html` and `tr/index.html` (hero + CTA) and `get/index.html`; update them all together.
- Fonts are the same variable TTFs the app ships (OFL-licensed Fraunces & Inter).
- Canonical / `og:` URLs point at `trydrachma.com` and are extensionless (`/privacy`, not
  `/privacy.html`): Cloudflare Pages 308-redirects `.html` URLs to the extensionless form.
- Keep every asset path relative while GitHub Pages is still live: the github.io copy sits
  under `/drachma/`, so root-absolute paths (`/style.css`) would break it there.

## Languages (English + Turkish)

- Every English page has a Turkish twin under `tr/` with the same structure. Change copy in
  both; the Turkish voice is informal "sen" and uses the app's own Turkish terms.
- Language choice: `?lang=en|tr` (what the header switcher and footer link use) is saved to
  `localStorage["drachma-lang"]`, then stripped from the URL. With no saved choice, an English
  page sends a device whose first language is Turkish to its `tr/` twin. Turkish pages only
  redirect on a saved "en", so shared `/tr/` links and crawlers stay put.
- Each pair declares `hreflang` alternates (`x-default` = English). `tr/index.html` uses
  `assets/og-image-tr.png`.
- `get/` and `404.html` are single pages that switch their few strings by the same rule.
- The Turkish privacy policy and terms are translations: they carry the same version and say
  the English text prevails. Bump both languages together.
