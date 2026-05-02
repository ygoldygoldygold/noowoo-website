# noowoo-website

Static website at <https://noowoo.app/>. Three pages: landing, privacy policy, Terms of Service. Hosted free on Cloudflare Pages, auto-deployed on every push to `main`.

## Files

- `index.html` — landing page (`/`)
- `privacy.html` — privacy policy (served at `/privacy`)
- `terms.html` — Terms of Service (served at `/terms`)
- `style.css` — shared styles
- `_redirects` — Cloudflare Pages clean-URL rules
- `assets/icon.png` — copy of NooWoo app icon

## Deploying

Push to `main`. Cloudflare Pages auto-deploys in ~30 seconds. Watch the deploy at: <https://dash.cloudflare.com> → Workers & Pages → noowoo-website → Deployments.

## Updating legal text

Source of truth is the spec at `C:\ClaudeProj\NooWoo\Specs\2026-05-02-web-presence-and-legal-design.md`. To update:

1. Edit the relevant section (Privacy Policy or Terms of Service) in the spec
2. Bump the "Last updated" date at the top of the page in both spec and HTML
3. Re-derive the HTML changes by hand (the spec is markdown; HTML conversion is mechanical: `**bold**` → `<strong>`, `[text](url)` → `<a href="url">text</a>`, `### N. Title` → `<h2>N. Title</h2>`)
4. Commit with a message like `update privacy section X`
5. Push

## Updating the icon

If the app icon at `C:\ClaudeProj\NooWoo\assets\icon.png` is updated:

```powershell
Copy-Item -Force -Path "C:\ClaudeProj\NooWoo\assets\icon.png" -Destination "C:\ClaudeProj\noowoo-website\assets\icon.png"
```

Commit and push.

## Custom domain

`noowoo.app` (root) and `www.noowoo.app` are configured in the Cloudflare Pages project as custom domains. DNS records live in the same Cloudflare zone as Email Routing (managed under the same Cloudflare account).
