# 🏠 Rental Tracker

A single-file, offline web app for tracking one rented house in Malaysia:
4 tenants + 1 car parking bay, monthly rent collection, mortgage, maintenance fee,
TNB/water, and everything else — with a real net-profit figure per month.

## How to use

1. Open `index.html` in any browser (Chrome, Edge, Firefox, Safari).
   Double-clicking the file works — no server, no install, no internet needed.
2. Go to **Setup** and fill in:
   - Address / label
   - Monthly mortgage (RM)
   - Maintenance fee (RM)
   - Mortgage end date (optional, shows "months left")
3. Go to **Tenants & Parking** → add your 4 tenants and 1 parking row.
   Put the agreed monthly amount for each. Parking is its own row on purpose.
4. Every month, go to **Monthly Update** and type in:
   - Rent **received** per tenant (leave blank if unpaid)
   - Payment method, date, reference
   - Each expense amount
   - Optional TNB / water meter readings
5. Check **Dashboard** for income, owner costs, net profit, margin, outstanding rent.

Tip: **Copy previous month** brings last month's expense figures forward so you only
type the bills that changed. Rent received is reset, so you must re-enter it.

## The one concept that matters

Every expense category is flagged **who bears it**:

- **You (landlord cost)** → subtracted from profit. Mortgage, maintenance fee,
  assessment tax, quit rent, IWK sewerage, repairs, insurance, agent commission.
- **Tenant (recoverable)** → shown for information but *not* subtracted, because
  you get it back from rent. TNB electricity, water, internet.

This is why "net profit" here is honest: tenant-borne utilities don't inflate your
costs, and your mortgage does.

Annual/periodic items (assessment tax, quit rent, insurance) are only entered in the
month you actually pay them. Enter the full invoice that month, or divide it
yourself across the months you want — the app does not guess for you.

## Reading the numbers

| Figure | Meaning |
|---|---|
| Total income | Rent received (paid tenants only) + parking received |
| Owner costs | Everything you actually bear this month |
| Net profit | Total income − owner costs |
| Margin | Net profit ÷ total income |
| Outstanding | Rent agreed but not yet received |
| Tenant-borne | Costs inside/alongside rent, not your expense |

Outstanding rent is tracked but **not counted as income**, so your profit is never
flattered by a tenant who hasn't paid.

## Data & backup

Data is stored in the browser's localStorage on the device you use it on.
⚠️ Clearing browsing data erases it, and it does not sync between devices.

- **Export** (header or Setup) → downloads `rental-tracker-backup.json`. Save it to
  cloud drive monthly.
- **Import / Restore** → loads that file back, replacing current data.
- The **History** tab has **Export CSV** — opens directly in Excel.
- **Print** produces a clean black-on-white report of all sections, for your
  accountant.

There is no login because there is no server: the file is only readable by whoever
opens it on that machine. Don't store tenant bank details in the note fields.

## Suggested monthly routine (~5 minutes)

1. When each tenant pays, open **Monthly Update** and type the amount + method + date.
2. Once the TNB/water bill arrives, fill the expense amounts.
3. Put the mortgage in if it differs from the Setup default.
4. Glance at **Dashboard** — net profit, margin, anyone unpaid.
5. **Export** the JSON backup.

## Reference

Modelled on the data model used by these open-source projects, which were reviewed
as prior art:

- `microrealestate/microrealestate` — rents/leases/receipts, self-hosted, MIT
- `clawnify/OpenProperty` — units, tenants, leases, rent ledger, work orders
- `mohsin-rafique/property-management` — landlord/tenant cost splits (maintenance %,
  electricity sub-meter split, deposit deductions)

Deliberately dropped from those: roles & multi-user, tenant portal, PDF receipts,
e-mail, screening, leases. This is a single-owner, single-house monthly ledger.