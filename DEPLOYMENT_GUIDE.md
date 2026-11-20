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

## 3. iPhone and iPad

1. Open the HTTPS application address in Safari.
2. Tap **Share**.
3. Select **Add to Home Screen**.
4. Keep **Open as Web App** enabled if that option appears.
5. Tap **Add**, then open the new home-screen icon once while online.

iOS behaviour varies by version. Test the actual device before operational use.

## 4. Windows

1. Open the HTTPS address in Edge or Chrome.
2. Select the install icon in the address bar, if shown, or use the browser menu:
   **Apps > Install this site as an app**.
3. Confirm installation and open it once while online.

## 5. Test offline

After the first successful online opening:

1. Close the application.
2. Enable airplane mode or disconnect Wi-Fi/mobile data.
3. Reopen Injury Certificate from its installed icon.
4. Test patient form entry, Add Injury, No Visible Injury, all three treatment
   options, Preview, Edit, Print and Save as DOC.
5. Test PDF output with the actual phones, computers and printers used by the clinic.

Do not use the application operationally until offline reopening and printing have
been tested on the actual devices.

## 6. Updates

For each new release, change the cache name in `service-worker.js`, for example:

`const CACHE_NAME = "injury-certificate-v2";`

Upload all updated files. Devices should reconnect to the HTTPS address to fetch the
new version. Ask staff to open the app online before their next offline session.

## 7. Privacy and data handling

- No login, backend API or patient database is included.
- The service worker caches application files only.
- Form submissions and certificate contents are not stored by the service worker.
- Do not place completed certificates or patient information in the hosting folder.
- Close the app after printing and follow the health complex's confidentiality policy.
- Browser memory, printing and file-export behaviour vary by device and browser.

## 8. Limitations

This is an offline-capable static PWA, not a medical-record system. HTTPS hosting is
needed for initial installation and later updates. If browser site data is cleared,
or the app is removed, it must be opened online again to cache the application.
