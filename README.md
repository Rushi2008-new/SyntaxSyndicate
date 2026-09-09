# Syntax Syndicate

## Google Sheets setup

1. Create or open the Google Sheet where submissions should be stored.
2. Copy the Sheet ID from its URL. It is the text between `/d/` and `/edit`.
3. Open **Extensions > Apps Script**, paste the contents of [Code.gs](Code.gs), and replace `PASTE_YOUR_GOOGLE_SHEET_ID_HERE`.
4. Set `SHEET_NAME` to the exact name of the destination tab, usually `Sheet1`.
5. Deploy it as a **Web app** with **Execute as: Me** and **Who has access: Anyone**.
6. Use the deployment URL in `GOOGLE_APPS_SCRIPT_URL` near the top of the HTML file.

The HTML page sends one row per final submission. Previous difficulty-level answers are included as separate columns in that row. After changing Apps Script code, deploy a **new version** of the web app.
