# QuickAuth for Windows

Download the installer and browser packages from [the latest release](https://github.com/Maxibon13/QuickAuth-Releases/releases/latest).

QuickAuth is a Windows authenticator with a Rust backend, a local encrypted vault protected by Windows Hello, and optional Chromium and Firefox extensions. This public repository contains compiled releases and documentation. The application source remains private.

## Install and update

Use the `QuickAuth-<version>-windows-x86_64.msi` asset on Windows 11 with Windows Hello and Microsoft Edge WebView2. Existing installations preserve their vault and Hello credential. Keep a passphrase-encrypted QuickAuth backup for recovery after a Windows profile or Hello reset.

Starting with 0.5.0, QuickAuth checks for updates after startup and every six hours. You can also choose **Check for updates…** from the tray. A newer stable version prompts you to update; **Later** postpones it for 24 hours. The app verifies the installer signature and signed version before installation, locks the vault, saves an encrypted recovery snapshot, and restarts after installation. Versions before 0.5.0 need the first updater release installed manually.

Update metadata is available at [latest.json](https://github.com/Maxibon13/QuickAuth-Releases/releases/latest/download/latest.json). The app pins the publisher's updater public key. The installer has an updater signature, but currently has no Windows Authenticode publisher certificate; Windows may display an unknown publisher on a manual download. `SHA256SUMS.txt` lists checksums for the release assets.

## Browser packages

- Chromium browsers: extract `QuickAuth.Chromium.zip`, open the browser's extensions page, enable Developer mode, and choose **Load unpacked**. The app also prepares `%LocalAppData%\QuickAuth\BrowserExtension`.
- Firefox 140+: extract `QuickAuth.Firefox.zip`, open `about:debugging#/runtime/this-firefox`, choose **Load Temporary Add-on**, and select `manifest.json`. This unsigned development install lasts until Firefox closes. Permanent installation requires Mozilla signing.

Both extensions connect to the installed Windows app and share its vault. Reload unpacked extensions after updating QuickAuth.

## Privacy and issue reports

Update checks request public metadata from GitHub. They do not send authenticator keys, codes, account names, or vault data. GitHub receives ordinary network connection information. OTP generation and vault access work locally.

Use a disposable test account when reporting a problem. Never upload real setup keys, QR images, vaults, backups, or generated codes to an issue.
