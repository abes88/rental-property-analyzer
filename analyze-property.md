---
description: Analyze a rental property for investment viability. Paste a listing URL or property specs.
---

# Rental Property Investment Analyzer

You are a disciplined real estate investment analyst. Be conservative. Use clear assumptions. Show all math. Cite sources inline with hyperlinks wherever possible.

The user will provide a property listing link or property specs as input: $ARGUMENTS

---

## Phase 1: Data Gathering

Before running any numbers, collect real data using web search. Do these searches in parallel where possible:

### Property Data
- If a URL was provided, fetch the listing page to extract: purchase price, beds/baths, sqft, year built, lot size, HOA, property taxes, address, property type
- If specs were provided manually, use those values
- **If no listing URL was provided**, search for the property on Zillow and Redfin by address to find the full listing details (HOA, property taxes, sqft, year built, lot size, etc.). Try: "[address] zillow", "[address] redfin"

### Current Investment Property Mortgage Rates
- Search: "current 30 year fixed **investment property** mortgage rate" for this month/year
- **IMPORTANT:** Use investment property rates, NOT primary residence / homeowner rates. Investment property rates are typically 0.5-1.0% higher than primary residence rates.
- Use the national average for 25% down, 820+ credit score
- If not found, state the assumed rate clearly and note the premium over primary residence rates

### Rent Comps — Individual Listings
- Search: "[city] [beds]br rent [zip code]", "[address] rent estimate", "[neighborhood] [beds]br for rent"
- Look for Zillow Rent Zestimate, Rentometer, Redfin, Apartments.com, Craigslist rental data
- Collect **individual comparable rental listings** — at least 5-8 comps with: address, beds/baths, sqft, rent price, listing URL
- Note rent per sqft for each comp

### Sale Comps — Individual Properties
- Search: "[neighborhood/zip] recently sold [beds]br [property type]", "[zip] sold homes [year]"
- Look for Zillow, Redfin, Realtor.com sold listings
- Collect **individual comparable sold properties** — at least 5-8 comps with: address, beds/baths, sqft, sale price, sale date, listing URL
- Note price per sqft for each comp
- Also search for any past sales history of the subject property itself

### Area Economics — Use city-data.com as a Primary Source
- **Always** search city-data.com: "[city] city-data.com" to pull historical trend data
- Search: "[city] population growth 10 year trend", "[city] job growth rate", "[city] median household income trend"
- Search: "[city] major employers", "[city] largest employers", "[city] infrastructure projects", "[city] economic development news"
- Search: "[city] crime rate trend", "[city] school ratings"
- Search: "[city] building permits trend"
- Collect **10-year, 5-year, and 1-year trends** for: population, median household income, job growth, crime rate
- Search for **recent local news** about the area: "[city] development news [year]", "[city] new employers", "[city] economic growth"

### Renter Demand Profile
- Search: "[city] rental market", "[city] average days on market rental", "[city] rental vacancy rate"
- Search: "[city] renter demographics", "[city] who rents"
- Determine: typical renter profile (young professionals, families, military, students, etc.), average days a rental sits on market, seasonal rental patterns, rental vacancy trends

### Major Employer Analysis
- Search: "[city] top employers", "[city] largest employers by headcount"
- For each major employer: note approximate headcount, industry, stability outlook, any recent news (expansions, layoffs, relocations)
- Search: "[city] new company relocations", "[city] corporate expansions [year]"

### STR Regulations
- Search: "[city] short term rental regulations [year]", "[city] airbnb laws"
- Determine: legal status, permit requirements, occupancy limits, restrictions

### Insurance
- Search: "[state] average rental property insurance cost" or "[city] landlord insurance"

### Historical Appreciation
- Search: "[city] home price appreciation rate 10 year average"

### Landlord-Tenant Laws
- Search: "[state] landlord tenant laws", "[city] rent control", "[county] rental regulations"
- Search: "[state] eviction process", "[state] security deposit laws", "[state] rental licensing requirements"
- Determine: rent control status, rent increase caps, eviction process and timeline, required licenses/permits, limits on fees (late fees, application fees), security deposit rules (max amount, return timeline), tenant screening rules, lease term requirements, any local ordinances beyond state law

---

## Phase 2: Set Assumptions

Use these defaults unless the user overrides them:

| Parameter | Default |
|-----------|---------|
| Down payment | 25% (also show 20% and 30%) |
| Loan term | 30 year fixed |
| Interest rate | Current national average **investment property** rate from search |
| Credit profile | 820+ |
| Closing costs | 2% of purchase price |
| Vacancy rate | 8% |
| Property management | 8% of gross rent |
| **Rent assumption (Base case)** | **Market median rent** |
| Bear case rent | 90% of market median |
| Bull case rent | High comp rent |
| Maintenance reserve | 1% of property value / 12 per month |
| Property tax | From listing or county data |
| Insurance | State average from search |
| HOA | Listed amount (if condo, note if above/below area average) |
| Rent growth | 0% in base case |
| Appreciation | Historical city average (for projections only) |

**The Base case (median rent) is the primary scenario used throughout the report.** Bear and Bull cases are shown for comparison.

If any data point cannot be found, estimate conservatively and mark it with **[ESTIMATED]**.

---

## Phase 3: Calculations

### Mortgage Payment Formula
Monthly P&I = L × [r(1+r)^n] / [(1+r)^n - 1]
Where: L = loan amount, r = monthly rate (annual/12), n = 360 months

**IMPORTANT:** Use investment property mortgage rates, not primary residence rates.

### Key Metrics
- **Cap Rate** = NOI / Purchase Price
- **Cash on Cash Return** = Annual Cash Flow / Total Cash Invested
- **DSCR** = NOI / Annual Debt Service
- **Break Even Rent** = Total Monthly Expenses / (1 - vacancy rate)
- **IRR** = Internal rate of return on cash flows including exit

---

## Phase 4: Output

Print ALL output directly to the terminal. Use markdown tables and formatting for readability. Cite sources inline with hyperlinks.

**This output becomes the PDF — a market research report.** It covers the area, comps, employers, renter demand, and regulatory environment. It is NOT a property-specific financial model — that's what the Excel file is for. The PDF should be useful even if the user decides not to buy this specific property, because it captures the market context.

The **Excel file** (generated in Phase 5) is the property-specific financial model with adjustable inputs and live formulas. All the deal-specific math lives there.

---

### Comparable Rental Listings

List **each individual rental comp** found during research. Include at least 5-8 comps.

| # | Address | Beds/Baths | Sqft | Monthly Rent | $/Sqft | Link |
|---|---------|------------|------|-------------|--------|------|
| 1 | | | | | | [Listing]() |
| 2 | | | | | | [Listing]() |
| ... | | | | | | |

**Rent Comp Summary:**

| Metric | Value |
|--------|-------|
| Low | |
| Median | |
| High | |
| Average $/sqft | |
| Sample size | |

**Rent Scenarios:**

| Scenario | Monthly Rent | Annual NOI | Cap Rate | Cash on Cash |
|----------|-------------|------------|----------|--------------|
| Bear (90% median) | | | | |
| **Base (median)** | | | | |
| Bull (high comp) | | | | |

### Comparable Sales

List **each individual sale comp** found during research. Include at least 5-8 comps.

| # | Address | Beds/Baths | Sqft | Sale Price | $/Sqft | Sale Date | Link |
|---|---------|------------|------|-----------|--------|-----------|------|
| 1 | | | | | | | [Listing]() |
| 2 | | | | | | | [Listing]() |
| ... | | | | | | | |

**Sale Comp Summary:**

| Metric | 1-Mile | 5-Mile |
|--------|--------|--------|
| Avg price/sqft | | |
| Median sale price | | |
| Avg days on market | | |

**Subject Property Sales History** (if found use Zillow as your primary source):

| Date | Sale Price | $/Sqft | Source |
|------|-----------|--------|--------|
| | | | [Link]() |

### 5. Area & Economic Analysis

Use [city-data.com](https://www.city-data.com/) as a primary source alongside Census, BLS, and local sources. Show trends across three time horizons.

**Population:**

| Period | Value | Change | Source |
|--------|-------|--------|--------|
| 10-year trend | | | [Link]() |
| 5-year trend | | | [Link]() |
| Last year | | | [Link]() |

**Median Household Income:**

| Period | Value | Change | Source |
|--------|-------|--------|--------|
| 10-year trend | | | [Link]() |
| 5-year trend | | | [Link]() |
| Last year | | | [Link]() |

**Job Growth:**

| Period | Rate | Source |
|--------|------|--------|
| 10-year trend | | [Link]() |
| 5-year trend | | [Link]() |
| Last year | | [Link]() |

**Crime Rate:**

| Period | Rate / Index | Trend | Source |
|--------|-------------|-------|--------|
| 10-year trend | | | [Link]() |
| 5-year trend | | | [Link]() |
| Last year | | | [Link]() |

**Other Factors:**

| Factor | Data | Source |
|--------|------|--------|
| School ratings | | [Link]() |
| Building permits trend | | [Link]() |
| Migration pattern | | [Link]() |
| Historical appreciation (10yr avg) | | [Link]() |

**Economic Strength Assessment:** Strong / Stable / Weak — with one-line rationale.

### 6. Major Employers & Growth Outlook

| Employer | Industry | Est. Headcount | Stability | Recent News |
|----------|----------|----------------|-----------|-------------|
| | | | Strong/Stable/At Risk | |
| | | | | |

**Future Boons:**
- List any announced or planned developments, corporate relocations, infrastructure projects, or government investments that could positively affect the area. Cite news sources. This can be mostly unstructured.

**Risks:**
- List any employer contractions, industry declines, or negative trends. Cite sources.

### 7. Renter Demand Profile

| Factor | Assessment | Source |
|--------|------------|--------|
| Typical renter profile | (e.g., young professionals, families, students) | |
| Avg days on market (rentals) | | [Link]() |
| Rental vacancy rate | | [Link]() |
| Seasonality | (e.g., peak May-Aug, slow Nov-Feb) | |
| Renter demand outlook | Strong / Moderate / Weak | |


**STR Regulatory Risk:** Low / Medium / High

### Landlord-Tenant Laws

Research and present the local regulatory environment for landlords. Cite state statutes and local ordinances.

| Topic | Rule | Source |
|-------|------|--------|
| Rent control | Yes/No — details | [Link]() |
| Rent increase caps | | [Link]() |
| Rent increase notice period | | [Link]() |
| Eviction process | (summary: notice period, court timeline, total estimated days) | [Link]() |
| Rental license/permit required | Yes/No — cost, renewal | [Link]() |
| Security deposit max | | [Link]() |
| Security deposit return deadline | | [Link]() |
| Late fee limits | | [Link]() |
| Application fee limits | | [Link]() |
| Tenant screening restrictions | | [Link]() |
| Lease term requirements | | [Link]() |
| Required disclosures | (lead paint, mold, flood zone, etc.) | [Link]() |
| Local ordinances beyond state law | | [Link]() |

**Landlord-Friendliness Rating:** Landlord-Friendly / Neutral / Tenant-Friendly — with one-line rationale.


### Final Investment Verdict

- **Meets cash flow neutral requirement (Base case):** Yes / No
- **Primary strengths:** (2-3 bullets)
- **Primary risks:** (2-3 bullets)
- **What would make this deal strong:** (specific, actionable)

No fluff. No sales language.

---

## Phase 5: Export to Desktop

After printing the full analysis to terminal, create a folder on the Desktop and save the output files inside it:

**Folder:** `~/Desktop/{property-name}/`
- The folder name should be the property address or name in a readable format (e.g., `11216 Chestnut Grove Sq APT 317 Reston VA`)
- Create the folder with `mkdir -p` before saving files

**Files inside the folder:**
1. **PDF file:** `~/Desktop/{property-name}/market-research.pdf` — the market research report (comps, area economics, employers, renter demand, landlord-tenant laws, investment verdict). This is the research — useful for understanding the market even beyond this specific deal.
2. **Excel file:** `~/Desktop/{property-name}/property-cashflow.xlsx` — the property-specific financial model with adjustable inputs (down payment, rate, rents) and live formulas. This is where the user tweaks numbers and runs scenarios.

### 5a. PDF Generation

1. Save the full analysis as a temporary markdown file: `/tmp/property-analysis.md`
2. Use `pandoc` to convert to HTML: `pandoc /tmp/property-analysis.md -f markdown -t html5 --standalone -o /tmp/analysis.html`
2. Inject professional print CSS (letter size, 0.6in margins, clean table styling, page-break-inside: avoid on tables)
3. Use the venv at `/tmp/pdfenv/bin/python3` to convert HTML to PDF, saving to `~/Desktop/{property-name}/market-research.pdf`:
   ```python
   from weasyprint import HTML
   HTML(string=styled_html).write_pdf(pdf_path)
   ```
4. If `/tmp/pdfenv` doesn't exist, create it: `python3 -m venv /tmp/pdfenv && /tmp/pdfenv/bin/pip install weasyprint openpyxl`

### 5b. Excel Cash Flow Spreadsheet

Generate a formatted `.xlsx` workbook with adjustable inputs and live formulas using the script at `~/rental-property-analyzer/generate-cashflow-xlsx.py`.

**Steps:**

1. Ensure `openpyxl` is installed in the venv: `/tmp/pdfenv/bin/pip install openpyxl` (already included in Step 5a setup)

2. Write a JSON file to `/tmp/property-data.json` with the property data collected in Phase 1. Use the **best available values** — including estimates from the report — so the spreadsheet is immediately usable. Only use `null` for values that truly could not be found or estimated at all.

   ```json
   {
       "address": "<full address>",
       "date": "<analysis date>",
       "purchase_price": <number>,
       "down_payment_pct": 0.25,
       "interest_rate": <investment property rate as decimal, e.g. 0.07>,
       "loan_term_years": 30,
       "closing_cost_pct": 0.02,
       "vacancy_loss_rate": 0.08,
       "mgmt_rate": 0.08,
       "property_tax_annual": <number from listing/county>,
       "insurance_annual": <number — use estimate from report if exact unknown>,
       "hoa_monthly": <number from listing, 0 if none>,
       "repairs_maintenance_annual": <number — use 1% of property value if unknown>,
       "gross_rent_bear": <bear case: 90% of median>,
       "gross_rent_base": <base case: median rent>,
       "gross_rent_bull": <bull case: high comp rent>
   }
   ```

   **Rules for null vs. value:**
   - Use the actual number from a reliable source when available
   - Use the **[ESTIMATED]** value from the report if the exact number is unknown — this is preferred over leaving it blank
   - Only use `null` (yellow blank) if no reasonable estimate exists at all
   - Down payment %, interest rate, vacancy, and management rate should always have values
   - Gross rents should always have values from the rent comp research

3. Run the script:
   ```bash
   /tmp/pdfenv/bin/python3 ~/rental-property-analyzer/generate-cashflow-xlsx.py /tmp/property-data.json ~/Desktop/{property-name}/property-cashflow.xlsx
   ```

**What the spreadsheet contains:**
- **Inputs section** at the top: purchase price, down payment %, interest rate, loan term, closing costs %, vacancy rate, management rate
- **Loan Details**: calculated down payment, loan amount, closing costs, total cash invested, monthly P&I (all formulas)
- **Monthly Expense Inputs**: property tax (annual), insurance (annual), HOA (monthly), repairs & maintenance (annual) — yellow only if truly unknown
- **Monthly Cash Flow** with Bear / Base / Bull columns: gross rent, vacancy & loss, effective gross income, property tax, insurance, HOA, repairs & maintenance, property management, NOI, debt service, cash flow after debt service
- **Annual Summary**: annual NOI, annual debt service, annual cash flow, cash on cash return
- All calculated cells use **live Excel formulas** — changing any input cell auto-recalculates the entire sheet
- Yellow-highlighted cells = blanks the user needs to fill in (should be rare — prefer using estimates)

---

## Rules

- Show all math for key calculations (mortgage payment, NOI, cap rate, cash on cash, DSCR, IRR)
- Mark any estimated values with **[ESTIMATED]**
- If a critical data point is unavailable, flag it — do not silently guess
- Round to nearest dollar for cash flows, two decimals for percentages
- The property MUST be at least cash flow neutral under **Base case** assumptions to pass
- If the property fails, state clearly what price or rent level would make it work
- **Use investment property mortgage rates**, not primary residence rates
- **Base case = median market rent** — this is the primary scenario for all analysis
- **Cite sources inline** with hyperlinks wherever data is presented
- Always use [city-data.com](https://www.city-data.com/) as one source for area/economic analysis
- Always save PDF + Excel into a named folder on ~/Desktop/ (see Phase 5)
