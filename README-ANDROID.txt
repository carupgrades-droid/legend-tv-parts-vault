LEGEND TV PARTS REPAIR VAULT — ANDROID PROJECT
==========================================

What this is
------------
This is the Android source project wrapping the existing offline TV Repair
Knowledge Vault in a native Android WebView shell. The app name on the device
is "Legend TV Parts Vault". The app stores entries in WebView local storage on that
device. It does not require an account or a server.

Important limitation
--------------------
This package is Android source code, not a precompiled APK. This workspace
does not have the Android SDK/Gradle toolchain installed, so it cannot truthfully
provide a tested installable APK from here. The included GitHub Actions workflow
can build a debug APK in the cloud after the project is uploaded to a GitHub
repository.

Build using a computer
----------------------
1. Install Android Studio.
2. Open this project folder.
3. Allow Gradle sync to complete.
4. Choose Build > Build Bundle(s) / APK(s) > Build APK(s).
5. The debug APK will be at:
   app/build/outputs/apk/debug/app-debug.apk

Build from a phone using GitHub Actions
---------------------------------------
1. Sign in to GitHub in your phone browser and create a NEW private repository.
2. Upload the contents of this ZIP into the repository (the files/folders inside
   the project folder, not the outer folder itself).
3. Open the repository's Actions tab and enable Actions if asked.
4. Select "Build Android APK" from the workflow list.
5. Tap "Run workflow".
6. When the run finishes successfully, open it and download the artifact named
   "tv-repair-vault-debug-apk". Unzip the artifact to get app-debug.apk.
7. Open the APK on Android and approve installation from that source if Android
   asks. Only install APKs you built yourself or trust.

For the web-only version
------------------------
The original standalone HTML version can also be used directly without compiling
Android code. It is included at:
app/src/main/assets/tv_repair_knowledge_vault_offline.html

Data and privacy
----------------
- No analytics, advertising SDK, or network permission is included.
- The app uses local browser/WebView storage. Export backups from inside the app
  regularly. Clearing app data or uninstalling can remove locally stored records.
- This is a debug build workflow, not a Play Store release pipeline. A Play Store
  release needs signing, policy checks, privacy disclosures, and testing.

Version: 1.0.0

UPGRADE 1.1.0 NOTES
- Uses a new local storage key (legendTvPartsVault_v3_clean) so the updated app starts with a clean workspace. Data under the old v2 key is not migrated or erased by this version.
- Adds stock cost value, potential sales value, and potential gross profit calculations.
- Adds manual market price and last-checked date fields.
- Adds compressed inventory photo attachments and experimental coarse visual similarity search against stored photos.
- Adds cross-compatible part records with model, alternate/original part number, relationship, evidence notes, and explicit verification status.
- Adds WebView file chooser handling for image selection and JSON backup restore.
- Visual photo matching is approximate only. OCR-based label reading is not included in this build; enter printed part numbers manually and verify compatibility against service information.


Version 1.2.0 upgrade notes
- Keeps the same localStorage database key so existing inventory can remain when updating the installed app. Back up before upgrading.
- Part cards can be tapped or edited with the Edit button; each card shows unit profit, margin, and total in-stock profit.
- Inventory supports multiple compressed part photos, market price and checked date, stock adjustment, and CSV export.
- Cross-compatible part links connect one inventory item to TV brands/models and alternate numbers; compatibility data is user-entered and must be verified.
- Adds bundled on-device ML Kit text recognition for label photos. OCR suggestions must be reviewed because characters can be misread; it does not verify compatibility.
- OCR image and text processing occurs locally on the device; no OCR service upload is used.

UPGRADE 1.4.0 NOTES
- Adds ML Kit barcode/QR scanning from a camera/gallery photo. Scanned values are searched against saved barcode values, SKUs, and part records; scanning does not identify external parts automatically.
- Adds TV model lookup against saved part model fields and user-entered cross-compatibility links. Verification status is displayed and compatibility must still be checked against reliable service information.
- Adds dedicated barcode/QR and shelf/bin location fields to inventory; both are included in CSV export and catalog PDF.
- Adds a printable catalog PDF export generated on-device, plus expanded spreadsheet CSV export.
- Improves JSON backup restore so part links are remapped correctly and inventory/compatibility views refresh after import. Full backup includes notes, inventory, photos, chapters, and compatibility links.
- Existing on-device storage key remains unchanged to preserve existing data. Export a JSON backup before installing/upgrading. APK build has not been executed in this workspace; use the included GitHub Actions workflow to compile and test the build.

Version 1.4.0 visible dashboard improvements: six shortcut tiles for add/edit part, part photos, OCR label scan, TV compatibility, market price tracking, and backup/export. App version is displayed in the header and footer.


UPGRADE 1.5.0 NOTES
- OCR recognized text is editable before applying it to the part number or notes. Editing the recognized text refreshes the suggested-part-number and add-to-notes controls.
- Updated the interface to a premium navy-and-gold theme with clearer focus states, stronger panel contrast, refined buttons, and more consistent visual hierarchy.
- Keeps the existing local storage key and inventory/backup data structure so installed data is preserved during an in-place upgrade. Export a JSON backup before upgrading as a precaution.
- Android versionCode 6 / versionName 1.5.0.
