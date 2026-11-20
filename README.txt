INJURY CERTIFICATE – OFFLINE PWA
================================

Version 1.0.1

This package contains the approved Injury Certificate application as an offline-capable
Progressive Web App (PWA).

Version 1.0.1 changes:
- Word-compatible DOC export now uses fixed-width HTML tables rather than Flexbox/Grid.
- Added a direct Download PDF action in the certificate preview. It generates an A4 PDF
  locally in the browser and does not open the print dialog.
- Existing Print, Edit, treatment options, injury table and certificate fields remain.

CONTENTS
--------
index.html                 Injury Certificate application
manifest.webmanifest       PWA installation settings
service-worker.js          Offline application-shell cache
assets/icons/              Android, Windows and Apple app icons
DEPLOYMENT_GUIDE.md        Hosting, installation and update instructions
README.txt                 This file
version.txt               Package version

IMPORTANT
---------
PWA installation and service-worker caching require HTTPS (or localhost for testing).
Opening index.html directly as a local file still works as a normal HTML application,
but does not install the PWA or activate service-worker caching.

There is no login, application backend, patient database or patient-data upload.
The service worker caches application files only; it does not cache patient form
entries or completed certificate contents. The preview and file export include iOS
Safari support, including the iOS Share sheet for Save to Files. The preview and file export include iOS
Safari support, including the iOS Share sheet for Save to Files.

The direct PDF file is created locally on the device. It is rendered as a high-resolution
page image to preserve the certificate's layout consistently; PDF text may not be
selectable/searchable. The DOC export is a Word-compatible HTML .doc file built with
table-based formatting. It is not a native .docx file.

QUICK START
-----------
1. Upload the CONTENTS of this folder to an HTTPS static host.
2. Open the HTTPS address on each device while online.
3. Install using the Android, iPhone/iPad or Windows instructions in DEPLOYMENT_GUIDE.md.
4. Open the installed app once online to cache the application.
5. Disconnect the internet and test the form, DOC export and PDF download.

UPDATES
-------
For a new release, change CACHE_NAME in service-worker.js (for example, v1-0-2), upload
the new files, and have devices reconnect to the HTTPS address.
