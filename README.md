# Ledger — Personal Finance Tracker

Ledger is an offline-first personal finance PWA designed around a spreadsheet workflow. It includes Quick Entry formulas and comments, income/expense/savings tracking, accounts, budgets, recurring transactions, reports, yearly analysis, goals, investments, receipt attachments, and JSON/CSV backup.

## Storage modes

- **Local browser storage (default):** works offline and requires no account. Data stays in that browser profile. Clearing browser storage can remove it, so use JSON backups.
- **Google Drive sync (optional):** stores one `Ledger data - Ledger.json` file in each user's own Google Drive. The app requests the Google Drive `drive.file` scope and only accesses the file created for Ledger. Local browser data is retained as a cache; connecting to an existing Drive file on a new device offers a choice to merge the browser's data or use the Drive copy.
- Independent record changes are merged by ID/key. If the same record is changed differently on two devices, Ledger asks whether to keep this device's version or the Drive version. Offline edits remain local until a sync can run. Sync when opening/returning to the app or use **Sync now**; it is not a real-time collaborative database.
- Google access tokens are kept in memory and are not written to localStorage. The OAuth Client ID is saved in that browser's settings; it is not a secret. Never put a client secret in this static app.

## Configure Google Drive

The site owner must configure OAuth before users can connect Drive:

1. Open [Google Cloud Console](https://console.cloud.google.com/), create/select a project, and enable **Google Drive API**.
2. Configure the OAuth consent screen. During development, add the Google accounts that will test the app. For a public audience, configure/publish the consent screen according to Google's current requirements.
3. Create an **OAuth client ID → Web application**.
4. Add the exact GitHub Pages origin under **Authorized JavaScript origins**, for example `https://YOUR-USERNAME.github.io`. The origin has no repository path. If using a custom domain, add that origin too.
5. Before publishing, optionally set `GOOGLE_CLIENT_ID_DEFAULT` in `index.html` to your public OAuth Web Client ID so visitors do not have to enter it themselves. Alternatively, enter the ID in the settings field for local testing. In Ledger, open **Data & Settings → Storage & Google Drive sync**, choose **Google Drive sync**, then click **Connect Google Drive** and approve access.
6. On the first device, if there is no Ledger file in Drive, the app creates it from that browser's current data. On another device, choose either **Merge this browser into Drive** or **Use Drive copy on this device** when prompted.

A GitHub Pages URL alone cannot create the OAuth project or authorize access to a user's Drive. Each user must consent with their own Google account. Google may show an unverified-app warning until the OAuth consent screen is configured and published appropriately.

## Main features

- **Spreadsheet formulas:** type `=200+300+600` in Quick Entry or amount fields; the amount evaluates to `1100` and the formula remains visible in the fx bar.
- **Comments:** notes on transactions and Quick Entry cells.
- **Transactions:** expense, saving/investment, income, transfer, and refund with category, account, payment method, merchant, tags, recurring source, and optional receipt image.
- **Budgets, recurring items, reports, yearly analysis, goals, and investments.**
- **Import/restore:** expense-grid copy/paste or CSV import, tab-separated row import, JSON backup/restore, and CSV export.
- **Dashboard Food grouping:** Breakfast, Lunch, Snacks, and Dinner are grouped under Food in category analytics.
- **PWA/offline:** installable from GitHub Pages. Local mode works offline; cloud sync requires internet.

## GitHub Pages

1. Upload the contents of this folder to the repository root, preserving the `icons/` folder.
2. Enable **Settings → Pages → Deploy from a branch → main / root**.
3. Open the published URL and configure Google OAuth if you want Drive mode.

The app uses relative paths and works from a repository sub-path. The service worker cache is versioned; after publishing, reload the site if an older build is cached.

## Privacy notes

Local mode stores data in the browser. Drive mode transfers ledger data only after the user explicitly connects Google Drive and grants permission. The file is stored in that user's Drive; other Ledger users do not share the file. Anyone who can access that Google account or its file may be able to access the ledger. Keep backups private, especially if they include receipt images.
