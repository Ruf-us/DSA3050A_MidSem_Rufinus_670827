#### Steps Taken

### A. Basic Data Cleaning

#### 1. Rename Unclear Columns

| Original | Renamed To |
| :--- | :--- |
| `Customer.ID` | Customer ID |
| `Customer.Name` | Customer Names |
| `Order.ID` | Order ID |
| `Order.Date` | Order Dates |
| `Ship.Date` | Shipping Dates |
| `Product.ID` | Product ID |
| `Product.Name` | Product Names |
| `Order.Priority` | Order Priority |
| `Ship.Mode` | Shipping Mode |
| `Sub.Category` | Sub Category |
| `Shipping.Cost` | Shipping Cost |
| `Row.ID` | Row ID |
| `Weeknum` | Weeknumber |
| `记录数(jì lù shù)` | Record Count |

#### 2. Change Data Types Correctly

| Column | Type |
| :--- | :--- |
| Order Date | Date |
| Ship Date | Date |
| Sales | Decimal Number |
| Profit | Decimal Number |
| Discount | Decimal Number |
| Quantity | Whole Number |
| Shipping Cost | Decimal Number |
| Year | Whole Number |
| weeknumber | Whole Number |

#### 3. Remove Duplicate Records
Unique identifier columns used for deduplication:
* `Order ID`
* `Product ID`

#### 4. Remove Blank Rows
* Removed all completely blank rows across the dataset.

#### 5. Trim and Clean Text Columns
* `Customer Name`
* `Product Name`

#### 6. Replace Inconsistent Values
* **Region:** Replaced `West` with `Western`
* **Market:** Replaced `US` with `United States`

#### 7. Remove Unnecessary Columns
* `记录数` / `Record Count` (non-English helper field)
* `weeknumber` (redundant)
* `Market2` / `Market` (duplicate market column removed)

---

### B. Intermediate Transformations

#### 1. Split One Column into Multiple Columns
* Split `Customer Name` into `First Name` and `Last Name`.

#### 2. Merge Two or More Columns
* Merged `First Name` + `Last Name` $\rightarrow$ `Customer Name`
* Merged `City` + `State` $\rightarrow$ `Location`

#### 3. Create a Custom Column
* **Total Cost:** `Sales - Profit`

#### 4. Create a Conditional Column
* **Profit Category:**
  * If `Profit` > 500 $\rightarrow$ **High Profit**
  * Else if `Profit` > 100 $\rightarrow$ **Medium Profit**
  * Else $\rightarrow$ **Low Profit**

#### 5. Date Extraction
* Extracted Year, Month, Quarter, and Day attributes from `Shipping Dates`.

#### 6. Multi-Condition Filtering
* Filtered dataset where `Country = "United States"` **AND** `Profit > 50`.

#### 7. Data Sorting
* Sorted data by `Sales` in **Descending** order.

#### 8. Index Column
* Added standard Index Column via `Add Column` $\rightarrow$ `Index Column`.

---

### C. Advanced Power Query Tasks

#### 1. Merge Queries Using a Common Key
1. Duplicated the main query, retaining only:
   * `Customer ID`
   * `Customer Name`
   * `Segment`
2. Performed a **Merge Queries** operation on key: `Customer ID`.
3. Expanded `Customer Name` and `Segment`.

#### 2. Append Datasets
* Duplicated `Superstore (2)` and appended the resulting tables together.

#### 3. Pivot Column
* Pivoted `Ship Mode` using `Sales` as the aggregation values column.

#### 4. Unpivot Columns
* Unpivoted the previously pivoted `Ship Mode` columns back to row format.

#### 5. Group By Aggregations
* Grouped by `Region` with the following aggregations:
  * **Total Sales:** Sum of Sales
  * **Total Profit:** Sum of Profit
  * **Average Discount:** Average of Discount

---

### Insights

* **Technology** is the highest-performing category, generating the greatest overall sales and profit, making it the company's strongest product line.
* **North America** contributes the largest share of total sales, indicating it is the most valuable market and should remain a primary strategic focus.
* The **Consumer** segment generates the highest revenue, suggesting marketing and customer retention efforts should prioritize this target group.

