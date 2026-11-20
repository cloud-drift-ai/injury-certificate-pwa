INJURY CERTIFICATE – OFFLINE PWA
================================

This package converts the approved Injury Certificate Version 8 into an installable
Progressive Web App (PWA). Existing certificate fields, treatment options, injury
table, preview, printing and DOC export are retained.

CONTENTS
--------
index.html                 Injury Certificate application
manifest.webmanifest       PWA installation settings
service-worker.js          Offline application-shell cache
assets/icons/              Android, Windows and Apple app icons
DEPLOYMENT_GUIDE.md        Hosting and installation instructions
version.txt               Package version

IMPORTANT
---------
PWA installation and service-worker caching require HTTPS (or localhost for testing).
Opening index.html directly as a local file still works as a normal HTML application,
but does not install the PWA or activate service-worker caching.

There is no login, application backend, patient database or patient-data upload.
The service worker caches application files only; it does not cache patient form
entries or completed certificate contents.

QUICK START
-----------
1. Upload the CONTENTS of this folder to an HTTPS static host.
2. Open the HTTPS address on each device while online.
3. Install using the Android, iPhone/iPad or Windows instructions in DEPLOYMENT_GUIDE.md.
4. Open the installed app once online to cache the application.
5. Disconnect the internet and test the app before operational use.

UPDATES
-------
For a new release, change CACHE_NAME in service-worker.js (for example, v2), upload
the new files, and have devices reconnect to the HTTPS address.

Version 1.0.3 update: The Clear Form action has been removed. Preview Certificate is now the only primary form action.
