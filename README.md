# Ledger — Personal Finance Tracker

Ledger is an offline-first personal finance PWA designed around a fast spreadsheet workflow. It keeps the original Quick Entry grid, but now adds spreadsheet formulas, comments, income/expense/transfer tracking, accounts, payment methods, budgets, recurring transactions, reports, yearly analysis, goals, investments, receipts, and JSON/CSV backup.

## Main features

- **Spreadsheet formulas:** type `=200+300+600` in the Quick Entry grid or amount fields and press Enter to save `1100`. The formula is retained with the transaction and is shown in a spreadsheet-style fx formula bar whenever you select the Quick Entry cell.
- **Comments:** every transaction can have a comment; Quick Entry cells have a dedicated comment box and optional comment prompt.
- **Transactions:** expense, saving/investment, income, transfer, and refund with category, account, payment method, merchant/payee, tags, recurring source, and optional receipt image.
- **Accounts:** simple Cash / Bank / Credit Card / Wallet / Investment / Other accounts with balances and opening balances.
- **Budgets:** monthly category budgets with progress and over-budget warnings.
- **Recurring:** monthly recurring income/expenses with one-click generation of due items.
- **Reports:** date-range category, merchant, payment-method, and monthly comparisons.
- **Yearly Analysis:** monthly income, expenses, net savings, and category breakdown.
- **Goals:** savings targets and progress.
- **Investments:** invested value, current value, gain/loss, and return percentage.
- **Quick actions:** duplicate, split, delete with undo, category reordering, and CSV-safe export.
- **Import/restore:** older 3-column spreadsheet imports are still supported, plus richer tab-separated imports.
- **PWA/offline:** installable from GitHub Pages; data is stored locally in the browser.

## Data and privacy

The app stores its data locally in the browser. No account or server is required. JSON backup is recommended before clearing browser data or moving to a different device. Receipts are stored locally inside the backup data, so keep backups private.

## GitHub Pages

1. Create a GitHub repository.
2. Upload the contents of this folder, preserving the `icons/` and `store-assets/` folders.
3. Enable **Settings → Pages → Deploy from a branch → main / root**.
4. Open the generated `github.io` URL.

The app uses relative paths, so it works from a repository sub-path as well as a root domain.

## Existing data migration

The upgraded app uses a v3 local data model with date-driven month navigation. If the browser already contains Ledger v1 data under `ledger_expense_data_v1`, the first load migrates those transactions into the v2 model automatically. Existing entries remain expenses and are assigned to the default Cash account until you edit them.

## Backup format

JSON backups include transactions, formulas, comments, receipt attachments, categories, accounts, payment methods, budgets, recurring rules, goals, and investments. CSV export contains the transaction ledger in a spreadsheet-friendly format.

- **Savings / Investments:** Mutual Fund, Equity, Gold Chit, or Savings can be entered as a separate Saving / Investment type; they are excluded from expense totals but reduce remaining cash flow.
- **Quick Entry modes:** Expense, Saving / Investment, and Income can each be entered with spreadsheet formulas and comments.


### Month navigation
The dashboard, Quick Entry, and transaction filters expose the current month plus a 36-month history and 36-month planning window. Existing transaction/budget/recurring months outside that window remain available too.
