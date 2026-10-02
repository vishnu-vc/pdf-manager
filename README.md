# Paperwork — PDF Studio

A static, browser-based PDF toolkit. No API keys, account, paid service, or server-side processing. All runtime libraries are included under `vendor/`.

## Deploy to Netlify

1. Extract the ZIP.
2. Open https://app.netlify.com/drop and sign in.
3. Drag the **pdf-studio** folder (the folder containing `index.html`) onto the deployment area.
4. Open the supplied HTTPS URL.

For Git-based Netlify deployment, put this folder's contents at repository root. Publish directory: `.`. No build is necessary; the included configuration provides a no-op command.

## Deploy to GitHub Pages

1. Create a repository and upload **all contents** of `pdf-studio`, including the entire `vendor` directory and `.nojekyll`.
2. Open Settings → Pages.
3. Choose “Deploy from a branch”, branch `main`, folder `/ (root)`, and Save.
4. Wait for deployment and open the Pages URL. Relative paths support repository subdirectories.

Do not upload only index.html. The JavaScript, CSS and vendor files are required. For many vendor files, use GitHub Desktop or git instead of uploading them individually.

## Run locally

Run `python -m http.server 8000` inside the extracted folder, then visit http://localhost:8000. Do not double-click index.html: browsers can block PDF workers on file:// URLs.

## Features and precise limitations

- **Edit PDF:** add movable/resizable text, PNG/JPEG images and hand-drawn visual signatures. Click Replace text, click a detected text run, then double-click the replacement to type. Cover color supports nonwhite page backgrounds. Use Cover area and Add text for scanned text. Original font matching, text reflow, OCR and native PDF content-stream editing are not included. Rotated text and complex typography may need manual cover placement. Edited pages are flattened to images; untouched pages retain their PDF page content. This is not a certified redaction tool. Review the exported file. A hand-drawn signature is not a cryptographic digital signature.
- **Merge:** reorder files using arrows, then merge all their pages.
- **Delete pages:** thumbnail selection; cannot remove every page.
- **JPEG/PNG to PDF:** ordered image pages, A4 fitting or image-sized pages, full source image embedding.
- **DOCX to PDF:** semantic Word conversion with preview. Basic text, tables, and images; complex layouts, floating objects, headers and footers may be lost. Direct download produces image-based pages. Use Print / save searchable PDF for browser printing with searchable text, choose “Save as PDF” and turn off browser headers/footers.
- **Legacy DOC:** limited Word 97–2003 compound-binary main-text extraction. Text only; no formatting, images, tables, headers or footers. Non-Western legacy compressed encodings may not decode correctly. Password protection, older Word formats and RTF/HTML disguised as DOC are unsupported. Save unsupported documents as DOCX in Word or LibreOffice first. Review the preview before converting.
- **Compress:** lossless object-stream rewrite, or lossy rasterization at 80/120/160 DPI with JPEG quality choices. A smaller file is not guaranteed; the original is offered if output would be larger. Lossy compression removes selectable text and interactive features.

Page-copy operations may not preserve document-level forms, outlines/bookmarks, attachments or other metadata. Editing invalidates existing digital signatures. Password-protected PDFs are rejected. Original files are never overwritten. The per-file limit is 100 MB, image limit 40 megapixels; practical capacity depends on browser memory. Large documents can take time. Close/reload to clear in-memory documents; download results before leaving.

Test on current Chrome or Edge for the best experience. Desktop is recommended for precise PDF editing. Mobile includes touch signature drawing and horizontal scrolling for the page canvas.

## Privacy

Documents are processed on your device and are not sent to a conversion service. The host receives normal requests for app assets. No analytics, document storage, external fonts, or CDN scripts are used. Word HTML is sanitized; external image references are removed. PDF.js dynamic evaluation is disabled. Keep vendored libraries updated when maintaining the app.

## Files

- `index.html`, `style.css`, `app.js`: editable application source.
- `vendor/`: locally hosted dependencies, PDF fonts and character maps.
- `netlify.toml`, `.nojekyll`: deployment configuration.
- `THIRD_PARTY/`: library license notices.
- `VALIDATION.md`: verification record.

## Deployment references

- https://docs.netlify.com/start/quickstarts/netlify-drop-quickstart/
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

No deployment has been made to your accounts by this package.
