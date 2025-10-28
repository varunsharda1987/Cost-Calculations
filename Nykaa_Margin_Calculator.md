# Nykaa Margin Calculator

## Input Values

| Parameter | Value | Unit |
|-----------|-------|------|
| **ASP (Average Selling Price)** | `____` | ₹ |
| **Manufacturing Cost** | `____` | ₹ |
| **Return %** | `____` | % |

---

## Automatic Calculations

### Step 1: Determine Tax Rate
```
IF ASP > ₹2,500:
    Product Tax Rate = 18%
ELSE:
    Product Tax Rate = 5%
```

### Step 2: Calculate Taxable Value
```
Taxable Value = ASP ÷ (1 + Tax Rate)
Product Tax Amount = ASP - Taxable Value
```

### Step 3: Calculate Nykaa Commission (25% of ASP)
```
Nykaa Commission = ASP × 0.25
Tax on Commission (18%) = Nykaa Commission × 0.18
Total Commission with Tax = Nykaa Commission × 1.18
```

### Step 4: Calculate Nykaa Marketing (10% of ASP)
```
Nykaa Marketing = ASP × 0.10
Tax on Marketing (18%) = Nykaa Marketing × 0.18
Total Marketing with Tax = Nykaa Marketing × 1.18
```

### Step 5: Calculate Logistics (Return % is Input)
```
Forward Logistics = ₹50 (fixed)
Reverse Logistics = ₹0 (fixed)
Return % = INPUT

Total Logistics = (50 + 0 × Return%) ÷ (1 - Return%)
Tax on Logistics (18%) = Total Logistics × 0.18
Total Logistics with Tax = Total Logistics × 1.18
```

### Step 6: Calculate TCS (0.5% of ASP)
```
TCS = ASP × 0.005
```

### Step 7: Calculate Final Payout
```
Final Payout = ASP - Total Commission with Tax - Total Marketing with Tax - Total Logistics with Tax - TCS
```

---

## Quick Calculation Table

| Item | Formula | Calculation |
|------|---------|-------------|
| **INPUT: ASP** | - | `____` |
| **INPUT: Manufacturing Cost** | - | `____` |
| **INPUT: Return %** | - | `____` |
| | | |
| **Product Tax Rate** | Conditional | `5% or 18%` |
| Taxable Value | ASP ÷ (1 + Tax%) | `____` |
| Product Tax | ASP - Taxable Value | `____` |
| | | |
| Nykaa Commission (25%) | ASP × 0.25 | `____` |
| Tax on Commission (18%) | Commission × 0.18 | `____` |
| **Total Commission** | Commission × 1.18 | `____` |
| | | |
| Nykaa Marketing (10%) | ASP × 0.10 | `____` |
| Tax on Marketing (18%) | Marketing × 0.18 | `____` |
| **Total Marketing** | Marketing × 1.18 | `____` |
| | | |
| Total Logistics | 50 ÷ (1 - Return%) | `____` |
| Tax on Logistics (18%) | Logistics × 0.18 | `____` |
| **Total Logistics with Tax** | Logistics × 1.18 | `____` |
| | | |
| TCS (0.5%) | ASP × 0.005 | `____` |
| | | |
| **FINAL PAYOUT** | ASP - All Deductions | `____` |

---

## Fixed Parameters (Standard for All Calculations)

- **Nykaa Commission Rate**: 25%
- **Nykaa Marketing Rate**: 10%
- **TCS Rate**: 0.5%
- **Tax on Commission**: 18%
- **Tax on Marketing**: 18%
- **Tax on Logistics**: 18%
- **Forward Logistics**: ₹50
- **Reverse Logistics**: ₹0

**Variable Input**: Return % (user input)

---

## Product Tax Rules

| ASP Range | Tax Rate |
|-----------|----------|
| ASP ≤ ₹2,500 | 5% |
| ASP > ₹2,500 | 18% |

---

## Example 1: Product with ASP ≤ ₹2,500

### Inputs:
- **ASP** = ₹1,699
- **Manufacturing Cost** = ₹630
- **Return %** = 50%

### Automatic Calculations:

| Item | Calculation | Value |
|------|-------------|-------|
| Product Tax Rate | ASP ≤ 2,500 | **5%** |
| Taxable Value | 1,699 ÷ 1.05 | ₹1,618.10 |
| Product Tax | 1,699 - 1,618.10 | ₹80.90 |
| Nykaa Commission | 1,699 × 0.25 | ₹424.75 |
| Tax on Commission | 424.75 × 0.18 | ₹76.46 |
| **Total Commission** | 424.75 × 1.18 | **₹501.21** |
| Nykaa Marketing | 1,699 × 0.10 | ₹169.90 |
| Tax on Marketing | 169.90 × 0.18 | ₹30.58 |
| **Total Marketing** | 169.90 × 1.18 | **₹200.48** |
| Total Logistics | 50 ÷ (1 - 0.5) | ₹100.00 |
| Tax on Logistics | 100 × 0.18 | ₹18.00 |
| **Total Logistics with Tax** | 100 × 1.18 | **₹118.00** |
| TCS | 1,699 × 0.005 | ₹8.50 |
| **FINAL PAYOUT** | 1,699 - 501.21 - 200.48 - 118 - 8.50 | **₹870.81** |

---

## Example 2: Product with ASP > ₹2,500

### Inputs:
- **ASP** = ₹3,999
- **Manufacturing Cost** = ₹1,200
- **Return %** = 50%

### Automatic Calculations:

| Item | Calculation | Value |
|------|-------------|-------|
| Product Tax Rate | ASP > 2,500 | **18%** |
| Taxable Value | 3,999 ÷ 1.18 | ₹3,388.98 |
| Product Tax | 3,999 - 3,388.98 | ₹610.02 |
| Nykaa Commission | 3,999 × 0.25 | ₹999.75 |
| Tax on Commission | 999.75 × 0.18 | ₹179.96 |
| **Total Commission** | 999.75 × 1.18 | **₹1,179.71** |
| Nykaa Marketing | 3,999 × 0.10 | ₹399.90 |
| Tax on Marketing | 399.90 × 0.18 | ₹71.98 |
| **Total Marketing** | 399.90 × 1.18 | **₹471.88** |
| Total Logistics | 50 ÷ (1 - 0.5) | ₹100.00 |
| Tax on Logistics | 100 × 0.18 | ₹18.00 |
| **Total Logistics with Tax** | 100 × 1.18 | **₹118.00** |
| TCS | 3,999 × 0.005 | ₹20.00 |
| **FINAL PAYOUT** | 3,999 - 1,179.71 - 471.88 - 118 - 20 | **₹2,209.41** |

---

## Summary

**Simple 3-Input Calculator:**
1. Enter your **ASP**
2. Enter your **Manufacturing Cost**
3. Enter your **Return %**
4. All other calculations are automatic based on fixed Nykaa parameters

**Key Deductions from ASP:**
- Commission (25%) + Tax = ASP × 0.295
- Marketing (10%) + Tax = ASP × 0.118
- Logistics with Tax = [50 ÷ (1 - Return%)] × 1.18
- TCS = ASP × 0.005

---

## Important Notes

✅ **3 inputs required**: ASP, Manufacturing Cost, and Return %  
✅ **Logistics vary with Return %**: Higher return % = Higher logistics cost  
✅ **All other parameters are fixed** (Nykaa standard rates)  
✅ **Product tax is automatic**: 5% for ASP ≤ ₹2,500 | 18% for ASP > ₹2,500  
✅ **Commission, Marketing, and TCS calculated on ASP**

---

*Simple Nykaa Margin Calculator - Enter ASP, Manufacturing Cost & Return %!*
