# Business Model Analysis - Detailed Cash Flow Structure

## Overview
Based on the provided business model, this analysis expands the research to include specific cash payment categories, cash receipts, and specialized journal types for the POS system.

## Cash Payment Categories (Money Out)

### 1. Core Business Operations
| Category | Description | GLS % | Account Type |
|----------|-------------|-------|--------------|
| **Purchases** | Inventory and raw materials | - | Cost of Goods Sold |
| **Delivery costs** | Shipping and delivery expenses | - | Operating Expense |
| **Extension Service costs** | Service delivery costs | - | Operating Expense |
| **Direct Salaries/wages** | Employee compensation | - | Operating Expense |
| **Payroll Taxes and Benefits-Direct** | Employer payroll costs | - | Operating Expense |
| **Staff meals** | Employee meal expenses | - | Operating Expense |

### 2. Technology & Communication
| Category | Description | GLS % | Account Type |
|----------|-------------|-------|--------------|
| **Computer Internet** | Internet and connectivity | - | Operating Expense |
| **Bank/mpesa Payment Charges** | Payment processing fees | - | Operating Expense |
| **Bank/Mpesa Collection Charges** | Collection processing fees | - | Operating Expense |
| **Telephone** | Communication costs | - | Operating Expense |
| **IT Enabled Services** | Website-as-a-Service | 1% | Operating Expense |

### 3. Office & Administrative
| Category | Description | GLS % | Account Type |
|----------|-------------|-------|--------------|
| **Office supplies (Stationery)** | Office materials | - | Operating Expense |
| **Hire of equipment** | Equipment rental | - | Operating Expense |
| **Security Expenses** | Security services | - | Operating Expense |
| **Printing, photocopying** | Document services | - | Operating Expense |
| **Business Registration** | Regulatory compliance | - | Operating Expense |
| **Maintenance** | Equipment maintenance | - | Operating Expense |
| **Cleaning materials** | Cleaning supplies | - | Operating Expense |
| **Packaging Materials** | Product packaging | - | Cost of Goods Sold |

### 4. Business Development
| Category | Description | GLS % | Account Type |
|----------|-------------|-------|--------------|
| **Recruitment, meeting & Conferencing** | HR and business development | - | Operating Expense |
| **Travel & Accom** | Business travel | - | Operating Expense |
| **Market Activations** | Marketing activities | 5% | Operating Expense |
| **Smart Extension Services** | Service delivery | 5% | Operating Expense |

### 5. Government & Regulatory (GLS - Government Levy System)
| Category | Description | GLS % | Account Type |
|----------|-------------|-------|--------------|
| **Loyalty-as-a-Service (LaaS)** | Government loyalty service | 15% | Tax Expense |
| **Withholding tax** | Tax withholding | 5% | Tax Expense |
| **Trading License** | Business license | 1% | Tax Expense |
| **Invest-Now-Pay-Loyalties (INPL) Interest** | Government investment interest | 1% | Interest Expense |
| **Teller Operations** | Banking operations | 10% | Operating Expense |
| **Curricula Development** | Educational development | 1% | Operating Expense |
| **Data-Science** | Data analytics services | 1% | Operating Expense |
| **Socio-enterprise Development** | Social enterprise support | 1% | Operating Expense |
| **Agronomy Services** | Agricultural services | 1% | Operating Expense |
| **Climate-Science** | Climate research | 1% | Operating Expense |
| **Rent + Utilities** | Facility costs | 5% | Operating Expense |
| **Climate-Enterprises** | Climate business support | 25% | Operating Expense |
| **Hospital Insurance** | Health insurance | 15% | Operating Expense |
| **Social Enterprises** | Social business support | 7% | Operating Expense |
| **INPL Smart Advances Repayments** | Government loan repayments | - | Interest Expense |

### 6. Special Categories
| Category | Description | GLS % | Account Type |
|----------|-------------|-------|--------------|
| **Depreciation-Direct** | Asset depreciation | - | Operating Expense |
| **Creditors** | Accounts payable payments | - | Liability Reduction |
| **Rewards** | Customer loyalty rewards | - | Operating Expense |

## Cash Receipt Categories (Money In)

### 1. Core Revenue Streams
| Category | Description | Account Type |
|----------|-------------|--------------|
| **Sales** | Product and service sales | Revenue |
| **Debtors** | Accounts receivable collections | Asset Reduction |
| **Member-ship Fees** | Membership revenue | Revenue |
| **Smart Extension Service** | Service delivery income | Revenue |
| **Kitchen salvages** | Waste reduction income | Other Income |
| **Hire of equipment** | Equipment rental income | Other Income |

### 2. Financial Operations
| Category | Description | Account Type |
|----------|-------------|--------------|
| **Investor funds** | Investment capital | Equity |
| **Over-drafts** | Bank overdraft facility | Liability |
| **Cash advances** | Customer advances | Liability |
| **Advance Payments** | Prepaid services | Liability |
| **Wifi charges** | Service charges | Revenue |

### 3. Social Impact & Development
| Category | Description | Account Type |
|----------|-------------|--------------|
| **Donations** | Charitable contributions | Other Income |
| **Climate Enterprise Income** | Climate business revenue | Revenue |
| **Social Enterprise Income** | Social business revenue | Revenue |
| **Climate Impact Bond Coupon Rate** | Bond interest income | Interest Income |
| **Fund-raisers** | Fundraising events | Other Income |
| **Joint-venture Income** | Partnership revenue | Revenue |
| **Endowment Building** | Endowment contributions | Equity |
| **Volunteer Valuation Time** | Volunteer services value | Other Income |

### 4. Other Revenue
| Category | Description | Account Type |
|----------|-------------|--------------|
| **Others Revenues** | Miscellaneous income | Other Income |

## Specialized Journal Types

### 1. Cost of Sales Journals
**Purpose**: Track the actual cost of preparing products/services

#### Structure:
- **Product/Service ID**: Reference to specific item
- **Raw Material Costs**: Ingredients, components
- **Labor Costs**: Direct labor for preparation
- **Overhead Allocation**: Indirect costs allocated
- **Total Cost**: Sum of all cost components
- **Profit Margin**: Selling price - total cost

#### Example Entry:
```
Product: Chicken Meal
Raw Materials: $5.00
Labor: $2.00
Overhead: $1.00
Total Cost: $8.00
Selling Price: $12.00
Profit Margin: $4.00 (33.3%)
```

### 2. Sales Journals
**Purpose**: Track selling prices and revenue recognition

#### Structure:
- **Product/Service ID**: Reference to specific item
- **Selling Price**: Customer-facing price
- **Quantity Sold**: Units sold
- **Total Revenue**: Selling price × quantity
- **Cost of Sales**: From cost of sales journal
- **Gross Profit**: Revenue - cost of sales

#### Example Entry:
```
Product: Chicken Meal
Selling Price: $12.00
Quantity Sold: 100
Total Revenue: $1,200.00
Cost of Sales: $800.00
Gross Profit: $400.00
```

### 3. Purchase Journals
**Purpose**: Track supplier purchases and inventory costs

#### Structure:
- **Supplier ID**: Reference to supplier
- **Product ID**: Purchased item
- **Purchase Price**: Cost from supplier
- **Quantity Purchased**: Units bought
- **Total Cost**: Purchase price × quantity
- **Wholesale Price**: Bulk pricing
- **Markup**: Selling price - wholesale price

#### Example Entry:
```
Supplier: ABC Foods
Product: Chicken (per kg)
Purchase Price: $3.00
Quantity: 50 kg
Total Cost: $150.00
Wholesale Price: $3.50
Markup: $8.50 (per meal)
```

### 4. Bank Deposits Journal
**Purpose**: Track all bank deposits and their nature

#### Structure:
- **Deposit Date**: When deposit was made
- **Deposit Amount**: Amount deposited
- **Deposit Type**: Nature of deposit
- **Source**: Where money came from
- **Bank Account**: Which account
- **Reference**: Transaction reference
- **Status**: Pending/Cleared/Failed

#### Example Entry:
```
Date: 2025-01-15
Amount: $5,000.00
Type: Sales Revenue
Source: POS Terminal
Bank Account: Business Checking
Reference: DEP-001
Status: Cleared
```

## Enhanced Chart of Accounts

### 1. Revenue Accounts (4000-4999)
```
4000 - REVENUE
4100 - Sales Revenue
4110 - Product Sales
4111 - Food Sales
4112 - Beverage Sales
4113 - Merchandise Sales
4120 - Service Revenue
4121 - Smart Extension Services
4122 - Equipment Rental
4130 - Membership Revenue
4131 - Annual Membership
4132 - Monthly Membership
4200 - Other Income
4210 - Interest Income
4211 - Climate Impact Bond Interest
4220 - Rental Income
4221 - Equipment Rental Income
4230 - Donation Income
4240 - Fundraising Income
4250 - Joint Venture Income
4260 - Climate Enterprise Income
4270 - Social Enterprise Income
4280 - Volunteer Valuation Income
4290 - Miscellaneous Income
```

### 2. Cost of Goods Sold (5000-5999)
```
5000 - COST OF GOODS SOLD
5100 - Direct Materials
5110 - Food Ingredients
5111 - Raw Materials
5112 - Packaging Materials
5120 - Direct Labor
5121 - Kitchen Staff
5122 - Service Staff
5130 - Manufacturing Overhead
5131 - Kitchen Utilities
5132 - Equipment Depreciation
5133 - Kitchen Supplies
```

### 3. Operating Expenses (6000-6999)
```
6000 - OPERATING EXPENSES
6100 - Personnel Expenses
6110 - Salaries and Wages
6111 - Direct Salaries
6112 - Administrative Salaries
6120 - Payroll Taxes and Benefits
6121 - Employer Payroll Taxes
6122 - Employee Benefits
6130 - Staff Meals
6200 - Technology Expenses
6210 - Computer Internet
6211 - IT Enabled Services
6212 - Website Services
6220 - Communication
6221 - Telephone
6222 - Bank Charges
6230 - Bank/Mpesa Charges
6231 - Payment Processing
6232 - Collection Processing
6300 - Administrative Expenses
6310 - Office Supplies
6311 - Stationery
6312 - Printing and Photocopying
6320 - Business Operations
6321 - Business Registration
6322 - Trading License
6330 - Facility Expenses
6331 - Rent and Utilities
6332 - Security Expenses
6333 - Maintenance
6334 - Cleaning Materials
6340 - Business Development
6341 - Recruitment
6342 - Meetings and Conferencing
6343 - Travel and Accommodation
6344 - Market Activations
6350 - Equipment
6351 - Hire of Equipment
6352 - Equipment Depreciation
```

### 4. Government and Regulatory Expenses (7000-7999)
```
7000 - GOVERNMENT AND REGULATORY
7100 - Government Levies (GLS)
7110 - Loyalty-as-a-Service (15%)
7120 - Withholding Tax (5%)
7130 - Trading License (1%)
7140 - INPL Interest (1%)
7150 - Teller Operations (10%)
7160 - Curricula Development (1%)
7170 - Data-Science (1%)
7180 - Socio-enterprise Development (1%)
7190 - Agronomy Services (1%)
7200 - Climate-Science (1%)
7210 - Rent + Utilities (5%)
7220 - Market Activations (5%)
7230 - Smart Extension Services (5%)
7240 - Climate-Enterprises (25%)
7250 - Hospital Insurance (15%)
7260 - Social Enterprises (7%)
7270 - INPL Smart Advances Repayments
```

## Journal Entry Templates

### 1. Cash Payment Entry Template
```sql
-- Template for cash payments
INSERT INTO journal_entry_templates (name, description, pos_accnt_id) VALUES
('Cash Payment', 'Standard cash payment entry', 1);

-- Template lines
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(1, 1, '6000', 'debit', 'Operating Expense Account'),
(1, 2, '1110', 'credit', 'Cash Account');
```

### 2. Cash Receipt Entry Template
```sql
-- Template for cash receipts
INSERT INTO journal_entry_templates (name, description, pos_accnt_id) VALUES
('Cash Receipt', 'Standard cash receipt entry', 1);

-- Template lines
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(1, 1, '1110', 'debit', 'Cash Account'),
(1, 2, '4100', 'credit', 'Sales Revenue Account');
```

### 3. Cost of Sales Entry Template
```sql
-- Template for cost of sales
INSERT INTO journal_entry_templates (name, description, pos_accnt_id) VALUES
('Cost of Sales', 'Cost of sales recognition', 1);

-- Template lines
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(1, 1, '5100', 'debit', 'Cost of Goods Sold'),
(1, 2, '1130', 'credit', 'Inventory Account');
```

## Business Rules and Validations

### 1. GLS (Government Levy System) Rules
- **Automatic Calculation**: System automatically calculates GLS percentages
- **Compliance Tracking**: Track all GLS payments and submissions
- **Reporting Requirements**: Generate GLS compliance reports
- **Payment Validation**: Ensure GLS payments are made on time

### 2. Cost of Sales Validation
- **Cost Accuracy**: Ensure all cost components are captured
- **Profit Margin Monitoring**: Alert when margins fall below threshold
- **Inventory Valuation**: Maintain accurate inventory costs
- **Waste Tracking**: Monitor kitchen salvages and waste

### 3. Cash Flow Management
- **Daily Reconciliation**: Reconcile cash receipts with bank deposits
- **Payment Tracking**: Track all cash payments by category
- **Budget Monitoring**: Compare actual vs budgeted expenses
- **Cash Flow Forecasting**: Predict future cash needs

## Integration Points

### 1. POS System Integration
- **Real-time Sales**: Automatically create sales journal entries
- **Payment Processing**: Track payment methods and amounts
- **Inventory Updates**: Update inventory levels and costs
- **Customer Tracking**: Monitor customer payments and credits

### 2. Banking Integration
- **Bank Deposits**: Automatically track bank deposits
- **Payment Processing**: Monitor bank charges and fees
- **Reconciliation**: Match POS transactions with bank statements
- **Cash Management**: Optimize cash flow and banking

### 3. Government Compliance
- **GLS Reporting**: Generate required government reports
- **Tax Calculations**: Calculate and track all taxes
- **Compliance Monitoring**: Ensure regulatory compliance
- **Audit Trail**: Maintain complete audit trail

This expanded analysis provides the specific business context needed to implement a comprehensive bookkeeping system that handles the unique requirements of this business model, including government levies, social impact tracking, and specialized revenue streams.
