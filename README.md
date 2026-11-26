# Financial Data Reconciliation & Budget Forecasting

**Python · pandas · NumPy · Excel · Financial analysis · Scenario forecasting**

An end-to-end financial analysis of a **simulated $60 million project budget (2030–2033)**. Starting with a raw general-ledger export, the project cleans and reconciles transactions, compares expenditure against the approved plan, estimates funding gaps, and identifies departments requiring management attention.

The initial case exercise was completed under an approximately **five-hour time constraint**. Documentation and presentation materials were developed further afterward. All financial figures are from a **fictional case study**, not a real employer or investment portfolio.

## Key findings

As of **June 30, 2032**, the project had spent **$45.96 million**, or **76.6% of its total funding**, with 62.5% of its planned duration elapsed. Actual spending exceeded the time-phased baseline by approximately **$7.22 million**.

| Metric | Result |
|---|---:|
| Total funding ceiling | $60.00M |
| Approved department baseline | $58.00M |
| Management reserve (already included in ceiling) | $2.00M |
| Posted actuals through June 2032 | $45.96M |
| Time-phased plan through June 2032 | $38.73M |
| Spending above phased plan | **$7.22M** |
| Funding remaining as of June 2032 | $14.04M |

### Forecast scenarios

| Scenario | Future spend | Cost at completion | Above $60M ceiling |
|---|---:|---:|---:|
| Department-submitted forecast (June 2032 vintage) | $19.83M | $65.79M | **$5.79M** |
| Recent spending relative to phased plan | $23.84M | $69.79M | **$9.79M** |
| Flat six-month burn rate (stress sensitivity) | $40.86M | $86.82M | **$26.82M** |

The **plan-phased continuation** provides a challenge/risk scenario, not a proven best estimate. The flat-burn calculation is deliberately presented as a stress sensitivity. Both primary scenarios imply a funding shortfall.

## Analytical workflow

### 1. Data cleaning and reconciliation

- Identified the correct field names in a raw export containing displaced headers and report-total rows.
- Standardized posting periods, transaction classifications, forecast vintages, identifiers, and signed amounts using the supplied accounting rules.
- Removed **18 confirmed duplicate copies ($159,832.69)** while preserving valid reversing entries.
- Maintained an audit trail and established **5,250 cleaned transaction lines** across actuals and historical/current forecasts.
- Disclosed source-control discrepancies rather than forcing cleaned detail to agree with printed subtotal cells.

### 2. Budget-versus-actual analysis

- Reconciled the **$58M approved baseline** across 10 departments, labor/non-labor categories, and the 48-month planning period.
- Compared posted actuals with **time-phased baseline spending**, not just the percentage of elapsed calendar time.
- Summarized spending by year, category, and department.
- Identified major historical department overruns: **Department 3 (+$1.85M), Department 7 (+$1.40M), and Department 4 (+$1.19M)**.

### 3. Scenario forecasting and recommendations

- Combined posted actuals through June 2032 with the applicable June-2032 forecast for July 2032–December 2033.
- Built an alternative forecast using recent actual spending relative to the corresponding phased plan.
- Evaluated a flat-burn stress case as a sensitivity, not a realistic base forecast.
- Recommended department-level estimate reviews, discretionary-spend controls, and **verification of feasible reductions** before claiming any savings.

## Methodology

**Version control:** Historical costs use only `Actual` / `Posted` entries through June 2032. Future submitted costs use the `Fcst Jun-32` vintage. The superseded `Fcst Dec-31` vintage is not added to current projections.

**Submitted forecast**

```text
Cost at completion = Posted actuals + June-2032 future forecast
```

**Recent spending relative to the phased plan**

```text
Recent spending factor = Jan–Jun 2032 actuals / Jan–Jun 2032 phased baseline
Future spend = Recent spending factor × Remaining phased baseline
Cost at completion = Posted actuals + Future spend
```

**Flat-burn stress sensitivity**

```text
Future spend = (Jan–Jun 2032 actuals / 6) × 18 remaining months
```

The $2M management reserve is **already part of** the $60M ceiling, not additional funding.

## Repository structure

```text
financial-data-reconciliation-forecasting/
├── Complete_Analysis.ipynb          # Reproducible cleaning, validation, scenarios, and analysis
├── Executive_Summary.pdf            # One-page management summary
├── ProjectX_Student_Data_Pack.xlsx  # Case-study input data (see data-use note below)
└── README.md
```

## Reproducing the analysis

1. Clone the repository:

   ```bash
   git clone https://github.com/Binhe-Jia/financial-data-reconciliation-forecasting.git
   cd financial-data-reconciliation-forecasting
   ```

2. Install the Python/Jupyter dependencies (Python 3.10+ recommended):

   ```bash
   python -m pip install notebook ipykernel numpy pandas matplotlib openpyxl
   ```

3. Confirm `ProjectX_Student_Data_Pack.xlsx` is in the same folder as `Complete_Analysis.ipynb`.
4. Open `Complete_Analysis.ipynb` in Jupyter and select **Kernel → Restart & Run All**.
5. Inspect the cleaning audit trail, validation checks, comparison scenarios, department watchlist, and data-quality exceptions. `Executive_Summary.pdf` contains the management-facing conclusions.

The notebook is the computational analysis; the repository **does not currently include a separately published, fully transaction-linked Excel reporting model or an oral presentation**.

## Data quality and limitations

- The printed FY2030, FY2031, and grand-total control cells do not agree with sums of the cleaned transaction records; differences are approximately **$0.44M, $1.37M, and $2.62M**. These exceptions remain explicitly unresolved.
- The submitted forecast is a planning estimate, not an audited commitment schedule.
- The recent-spending scenario assumes cost pressure persists and is sensitive to the chosen six-month observation window.
- Recommended cuts are **illustrative targets**, not demonstrated realizable contract or staffing savings.
- The reporting date is **June 2032 within the fictional scenario**, not today's date.

### Data-use note

The source workbook was supplied as part of a case exercise. Its presence here **does not imply a right to redistribute it**. Confirm the case provider permits public sharing; if not, remove the source workbook from the repository (and, if needed, Git history), and provide instructions for authorized users to obtain and place their own copy locally.

## Skills demonstrated

**Data preparation and validation:** Python, pandas, messy Excel extraction, deduplication, policy-based classification, reconciliation, traceable quality checks.

**Financial analytics:** Budget-versus-actual analysis, phased baselines, cash-spend forecasts, scenario comparisons, variance investigation, management recommendations.

**Communication:** Executive-summary writing, quantified risks, uncertainty disclosure, and decisions supported by reproducible analysis.

---

*Portfolio exercise for analytical demonstration. Figures are simulated and should not be interpreted as actual corporate financial results.*
