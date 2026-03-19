# Morphix — Browser-Based Image Format Converter

A client-side image format conversion tool that processes up to 100 images simultaneously without uploading a single byte to any server. Built entirely with HTML, CSS, and vanilla JavaScript.

---

## Overview

Morphix converts images between WebP, JPEG, PNG, BMP, and GIF formats directly inside the user's browser using the HTML5 Canvas API. No backend, no installation, no accounts. Users drag and drop their images, select an output format, and download the converted files individually or as a single ZIP archive.

---

## Features

- Convert up to 100 images in a single session
- Five output formats: WebP, JPEG, PNG, BMP, GIF
- Drag-and-drop or file picker upload
- Optional quality control for lossy formats (1–100%)
- Optional resize with aspect ratio lock
- Batch download as a ZIP file via JSZip
- Original filename preserved on every converted file
- White background fill applied automatically when converting to formats that do not support transparency
- Fully client-side — no data ever leaves the browser

---

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript
- HTML5 Canvas API (image processing and format conversion)
- JSZip 3.10 (loaded on demand from cdnjs for ZIP generation)

---

## How It Works

Each image is loaded into an off-screen HTML5 Canvas element. The canvas is then exported as a Blob in the target format using the `toBlob()` API. For formats that do not support transparency — JPEG and BMP — a white background is drawn before the image is composited, preventing visual artifacts. The resulting Blob is kept in memory and made available for download via an object URL.

When the user requests a bulk download, JSZip is loaded from the CDN and all converted Blobs are packed into a single ZIP file client-side, then triggered as a browser download.

---

## Live Demo

To use the tool right now, paste this link into your browser:

```
https://ahmad-344.github.io/image-converter/
```

To run it on your local machine, download the `index.html` file and open it directly in any browser. No server or internet connection required after that point.

---

## Usage

**Conversion workflow:**

1. Select the desired output format from the format picker
2. Adjust quality and resize options if needed
3. Drag and drop images onto the upload area, or click to browse
4. Click "Convert All"
5. Download individual files or click "Download All" for a ZIP

---

## Browser Compatibility

| Browser | Support |
|---|---|
| Chrome 90+ | Full |
| Edge 90+ | Full |
| Firefox 89+ | Full |
| Safari 15+ | Full |

WebP output is supported in all modern browsers. BMP and GIF support depends on the browser's implementation of `canvas.toBlob()`.

---

## Deployment

If you want to publish this tool on your own GitHub Pages or Netlify account, follow the steps below.

**GitHub Pages:**

1. Upload `index.html` to a public GitHub repository (rename it `index.html` if needed)
2. Go to repository Settings > Pages
3. Set source to the `main` branch, root folder
4. Your site will be live at `https://your-username.github.io/repository-name/`

**Netlify:**

Drag and drop `index.html` onto the Netlify dashboard at netlify.com. The site goes live immediately with an auto-generated URL.

---

## Privacy

All image processing is performed locally in the browser. No images, filenames, or metadata are transmitted anywhere. The only external request made is a one-time load of the JSZip library from cdnjs when the user initiates a bulk ZIP download.

---

## License

MIT License. Free to use, modify, and distribute.
