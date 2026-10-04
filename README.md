# నా కథలు – Flipbook Library (GitHub-stored uploads)

Static website (GitHub Pages). Books are shown as page-turning flipbooks.
The admin can upload a PDF in the browser; it is converted to page images and **committed into this repo**,
so every visitor sees it.

## Project structure
```
index.html            whole site (HTML + CSS + JS)
books/books.json      list of books shown on the site (edited automatically by uploads)
books/<id>/page-NN.jpg  pages of each uploaded book (added automatically)
assets/pages/         pages of the first built-in book
assets/signature.png  author signature
```

## 1. Publish
Upload all files to a **public** GitHub repo → Settings → Pages → Branch `main` / root → Save.
Site: `https://sandeepsrisiva123.github.io/naakathalu/`

## 2. Create an access token (one time)
GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate.
- Repository access: **Only select repositories** → this repo
- Permissions → Repository permissions → **Contents: Read and write**
- Set an expiry, copy the token (`github_pat_…`). Never put it in the code.

## 3. Upload a book
Open the site → **అప్‌లోడ్** → login → open "GitHub settings", enter username, repo, branch, token → Save
→ choose PDF → upload. After 1–2 minutes (Pages rebuild) all visitors see it.

## Login / password
Username `admin`. Password is stored as a SHA-256 hash (`HASH` near the end of `index.html`).
Change: `python3 -c "import hashlib;print(hashlib.sha256(b'naa-kathalu|NEWPASSWORD').hexdigest())"`
Real protection is the GitHub token: without it nobody can write to the repo. The token is kept only in
your browser (localStorage) on the device you entered it.

Flip effect: StPageFlip (jsDelivr). PDF conversion: PDF.js (cdnjs). Fonts: NTR, Anek Telugu.
