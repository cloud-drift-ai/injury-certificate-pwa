# Injury Certificate PWA – Deployment Guide

## 1. Publish the package

The PWA must be served from an HTTPS address. A `file://` link cannot register a
service worker. Use a static host; no application server or database is required.

Upload the **contents** of this folder so these files are available from one HTTPS
origin: `index.html`, `manifest.webmanifest`, `service-worker.js`, and the files in
`assets/icons/`.

Static hosting options include GitHub Pages, Cloudflare Pages, or Netlify. Use an
organization-controlled account and enable HTTPS. Do not upload patient records,
completed certificates, or real patient data.

## 2. Android

1. Open the HTTPS application address in Chrome.
2. Choose **Install app**, or use the browser menu and select **Install app** /
   **Add to Home screen**.
3. Confirm installation.
4. Open the installed app once while online.

## 3. iPhone and iPad (iOS-compatible build)

1. Open the HTTPS application address in Safari.
2. Tap **Share**.
3. Select **Add to Home Screen**.
4. Keep **Open as Web App** enabled if that option appears.
5. Tap **Add**, then open the new home-screen icon once while online.

iOS behaviour varies by version. Test the actual device before operational use.

### Saving PDF and DOCX on iPhone/iPad
- Tap **Download PDF** or **Save as DOCX** in the certificate preview.
- On supported iOS versions, the iOS Share sheet opens.
- Choose **Save to Files**, then select the required folder and tap **Save**.
- If file sharing is not available on an older iOS version, the file opens in a new
  browser view; use Share > Save to Files from there.

## 4. Windows

1. Open the HTTPS address in Edge or Chrome.
2. Select the install icon in the address bar, if shown, or use the browser menu:
   **Apps > Install this site as an app**.
3. Confirm installation and open it once while online.

## 5. Test offline and exports

After the first successful online opening:

1. Close the application.
2. Enable airplane mode or disconnect Wi-Fi/mobile data.
3. Reopen Injury Certificate from its installed icon.
4. Test patient form entry, Add Injury, No Visible Injury, all three treatment options,
   Preview, Edit, Print, Download PDF and Save as DOCX.
5. Open the DOCX file in Microsoft Word or Google Docs and check the A4 page layout.
6. Open the PDF and check the A4 page layout and legibility.

The direct PDF action generates a PDF locally without opening the print dialog. It uses a
high-resolution image of the certificate to preserve layout; text in that PDF may not be
selectable. The DOCX export is a native Office Open XML `.docx` file generated locally.

Do not use the application operationally until offline reopening, PDF/DOCX exports and
printing have been tested on the actual devices and printers used by the health complex.

## 6. Updates

For each new release, change the cache name in `service-worker.js`, for example:

`const CACHE_NAME = "injury-certificate-v1-0-5";`

Upload all updated files. Devices should reconnect to the HTTPS address to fetch the
new version. Ask staff to open the app online before their next offline session.

## 7. Privacy and data handling

- No login, backend API or patient database is included.
- The service worker caches application files only.
- Form submissions and certificate contents are not stored by the service worker.
- Do not place completed certificates or patient information in the hosting folder.
- Close the app after printing/exporting and follow the health complex's confidentiality
  policy.
- Browser memory, file downloads and printing behaviour vary by device and browser.


## Version 1.0.4 – Consistent PDF typography
The certificate preview includes embedded Carlito (Calibri-metric-compatible) and Noto Sans Bengali font files. The Download PDF button remains disabled until these fonts load. The generated PDF is image-based, so its font appearance and line wrapping are fixed at generation time and are not substituted by PDF viewers.


## Version 1.0.5 – DOCX, legal reference and signature layout
- The preview action is now **Save as DOCX** and creates a genuine Office Open XML `.docx` file locally.
- The certificate body, injury table and signature labels use 11 pt text.
- Nature of injury offers Simple and Grievous selections. No Visible Injury prints N/A.
- The injury form includes a collapsed Section 320 statutory reference with a link to the official Bangladesh Laws website.
- Attending doctor details (name, designation, workplace, PDS code and BMDC code) print above the attending doctor's signature when entered.
- The DOCX signature table is positioned at the bottom of the final page. Pagination reserves room for it and moves injury rows to the signature page when needed.

Test with Microsoft Word and Google Docs on representative devices before official use. Check multi-page injury descriptions and confirm the final-page injury row and signatures remain together.
