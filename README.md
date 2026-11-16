# Midwest Cards — Email Signature Generator

A single-page tool for creating a consistent, branded Midwest Cards email signature. Team members fill in their details, hit **Copy signature**, and paste it into Gmail or Outlook.

**Live generator:** https://midwestcards.github.io/mwc-email-signature/

## What it makes

Three versions from the same details:

- **Full** (new emails): headshot on the left; name, title, gold line, logo, phone and email, website, work address, and links to Instagram, Whatnot Live and Midwest Insider; confidentiality note underneath.
- **Reply** (replies and forwards): text only — name, title, phone, website, beside a gold line.
- **Phone app**: plain text for the Gmail mobile signature.

Brand fonts are Montserrat (name, contact lines) and Barlow Condensed (title, links, fine print), with Arial as the fallback. Recipients who don't have the fonts installed see Arial in the same layout; email can't send fonts along with a signature.

Typed text is title case. The logo wordmark is the only all-caps element (brand guide: the wordmark is artwork and is never re-typeset), so the company name isn't typed after the title.

## For new team members

1. Open the [live generator](https://midwestcards.github.io/mwc-email-signature/) (or open `index.html` in a browser).
2. Fill in your name, title, phone, email, and (optionally) a second phone, your work address, and a headshot link.
3. Copy each version (Full, Reply, Phone app) and paste it into your email settings:
   - **Gmail:** Settings (gear) → See all settings → General → Signature → Create new → paste. Set Full as the default for new emails and Reply for replies/forwards, tick *Insert signature before quoted text*, then Save Changes.
   - **Gmail phone app:** Settings → your account → Signature settings / Mobile signature → paste the Phone app version.
   - **Outlook:** Settings → Account → Signatures (classic Windows: File → Options → Mail → Signatures). If pasting drops the formatting, use **Show HTML → Copy code**.

### Headshots

The photo shows at 138 × 186 px, the exact height of the text block, so it needs to be a **3:4 portrait**.

- **Best:** a 276 × 372 px JPG in `assets/headshots/` (ask Tyler), linked as `https://midwestcards.github.io/mwc-email-signature/assets/headshots/<name>.jpg`. The page has a **headshot maker** that crops any photo to that size for you.
- **Also works:** a Google Drive link to a photo shared "anyone with the link can view". The generator turns it into a Google image link cropped to 3:4.
- The generator warns you if a photo isn't 3:4. It never stretches a photo (height is set to auto), but a square photo won't line up with the text.

## For maintainers

Everything lives in `index.html` — no build step, no dependencies.

Team-wide defaults (website, links row, default location, disclaimer, logo URL, brand colors) live in the **CONFIG** block at the top of the `<script>`. Edit once, commit, and everyone gets the update. The layout keeps the text block at a fixed height (three contact lines; "Columbus, OH" fills the address line when it's left blank) so the photo always lines up.

### Brand assets

All signature images live in `assets/` and are served by this repo's GitHub Pages site — signatures reference them by absolute URL, so they load for email recipients too:

- `midwestcards_horizontal_color.png` — logo used by the current signature (from the brand library, high-res)
- `insider_banner.png`, `icons/`, `midwestcards_stacked_color.png` — used by the previous signature design; not used by the current generator, but **kept because older signatures in use still point at them**
- `headshots/` — team headshots (3:4, 276 × 372 px); add new ones here so everyone has a permanent photo URL

To swap an image, replace the file **keeping the same filename** and push — Pages redeploys automatically.

The page carries a `noindex, nofollow` robots meta tag — it's an internal tool and must stay out of search engines. Keep that tag in place, and don't add office addresses anywhere on this page (people type their own work address into the form).

⚠️ Don't rename or delete files in `assets/` — every signature already in use points at those URLs.
