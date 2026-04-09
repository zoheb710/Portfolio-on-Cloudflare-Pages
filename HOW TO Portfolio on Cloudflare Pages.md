---

# 🚀 Host Your DevOps Portfolio on Cloudflare Pages
### Free Tier · Custom GoDaddy Domain · HTTPS Included

***

## 🧱 Stack Overview

| Component | Role |
|---|---|
| ☁️ **Cloudflare Pages** | Free static hosting on global CDN |
| 🌐 **GoDaddy Domain** | Domain registration only — DNS moves to Cloudflare |
| 🔒 **SSL/TLS** | Auto-provisioned free certificate |
| ♾️ **Bandwidth** | Unlimited on free plan |

***

## 📁 Phase 1 — Prepare Your Files

Structure your project like this before doing anything:

```
portfolio/
├── index.html       ← Main homepage
├── style.css        ← Styles
├── script.js        ← Scripts
└── assets/
    └── images, icons, etc.
```

> ⚠️ **Important:** `index.html` must be a **pure static file** — no PHP, no Node.js, no server-side code.

***

## 🚢 Phase 2 — Deploy to Cloudflare Pages

### Step 1 — Create a Cloudflare Account
```
cloudflare.com → Sign Up → Free Plan
```

***

### Step 2 — Navigate to Pages
```
Dashboard → Workers & Pages (sidebar)
         → Create
         → Pages tab
         → Upload assets (Direct Upload)
```

***

### Step 3 — Upload Your Files

- Name your project → e.g., `zoheb-devops-portfolio`
- This becomes your staging URL:
```
https://zoheb-devops-portfolio.pages.dev
```
- Drag your `portfolio/` folder into the uploader
- Click **Deploy site**

```
✅ Live at https://your-project.pages.dev
✅ HTTPS enabled automatically — zero config
```

***

### Step 4 — Connect GitHub for Auto-Deploy *(Recommended)*

```
Cloudflare Pages → Create → Connect to Git
                          → Select your repo
                          → Framework preset: None
                          → Output directory: .  (root)
                          → Save & Deploy
```

> 💡 Every `git push` to `main` triggers an automatic redeploy — a clean DevOps workflow worth documenting on GitHub.

***

## 🌍 Phase 3 — Add GoDaddy Domain to Cloudflare

> You're moving **DNS management** (not domain ownership) from GoDaddy to Cloudflare.

***

### Step 5 — Add Domain in Cloudflare
```
Dashboard → Add a domain
          → Enter: yourdomain.com
          → Select: Free Plan
          → Continue
```

***

### Step 6 — Review Imported DNS Records

Cloudflare **auto-scans** your GoDaddy DNS records and imports them.
Review the list, then click **Continue to nameservers**.

***

### Step 7 — Copy Your Cloudflare Nameservers

Cloudflare gives you 2 custom nameservers. Example:
```
leah.ns.cloudflare.com
tim.ns.cloudflare.com
```
> 📋 Copy both — you'll paste them into GoDaddy next. Keep this tab open.

***

### Step 8 — Update Nameservers in GoDaddy
```
godaddy.com → My Products → Your Domain
            → ⋯ (three dots) → Manage DNS
            → Nameservers → Change
            → Enter my own nameservers (advanced)
            → Paste both Cloudflare nameservers
            → Save
```

***

### Step 9 — Verify Propagation in Cloudflare
```
Cloudflare → Done, check nameservers
```

| Propagation | Time |
|---|---|
| ⚡ Best case | 15 minutes |
| 🕐 Typical | 1–4 hours |
| 🐢 Maximum | 48 hours |

> 📧 Cloudflare emails you when your domain goes active.

***

## 🔗 Phase 4 — Connect Custom Domain to Pages

### Step 10 — Add Custom Domain
```
Workers & Pages → Your Project
               → Custom Domains tab
               → Set up a custom domain
               → Enter: yourdomain.com
               → Activate domain
```
> Cloudflare **automatically creates** the CNAME record since your DNS is already on Cloudflare.

***

### Step 11 — Enable HTTPS
```
SSL/TLS → Mode → Full
```
> 🔒 Free SSL certificate is provisioned automatically — no Let's Encrypt setup needed.

***

### Step 12 — www → Root Redirect *(Optional but Clean)*
```
Rules → Redirect Rules → Create rule

IF:   Hostname = www.yourdomain.com
THEN: Static redirect → https://yourdomain.com
      Type: 301 Permanent

→ Deploy
```

***

## ✅ Final Verification Checklist

```
□  Pages staging URL loads        →  your-project.pages.dev
□  DNS propagated                 →  dnschecker.org
□  Custom domain works            →  https://yourdomain.com
□  SSL active                     →  🔒 padlock in browser
□  www redirects to root          →  www.yourdomain.com → yourdomain.com
□  Auto-deploy works              →  git push → Pages dashboard
```

***

## ⚙️ Pro DevOps Tips

```
📊  Cloudflare Analytics     →  Free traffic monitoring (great for LinkedIn posts)
🤖  Bot Fight Mode           →  Security → Bots → Enable (free DDoS protection)
🔀  _redirects file          →  Add to project root for path-based URL routing
🖥️  Wrangler CLI deploy      →  wrangler pages deploy ./portfolio
```

***

> 🎯 **You now have:** A DevOps portfolio hosted on a global CDN, with a custom domain, free SSL, auto-deploy from GitHub, and DDoS protection — all at **$0/month**.
