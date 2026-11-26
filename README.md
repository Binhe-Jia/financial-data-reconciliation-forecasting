# Financial Data Reconciliation & Budget Forecasting

**Python · pandas · NumPy · Excel · Financial analysis · Scenario modeling**

An end-to-end analysis of a **simulated $60 million, four-year project budget**, from a messy general-ledger export to a management-ready funding assessment. The case combines transaction cleaning, financial reconciliation, spending analysis, forecast comparison, and department-level variance investigation.

The initial exercise was completed under a roughly five-hour time constraint; the documentation and reporting artifacts were expanded afterward. The figures describe a **fictional case study**, not an actual employer or investment portfolio.

## Executive summary

**As of June 2032, Project X had spent $45.96 million (76.6% of its funding) after 62.5% of its planned timeline.** Spending exceeded the time-phased baseline by **$7.22 million**. Both the department-submitted forecast and a recent-spending-based projection indicated that the project would exceed its **$60 million funding ceiling**.

| Measure | Result |
| --- | ---: |
| Total funding ceiling | $60.00M |
| Approved department baseline | $58.00M |
| Management reserve (included in funding ceiling) | $2.00M |
| Posted actual spending through June 2032 | $45.96M |
| Planned spending through June 2032 | $38.73M |
| Spending above time-phased plan | **$7.22M** |
| Funding remaining at reporting date | $14.04M |

### Projected cost at completion

| Scenario | Estimated future spend | Total estimated cost | Over $60M ceiling |
| --- | ---: | ---: | ---: |
| Department-submitted forecast (June 2032 vintage) | $19.83M | $65.79M | **$5.79M** |
| Recent spending relative to the phased plan | $23.84M | $69.79M | **$9.79M** |
| Flat six-month burn rate (stress sensitivity) | $40.86M | $86.82M | **$26.82M** |

The **plan-phased projection** is used as a conservative *challenge scenario*, not as a proven best estimate. The flat burn-rate projection is a stress test rather than the base case.

## What the analysis covers

### 1. General-ledger cleaning and validation

- Corrected misplaced spreadsheet headers, report totals, mixed posting-period formats, and inconsistent field types.
- Standardized record types, forecast versions, departments, transaction classes, account codes, descriptions, and signed dollar amounts using the case's accounting rules.
- Identified **18 exact duplicate copies** totaling **$159,832.69** and excluded those copies while retaining legitimate reversal entries.
- Retained an audit trail and verified the resulting **5,250 cleaned transaction lines** across actuals and forecast vintages.
- Separated posted actuals from superseded and current forecast versions to avoid double counting.

### 2. Spending and budget variance analysis

- Reconciled the approved **$58M baseline** across 48 months and 10 departments, broken out by labor and non-labor costs.
- Compared actual expenditures with the **monthly phased budget**, rather than assuming spending should progress evenly with calendar time.
- Summarized expenditures by year, cost class, and department.
- Flagged the largest historical department overruns: **Department 3 (+$1.85M), Department 7 (+$1.40M), and Department 4 (+$1.19M)**.

### 3. Forecasting and management recommendations

- Evaluated the current department-submitted forecast against an alternative projection based on recent spending relative to the phased plan.
- Tested a third, intentionally aggressive flat-burn scenario.
- Quantified funding gaps and identified the departments requiring updated cost estimates and commitment reviews.
- Recommended spending controls, revised estimates to complete, and **verified** reductions sufficient to close the forecast shortfall. Proposed reduction targets are illustrative, not confirmed savings.

## Methods

**Forecast selection:** Historical expenditure includes only `Actual` / `Posted` records through **June 2032**. Future expenditure uses the `Fcst Jun-32` vintage for **July 2032–December 2033**; the superseded `Fcst Dec-31` vintage is not added to the current forecast.

**Submitted completion estimate**

```text
Completion cost = Posted actuals + June-2032 submitted future forecast
```

**Recent spending / phased-plan scenario**

```text
Recent spending factor = Jan–Jun 2032 actuals / Jan–Jun 2032 phased baseline
Projected future spend = Recent spending factor × Remaining phased baseline
Completion cost = Posted actuals + Projected future spend
```

**Flat-burn stress sensitivity**

```text
Projected future spend = (Jan–Jun 2032 actuals / 6) × 18 remaining months
```

The analysis keeps the **$2M management reserve inside the $60M funding ceiling**. It is not treated as additional funding.

## Repository files

```text
financial-data-reconciliation-forecasting/
├── README.md
├── Project_X_Complete_Analysis.ipynb       # Cleaning, reconciliation, analysis, QA
├── Project_X_Financial_Analysis_Workbook.xlsx # Linked summary formulas and charts
├── Project_X_Executive_Summary.pdf         # One-page management decision summary
├── requirements.txt
└── .gitignore
```

The original input, `ProjectX_Student_Data_Pack.xlsx`, is **not included** in this repository package. The notebook requires it to rerun transaction-level calculations. Do not publish the case-provider's original material without permission.

## Reproducing the analysis

1. Clone the repository and install the Python packages:

   ```bash
   python -m pip install -r requirements.txt
   ```

2. If you have permission to access the original case data, place **`ProjectX_Student_Data_Pack.xlsx` in the repository root** alongside the notebook. The input workbook must contain the `GL_Extract`, `Baseline_Plan`, `Funding`, `Dept_Directory`, and `Data_Dictionary` sheets.
3. Open `Project_X_Complete_Analysis.ipynb` in Jupyter and select **Restart Kernel and Run All Cells**.
4. Inspect the validation assertions, raw-to-clean bridge, scenario tables, department watchlist, and open reconciliation exceptions.
5. Open the Excel workbook and PDF for the management-facing presentation of the existing results.

**Important distinction:** The supplied Excel workbook is a **linked, aggregate-level reporting workbook** populated from results already calculated in the notebook. It does not contain the original 5,250-line ledger or every month-by-department baseline input. It should not be represented as an independently recalculating, transaction-level model until the original input data is supplied and linked.

## Data-quality findings and limitations

A successful raw-to-clean bridge does **not** resolve every source-data question. The printed FY2030 and FY2031 subtotals and the source grand total still disagree with totals calculated from cleaned transaction lines. Their differences are approximately **$0.44M, $1.37M, and $2.62M**, respectively. These variances are disclosed rather than eliminated with unsupported adjustments.

Additional limitations:

- The latest department forecast is a submitted planning estimate, not an audited set of commitments.
- The relative-to-plan scenario assumes recent cost pressure persists; its results are sensitive to the recent six-month window.
- Department-level phased-baseline coverage in the published Excel summary remains partial without the source workbook.
- Proposed cuts require validation against contracts, staffing obligations, and delivery priorities before implementation.
- The original case also requested an oral readout and a fully transaction-linked Excel analysis workbook; the repository contains a written executive summary, a computational notebook, and an aggregate reporting workbook, **not evidence of a delivered oral presentation or a complete source-linked Excel model**.

## Skills demonstrated

Financial data cleaning and reconciliation · Python/pandas · Accounting-policy validation · Time-series aggregation · Budget versus actual analysis · Forecast scenario design · Department variance analysis · Reproducible notebooks · Excel reporting · Executive communication

---

*Portfolio case study for learning and demonstration. All project amounts and department labels originate from a simulated exercise. Analysis reflects a June 2032 reporting cut-off, not the current calendar year.*
