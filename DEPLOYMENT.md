# Deployment — Onezero s.r.o. website

Static site hosted on **GitHub Pages**, served at the custom domain **onezero.sk**.
Updating the site = commit and `git push` to `main`; Pages redeploys automatically.

---

## One-time setup

### Prerequisites (you)
- A GitHub account.
- The domain **onezero.sk** registered at a Slovak registrar (websupport.sk, webglobe.sk, exohosting.sk, …).

### 1. Authenticate the GitHub CLI
```bash
gh auth login          # choose GitHub.com → HTTPS → login with a web browser
```
Credentials are stored in the system keychain, so future updates need no re-login.

### 2. Create the repo and push
```bash
cd ~/Downloads/onezero-website
gh repo create onezero-website --public --source=. --remote=origin --push
```

### 3. Enable GitHub Pages (deploy from branch)
```bash
gh api -X POST repos/<USERNAME>/onezero-website/pages \
  -f source.branch=main -f source.path=/
```
The site is now live at `https://<USERNAME>.github.io/onezero-website/`
(and at `https://onezero.sk` once DNS below is set).

---

## DNS for onezero.sk (set at your registrar)

The repo's `CNAME` file already contains `onezero.sk`, so GitHub serves the apex domain.

**Apex `onezero.sk` — four A records (IPv4):**
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**Apex `onezero.sk` — four AAAA records (IPv6, optional but recommended):**
```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**`www.onezero.sk` — one CNAME record:**
```
www  CNAME  <USERNAME>.github.io.
```

After DNS propagates (minutes to a few hours), enable HTTPS:
```bash
gh api -X PUT repos/<USERNAME>/onezero-website/pages -f https_enforced=true
```
(or tick **Enforce HTTPS** in the repo's Settings → Pages.) GitHub issues a free
Let's Encrypt certificate automatically.

---

## Updating the site later
```bash
cd ~/Downloads/onezero-website
# edit files…
git add -A
git commit -m "Describe the change"
git push
```
Pages rebuilds within ~1 minute. (Claude can do all of this in a future session.)
