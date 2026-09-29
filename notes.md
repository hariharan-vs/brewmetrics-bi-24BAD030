# Copilot DAX Notes

## Measure 1: MoM Sales Growth %

### Copilot Initial Suggestion

```DAX
MoM Sales Growth % =
VAR CurrentMonthSales =
    SUM ( Fact_Sales[sales_amount] )
VAR PreviousMonthSales =
    CALCULATE (
        SUM ( Fact_Sales[sales_amount] ),
        DATEADD ( Dim_Date[date], -1, MONTH )
    )
RETURN
    IF (
        ISBLANK ( PreviousMonthSales ) || PreviousMonthSales = 0,
        BLANK (),
        DIVIDE (
            CurrentMonthSales - PreviousMonthSales,
            PreviousMonthSales
        )
    )
Review / Correction

The Copilot-generated DAX was reviewed and found to correctly calculate month-over-month sales growth.

CurrentMonthSales calculates sales in the current filter context. PreviousMonthSales calculates sales after shifting the date context back by one month using DATEADD.

The IF condition returns BLANK() when previous-month sales are blank or zero, preventing an invalid division. DIVIDE calculates the month-over-month growth ratio.

No modification was made to the DAX.

Copilot identified that the Dim_Date table is based on distinct sales dates rather than a continuous calendar. This is a model-level consideration for time-intelligence calculations and was not changed for this measure.

Final Decision

The Copilot-generated DAX was retained without modification.

Measure 2: Running Total Sales
Copilot Initial Suggestion
Running Total Sales =
VAR CurrentDate =
    MAX ( Dim_Date[date] )
RETURN
    CALCULATE (
        SUM ( Fact_Sales[sales_amount] ),
        FILTER (
            ALL ( Dim_Date ),
            Dim_Date[date] <= CurrentDate
        )
    )
Review / Correction

The Copilot-generated DAX was reviewed and correctly calculates cumulative sales up to the current date.

CurrentDate captures the latest date in the current visual context.

ALL ( Dim_Date ) removes the existing date filters so that dates before the current date can be included.

FILTER keeps dates up to and including the current date.

CALCULATE calculates the total sales over the resulting date range.

Other filters, such as city, product, and store format, remain in effect.

No modification was required to the Copilot-generated DAX.

Final Decision

The Copilot-generated DAX was retained without modification.

Measure 3: City Sales Rank
Copilot Initial Suggestion
City Sales Rank =
RANKX (
    ALLSELECTED ( Dim_City[city] ),
    CALCULATE ( SUM ( Fact_Sales[sales_amount] ) ),
    ,
    DESC,
    DENSE
)
Review / Correction

The Copilot-generated DAX was reviewed and found to correctly rank cities based on total sales.

ALLSELECTED ( Dim_City[city] ) provides the cities in the current selection for comparison while preserving other report filters.

CALCULATE ( SUM ( Fact_Sales[sales_amount] ) ) evaluates total sales for each city.

DESC ranks the highest sales value as rank 1.

DENSE assigns the same rank to tied values without skipping the next rank.

No modification was required to the Copilot-generated DAX.

Final Decision

The Copilot-generated DAX was retained without modification.

Measure 4: Average Transaction Value
Copilot Initial Suggestion
Average Transaction Value =
VAR TotalSales =
    SUM ( Fact_Sales[sales_amount] )
VAR TotalQuantity =
    SUM ( Fact_Sales[quantity] )
RETURN
    DIVIDE ( TotalSales, TotalQuantity )
Review / Correction

The Copilot-generated DAX was reviewed and found to correctly calculate sales per unit of quantity.

TotalSales calculates the total sales amount within the current report filter context.

TotalQuantity calculates the total quantity within the current report filter context.

DIVIDE calculates the ratio of total sales to total quantity and safely handles cases where the quantity is zero or blank.

No modification was required to the Copilot-generated DAX.

Final Decision

The Copilot-generated DAX was retained without modification.