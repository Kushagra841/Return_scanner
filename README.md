# Return Packing Log

A copy of the Packing Scan Log (https://github.com/Kushagra841/scanner) for **returns**. Same page and features, with:

- Maroon theme so staff can tell it apart from the packing page at a glance.
- Its own Google Sheet and Apps Script (scans never mix with packing scans).
- Status column says `Return` instead of `Forward`.
- Its own saved data on the PC, so the packing page's waiting scans are never sent here and vice versa.

Live page: https://kushagra841.github.io/return_scanner/

## Files

| File | What it is |
|---|---|
| `index.html` | The page staff use (hosted by GitHub Pages) |
| `scan_server.gs` | The Google Apps Script inside the returns Google Sheet that receives and stores the scans |

## First-time setup of the returns Google Sheet

1. Create a new Google Sheet (for example "Return Packing Log").
2. **Extensions → Apps Script**, delete the sample code, paste in `scan_server.gs`.
3. Change `const ADMIN_KEY = "...";` to your own admin password. Save.
4. **Deploy → New deployment → type: Web app**. Execute as: **Me**. Who has access: **Anyone**. Deploy and allow access.
5. Copy the Web app URL (ends in `/exec`) and put it in `index.html` as `SCRIPT_URL`.
6. Run `setupMonthlyArchive` once to switch on the monthly archive.

## Updating the Google script later

1. Open the returns Google Sheet → **Extensions → Apps Script**.
2. Copy your current `const ADMIN_KEY = "...";` line.
3. Replace all the code with `scan_server.gs` from here, then put your `ADMIN_KEY` line back.
4. **Deploy → Manage deployments → ✏️ Edit → Version: New version → Deploy.** (Not "New deployment": that changes the web address the page sends to.)

`SECRET` must be the same in `scan_server.gs` and `index.html`.
