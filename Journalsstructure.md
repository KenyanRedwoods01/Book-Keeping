# Enhanced Journal Structure - Business-Specific Implementation

## Overview
This document provides the enhanced journal structure specifically designed for the business model with detailed cash payment categories, cash receipts, and specialized journal types.

## Enhanced Journal Entry Types

### 1. Cash Payment Journal Entries
**Purpose**: Track all money going out of the business

#### Payment Categories and Account Mappings:

##### Core Business Operations
```sql
-- Purchases
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Payment - Purchases', 'purchase', 1);

-- Template lines for purchases
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(1, 1, '5100', 'debit', 'Direct Materials - Food Ingredients'),
(1, 2, '1110', 'credit', 'Cash Account');
```

##### Technology & Communication
```sql
-- Computer Internet
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Payment - Computer Internet', 'expense', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(2, 1, '6210', 'debit', 'Computer Internet Expense'),
(2, 2, '1110', 'credit', 'Cash Account');

-- Bank/Mpesa Charges
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Payment - Bank Charges', 'expense', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(3, 1, '6230', 'debit', 'Bank/Mpesa Charges'),
(3, 2, '1110', 'credit', 'Cash Account');
```

##### Government & Regulatory (GLS)
```sql
-- Loyalty-as-a-Service (15% GLS)
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Payment - LaaS (15% GLS)', 'expense', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(4, 1, '7110', 'debit', 'Loyalty-as-a-Service (15% GLS)'),
(4, 2, '1110', 'credit', 'Cash Account');

-- Withholding Tax (5% GLS)
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Payment - Withholding Tax (5% GLS)', 'expense', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(5, 1, '7120', 'debit', 'Withholding Tax (5% GLS)'),
(5, 2, '1110', 'credit', 'Cash Account');
```

### 2. Cash Receipt Journal Entries
**Purpose**: Track all money coming into the business

#### Receipt Categories and Account Mappings:

##### Core Revenue Streams
```sql
-- Sales Revenue
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Receipt - Sales', 'sale', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(6, 1, '1110', 'debit', 'Cash Account'),
(6, 2, '4110', 'credit', 'Product Sales Revenue');

-- Membership Fees
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Receipt - Membership Fees', 'income', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(7, 1, '1110', 'debit', 'Cash Account'),
(7, 2, '4130', 'credit', 'Membership Revenue');
```

##### Social Impact & Development
```sql
-- Climate Enterprise Income
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Receipt - Climate Enterprise', 'income', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(8, 1, '1110', 'debit', 'Cash Account'),
(8, 2, '4260', 'credit', 'Climate Enterprise Income');

-- Donations
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cash Receipt - Donations', 'income', 1);

INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(9, 1, '1110', 'debit', 'Cash Account'),
(9, 2, '4230', 'credit', 'Donation Income');
```

### 3. Cost of Sales Journal Entries
**Purpose**: Track actual cost of preparing products/services

#### Cost Structure:
```sql
-- Cost of Sales Template
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Cost of Sales - Product Preparation', 'cost_of_sales', 1);

-- Raw Materials
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(10, 1, '5110', 'debit', 'Food Ingredients - Raw Materials'),
(10, 2, '1130', 'credit', 'Inventory Account');

-- Direct Labor
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(11, 1, '5120', 'debit', 'Direct Labor - Kitchen Staff'),
(11, 2, '1110', 'credit', 'Cash Account');

-- Manufacturing Overhead
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(12, 1, '5130', 'debit', 'Manufacturing Overhead'),
(12, 2, '1110', 'credit', 'Cash Account');
```

#### Cost Calculation Logic:
```java
@Service
public class CostOfSalesService {
    
    public CostOfSalesCalculation calculateProductCost(Long productId, Integer quantity) {
        // Get raw material costs
        BigDecimal rawMaterialCost = getRawMaterialCost(productId, quantity);
        
        // Get direct labor costs
        BigDecimal laborCost = getDirectLaborCost(productId, quantity);
        
        // Get overhead allocation
        BigDecimal overheadCost = getOverheadAllocation(productId, quantity);
        
        // Calculate total cost
        BigDecimal totalCost = rawMaterialCost.add(laborCost).add(overheadCost);
        
        // Calculate profit margin
        BigDecimal sellingPrice = getSellingPrice(productId);
        BigDecimal profitMargin = sellingPrice.subtract(totalCost);
        BigDecimal marginPercentage = profitMargin.divide(sellingPrice, 4, RoundingMode.HALF_UP)
                                                 .multiply(new BigDecimal("100"));
        
        return new CostOfSalesCalculation(
            productId, quantity, rawMaterialCost, laborCost, 
            overheadCost, totalCost, sellingPrice, profitMargin, marginPercentage
        );
    }
}
```

### 4. Sales Journal Entries
**Purpose**: Track selling prices and revenue recognition

#### Sales Structure:
```sql
-- Sales Revenue Template
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Sales Revenue Recognition', 'sale', 1);

-- Product Sales
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(13, 1, '1110', 'debit', 'Cash Account'),
(13, 2, '4110', 'credit', 'Product Sales Revenue');

-- Cost of Sales Recognition
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(14, 1, '5100', 'debit', 'Cost of Goods Sold'),
(14, 2, '1130', 'credit', 'Inventory Account');
```

#### Profit Calculation Logic:
```java
@Service
public class SalesProfitService {
    
    public SalesProfitCalculation calculateSalesProfit(Long saleId) {
        // Get sale details
        Sale sale = saleRepository.findById(saleId);
        
        // Get product sales
        List<ProductSale> productSales = productSaleRepository.findBySaleId(saleId);
        
        BigDecimal totalRevenue = BigDecimal.ZERO;
        BigDecimal totalCost = BigDecimal.ZERO;
        
        for (ProductSale productSale : productSales) {
            // Calculate revenue
            BigDecimal revenue = productSale.getTotal();
            totalRevenue = totalRevenue.add(revenue);
            
            // Calculate cost
            BigDecimal cost = costOfSalesService.calculateProductCost(
                productSale.getProductId(), 
                productSale.getQty().intValue()
            ).getTotalCost();
            totalCost = totalCost.add(cost);
        }
        
        // Calculate profit
        BigDecimal grossProfit = totalRevenue.subtract(totalCost);
        BigDecimal profitMargin = grossProfit.divide(totalRevenue, 4, RoundingMode.HALF_UP)
                                            .multiply(new BigDecimal("100"));
        
        return new SalesProfitCalculation(
            saleId, totalRevenue, totalCost, grossProfit, profitMargin
        );
    }
}
```

### 5. Purchase Journal Entries
**Purpose**: Track supplier purchases and inventory costs

#### Purchase Structure:
```sql
-- Purchase Template
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Purchase from Supplier', 'purchase', 1);

-- Inventory Purchase
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(15, 1, '1130', 'debit', 'Inventory Account'),
(15, 2, '2110', 'credit', 'Accounts Payable');

-- Cash Payment for Purchase
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(16, 1, '2110', 'debit', 'Accounts Payable'),
(16, 2, '1110', 'credit', 'Cash Account');
```

#### Wholesale vs Retail Pricing:
```java
@Service
public class PurchasePricingService {
    
    public PurchasePricingCalculation calculatePricing(Long productId, Integer quantity) {
        // Get purchase price from supplier
        BigDecimal purchasePrice = getPurchasePrice(productId);
        
        // Calculate wholesale price (with markup)
        BigDecimal wholesaleMarkup = getWholesaleMarkup(productId);
        BigDecimal wholesalePrice = purchasePrice.multiply(wholesaleMarkup);
        
        // Calculate retail price (with additional markup)
        BigDecimal retailMarkup = getRetailMarkup(productId);
        BigDecimal retailPrice = wholesalePrice.multiply(retailMarkup);
        
        // Calculate total costs and profits
        BigDecimal totalPurchaseCost = purchasePrice.multiply(new BigDecimal(quantity));
        BigDecimal totalWholesaleValue = wholesalePrice.multiply(new BigDecimal(quantity));
        BigDecimal totalRetailValue = retailPrice.multiply(new BigDecimal(quantity));
        
        return new PurchasePricingCalculation(
            productId, quantity, purchasePrice, wholesalePrice, retailPrice,
            totalPurchaseCost, totalWholesaleValue, totalRetailValue
        );
    }
}
```

### 6. Bank Deposits Journal Entries
**Purpose**: Track all bank deposits and their nature

#### Deposit Structure:
```sql
-- Bank Deposit Template
INSERT INTO journal_entry_templates (name, reference_type, pos_accnt_id) VALUES
('Bank Deposit', 'bank_deposit', 1);

-- Cash to Bank Transfer
INSERT INTO journal_entry_template_lines (template_id, line_order, account_code, debit_credit, description) VALUES
(17, 1, '1113', 'debit', 'Cash in Bank'),
(17, 2, '1110', 'credit', 'Cash in Hand');
```

#### Deposit Tracking:
```java
@Entity
@Table(name = "bank_deposits")
public class BankDeposit {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(name = "deposit_date", nullable = false)
    private LocalDate depositDate;
    
    @Column(name = "deposit_amount", precision = 15, scale = 2, nullable = false)
    private BigDecimal depositAmount;
    
    @Enumerated(EnumType.STRING)
    @Column(name = "deposit_type", nullable = false)
    private DepositType depositType;
    
    @Column(name = "source_reference")
    private String sourceReference;
    
    @Column(name = "bank_account", nullable = false)
    private String bankAccount;
    
    @Enumerated(EnumType.STRING)
    @Column(name = "status", nullable = false)
    private DepositStatus status;
    
    @Column(name = "pos_accnt_id", nullable = false)
    private Long posAccntId;
    
    // Getters, setters, constructors
}

public enum DepositType {
    SALES_REVENUE,
    MEMBERSHIP_FEES,
    DONATIONS,
    INVESTOR_FUNDS,
    CASH_ADVANCES,
    ADVANCE_PAYMENTS,
    EQUIPMENT_RENTAL,
    CLIMATE_ENTERPRISE,
    SOCIAL_ENTERPRISE,
    FUNDRAISING,
    JOINT_VENTURE,
    ENDOWMENT,
    VOLUNTEER_VALUATION,
    OTHER_REVENUE
}

public enum DepositStatus {
    PENDING,
    CLEARED,
    FAILED,
    RETURNED
}
```

## Enhanced Chart of Accounts

### 1. Complete Account Structure
```sql
-- Create enhanced chart of accounts
INSERT INTO chart_of_accounts (account_code, account_name, account_type, normal_balance, pos_accnt_id, created_by) VALUES

-- ASSETS (1000-1999)
('1000', 'ASSETS', 'asset', 'debit', 1, 1),
('1100', 'Current Assets', 'asset', 'debit', 1, 1),
('1110', 'Cash and Cash Equivalents', 'asset', 'debit', 1, 1),
('1111', 'Petty Cash', 'asset', 'debit', 1, 1),
('1112', 'Cash in Hand', 'asset', 'debit', 1, 1),
('1113', 'Cash in Bank', 'asset', 'debit', 1, 1),
('1120', 'Accounts Receivable', 'asset', 'debit', 1, 1),
('1121', 'Trade Receivables', 'asset', 'debit', 1, 1),
('1122', 'Other Receivables', 'asset', 'debit', 1, 1),
('1130', 'Inventory', 'asset', 'debit', 1, 1),
('1131', 'Raw Materials', 'asset', 'debit', 1, 1),
('1132', 'Finished Goods', 'asset', 'debit', 1, 1),
('1133', 'Packaging Materials', 'asset', 'debit', 1, 1),

-- LIABILITIES (2000-2999)
('2000', 'LIABILITIES', 'liability', 'credit', 1, 1),
('2100', 'Current Liabilities', 'liability', 'credit', 1, 1),
('2110', 'Accounts Payable', 'liability', 'credit', 1, 1),
('2111', 'Trade Payables', 'liability', 'credit', 1, 1),
('2112', 'Other Payables', 'liability', 'credit', 1, 1),
('2120', 'Accrued Expenses', 'liability', 'credit', 1, 1),
('2130', 'Tax Payable', 'liability', 'credit', 1, 1),
('2131', 'Sales Tax Payable', 'liability', 'credit', 1, 1),
('2132', 'Withholding Tax Payable', 'liability', 'credit', 1, 1),

-- EQUITY (3000-3999)
('3000', 'EQUITY', 'equity', 'credit', 1, 1),
('3100', 'Owner Equity', 'equity', 'credit', 1, 1),
('3110', 'Capital Account', 'equity', 'credit', 1, 1),
('3120', 'Owner Drawings', 'equity', 'debit', 1, 1),
('3200', 'Retained Earnings', 'equity', 'credit', 1, 1),

-- REVENUE (4000-4999)
('4000', 'REVENUE', 'revenue', 'credit', 1, 1),
('4100', 'Sales Revenue', 'revenue', 'credit', 1, 1),
('4110', 'Product Sales', 'revenue', 'credit', 1, 1),
('4111', 'Food Sales', 'revenue', 'credit', 1, 1),
('4112', 'Beverage Sales', 'revenue', 'credit', 1, 1),
('4120', 'Service Revenue', 'revenue', 'credit', 1, 1),
('4121', 'Smart Extension Services', 'revenue', 'credit', 1, 1),
('4122', 'Equipment Rental', 'revenue', 'credit', 1, 1),
('4130', 'Membership Revenue', 'revenue', 'credit', 1, 1),
('4200', 'Other Income', 'revenue', 'credit', 1, 1),
('4210', 'Interest Income', 'revenue', 'credit', 1, 1),
('4211', 'Climate Impact Bond Interest', 'revenue', 'credit', 1, 1),
('4220', 'Rental Income', 'revenue', 'credit', 1, 1),
('4230', 'Donation Income', 'revenue', 'credit', 1, 1),
('4240', 'Fundraising Income', 'revenue', 'credit', 1, 1),
('4250', 'Joint Venture Income', 'revenue', 'credit', 1, 1),
('4260', 'Climate Enterprise Income', 'revenue', 'credit', 1, 1),
('4270', 'Social Enterprise Income', 'revenue', 'credit', 1, 1),
('4280', 'Volunteer Valuation Income', 'revenue', 'credit', 1, 1),
('4290', 'Miscellaneous Income', 'revenue', 'credit', 1, 1),

-- COST OF GOODS SOLD (5000-5999)
('5000', 'COST OF GOODS SOLD', 'expense', 'debit', 1, 1),
('5100', 'Direct Materials', 'expense', 'debit', 1, 1),
('5110', 'Food Ingredients', 'expense', 'debit', 1, 1),
('5111', 'Raw Materials', 'expense', 'debit', 1, 1),
('5112', 'Packaging Materials', 'expense', 'debit', 1, 1),
('5120', 'Direct Labor', 'expense', 'debit', 1, 1),
('5121', 'Kitchen Staff', 'expense', 'debit', 1, 1),
('5122', 'Service Staff', 'expense', 'debit', 1, 1),
('5130', 'Manufacturing Overhead', 'expense', 'debit', 1, 1),
('5131', 'Kitchen Utilities', 'expense', 'debit', 1, 1),
('5132', 'Equipment Depreciation', 'expense', 'debit', 1, 1),
('5133', 'Kitchen Supplies', 'expense', 'debit', 1, 1),

-- OPERATING EXPENSES (6000-6999)
('6000', 'OPERATING EXPENSES', 'expense', 'debit', 1, 1),
('6100', 'Personnel Expenses', 'expense', 'debit', 1, 1),
('6110', 'Salaries and Wages', 'expense', 'debit', 1, 1),
('6111', 'Direct Salaries', 'expense', 'debit', 1, 1),
('6112', 'Administrative Salaries', 'expense', 'debit', 1, 1),
('6120', 'Payroll Taxes and Benefits', 'expense', 'debit', 1, 1),
('6121', 'Employer Payroll Taxes', 'expense', 'debit', 1, 1),
('6122', 'Employee Benefits', 'expense', 'debit', 1, 1),
('6130', 'Staff Meals', 'expense', 'debit', 1, 1),
('6200', 'Technology Expenses', 'expense', 'debit', 1, 1),
('6210', 'Computer Internet', 'expense', 'debit', 1, 1),
('6211', 'IT Enabled Services', 'expense', 'debit', 1, 1),
('6212', 'Website Services', 'expense', 'debit', 1, 1),
('6220', 'Communication', 'expense', 'debit', 1, 1),
('6221', 'Telephone', 'expense', 'debit', 1, 1),
('6222', 'Bank Charges', 'expense', 'debit', 1, 1),
('6230', 'Bank/Mpesa Charges', 'expense', 'debit', 1, 1),
('6231', 'Payment Processing', 'expense', 'debit', 1, 1),
('6232', 'Collection Processing', 'expense', 'debit', 1, 1),

-- GOVERNMENT AND REGULATORY (7000-7999)
('7000', 'GOVERNMENT AND REGULATORY', 'expense', 'debit', 1, 1),
('7100', 'Government Levies (GLS)', 'expense', 'debit', 1, 1),
('7110', 'Loyalty-as-a-Service (15% GLS)', 'expense', 'debit', 1, 1),
('7120', 'Withholding Tax (5% GLS)', 'expense', 'debit', 1, 1),
('7130', 'Trading License (1% GLS)', 'expense', 'debit', 1, 1),
('7140', 'INPL Interest (1% GLS)', 'expense', 'debit', 1, 1),
('7150', 'Teller Operations (10% GLS)', 'expense', 'debit', 1, 1),
('7160', 'Curricula Development (1% GLS)', 'expense', 'debit', 1, 1),
('7170', 'Data-Science (1% GLS)', 'expense', 'debit', 1, 1),
('7180', 'Socio-enterprise Development (1% GLS)', 'expense', 'debit', 1, 1),
('7190', 'Agronomy Services (1% GLS)', 'expense', 'debit', 1, 1),
('7200', 'Climate-Science (1% GLS)', 'expense', 'debit', 1, 1),
('7210', 'Rent + Utilities (5% GLS)', 'expense', 'debit', 1, 1),
('7220', 'Market Activations (5% GLS)', 'expense', 'debit', 1, 1),
('7230', 'Smart Extension Services (5% GLS)', 'expense', 'debit', 1, 1),
('7240', 'Climate-Enterprises (25% GLS)', 'expense', 'debit', 1, 1),
('7250', 'Hospital Insurance (15% GLS)', 'expense', 'debit', 1, 1),
('7260', 'Social Enterprises (7% GLS)', 'expense', 'debit', 1, 1),
('7270', 'INPL Smart Advances Repayments', 'expense', 'debit', 1, 1);
```

## Business Rules and Validations

### 1. GLS (Government Levy System) Validation
```java
@Service
public class GLSValidationService {
    
    public void validateGLSPayment(BigDecimal amount, GLSCategory category) {
        BigDecimal expectedGLS = calculateGLSAmount(amount, category);
        
        // Validate GLS percentage
        if (!isValidGLSPercentage(category, expectedGLS, amount)) {
            throw new GLSValidationException("Invalid GLS percentage for category: " + category);
        }
        
        // Check compliance deadlines
        if (isGLSPaymentOverdue(category)) {
            throw new GLSComplianceException("GLS payment overdue for category: " + category);
        }
    }
    
    private BigDecimal calculateGLSAmount(BigDecimal amount, GLSCategory category) {
        return amount.multiply(category.getGLSPercentage()).divide(new BigDecimal("100"));
    }
}
```

### 2. Cost of Sales Validation
```java
@Service
public class CostOfSalesValidationService {
    
    public void validateCostOfSales(CostOfSalesCalculation calculation) {
        // Validate profit margin
        if (calculation.getMarginPercentage().compareTo(new BigDecimal("10")) < 0) {
            throw new LowProfitMarginException("Profit margin below 10% threshold");
        }
        
        // Validate cost components
        if (calculation.getRawMaterialCost().compareTo(BigDecimal.ZERO) <= 0) {
            throw new InvalidCostException("Raw material cost must be positive");
        }
        
        if (calculation.getLaborCost().compareTo(BigDecimal.ZERO) <= 0) {
            throw new InvalidCostException("Labor cost must be positive");
        }
    }
}
```

This enhanced journal structure provides a complete framework for implementing the specific business model with detailed cash flow tracking, government compliance, and specialized revenue streams.
