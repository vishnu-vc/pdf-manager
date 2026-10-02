# Validation record

Automated checks were run against a local HTTP server in headless Chromium.

Passed:
- Load and render a three-page PDF.
- Add text, select an existing text run for visual replacement, add an image, draw and add a signature.
- Export edited PDF with three pages; edited page flattened, untouched pages retain searchable text.
- Switch pages and restore editing objects.
- Merge two three-page PDFs; output has six pages in expected order.
- Remove page 2; output retains original pages 1 and 3.
- Convert JPEG and PNG images into a two-page PDF.
- Convert DOCX containing text, a table and an image into a PDF.
- Extract main text from a controlled Word 97–2003 binary fixture and export PDF. Broad compatibility with real-world legacy DOC variants has not been established.
- Image compression on a 3.09 MB noise-image PDF reduced output to approximately 118 KB (96.3%). This intentionally difficult test image is not representative of expected savings on ordinary documents.
- Attempt compression on a small text PDF; retain original when rasterized output would be larger.
- 390px mobile empty-state layout has no document-level horizontal overflow.
- Exported PDFs reopened successfully using PDF libraries; merge order and deletion contents were independently checked.
- JavaScript syntax check and remaining-flow browser error check passed.
- Desktop working surface visually inspected.

Not verified: deployment to a live Netlify/GitHub account, every mobile browser, complex/rotated PDFs, encrypted documents, long/complex Word pagination, all legacy DOC encodings, large-file memory limits, or print-dialog behavior across operating systems.

Read README.md for feature limits before using this on important documents.
