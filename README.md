# HG Vault

A mobile-first, black-and-purple private-vault web app designed for Safari on iPhone.

## Deploy with GitHub Pages
1. Open **Settings → Pages** in this repository.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **main** and **/(root)**, then Save.
4. Wait for GitHub Pages to publish. The URL is usually `https://hugolocksgio-a11y.github.io/HG-vault/`.
5. Open that HTTPS URL in Safari. Use **Share → Add to Home Screen** to install it.

## Current features
- First-run six-digit PIN creation and confirmation.
- PIN-derived AES-GCM encryption for vault data, with PBKDF2-SHA-256 (310,000 iterations) for key derivation.
- Encrypted vault data stored in IndexedDB, with a migration path for existing localStorage vaults and a request for persistent browser storage.
- Create, edit, search and delete written notes; favourite notes.
- Import and preview photos/videos, import/export files, and record/play back voice notes where supported.
- Apple Find Devices shortcut to https://www.icloud.com/find.
- Fixed five-item bottom navigation and an offline app shell.

## Important limitations
- This is an early web-app MVP, not a professionally audited security product.
- A six-digit PIN has a small search space. The encrypted data and salt are stored locally, so someone who copies the browser storage can attempt offline PIN guesses. Use a strong PIN only as one layer of protection; do not store highly sensitive material until the design has been reviewed.
- The PIN is not recoverable. If you forget it, or Safari clears the site's storage, data may be permanently lost. There is no iCloud backup, cross-device sync, or secure transfer yet.
- Optional Face ID/device-biometric verification uses WebAuthn in supported Safari versions, but it is an extra check before the PIN—not a replacement for the PIN or a claim that Face ID itself encrypts the vault. This browser-only check is not a professionally audited second-factor security system. Decoy/duress PINs, secure deletion, sharing, and real-time device tracking inside the app are not implemented. Find My opens Apple's own service.
- IndexedDB usually allows substantially more storage than localStorage, but browser/device quotas still apply. No app can promise unlimited storage; very large collections may still hit the iPhone's available storage or browser quota. Keep separate backups of originals.
- Imported media is not bundled on first launch; add it from the device using **Add media**.
- The app does not access or store biometric data, and does not claim that Face ID encrypts or unlocks the vault.
