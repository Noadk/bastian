# Theme Development Workflow

## Branch structure

| Branch | Purpose | Shopify theme |
|--------|---------|---------------|
| `dev` | Active development & testing | Development/preview theme |
| `main` | Production-ready code | Live theme |

**Rule: never commit directly to `main`. All changes go through `dev` first.**

---

## Day-to-day process

### 1. Start work on `dev`
```bash
git checkout dev
git pull origin dev
```

### 2. Make changes, then commit
```bash
git add <file(s)>
git commit -m "Short description of change"
git push origin dev
```
If GitHub Actions is set up, pushing to `dev` auto-deploys to the development theme on Shopify for review.

### 3. Promote to production (merge dev → main)
Once changes are tested and approved:
```bash
git checkout main
git pull origin main
git merge dev
git push origin main
```
Pushing to `main` auto-deploys to the live Shopify theme.

---

## GitHub Actions (auto-deploy) setup

Auto-deployment requires two things:

**A. A Shopify Theme Access password**
1. Go to your Shopify admin → Settings → Apps → Theme Access (or Partner Dashboard)
2. Generate a token with theme write access
3. Note the theme IDs for both the live theme and the dev/preview theme (Shopify admin → Online Store → Themes → theme ID is in the URL)

**B. GitHub repository secrets**
Go to GitHub repo → Settings → Secrets and variables → Actions, and add:

| Secret name | Value |
|-------------|-------|
| `SHOPIFY_STORE` | `your-store.myshopify.com` |
| `SHOPIFY_THEME_TOKEN` | Theme Access password from step A |
| `LIVE_THEME_ID` | Theme ID of your live theme |
| `DEV_THEME_ID` | Theme ID of your development/preview theme |

**C. Add the workflow file**
Create `.github/workflows/deploy.yml` in the repo (ask Claude Code to generate this).

---

## Quick reference

```
dev     →  test changes here first
main    →  production / live store
```

```
git checkout dev          # switch to dev
git pull origin dev       # get latest
# ... make changes ...
git add . && git commit -m "my change"
git push origin dev       # triggers dev theme deploy

git checkout main
git merge dev
git push origin main      # triggers live theme deploy
```
