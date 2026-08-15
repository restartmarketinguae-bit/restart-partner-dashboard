# reSTART Partners & Athletes Dashboard

Internal dashboard for reception staff to look up partner/sponsor details, discount codes, and track service vouchers.

---

## Setup (10 minutes)

### Step 1: Create the Google Sheet

Create a new Google Sheet with **3 tabs** named exactly:

**Tab 1: `Athletes`**

| Name | Sport | Contract Start | Contract End | Discount Code | Discount % | Notes |
|------|-------|---------------|-------------|---------------|------------|-------|
| Khalifa Al Mansoori | MMA / Boxing | 2024-06-01 | 2025-06-01 | KHALIFA25 | 25 | Monthly 2 free sessions |

**Tab 2: `Partners`**

| Name | Category | Contract Start | Contract End | Referral Code | Discount % | Notes |
|------|----------|---------------|-------------|---------------|------------|-------|
| MOUV Pilates Studio | Fitness Studio | 2025-01-01 | 2025-12-31 | MOUV15 | 15 | Cross referral |

**Tab 3: `Vouchers`**

| Issued To | Type | Service | Issue Date | Expiry Date | Redeemed |
|-----------|------|---------|------------|-------------|----------|
| MOUV Pilates Studio | Partner | Sports Massage (60 min) | 2025-07-10 | 2025-10-10 | No |

**Important:**
- Date format: `YYYY-MM-DD` (e.g. `2025-08-14`)
- `Type` column in Vouchers: use `Athlete` or `Partner`
- `Redeemed` column: use `Yes` or `No`

### Step 2: Publish the Sheet

1. Open your Google Sheet
2. Go to **File → Share → Publish to web**
3. Select **Entire Document** and **Web page**
4. Click **Publish**
5. Copy the Sheet ID from the URL: `https://docs.google.com/spreadsheets/d/THIS_IS_YOUR_SHEET_ID/edit`

### Step 3: Connect to Dashboard

Open `index.html` and find this line near the top of the script:

```javascript
const SHEET_ID = '';
```

Paste your Sheet ID between the quotes:

```javascript
const SHEET_ID = '1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms';
```

### Step 4: Host on GitHub Pages

1. Create a new GitHub repository (e.g. `restart-dashboard`)
2. Upload `index.html` to the repo
3. Go to **Settings → Pages**
4. Source: **Deploy from a branch**
5. Branch: `main`, folder: `/ (root)`
6. Save

Your dashboard will be live at: `https://yourusername.github.io/restart-dashboard/`

---

## How It Works

- Dashboard auto fetches data from Google Sheets every time someone opens or refreshes
- Contract status is calculated automatically (Active / Expiring Soon / Expired)
- "Expiring Soon" triggers at 30 days before contract end
- Click any discount code to copy it to clipboard
- Expand arrow shows extra notes for each entry
- Voucher tracker filters by All / Pending / Redeemed
- Search works across names, codes, categories

---

## Updating Data

Just edit the Google Sheet. Changes show on the dashboard next time anyone opens or clicks Refresh. No code changes needed.
