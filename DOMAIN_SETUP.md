# ALETHINX DOMAIN & DEPLOYMENT GUIDE
## alethinx.ai (Marketing) + app.alethinx.ai (Product App)

---

## ARCHITECTURE

```
alethinx.ai          → Marketing site (this HTML file)
www.alethinx.ai      → Redirects to alethinx.ai
app.alethinx.ai      → Your Lovable app (current site)
alethinx.com         → Redirects to alethinx.ai
www.alethinx.com     → Redirects to alethinx.ai
```

---

## STEP 1: DEPLOY MARKETING SITE (alethinx.ai)

### Option A: Vercel (Recommended — Free, Fast)

1. Go to vercel.com → Sign up with GitHub
2. Create a new GitHub repo: `alethinx-marketing`
3. Push the index.html file to it:
   ```bash
   mkdir alethinx-marketing
   cp index.html alethinx-marketing/
   cd alethinx-marketing
   git init
   git add .
   git commit -m "Alethinx marketing site"
   git remote add origin https://github.com/maruthi25/alethinx-marketing.git
   git push -u origin main
   ```
4. In Vercel → "Import Project" → select the repo
5. Deploy (takes ~30 seconds)
6. Vercel gives you a URL like `alethinx-marketing.vercel.app`

### Option B: Netlify (Also Free)

1. Go to netlify.com → Sign up
2. Drag and drop the `index.html` file onto the dashboard
3. Done — Netlify gives you a URL

---

## STEP 2: CONNECT alethinx.ai DOMAIN

### In Vercel (after deploying):
1. Go to your project → Settings → Domains
2. Add: `alethinx.ai`
3. Add: `www.alethinx.ai` (redirect to alethinx.ai)
4. Vercel will show you DNS records to add

### In Your Domain Registrar (where you bought alethinx.ai):
Add these DNS records:

| Type  | Name | Value                    |
|-------|------|--------------------------|
| A     | @    | 76.76.21.21              |
| CNAME | www  | cname.vercel-dns.com     |

(Vercel will give you the exact values — use theirs)

---

## STEP 3: CONNECT app.alethinx.ai TO LOVABLE

### In Lovable:
1. Open your project → Settings → Domains
2. Click "Add Custom Domain"
3. Enter: `app.alethinx.ai`
4. Lovable will show you a CNAME record to add

### In Your Domain Registrar:
Add this DNS record:

| Type  | Name | Value                                      |
|-------|------|--------------------------------------------|
| CNAME | app  | (whatever Lovable tells you, likely something.lovable.app) |

Wait 5-30 minutes for DNS propagation.

---

## STEP 4: REDIRECT alethinx.com

### In Your Domain Registrar for alethinx.com:
Option 1 — If registrar supports forwarding:
- Set up URL forwarding: alethinx.com → https://alethinx.ai

Option 2 — DNS records pointing to Vercel:
Same A and CNAME records as alethinx.ai, then add
alethinx.com as a domain in Vercel (it will auto-redirect).

---

## STEP 5: UPDATE LOVABLE APP LINKS

Once app.alethinx.ai is working, update internal links.
In Lovable chat:

> "The site is now live at app.alethinx.ai. Please update
> any hardcoded references to althinx-deal-insight.lovable.app
> to use app.alethinx.ai instead."

---

## VERIFICATION CHECKLIST

| URL | Expected Result |
|-----|----------------|
| alethinx.ai | Marketing site loads |
| www.alethinx.ai | Redirects to alethinx.ai |
| alethinx.com | Redirects to alethinx.ai |
| www.alethinx.com | Redirects to alethinx.ai |
| app.alethinx.ai | Lovable product app loads |
| app.alethinx.ai/auth | Login/signup page |
| app.alethinx.ai/agentic | Agentic AI page (after login) |
| app.alethinx.ai/market-opportunity | Market data page |

---

## WHAT THE MARKETING SITE SHOWS vs. HIDES

✅ SHOWS (safe for public):
- Value proposition and headline stats
- Feature names and descriptions (high-level)
- Market opportunity summary numbers
- Pricing tiers
- FAQ
- Email capture

❌ HIDES (behind app.alethinx.ai login):
- Actual deal data and cards
- Board Claw analysis interface
- AI prompt architecture details
- Zero-PG financing templates
- Claw-by-Claw technical breakdown
- All proprietary tools and calculators
