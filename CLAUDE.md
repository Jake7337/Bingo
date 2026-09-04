# Free Apps That Help

## Project Info
- **Live URL:** https://freeapps.pages.dev  (Cloudflare Pages, project `freeapps`, `main` branch, repo root - `git push` auto-deploys in ~30s)
- **Old URL:** https://jake7337.github.io/Bingo/  (GitHub Pages, still live on purpose as a safety net for links already shared - Cloudflare only reads the repo, so both serve the same site)
- **Note:** Cloudflare serves extensionless URLs - `/about`, `/bingo/info`. The old `.html` forms 308-redirect, so existing links keep working. Every internal link in the site is relative, so nothing broke when the `/Bingo/` path segment went away.
- **GitHub:** https://github.com/Jake7337/Bingo  (repo name is still `Bingo`; URLs stay stable — don't rename without Jake asking)
- **Creator:** Jake — makes all art/ideas with AI tools; gives the code away to help others
- **The point:** free tools that actually help someone — a group raising money on bingo night, or a person needing to put something heavy down. "Maybe it saves one life." Keep the tone honest and unslick, never markety.

## Structure (site became a multi-app hub 2026-08-29)
Was a single bingo caller, then Jake's own landing page (July), now a hub of apps.

```
index.html            <- the hub ("Free apps that help") — front door, links each app
bingo/index.html      <- Bingo Caller app  (Jake's July "caller.html", SILENT edition)
bingo/info.html       <- Bingo Caller showcase  (Jake's July landing page, moved + relinked)
burn-book/index.html  <- Burn Book app  (mirrors C:\Users\jrsrl\OneDrive\Desktop\burnbook.html)
burn-book/info.html   <- Burn Book showcase
burn-book/cover.jpg   <- cover art (the app has its own embedded copy)
dinner/index.html     <- Just Pick Something app  (mirrors C:\Users\jrsrl\OneDrive\Desktop\Just_Pick_Something.html)
dinner/info.html      <- Just Pick Something showcase
og-preview.png        <- link-preview image for the bingo info page (abs URL in its meta)
og-hub.png            <- link-preview image for the hub  [STALE: names only 2 of the 3 apps]
burn-book/og-burn-book.png <- link-preview image for the burn book info page
dinner/og-dinner.png       <- link-preview image for the dinner info page
```

- Every app is ONE self-contained HTML file: embedded CSS/JS/assets, no build step, no dependencies, works offline.
- Hub cards: **Open** (new tab) · **Download** (`download` attr, forced filename) · **Info** (the showcase page).
- Adding an app = `app-name/index.html` (+ optional `info.html`) + an `<article class="card">` in `index.html` + a row in `README.md`.

### The hub (`index.html`)
- Theme-aware (light base; `prefers-color-scheme: dark` + `[data-theme]` token overrides).
- Fonts: Fraunces + IBM Plex Sans via Google Fonts (the only page here that uses a CDN — the info pages and apps are fully self-contained). Revisit if Jake wants everything CDN-free.
- Warm near-black / off-white, single ember accent. Inline-SVG icons, no emoji.

### Bingo Caller (`bingo/index.html`) — Jake's, mostly hands-off
- Live at https://freeapps.pages.dev/bingo/ (was the bare `/Bingo/` on GitHub Pages).
- Originally built for one club's fundraiser bingo night (hence the TV-first, silent design). As of 2026-08-29 Jake has **disassociated it from that club** — they run their own copy now, and the public copy is a general free tool. Don't name any specific club/org in public-facing copy.
- Full-screen 75-ball board, colour-coded B/I/N/G/O rows, right sidebar (Last Call, Now Playing + mini grid, Choose Game, Rotate, Pace 0–15s, Call/Reset/Fullscreen), pattern picker modal (17 presets + custom painter), "Let's Play" reveal, Wake Lock, fullscreen.
- **SILENT by design.** Voice code is intact but gated behind `const SPEECH_ENABLED = false` (forces a local/offline voice when re-enabled). Don't describe it as "speaking" or "spoken calls" anywhere.
- Start screen has a "← What is this?" link → `info.html`.
- No video/image assets — removed 2026-07-01, don't re-add without Jake asking.

### Bingo info (`bingo/info.html`) — Jake's July landing page
- Self-contained (no CDN, no JS). Impact/system display font, same palette as the caller.
- Full copy: what it is, who it's for, "about the free part", how to use it, what's in it, "straight talk about what it doesn't do".
- Commented-out but ready: a "What people are saying" quotes block, and an "Anything you want to say" block with a Facebook button (`FACEBOOK_PAGE_URL`) + mailto (`SOMEBODY@SOMEWHERE.COM`), and a PayPal donate block (`YOUR_PAYPAL_LINK_HERE`). Jake turns these on when he has real content / addresses.
- START THE CALLER → `index.html` (same folder). "All free apps" → `../`.

### Burn Book (`burn-book/index.html` + `info.html`)
- App: cover screen (tap the embedded cover image) → dark leather writing page → hold "burn" → canvas fire eats the text, ~3s, wiped. Nothing persisted, ever. iOS: cover opens on click/touchend/pointerup, img is `pointer-events:none`. Master copy on Jake's Desktop — keep in sync.
- Info page: deliberately darker than the bingo page (near-black, hot pink, embers canvas), Permanent Marker + IBM Plex Sans. Steps 1-2-3, "where it goes: nowhere" privacy section.

### Just Pick Something (`dinner/index.html` + `info.html`) - added 2026-09-03
- The dinner decider. One start page: title, one line of what it is, a big "Help Me Choose" button, and the answer lands in a panel below it on the same page. "That's it" locks it in. Opens already showing a dinner, never an empty box.
- **It is deliberately tiny.** A first version had filters (time / effort / cost / one-pan), a spin wheel, swipe mode, favorites, a grocery list and a vote mode - Jake cut all of it: *"too busy... it's a what do you want for dinner idk what do you want."* The whole product is one button and one name. **Don't add features back without Jake asking.**
- `IDEAS` near the bottom of the script is a plain template string, one dinner per line as `emoji space name` - that's the only thing meant to be edited. 105 of them, plain central-PA everyday food (chicken and noodles, haluski, ham pot pie, tater tot casserole, chipped ham barbecues, wedding soup). Keep that register: no cheffy or trendy food.
- Won't repeat anything from the last 12 taps. No localStorage except the light/dark choice.
- Palette is its own: olive-biased neutrals, one saffron accent (`#E8A317` light / `#F5B933` dark). System font stack at weight 900 for display - no CDN, per the single-file rule.
- Name was picked over "What's For Dinner" (too generic). Desktop master copy: `Just_Pick_Something.html`.

## Notes
- Jake builds in sections — validate each before the next. Ask what's next, don't assume.
- Jake works across several AI tools that don't share memory — the July landing page was built with another tool and pushed straight to the repo. **Always `git fetch` and check the remote before restructuring this repo.**
- Keep every app a single file, no dependencies, no trackers/ads/accounts — it's the whole pitch.
