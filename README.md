
# Financial Data Reconciliation & Budget Forecasting

**Python · pandas · NumPy · Excel · Financial analysis · Scenario forecasting**

An end-to-end analysis of a **simulated $60 million project budget (2030–2033)**, from a messy general-ledger export to a management-oriented funding assessment. The project covers data cleaning, transaction reconciliation, budget-versus-actual analysis, forecast scenarios, and department-level spending risks.

The initial ledger cleaning and reconciliation were completed in approximately **five hours**. The broader analysis and reporting materials were developed afterward. All financial figures relate to a **fictional case study**, not an actual organization's finances.

## Key findings

As of **June 30, 2032** in the case scenario, Project X had spent approximately **$45.96 million**, or **76.6% of its total funding**, while **62.5% of the four-year project timeline** had elapsed. Spending was approximately **$7.22 million above the time-phased baseline**.

| Metric | Result |
|---|---:|
| Total funding ceiling | $60.00M |
| Approved departmental baseline | $58.00M |
| Management reserve (included in ceiling) | $2.00M |
| Actual expenditure through June 2032 | $45.96M |
| Time-phased baseline through June 2032 | $38.73M |
| Spending above phased baseline | **~$7.22M** |
| Remaining funding as of June 2032 | $14.04M |

### Cost-at-completion scenarios

| Scenario | Forecast future spend | Estimated completion cost | Above funding ceiling |
|---|---:|---:|---:|
| Department-submitted forecast (June 2032 version) | $19.83M | $65.79M | **$5.79M** |
| Recent spending relative to phased plan | $23.84M | $69.79M | **$9.79M** |
| Flat six-month burn rate (stress sensitivity) | $40.86M | $86.82M | **$26.82M** |

Both primary scenarios exceed the **$60M ceiling**. The phased-plan continuation is treated as a **challenge/risk scenario**, not a proven best estimate. The flat-burn projection is an intentionally severe stress sensitivity.

**Management implications:** Revalidate departmental estimates to complete, review outstanding commitments, and prioritize Departments **3, 7, and 4**, which show the largest historical overruns against their respective phased baselines.

For the concise management-facing findings, see the [Executive Summary](./Executive_Summary.pdf).

## Analytical workflow

### 1. Clean and reconcile the general ledger

- Identified the actual data headers in a raw Excel export containing report headers, subtotal rows, and mixed field formats.
- Standardized posting periods, transaction categories, departments, forecast versions, and signed amounts in accordance with the case's data dictionary.
- Removed **18 exact duplicate copies** totaling **$159,832.69**, while preserving legitimate reversing entries.
- Retained **5,250 cleaned ledger records** covering actuals and forecast versions, with an audit trail for cleaning decisions.
- Identified discrepancies between cleaned transaction totals and printed source control totals instead of forcing an unsupported reconciliation.

### 2. Analyze spending and budget variances

- Validated the **$58M baseline plan** across 10 departments, labor/non-labor categories, and 48 months.
- Compared actual spending against the **time-phased baseline**, rather than treating the budget as evenly distributed over time.
- Broke down expenditure by year, cost class, and department.
- Flagged the largest department overruns through June 2032:
  - **Department 3:** approximately **$1.85M** above plan, primarily non-labor.
  - **Department 7:** approximately **$1.40M** above plan, primarily labor.
  - **Department 4:** approximately **$1.19M** above plan, across labor and non-labor.

### 3. Build forecasts and propose actions

- Calculated the projected completion cost using the latest department-submitted forecast.
- Constructed a separate forecast that applies recent spending relative to the phased plan to the remaining planned spending.
- Included a flat-burn stress scenario to illustrate sensitivity to continued elevated spending.
- Quantified projected funding gaps and proposed spending controls, commitment reviews, and revised departmental estimates.
- Treated proposed savings as **targets requiring validation**, not secured reductions.

## Forecast methodology

**Cutoff and version selection:** Actual expenditure includes only posted actuals through **June 2032**. The submitted future forecast uses the **June 2032 forecast version** for **July 2032–December 2033**. The superseded December 2031 forecast is excluded from the current cost-at-completion calculation to avoid double counting.

**Submitted forecast**

```text
Completion cost = Actual spending to date + Submitted future forecast
```

**Recent spending relative to phased plan**

```text
Recent spending factor = Jan–Jun 2032 actuals / Jan–Jun 2032 phased baseline
Projected future spend = Recent spending factor × Remaining phased baseline
Completion cost = Actual spending to date + Projected future spend
```

**Flat-burn stress sensitivity**

```text
Projected future spend = (Jan–Jun 2032 actuals / 6) × 18 remaining months
Completion cost = Actual spending to date + Projected future spend
```

The **$2M management reserve is already included** within the $60M total funding ceiling; it is not additional funding.

## Repository structure

```text
financial-data-reconciliation-forecasting/
├── Complete_Analysis.ipynb          # Cleaning, reconciliation, scenarios, and findings
├── Executive_Summary.pdf            # One-page management summary
├── ProjectX_Student_Data_Pack.xlsx  # Supplied case-study data (see permissions note)
└── README.md                        # Project overview and methodology
```

These are the files currently published in the repository. A separate, fully transaction-linked Excel analysis workbook is **not currently published** here.

## Reproduce the analysis

1. Clone the repository:

   ```bash
   git clone https://github.com/Binhe-Jia/financial-data-reconciliation-forecasting.git
   cd financial-data-reconciliation-forecasting
   ```

2. Install the main dependencies in a Python environment (Python 3.10+ recommended):

   ```bash
   python -m pip install notebook ipykernel numpy pandas matplotlib openpyxl
   ```

3. Keep `ProjectX_Student_Data_Pack.xlsx` in the same folder as `Complete_Analysis.ipynb`. The source workbook contains sheets including `GL_Extract`, `Baseline_Plan`, `Funding`, `Dept_Directory`, and `Data_Dictionary`.
4. Launch Jupyter and open the notebook:

   ```bash
   jupyter notebook Complete_Analysis.ipynb
   ```

5. Select **Kernel → Restart & Run All**. Review the raw-to-clean reconciliation, validation checks, spending breakdowns, forecast comparisons, department watchlist, and documented exceptions.

The notebook is the computational deliverable; the PDF presents the management-facing conclusions. The original case brief also requested a fully traceable Excel workbook and an oral presentation, neither of which is represented as a completed, published deliverable in this repository.

## Data quality and limitations

- **Unresolved source controls:** The printed FY2030, FY2031, and overall grand-total cells differ from sums of the cleaned transaction records by approximately **$0.44M**, **$1.37M**, and **$2.62M**, respectively. The differences are disclosed rather than overridden.
- **Forecast uncertainty:** Department-submitted figures are planning estimates, not audited commitments. The recent-spending scenario assumes observed cost pressure continues and is sensitive to the chosen six-month window.
- **Practical feasibility:** Suggested spending reductions require checks of contracts, staffing obligations, and project priorities before they can be implemented.
- **Simulation:** The reporting date of June 2032 and all project financial amounts belong to the hypothetical scenario.

## Data Source & Acknowledgements

The original Project X case brief and dataset were provided by
**Muhammad Gazain** as part of a financial analysis case study.

I would like to thank Muhammad Gazain for developing and
sharing this exercise.

All data cleaning, reconciliation, financial analysis,
forecasting, and interpretation in this repository
represent my own project work.

The dataset describes a simulated business scenario
and does not contain actual company financial records.

**Dataset redistribution:** Attribution is not the same as permission to redistribute. Before keeping the source Excel workbook publicly available, confirm that the provider authorizes publication. If permission is not granted, remove the workbook from the public repository **and its Git history**; authorized users can obtain the dataset separately and place it locally to reproduce the notebook. Any license applied to original code or documentation in this repository does **not** automatically cover the third-party dataset.

## Skills demonstrated

**Data analysis:** Python, pandas, NumPy, Excel data extraction, data cleaning, deduplication, and reconciliation.

**Financial analytics:** Budget-versus-actual reporting, variance analysis, phased-budget forecasting, scenario comparisons, and funding-gap assessment.

**Research communication:** Transparent assumptions, documented limitations, executive-summary writing, and actionable recommendations.

---

*Portfolio project for analytical demonstration. Results concern a simulated business case and should not be interpreted as actual corporate financial performance.*
