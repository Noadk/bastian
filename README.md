# Bastian Inverun Shopify Theme

This is the Shopify theme for the Bastian Inverun store. It lives in two places at once:
- **OneDrive** (local files on your computer): `OneDrive > Marketing - Dokumenter > General > ONLINE > GITHUB TEST ENVIRONMENT > SHOPIFY-THEME-BI`
- **GitHub** (online backup + version control): [github.com/Noadk/bastian](https://github.com/Noadk/bastian)
- **Shopify admin** (what the store actually runs): Online Store → Themes

> Changes made in any of these places can sync to the others — see below.

---

## Branches (versions)

There are two versions of the theme code:

| Branch | Purpose |
|--------|---------|
| `dev` | Where you make and test changes |
| `main` | The stable, approved version |

**Always work in `dev` first. Only move to `main` when everything looks good.**

---

## How to make changes

There are two ways to make changes to the theme:

### Option 1 — Directly in Shopify (no coding needed)

Use this for: changing colors, fonts, text, banners, layout, images, and content.

1. Go to **Shopify admin → Online Store → Themes**
2. Find the **dev theme** → click **Customize**
3. Make your changes in the visual editor
4. Click **Save**

> Any change saved in Shopify automatically syncs back to GitHub. No extra steps needed.

**Note:** Products, prices, and inventory are managed separately under **Shopify admin → Products** — not in the theme editor.

---

### Option 2 — Via Claude Code (for code changes)

Use this for: custom code, new features, bug fixes, or anything not possible in the visual editor.

**Step 1 — Open the project folder**

The project is located at:
```
OneDrive > Marketing - Dokumenter > General > ONLINE > GITHUB TEST ENVIRONMENT > SHOPIFY-THEME-BI
```

**Step 2 — Open Claude Code**

- Open **VS Code**
- Open the folder above (File → Open Folder)
- Claude Code runs as an extension in the sidebar — click the Claude icon

Or via terminal:
```bash
cd ~/Library/CloudStorage/OneDrive-Deltebiblioteker–NordahlAndersen/Marketing\ -\ Dokumenter/General/ONLINE/GITHUB\ TEST\ ENVIRONMENT/SHOPIFY-THEME-BI
claude
```

**Step 3 — Make sure you're on the dev branch**

Ask Claude Code: *"Switch to dev branch"* or run:
```bash
git checkout dev
git pull origin dev
```

**Step 4 — Describe what you want**

Just tell Claude Code what you want to change in plain language, for example:
- *"Move the logo to the center of the header"*
- *"Add a sale banner at the top of the page"*
- *"Change the button colour to black"*

**Step 5 — Save and push to GitHub**

Claude Code can do this for you, or you can run:
```bash
git add .
git commit -m "Brief description of change"
git push origin dev
```

---

## Moving changes from dev to main (going live)

Once you have tested your changes on the dev theme and everything looks good:

```bash
git checkout main
git merge dev
git push origin main
```

Or ask Claude Code: *"Merge dev into main and push"*

---

## Quick overview

```
Shopify editor (visual)  ──saves──►  GitHub (auto-sync)
Claude Code (code)       ──push───►  GitHub  ──►  Shopify theme updates
```

```
dev branch   = work in progress / testing
main branch  = approved / ready for production
```
