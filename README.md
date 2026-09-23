# Quick Calculator

A single-page loan cash flow calculator using fixed (flat) interest. Change the principal, interest rate, tenure or payment frequency and the installment, chart and full cash flow schedule update immediately. It also works out the IRR from the actual cash flows (including any upfront fees), shows an NPV-versus-discount-rate chart where the curve crosses zero at the IRR, and gives an IRR workings table. The schedule can be viewed by payment, by year or as IRR workings, and exported as a CSV or a standalone HTML report.

## Loan portfolio upload

Switch to **Loan portfolio** to upload many loans at once from an Excel (.xlsx, .xls) or CSV file, or paste rows copied from Excel. Start from `AshokCalc-Input-Template.xlsx` (also downloadable from the page): one row per loan with Principal, Fixed Interest, Tenure, Frequency, Upfront Fees and First Payment Date. AshokCalc then shows consolidated totals, principal-weighted rate and tenure, the portfolio XIRR on actual dates, an NPV curve, consolidated cash flows by month and year, and each loan's IRR and XIRR. Results export to an Excel workbook or an HTML report. Files are read in the browser and are not uploaded anywhere.

## Publish on GitHub Pages

1. Create a new public repository (for example `AshokCalc`).
2. Upload all the files (`index.html`, `manifest.webmanifest`, the three `icon-*.png` files, `AshokCalc-Input-Template.xlsx` and this `README.md`) to the root of the repository.
3. Open **Settings → Pages**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then save.
4. After a minute the calculator is live at `https://<your-username>.github.io/AshokCalc/`.

The page updates its URL as you change inputs (for example `?p=1000000&r=9.5&t=5&u=years&f=monthly`), so you can share a link that opens with the same scenario.

## Add to an Android home screen

Open the GitHub Pages link in Chrome, tap the ⋮ menu and choose **Add to Home screen** (or **Install app**). The AshokCalc icon and name come from `manifest.webmanifest`, and the calculator opens full screen like an app.

## How the numbers are worked out

- Interest is fixed (flat): every period is charged principal × annual rate ÷ payments per year, on the original principal. It does not reduce as principal is repaid.
- Principal is repaid in equal parts (principal ÷ number of payments), so installment = principal ÷ n + fixed interest per period.
- Total interest = principal × annual rate × years. Amounts are rounded to two decimals and the final payment absorbs any rounding difference.
- IRR: the net amount disbursed (principal less upfront fees) is paid out one period before the first installment, and the periodic IRR is the rate at which the present value of all cash flows is zero. Nominal annual IRR = periodic IRR × payments per year; effective annual IRR = (1 + periodic IRR)^payments per year − 1; XIRR uses actual days on a 365-day year.
