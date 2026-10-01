# Famous Foods — Website

Static marketing site with a visitor lead gate, product catalogue, WhatsApp
enquiries, and a password-protected admin page to view captured leads.

## What is included
- Full-screen visitor information gate: Name + WhatsApp number, saved to Supabase.
- 11 product cards with local images (`images/`) — clicking anywhere on a card
  opens the enquiry modal for that product.
- Product enquiries open WhatsApp to **+91 91526 72712** with the visitor's name
  and the selected product pre-filled.
- `admin.html` — protected leads dashboard (view, refresh, export CSV).
- GitHub Action that pings Supabase twice a week so the free-tier project never
  pauses due to inactivity.
- Responsive mobile/desktop design.

## 1. Supabase setup
1. Create a project at [supabase.com](https://supabase.com).
2. Open **SQL Editor** and run `schema.sql`. It creates the `leads` table, the
   public INSERT policy (website visitors) and the admin SELECT policy
   (signed-in admins only). If you already ran the original schema, just run the
   last section (`Admins can view leads`) on its own.
3. Create your admin login: **Authentication → Users → Add user** — enter your
   email and a strong password, keep **Auto Confirm User** enabled.

`index.html` and `admin.html` already contain this project's URL and public
anon key. Use the anon key only — never put the service-role key in the frontend.

## 2. Admin / leads page (the "route")
- URL: `https://<your-domain>/admin.html` (e.g. on GitHub Pages:
  `https://syed-roshan01.github.io/business-vcard/admin.html`)
- Sign in with the admin account created in step 1.
- Shows every lead: name, WhatsApp number (click to open a WhatsApp chat) and
  the date/time received, newest first.
- **Export CSV** downloads all leads for Excel / Google Sheets.
- Security: anonymous visitors can only INSERT; only authenticated admins can
  SELECT. The page is not linked from the main site and is marked `noindex`.

## 3. Keep Supabase from pausing
Free-tier Supabase projects pause after **7 days of inactivity**. This repo
includes `.github/workflows/keep-supabase-active.yml`, a GitHub Action that
pings the project's REST API every Monday and Thursday. As long as this repo
lives on GitHub, the project keeps registering activity and never pauses.
You can also trigger it manually from the repo's **Actions** tab
(*Keep Supabase Active → Run workflow*).

Alternative: upgrading the Supabase project to Pro also prevents pausing.

## 4. Files
- `index.html` — main website
- `admin.html` — leads dashboard (protected)
- `images/` — product photos (`.jpeg`)
- `schema.sql` — Supabase table + security policies
- `index1.html` — older draft with Cloudinary images (kept for reference)
- `.github/workflows/keep-supabase-active.yml` — Supabase keep-alive

## 5. Deploy
This is a static site — host it on GitHub Pages, Vercel, Netlify, Cloudflare
Pages or any normal web host. For GitHub Pages: **Settings → Pages → Deploy
from branch → main** (root).
