# నా కథలు – Flipbook Library

A static website that shows books as page-turning flipbooks (Telugu story "మన ఇంటి గడప").

## Files
- `index.html` – the whole website (HTML, CSS, JavaScript)
- `assets/pages/` – the book pages as images
- `assets/signature.png` – author's signature

## Run / publish
Open `index.html` in a browser, or publish free with **GitHub Pages**:
Settings → Pages → Branch: `main` / root → Save.

## Add another book
1. Convert the PDF to images: `pdftoppm -jpeg -r 170 book.pdf assets/pages2/page`
2. Add a new entry to the `BOOKS` list in `index.html` (title, sub, pages).

Flip effect: [StPageFlip](https://github.com/Nodlik/StPageFlip) loaded from jsDelivr. Fonts: NTR and Anek Telugu (Google Fonts).

## Admin upload (PDF → flipbook)
Click **అప్‌లోడ్** in the menu, log in, choose a PDF, press convert.
- Username: `admin`. Password is stored only as a SHA-256 hash (`HASH` near the end of `index.html`).
- Change password: `python3 -c "import hashlib;print(hashlib.sha256(b'naa-kathalu|NEWPASSWORD').hexdigest())"` and paste the result into `HASH`.
- Note: login and storage run in the browser only. Uploaded books are saved in that browser (IndexedDB) and are not visible to other visitors. A real shared upload needs a backend (e.g. Firebase/Supabase).
