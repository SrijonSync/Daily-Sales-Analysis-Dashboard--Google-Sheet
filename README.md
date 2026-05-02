# Daily-Sales-Analysis-Dashboard--Google-Sheet

# 📊 Daily Sales Analysis Dashboard

A comprehensive multi-brand daily sales tracking and analysis dashboard built entirely in **Google Sheets / Excel**, using advanced formulas for real-time reporting across brands, locations, and time periods.

> ⚠️ This repository uses **dummy/anonymized data** for demonstration purposes. All brand names, figures, and personnel names are fictional.

---

## 🖼️ Overview

This dashboard tracks daily sales performance for a **multi-brand food & beverage business** operating across multiple locations. It provides granular insights at the brand, location, day, and month level — all driven by a single source-of-truth data sheet.

---

## 📁 Project Structure

```
sales-dashboard/
├── Daily_Sales_Analysis_DEMO.xlsx   ← Main dashboard file (dummy data)
├── README.md                        ← This file
├── screenshots/                     ← Dashboard screenshots
├── docs/
│   ├── formula_guide.md             ← Formula documentation
│   └── data_dictionary.md           ← Column & field definitions
└── sample_data/
    └── sample_input.csv             ← Sample DATA sheet format
```

---

## 📋 Sheet Structure

The workbook contains **22 sheets**, all driven by the `DATA` sheet:

| Sheet | Description |
|---|---|
| `DATA` | 📥 Main raw input — one row per brand/location/day |
| `Accounts` | Per-outlet daily sales lookup by date |
| `Date` | Daily view with targets vs actuals |
| `Brand` | Brand-wise performance with filters |
| `Location` | Location-wise breakdown |
| `Month` | Monthly summary with targets |
| `MoM` | Month-over-Month comparison |
| `DAY WISE` | Day-of-week performance analysis |
| `TARGET` | Budget/target per brand & location |
| `Avg. Sales` | Average daily sales by month |
| `Mnth & Mnth` | Side-by-side monthly brand comparison |
| `Summ_Location` | Location-wise Today/MTD/YTD |
| `Daily Input Check` | Input validation per outlet |
| `Sales SameCurrent Store` | Same-store sales comparison across years |
| `CC SameCurrent Store` | Same-store customer count comparison |
| `ABV SameCurrent Store` | Same-store average bill value comparison |

---

## 🔢 DATA Sheet — Column Reference

| Column | Field | Description |
|---|---|---|
| A | Year | Financial year (e.g. 2025) |
| B | Month | Month label (e.g. Jan-25) |
| C | Day | Day of week |
| D | Date | Actual date |
| E | Brand | Brand name |
| F | Category | Own Brand / Franchise |
| G | Location | Outlet location / zone |
| H | Target | Daily sales target |
| I | Actual | Actual sales achieved |
| J | CC | Customer count |

---

## 📐 Key Formulas Used

### SUMIFS (multi-condition aggregation)
```excel
=SUMIFS(DATA!I:I, DATA!$E:$E, $C2, DATA!$U:$U, ">="&$AE$2, DATA!$U:$U, "<="&$AF$2)
```

### XLOOKUP (dynamic lookups)
```excel
=XLOOKUP(AH2, AB:AB, AC:AC, "")
```

### Dynamic arrays — FILTER + UNIQUE + SORT
```excel
=SORT(UNIQUE(FILTER(DATA!E:E, (DATA!E:E<>"")*(DATA!E:E<>"BRAND NAME"))), 1, -1)
```

### Achievement % with error handling
```excel
=IFERROR(E2/D2, "")
```

### Month-over-Month growth
```excel
=IFERROR((E2/F2) - 1, "")
```

### Day-wise average (excluding zeros)
```excel
=SUM(D4:D127) / (COUNT(D4:D127) - COUNTIF(D4:D127, 0))
```

---

## 🏷️ Brands (Demo)

| Brand | Category |
|---|---|
| CrunchMaster | Chicken Fry |
| Velvet Crumble | Desserts |
| GreenBowl | Salads |
| Golden Wok | Chinese |
| JuicyPress | Juice |
| Bangkok Street | Thai |
| Deshi Ranna | Bangladeshi |
| Mishti Dokan | Bengali Sweets |
| La Bella Cucina | Italian |
| BrewNest | Coffee |
| Grill Street | Kebab |
| The Smoky Barrel | BBQ |
| Masala Mantra | Indian |
| Char & Coal | Kebab |

---

## 🗺️ Locations (Demo)

Outlets are grouped into zones:
- **Centre Zone** — CTA, CTD, CTC
- **North Zone** — CTN, CTG-1
- **South Zone** — CTS, CTG-2
- **East Zone** — Khilgaon, UIU
- **West Zone** — Banani, Gulshan
- **Outside** — Sylhet, Uttara, Mirpur

---

## 🚀 How to Use

1. **Download** `Daily_Sales_Analysis_DEMO.xlsx`
2. **Open** in Google Sheets (File → Import) or Microsoft Excel
3. **Navigate** to the `DATA` sheet to see the input format
4. **Replace** the dummy data with your own data following the same column structure
5. All other sheets will **auto-update** via formulas

### Adding New Data
- Add rows to the `DATA` sheet only
- Follow the exact column structure (Year, Month, Day, Date, Brand, Category, Location, Target, Actual, CC)
- All summary sheets update automatically

---

## ⚙️ Requirements

- **Google Sheets** (recommended) or **Microsoft Excel 365**
- Some features use Google Sheets-specific functions:
  - `IMPORTRANGE` — for pulling data from another sheet
  - `FILTER`, `UNIQUE`, `SORT` — dynamic array functions (available in Excel 365 too)
  - `COUNTUNIQUEIFS` — Google Sheets only (use `SUMPRODUCT` alternative in Excel)

---

## 📊 Metrics Tracked

- **Sales** — Daily, MTD, YTD vs Target
- **CC** (Customer Count) — Footfall per outlet
- **ABV** (Average Bill Value) — Sales ÷ Customer Count
- **Achievement %** — Actual vs Target
- **Y2Y Growth** — Year-over-Year comparison
- **M2M Growth** — Month-over-Month comparison
- **Same-Store Growth** — Performance of consistent outlets across years

---

## 📄 License

This project is shared for educational and portfolio purposes.  
Feel free to fork and adapt for your own use.

---

## 🙋 Author

Built and maintained as an internal sales operations tool.  
Shared as an open portfolio project with anonymized data.
