# Le's O Nails, Oxnard

Transfer-ready static website for **Le's O Nails** at 2319 N Oxnard Blvd, Oxnard, CA 93036. One-page site (`index.html`) with services, hours, and a appointment request form. Deploy as-is to GitHub Pages, Cloudflare Pages, or Netlify, then hand the repo (or a zip) to the client after payment.

Public details on this preview (hours, services, and any review excerpts) were gathered from listings such as the business Nextdoor page, Google-style place pages, and public reviews. They should be confirmed with the owner before calling the site official.

## Swap the notification email (handoff)

Appointment requests are emailed through [FormSubmit](https://formsubmit.co) at no cost. Open `index.html` and change one line near the top of the `<script>` block:

```js
const BUSINESS_CONFIG = {
  businessName: "Le's O Nails",
  notificationEmail: "df194246@gmail.com", // change this to the client's email
  phone: "(805) 485-6877",
  address: "2319 N Oxnard Blvd, Oxnard, CA 93036",
  timezone: "America/Los_Angeles",
  mapsQuery: "Le's O Nails 2319 N Oxnard Blvd Oxnard CA 93036"
};
```

The in-page confirmation still appears instantly. If the email request fails or is blocked, the visitor still sees a clean confirmation.

**First-time activation:** FormSubmit sends a one-time confirmation to the new address the first time a form is submitted. Open that email and click the confirmation link, then submit once more. After that, notifications arrive automatically.

## Transfer ownership

After payment, give the client the live site and the source in one of these ways:

1. **GitHub (recommended):** Push this repo to GitHub, then go to **Settings, General, Danger Zone, Transfer ownership** and transfer it to the client's GitHub account. They then own the code, Pages site, and future edits.
2. **Zip handoff:** Download the folder (or `git archive --format=zip -o les-o-nails-oxnard.zip HEAD`) and send it to the client. They can drop `index.html` into their own GitHub, Cloudflare Pages, or Netlify project.
3. **Cloudflare Pages / Netlify:** In the host dashboard, transfer the project to the client's account, or have them create a new project from this repo after the GitHub transfer.

## Attach a custom `.com` domain

1. Buy the domain (about $10 to $12/year) or use one the client already owns.
2. In this repo, add a `CNAME` file in the root (filename has no extension) containing only the domain, for example:

   ```
   lesonailsoxnard.com
   ```

3. Point DNS at the host:

   **GitHub Pages**
   - Apex: `A` records to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (and optional `AAAA` records from GitHub's docs).
   - `www`: `CNAME` to `USERNAME.github.io`.
   - Then: repo **Settings, Pages, Custom domain**, enter the domain, and enable HTTPS once DNS has propagated.

   **Cloudflare Pages:** In the Pages project, open **Custom domains**, add the domain, and follow the DNS records Cloudflare shows (often a `CNAME` to `your-project.pages.dev`).

   **Netlify:** In **Domain management**, add the custom domain. For the apex, use Netlify's `A`/`ALIAS` records; for `www`, a `CNAME` to `your-site.netlify.app`.

4. Commit and push the `CNAME` file if you are using GitHub Pages, then wait for HTTPS to become active (usually a few minutes to a few hours).

## Deploy (free)

- **GitHub Pages:** Settings, Pages, Deploy from a branch, `main` / root (`/`).
- **Cloudflare Pages or Netlify:** Import this repo, build command left blank, publish directory `/` (or `.`).

No build step is required. The site is a single static `index.html` plus a favicon.
