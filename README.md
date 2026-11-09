# preops.com — The Preops Clinic website

Static site. No build step, no server code. Upload the contents of this folder to any web host and point preops.com at it.

## Files

- `index.html` — home page (hero, refer panel, how it works, surgeons' offices, patients, insurance, about teaser)
- `about.html` — About page
- `styles.css` — all styles (brand tokens at the top)
- `referral-form.pdf` — the fax referral form schedulers download
- `quick-reference.pdf` — the scheduler quick-reference sheet
- `favicon.svg` — the ring-check mark

## Hosting (pick one)

- **Cloudflare Pages** or **Netlify** — free, drag the folder in, add `preops.com` as a custom domain, HTTPS is automatic.
- **Kinsta Static Site Hosting** — free tier; same idea, and it sits next to the VHR site.
- Any shared host — upload via SFTP to the web root.

Set up the short link **preops.com/refer**: a redirect from `/refer` to `/index.html#refer`. On Cloudflare Pages or Netlify that is one line in a `_redirects` file:

```
/refer   /index.html#refer   302
```

Printed pieces point to preops.com/refer, so keep that redirect alive.

## The online referral form (JotForm HIPAA)

A referral carries PHI (patient name, phone, surgery date), so the online form runs on your JotForm HIPAA account, which is covered by JotForm's BAA. HIPAA forms live at `hipaa.jotform.com`, and the site embeds from there.

**To connect it (one edit):**

1. Build the form in JotForm — the field list is in `jotform-fields.md`. Fastest route: Create Form → Import → **PDF form**, upload `referral-form.pdf`, and JotForm turns the fax form into the online form with the same fields.
2. The form built on 2026-10-26 has ID **262983131694061** (link: https://hipaa.jotform.com/262983131694061). If you rebuild the form, copy the new number from the end of its link.
3. In `index.html`, `<section ... id="refer-form" data-jotform-id="262983131694061"` already carries it; change the number there if the form changes.

That's it. The "Refer Online (secure form)" button appears in the hero panel and the form section appears below it. With the ID empty, both stay hidden and fax, email, and phone still work.

**JotForm settings worth checking:** Settings → Emails → notification to referrals@preops.com (HIPAA mode sends a link rather than the PHI itself); Settings → Form Settings → Thank-you page text, e.g. "Received. We'll call the patient to schedule and fax the letter to your office."; enable the file-upload field's encryption (on by default on HIPAA plans).

Do not move the form to Formspree, Netlify Forms, Typeform, Mailchimp, or a non-HIPAA JotForm plan.

## Replacing the logo

The wordmark is set live in Outfit with an inline SVG ring-check. When the designer's final SVG arrives, replace the contents of each `<span class="logo">` with an `<img>` of that SVG (there are two per page: header and footer; the footer uses the white version).

## Placeholders to fill

- `[HOURS]` — footer and About page
- `[PHOTO]` — About page portrait
- Privacy and Accessibility footer links point to `#` until those pages exist

## Hosting as deployed (Nov 2026)

GitHub Pages, repo `mwakslak-del/preops-site`, branch `main`, root folder. Custom domain `www.preops.com` (CNAME file); apex `preops.com` redirects to www. DNS at GoDaddy: four A records on `@` to GitHub Pages (185.199.108.153, .109.153, .110.153, .111.153) and `www` CNAME to `mwakslak-del.github.io`. To update the site, change the files and push to `main`; Pages redeploys in about a minute.

## Search and AI visibility

- `robots.txt` allows all crawlers and names the AI crawlers explicitly (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, Applebot, and others).
- `sitemap.xml` lists both pages and both PDFs.
- `llms.txt` is a plain-text summary of the clinic for AI assistants.
- `index.html` carries JSON-LD: MedicalClinic / MedicalBusiness, Physician, WebSite, and FAQPage. Keep the phone, fax, address, and insurance list in sync when they change.
- `refer/index.html` makes `preops.com/refer` (the address on every printed piece) land on the referral section.
- Still to do by hand: Google Business Profile for "The Preops Clinic" at the Suite 216 address (business.google.com), and Google Search Console (add `preops.com` as a domain property; it should auto-verify from the existing Workspace DNS record) then submit the sitemap.
