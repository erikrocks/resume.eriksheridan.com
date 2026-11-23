# CLAUDE.md — resume.eriksheridan.com

Erik Sheridan's resume. One self-contained `index.html`, GitHub Pages, push to `main` to
redeploy. Custom domain via the `CNAME` file; certificate approved, Enforce HTTPS on.

**This is one of four sites.** The full architecture — all four addresses, the DNS setup,
the GitHub Pages certificate trap, and the shared design system — is documented in the hub
repo: `erikrocks/eriksheridan.com` → `CLAUDE.md`. **Read that first**; don't rediscover it.

Erik is not an engineer. Handle setup for him and explain by consequence, not mechanism.

## Specific to this page

- It used to live at the apex. It moved here in September 2026 when `eriksheridan.com`
  became a project menu.
- **The nav name in the top-left links back to `https://eriksheridan.com`** — that's the
  only way back to the hub. Don't remove it.
- Sections: Nav, Hero, About, Experience, Education, Contact, Footer.
- **The Skills section was removed on 4 Nov 2026** at Erik's request — the section, its
  nav link, and the `.skills-*` / `.pill` CSS all went. Don't reintroduce it unless he
  asks; the pill styling was only ever used there.
- The headshot is `headshot.jpg`, a real 400x400 file in the repo root (it was an inlined
  base64 blob until 4 Nov 2026 — extracting it took the page from 111KB to 20KB). The same
  file exists in the hub repo; changing the photo means replacing it in both. **Don't
  inline it again.**
- `favicon.svg` and Open Graph / Twitter card tags were added 4 Nov 2026, same as the hub.
  `og:url` and `og:image` must stay absolute URLs or previews break.
- **`.fade-up` starts at `opacity: 0`.** The reduced-motion block therefore forces
  `.fade-up { opacity: 1; animation: none; }` — disabling the animation without that leaves
  the entire hero invisible for anyone with reduce-motion on. Don't simplify that rule.
- Design: `DM Serif Display` + `DM Sans`, green `#3B6D11`, ground `#fafaf8`. Light only.
  The hub uses the same tokens on purpose — keep them in sync.

## Verifying a deploy

`/pages/builds/latest` reports a stale commit sha. Check the bytes instead:

```
curl -sS -o /tmp/live.html "https://resume.eriksheridan.com/?cb=$RANDOM"; diff /tmp/live.html index.html
```

## Analytics

Cloudflare Web Analytics, added 22 Nov 2026 at Erik's request. It's cookie-free and has no consent banner. A one-line
`static.cloudflareinsights.com/beacon.min.js` snippet sits just before `</body>`, and the site is set
to "JS snippet installation" in Cloudflare (not automatic injection). eriksheridan.com and games.html
share one site token; resume.eriksheridan.com has its own. Stats are in the Cloudflare dashboard →
Web Analytics. **Never add it to bubble. or kudr.eriksheridan.com:** their privacy policies promise
"no analytics or tracking tools", and the same files ship in the kids' apps.
