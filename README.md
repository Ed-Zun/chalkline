# Chalk Line website

Plain HTML + CSS. No build step.

```
index.html              landing + all sections
blog/index.html         essay archive
blog/post-template.html copy this for each new essay
assets/style.css        all styling
.nojekyll               tells GitHub Pages to serve files as-is
```

## Before publishing
- Replace `hello@example.com` (index.html, blog/index.html, blog/post-template.html) with your real address.
- Check the timeline dates against the linked sources.

## Publish on GitHub Pages with a Strato domain

1. **Repo.** Create a GitHub repository (e.g. `chalkline`), upload these files to the root of the `main` branch.
2. **Enable Pages.** Repo → Settings → Pages → Source: "Deploy from a branch" → Branch `main`, folder `/ (root)` → Save.
3. **Custom domain.** In the same Pages screen, enter your domain (e.g. `www.yourdomain.nl`) and save. GitHub creates a `CNAME` file in the repo. Tick "Enforce HTTPS" once it becomes available.
4. **DNS at Strato.** Log in to Strato → Domains → your domain → DNS / Nameserver settings → manage DNS records:
   - `www` → **CNAME** → `YOUR-GITHUB-USERNAME.github.io`
   - Apex (`yourdomain.nl`, no www) → four **A** records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Optionally four **AAAA** records: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
   - Remove any existing A/AAAA/CNAME records on the same host names that point to Strato's own hosting (parking page).
5. **Wait.** DNS can take from minutes to a few hours. GitHub issues the HTTPS certificate automatically after it detects the DNS.

Check GitHub's current values at docs.github.com → "Managing a custom domain for your GitHub Pages site", as IPs can change.
