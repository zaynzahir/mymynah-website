# Deploy My Mynah website to GitHub Pages + Squarespace domain

Follow these steps to push the site to GitHub, turn on GitHub Pages, and point your Squarespace domain to it.

---

## Part 1: Push the website to GitHub

### 1.1 Create a new repository on GitHub

1. Go to [github.com](https://github.com) and sign in.
2. Click **+** → **New repository**.
3. Name it (e.g. `mymynah-website` or `mynah-website`).
4. Choose **Public**, leave "Add a README" **unchecked**.
5. Click **Create repository**.

### 1.2 Push the website folder from your computer

Open Terminal and run these commands (replace `YOUR_USERNAME` and `YOUR_REPO` with your GitHub username and repo name):

```bash
cd /Users/zaynzahir/Desktop/Mynah/mynah/website

# Initialize git here (if this folder isn’t already a git repo)
git init

# Add all files
git add .

# First commit
git commit -m "My Mynah website - initial commit"

# Add GitHub as remote (replace with your repo URL)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git

# Rename branch to main if needed, then push
git branch -M main
git push -u origin main
```

Example if your repo is `https://github.com/zaynzahir/mymynah-website`:

```bash
git remote add origin https://github.com/zaynzahir/mymynah-website.git
git branch -M main
git push -u origin main
```

After this, the website files (including `index.html`, `privacy.html`, `terms.html`, and `Icon background removed.png`) will be on GitHub.

---

## Part 2: Turn on GitHub Pages

1. On GitHub, open your repo (e.g. `mymynah-website`).
2. Go to **Settings** → **Pages** (left sidebar).
3. Under **Build and deployment**:
   - **Source**: Deploy from a branch
   - **Branch**: `main` (or `master`)
   - **Folder**: `/ (root)`
4. Click **Save**.

After a minute or two, your site will be live at:

- **https://YOUR_USERNAME.github.io/YOUR_REPO/**

Example: `https://zaynzahir.github.io/mymynah-website/`

Open that URL to confirm the site loads. Then you can connect your Squarespace domain.

---

## Part 3: Use your Squarespace domain with GitHub Pages

You’ll point your domain (e.g. `mymynah.com`) to GitHub Pages from Squarespace’s DNS.

### 3.1 Add your custom domain in the GitHub repo

1. In your repo, go to **Settings** → **Pages**.
2. Under **Custom domain**, type your domain (e.g. `mymynah.com`) and click **Save**.
3. (Optional but recommended) Check **Enforce HTTPS** after DNS has propagated.

### 3.2 Create a CNAME file in the website (for custom domain)

So GitHub knows which domain to use, add a file named `CNAME` (no extension) in the `website` folder with one line: your domain.

Example content of `CNAME`:

```
mymynah.com
```

Then commit and push:

```bash
cd /Users/zaynzahir/Desktop/Mynah/mynah/website
echo "mymynah.com" > CNAME
git add CNAME
git commit -m "Add CNAME for custom domain"
git push
```

(Use your real domain instead of `mymynah.com` if it’s different.)

### 3.3 Point the domain in Squarespace to GitHub

1. Log in to **Squarespace** → go to **Settings** → **Domains**.
2. Select the domain you use for My Mynah (e.g. `mymynah.com`).
3. Look for **DNS settings** or **Advanced settings** / **Use custom nameservers** or **Connect external host** (wording varies by plan).
4. Add these records so the domain points to GitHub Pages:

| Type | Host / Name | Value / Points to |
|------|-------------|-------------------|
| **A** | `@` | `185.199.108.153` |
| **A** | `@` | `185.199.109.153` |
| **A** | `@` | `185.199.110.153` |
| **A** | `@` | `185.199.111.153` |
| **CNAME** | `www` | `YOUR_USERNAME.github.io` |

- Replace `YOUR_USERNAME` with your GitHub username (e.g. `zaynzahir.github.io`).
- If Squarespace already has A or CNAME records for this domain, edit or replace them so they match the table above.

5. Save. DNS can take from a few minutes up to 24–48 hours to propagate.

### 3.4 (Optional) Redirect www to non-www or vice versa

- If you want **https://mymynah.com** as the main URL: set the **Custom domain** in GitHub Pages to `mymynah.com` (as in 3.1) and keep the A records for `@` and CNAME for `www` as above.
- In GitHub Pages settings you can only set one custom domain; the other (e.g. www vs non-www) can be handled by adding a redirect in Squarespace if your plan supports it, or by using only one of them in the CNAME file and DNS.

---

## Summary checklist

- [ ] Create GitHub repo and push `website` folder (Part 1).
- [ ] Enable GitHub Pages from branch `main`, folder `/ (root)` (Part 2).
- [ ] Confirm site at `https://YOUR_USERNAME.github.io/YOUR_REPO/`.
- [ ] Add custom domain in GitHub Pages and add `CNAME` file (Part 3.1–3.2).
- [ ] In Squarespace, set A and CNAME records to point to GitHub (Part 3.3).
- [ ] After DNS propagates, turn on **Enforce HTTPS** in GitHub Pages.

If you tell me your GitHub username and exact domain (e.g. mymynah.com), I can fill in the exact commands and CNAME content for you.
