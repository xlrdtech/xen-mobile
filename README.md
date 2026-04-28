# Xen Browser Mobile

Mobile-first PWA edition of Xen Browser, hosted at https://web.xlrd.org.

Static site → GitHub Pages → CNAME `web.xlrd.org`.

Origin canon: `~/.claude/projects/-Users-qi-XenV40/memory/canon_xen_browser_mobile_web.md`.

## Files
- `index.html` — single-page Xen Browser shell (tabs, URL bar, voice mic, omninbox, PIN gate)
- `manifest.webmanifest` — PWA manifest
- `sw.js` — service worker (offline + cache)
- `CNAME` — GitHub Pages custom domain

## Backend
Talks to omnimind via `https://api.xlrd.org` (Cloudflare tunnel → localhost:4441).

Endpoints used:
- `POST /api/qi-verify` — username + PIN gate
- `POST /api/web-chat/reply` — push voice/text into firehose
- `GET  /api/web-chat/poll?sid=…` — pull inbound replies for TTS
- `/unified-log.html?sid=…` — embedded omninbox

## Deploy
1. `gh repo create xlrdtech/xen-mobile --public --source . --push`
2. Settings → Pages → Deploy from branch `main`
3. Cloudflare DNS for `web.xlrd.org` → CNAME `xlrdtech.github.io` (proxy off so cert provisions)
