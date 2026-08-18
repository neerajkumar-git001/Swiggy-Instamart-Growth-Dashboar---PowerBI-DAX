# DAX Measures

This document contains the DAX measures and field parameter used in the Grocery Shop Analytics Dashboard. These calculations are used to evaluate sales performance, transaction activity, customer ratings, KPI selection, and category-level sales contribution.

---

## 1. Total Sales

```
Total Sales =
SUM('Grocery Shop'[Sales])
```

**Description:** Calculates the total sales value from the Sales column in the Grocery Shop dataset.


## 2. Sales Records
```
Sales Records =
COUNT('Grocery Shop'[Sales])
```
**Description:** Counts the number of sales records available in the Grocery Shop dataset.

## 3. Sales Per Record
```
Sales Per Record =
AVERAGE('Grocery Shop'[Sales])
```
**Description:** Calculates the average sales value for each recorded sales transaction.

## 4. Average Rating
```
Average Rating =
AVERAGE('Grocery Shop'[Rating])
```
**Description:** Calculates the average rating from the Rating column in the Grocery Shop dataset.


## 5. Sales % Of Total
```
Sales % Of Total =
DIVIDE(
    [Total Sales],
    CALCULATE(
        [Total Sales],
        ALL('Grocery Shop'[Category])
    )
)

```
**Description:** Calculates the percentage contribution of each category to the overall sales value. The **ALL()** function removes the category filter from the total sales calculation, allowing each category to be compared against the overall total sales.

## 6. KPI Parameter
```
Parameter = {
    ("Total Sales", NAMEOF('KPI''s'[Total Sales]), 0),
    ("Sales Records", NAMEOF('KPI''s'[Sales Records]), 1),
    ("Sales Per Record", NAMEOF('KPI''s'[Sales Per Record]), 2),
    ("Average Rating", NAMEOF('KPI''s'[Average Rating]), 3)
}
```
**Description:** Creates a field parameter containing the available KPI measures. It allows the dashboard to dynamically switch between **Total Sales**, **Sales Records**, **Sales Per Record**, and **Average Rating**.


