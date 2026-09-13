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
- Sections: Nav, Hero, About, Experience, Skills, Education, Contact, Footer.
- The headshot is a base64 `data:` URI (~92KB) embedded in the HTML, **byte-identical to the
  copy in the hub repo**. Changing the photo means changing both files.
- Design: `DM Serif Display` + `DM Sans`, green `#3B6D11`, ground `#fafaf8`. Light only.
  The hub uses the same tokens on purpose — keep them in sync.

## Verifying a deploy

`/pages/builds/latest` reports a stale commit sha. Check the bytes instead:

```
curl -sS -o /tmp/live.html "https://resume.eriksheridan.com/?cb=$RANDOM"; diff /tmp/live.html index.html
```
