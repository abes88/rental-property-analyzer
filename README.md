# Rental Property Investment Analyzer

A Claude Code slash command that performs comprehensive investment property analysis — pulling live market data, running the numbers, and delivering a professional report with a clear invest/pass verdict.

Paste a listing URL or property specs, get a full investment analysis in under 2 minutes.

## What You Get

A 9-section analysis covering:

| Section | What's in it |
|---------|-------------|
| **Executive Summary** | Purchase price, cash to close, monthly cash flow, cap rate, cash-on-cash return, DSCR, break-even rent |
| **Property Financial Breakdown** | Side-by-side comparison at 20%/25%/30% down; full monthly carrying cost breakdown |
| **Comparable Analysis** | Sale comps (1-mile and 5-mile), rent comps (low/median/high), three rent scenarios with NOI and cap rate |
| **Area & Economic Analysis** | Population growth, job growth, median income, major employers, infrastructure, crime, schools |
| **Rental Strategy Comparison** | Long-term rental metrics + short-term rental feasibility with local STR regulation check |
| **12-Month Cash Flow Table** | Month-by-month projection with principal paydown and cumulative equity tracking |
| **5-Year and 10-Year Projection** | Property value, loan balance, equity, cumulative cash flow, total ROI, and IRR |
| **Sensitivity Analysis** | Base case vs. rate +1%, vacancy 10%, rent -5%, and all three combined |
| **Final Investment Verdict** | Pass/fail on cash flow neutrality, strengths, risks, and what would make the deal work |

## Installation

Copy the slash command file into your Claude Code commands directory:

```bash
# Create the commands directory if it doesn't exist
mkdir -p ~/.claude/commands

# Copy the command file
cp analyze-property.md ~/.claude/commands/analyze-property.md
```

That's it. The command is now available in Claude Code.

## Usage

In any Claude Code session:

```
/analyze-property <listing URL or property specs>
```

**Examples:**

```
/analyze-property https://www.zillow.com/homedetails/123-Main-St/12345_zpid/

/analyze-property 3BR/2BA condo in Austin TX, asking $425,000, HOA $350/mo

/analyze-property 11216 Chestnut Grove Sq APT 317, Reston VA 20190 - $357,400
```

## What Data It Pulls

The analyzer searches for live data across these categories:

- **Mortgage rates** — Current 30-year fixed investment property rates
- **Rent comps** — Zillow Rent Zestimate, Rentometer, Redfin rental data
- **Sale comps** — Recent sold properties by radius, price/sqft, days on market
- **Area economics** — Population growth, job growth, median income, major employers
- **STR regulations** — Local short-term rental laws, permit requirements, restrictions
- **Insurance** — State/city average homeowners insurance costs
- **Historical appreciation** — 10-year average home price appreciation for the area

## Default Assumptions

These conservative defaults are used unless you override them:

| Parameter | Default |
|-----------|---------|
| Down payment | 25% (also shows 20% and 30%) |
| Loan term | 30-year fixed |
| Interest rate | Current national average from search |
| Closing costs | 2% of purchase price |
| Vacancy rate | 8% |
| Property management | 8% of gross rent |
| Rent assumption | 90% of market median (conservative) |
| Maintenance reserve | 1% of property value / year |
| Rent growth | 0% in base case |

Override any default by including it in your prompt:

```
/analyze-property https://zillow.com/... assume 20% down, 5% vacancy, self-managed
```

## Requirements

- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** — the CLI tool from Anthropic
- **pandoc** + **weasyprint** — for PDF export (optional but included in the command)

Install the optional PDF dependencies:

```bash
# macOS
brew install pandoc
python3 -m venv /tmp/pdfenv && /tmp/pdfenv/bin/pip install weasyprint

# Ubuntu/Debian
sudo apt install pandoc
python3 -m venv /tmp/pdfenv && /tmp/pdfenv/bin/pip install weasyprint
```

The analyzer saves both a `.md` and `.pdf` file to your Desktop automatically.

## Customization

The command file (`analyze-property.md`) is a plain markdown prompt — edit it to fit your investment criteria:

- **Change default assumptions** — adjust vacancy rate, management fee, down payment, etc. in the Phase 2 table
- **Add/remove output sections** — modify Phase 4 to include sections relevant to your market
- **Change the pass/fail criteria** — the default requires cash flow neutrality; adjust in the Rules section
- **Modify export behavior** — change the output path or disable PDF generation in Phase 5

## Example Output

See [`example-output.md`](example-output.md) for a complete analysis of a 4BR condo in Reston, VA — including a clear "pass" or "fail" verdict with the math behind it.

## License

MIT — see [LICENSE](LICENSE).
