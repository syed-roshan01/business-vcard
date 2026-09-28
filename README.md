# Famous Foods — Website

## What is included
- Full-screen visitor information gate: Name + WhatsApp number.
- Lead saved to Supabase.
- About Us section.
- Social media section.
- 3 product cards.
- Product-specific Enquire Now buttons.
- WhatsApp message opens to +91 70919 82594.
- Responsive mobile/desktop design.
- LocalStorage fallback for testing before Supabase is configured.

## 1. Add the 3 Cloudinary image URLs
Open `index.html` and replace:
- `IMAGE_URL_1` → Royal Tea image
- `IMAGE_URL_2` → Smokey Schezwan image
- `IMAGE_URL_3` → Ready-to-Cook Masala image

## 2. Connect Supabase
Create a Supabase project and run `schema.sql` in SQL Editor.

Then in `index.html` replace:
- `YOUR_SUPABASE_URL`
- `YOUR_SUPABASE_ANON_KEY`

Use the project's public anon key only. Never put a service-role key in the frontend.

## 3. Add social links
Replace the `href="#"` values for Instagram/Facebook/YouTube with the client's actual URLs.

## 4. WhatsApp flow
The enquiry destination is already configured as:
+91 70919 82594

The message contains:
- Visitor name
- Selected product
- Product enquiry text

## 5. Deploy
This is a static site and can be deployed directly on Vercel, Netlify, Cloudflare Pages, or any normal web host.
