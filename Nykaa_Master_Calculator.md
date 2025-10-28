# Nykaa Margin Calculator - Master Document
## All Order Statuses

---

## Order Status Overview

This calculator handles all Nykaa order statuses with their respective calculation methods:

| Status | Calculation Type |
|--------|------------------|
| **Shipped** | Full Calculation (Payout + Margin) |
| **Confirmed** | Full Calculation (Payout + Margin) |
| **Manifest Scanned** | Full Calculation (Payout + Margin) |
| **Pending** | Full Calculation (Payout + Margin) |
| **Assigned** | Full Calculation (Payout + Margin) |
| **Upcoming** | Full Calculation (Payout + Margin) |
| **Returned** | Payout = -₹59, Margin = -₹59 |
| **Cancelled** | Payout = ₹0, Margin = ₹0 |

---

## Input Parameters

| Parameter | Value | Unit | Notes |
|-----------|-------|------|-------|
| **ASP (Average Selling Price)** | `____` | ₹ | Selling price with tax |
| **Manufacturing Cost** | `____` | ₹ | Without tax |
| **Return %** | `____` | % | Calculated from order data |
| **Order Status** | `____` | - | See status list above |

---

## Return % Calculation

Return % is calculated from actual order data:

```
Return % = Total "RETURNED" Status Orders / Total Orders Processed

Where:
Total Orders Processed = All orders EXCEPT "CANCELLED" status
```

**Example:**
- Total Orders = 1,000
- Cancelled Orders = 50
- Returned Orders = 100

```
Total Orders Processed = 1,000 - 50 = 950
Return % = 100 / 950 = 10.53%
```

This Return % is then used in the logistics calculation for all active order statuses.

---

## CALCULATION METHOD 1: FULL CALCULATION
### (For: Shipped, Confirmed, Manifest Scanned, Pending, Assigned, Upcoming)

### PART 1: FINAL PAYOUT CALCULATION

#### Elements Calculated:
1. Final Commission Amount per Unit
2. Tax Amount on Commission
3. Shipping Charges Calc (Forward Logistics)
4. Tax Amount on Charges
5. TCS

#### Step-by-Step Formulas:

**Step 1: Calculate Commission**
```
Commission = ASP × 0.25
Tax on Commission = Commission × 0.18
Total Commission with Tax = Commission × 1.18
```

**Step 2: Calculate Forward Logistics**
```
Forward Logistics = ₹50 (fixed)
Tax on Forward Logistics = 50 × 0.18 = ₹9
Total Forward Logistics with Tax = ₹59 (fixed)
```

**Step 3: Calculate TCS**
```
TCS = ASP × 0.005
```

**Step 4: Calculate Final Payout**
```
Final Payout = ASP - Total Commission with Tax - Total Forward Logistics with Tax - TCS
Final Payout = ASP - (ASP × 0.25 × 1.18) - 59 - (ASP × 0.005)
```

#### Quick Table - Part 1:

| Element | Formula | Value |
|---------|---------|-------|
| ASP | Input | `____` |
| Commission (25%) | ASP × 0.25 | `____` |
| Tax on Commission (18%) | Commission × 0.18 | `____` |
| **Total Commission with Tax** | Commission × 1.18 | `____` |
| Forward Logistics | Fixed | **₹50.00** |
| Tax on Forward Logistics (18%) | 50 × 0.18 | **₹9.00** |
| **Total Forward Logistics with Tax** | - | **₹59.00** |
| TCS (0.5%) | ASP × 0.005 | `____` |
| **FINAL PAYOUT** | ASP - Commission - Logistics - TCS | `____` |

---

### PART 2: MARGIN ON SALE CALCULATION

#### Additional Elements Required:
1. Nykaa Marketing (10% of ASP)
2. Additional Marketing (5% of ASP)
3. Total Logistics Cost (based on Return %)
4. Manufacturing Cost with Tax
5. Return Logistics (additional cost)
6. TCS (add back as reimbursement)

#### Step-by-Step Formulas:

**Step 1: Calculate Marketing Costs**
```
Nykaa Marketing = ASP × 0.10
Tax on Nykaa Marketing = Nykaa Marketing × 0.18
Total Marketing with Tax = Nykaa Marketing × 1.18
```

**Step 2: Calculate Additional Marketing**
```
Additional Marketing = ASP × 0.05
Tax on Additional Marketing = Additional Marketing × 0.18
Total Additional Marketing with Tax = Additional Marketing × 1.18
```

**Step 3: Calculate Manufacturing Cost with Tax**
```
Manufacturing Cost with Tax = Manufacturing Cost × 1.05
```
*Note: 5% output tax on manufacturing cost*

**Step 4: Calculate Return Logistics**
```
Total Logistics = (Forward Logistics + (Reverse Logistics × Return%)) / (1 - Return%)
Total Logistics = (50 + 0 × Return%) / (1 - Return%)
Total Logistics = 50 / (1 - Return%)

Return Logistics = Total Logistics - Forward Logistics with Tax
Return Logistics = Total Logistics - 59
```

**Step 5: Calculate Margin on Sale**
```
Margin = Final Payout - [
  Total Marketing with Tax
  + Total Additional Marketing with Tax
  + Manufacturing Cost with Tax
  + Return Logistics
] + TCS
```

*Note: TCS is added back because it's a reimbursement we receive*

#### Quick Table - Part 2:

| Element | Formula | Value |
|---------|---------|-------|
| **Starting Point:** | | |
| Final Payout | From Part 1 | `____` |
| | | |
| **Marketing Costs:** | | |
| Nykaa Marketing (10%) | ASP × 0.10 | `____` |
| Tax on Marketing (18%) | Marketing × 0.18 | `____` |
| **Total Marketing with Tax** | Marketing × 1.18 | `____` |
| | | |
| Additional Marketing (5%) | ASP × 0.05 | `____` |
| Tax on Additional Marketing (18%) | Additional Marketing × 0.18 | `____` |
| **Total Additional Marketing with Tax** | Additional Marketing × 1.18 | `____` |
| | | |
| **Manufacturing:** | | |
| Manufacturing Cost | Input | `____` |
| Tax on Manufacturing (5%) | Mfg Cost × 0.05 | `____` |
| **Total Manufacturing Cost with Tax** | Mfg Cost × 1.05 | `____` |
| | | |
| **Logistics:** | | |
| Total Logistics | 50 ÷ (1 - Return%) | `____` |
| Already Paid (Part 1) | Fixed | **₹59.00** |
| **Return Logistics (additional)** | Total Logistics - 59 | `____` |
| | | |
| **TCS Reimbursement:** | | |
| TCS (add back) | From Part 1 | `+____` |
| | | |
| **Total Deductions** | Sum of all costs | `____` |
| **MARGIN ON SALE** | Payout - Deductions + TCS | `____` |

---

## CALCULATION METHOD 2: RETURNED STATUS

For orders with **"RETURNED"** status:

```
Final Payout = -₹59
Margin = -₹59
```

**Explanation:**
- Customer returned the product
- We owe back the forward logistics cost
- Forward Logistics + Tax = ₹50 + ₹9 = ₹59
- This is a loss/liability

**No further calculations needed.**

---

## CALCULATION METHOD 3: CANCELLED STATUS

For orders with **"CANCELLED"** status:

```
Final Payout = ₹0
Margin = ₹0
```

**Explanation:**
- Order was cancelled before processing
- No financial transaction occurred
- These orders are excluded from Return % calculation

**No further calculations needed.**

---

## Complete Examples

### Example 1: SHIPPED Status Order

**Given:**
- ASP = ₹1,699
- Manufacturing Cost = ₹630 (without tax)
- Return % = 50%
- Status = Shipped

#### PART 1: FINAL PAYOUT

| Element | Calculation | Amount |
|---------|-------------|--------|
| ASP | - | ₹1,699.00 |
| Commission (25%) | 1,699 × 0.25 | ₹424.75 |
| Tax on Commission (18%) | 424.75 × 0.18 | ₹76.46 |
| **Total Commission with Tax** | 424.75 × 1.18 | **₹501.21** |
| Forward Logistics | Fixed | ₹50.00 |
| Tax on Forward Logistics (18%) | 50 × 0.18 | ₹9.00 |
| **Total Forward Logistics with Tax** | - | **₹59.00** |
| TCS (0.5%) | 1,699 × 0.005 | **₹8.50** |
| **FINAL PAYOUT** | 1,699 - 501.21 - 59 - 8.50 | **₹1,130.29** |

#### PART 2: MARGIN ON SALE

| Element | Calculation | Amount |
|---------|-------------|--------|
| Final Payout | From Part 1 | ₹1,130.29 |
| | | |
| **Deductions:** | | |
| Nykaa Marketing (10%) | 1,699 × 0.10 | ₹169.90 |
| Tax on Marketing (18%) | 169.90 × 0.18 | ₹30.58 |
| Total Marketing with Tax | 169.90 × 1.18 | ₹200.48 |
| | | |
| Additional Marketing (5%) | 1,699 × 0.05 | ₹84.95 |
| Tax on Additional Marketing (18%) | 84.95 × 0.18 | ₹15.29 |
| Total Additional Marketing with Tax | 84.95 × 1.18 | ₹100.24 |
| | | |
| Manufacturing Cost | - | ₹630.00 |
| Tax on Manufacturing (5%) | 630 × 0.05 | ₹31.50 |
| Total Manufacturing Cost with Tax | 630 × 1.05 | ₹661.50 |
| | | |
| Total Logistics | 50 ÷ (1 - 0.5) | ₹100.00 |
| Already Paid | - | ₹59.00 |
| Return Logistics (additional) | 100 - 59 | ₹41.00 |
| | | |
| **Total Deductions** | - | **₹1,003.22** |
| | | |
| TCS Reimbursement | From Part 1 | **+₹8.50** |
| | | |
| **MARGIN ON SALE** | 1,130.29 - 1,003.22 + 8.50 | **₹135.57** |

**Summary:**
- **Final Payout: ₹1,130.29**
- **Margin: ₹135.57**
- **Margin %: 7.98%** (135.57 ÷ 1,699 × 100)

---

### Example 2: RETURNED Status Order

**Given:**
- ASP = ₹1,699
- Status = Returned

**Calculation:**
```
Final Payout = -₹59
Margin = -₹59
```

**Explanation:** Customer returned the product. We owe the forward logistics cost of ₹59.

---

### Example 3: CANCELLED Status Order

**Given:**
- ASP = ₹1,699
- Status = Cancelled

**Calculation:**
```
Final Payout = ₹0
Margin = ₹0
```

**Explanation:** Order was cancelled. No financial impact.

---

## Summary of All Formulas

### Full Calculation Statuses (Shipped, Confirmed, Manifest Scanned, Pending, Assigned, Upcoming):

**Part 1 - Final Payout:**
```
Final Payout = ASP - (ASP × 0.25 × 1.18) - 59 - (ASP × 0.005)
```

**Part 2 - Margin on Sale:**
```
Margin = Final Payout 
       - (ASP × 0.10 × 1.18)                    // Marketing with tax
       - (ASP × 0.05 × 1.18)                    // Additional Marketing with tax
       - (Manufacturing Cost × 1.05)             // Mfg Cost with tax
       - ([50 ÷ (1 - Return%)] - 59)            // Return Logistics
       + (ASP × 0.005)                          // TCS add back
```

### Returned Status:
```
Final Payout = -₹59
Margin = -₹59
```

### Cancelled Status:
```
Final Payout = ₹0
Margin = ₹0
```

---

## Fixed Parameters

| Parameter | Value | Notes |
|-----------|-------|-------|
| **Commission Rate** | 25% | Of ASP |
| **Marketing Rate** | 10% | Of ASP |
| **Additional Marketing Rate** | 5% | Of ASP |
| **TCS Rate** | 0.5% | Of ASP |
| **Forward Logistics** | ₹50 | Fixed |
| **Reverse Logistics** | ₹0 | Fixed |
| **Tax on Commission, Marketing, Additional Marketing, Logistics** | 18% | GST Input |
| **Tax on Manufacturing Cost** | 5% | GST Output |

---

## Key Notes

### Status-Based Logic:
1. ✅ **6 statuses use full calculation**: Shipped, Confirmed, Manifest Scanned, Pending, Assigned, Upcoming
2. ✅ **Returned** = Fixed loss of ₹59
3. ✅ **Cancelled** = No financial impact

### TCS Treatment:
- Deducted in Final Payout (Part 1)
- Added back in Margin calculation (Part 2) as it's a reimbursement

### Return % Impact:
- Calculated from actual order data: Returned Orders / Total (except Cancelled)
- Higher Return % = Higher Total Logistics cost
- Affects Margin calculation for all active orders

### Logistics Calculation:
- **Part 1 (Payout)**: Only Forward Logistics (₹59) deducted
- **Part 2 (Margin)**: Additional Return Logistics deducted based on Return %
- Total Logistics = 50 ÷ (1 - Return%)
- Return Logistics = Total Logistics - 59

### Tax Treatment:
- **Input Tax (18%)**: On Commission, Marketing, Additional Marketing, Logistics
- **Output Tax (5%)**: On Manufacturing Cost
- Net effect is built into the margin calculation

---

## Order Processing Flow

```
Order Placed
    ↓
Status: Upcoming / Assigned / Pending / Confirmed / Manifest Scanned
    ↓ (Use Full Calculation)
Status: Shipped
    ↓ (Use Full Calculation)
    ├─→ Status: Returned → Payout = -₹59, Margin = -₹59
    └─→ Delivered (Keep Shipped calculation)

Order Cancelled (anytime)
    → Payout = ₹0, Margin = ₹0
```

---

## Usage Instructions

1. **Identify Order Status** from the 8 possible statuses
2. **Collect Inputs**: ASP, Manufacturing Cost, Return %
3. **Apply Calculation Method**:
   - Full Calculation for most statuses
   - Fixed values for Returned and Cancelled
4. **Calculate Return %** from your order data for accurate logistics costs
5. **Review both Payout and Margin** to understand profitability

---

*Nykaa Master Margin Calculator - All Order Statuses*
*Version 1.0*
