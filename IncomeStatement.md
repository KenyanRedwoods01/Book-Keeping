# Enhanced Income Statement - Business-Specific Implementation

## Overview
This document provides an enhanced income statement structure specifically designed for the business model with detailed cash payment categories, cash receipts, and specialized revenue streams.

## Enhanced Income Statement Structure

### 1. Revenue Section (Money In)

#### Core Business Revenue
```
REVENUE
├── Sales Revenue
│   ├── Product Sales
│   │   ├── Food Sales
│   │   ├── Beverage Sales
│   │   └── Merchandise Sales
│   └── Service Revenue
│       ├── Smart Extension Services
│       └── Equipment Rental
├── Membership Revenue
│   ├── Annual Membership
│   └── Monthly Membership
└── Other Business Income
    ├── Kitchen Salvages
    ├── Equipment Rental Income
    └── Wifi Charges
```

#### Social Impact Revenue
```
SOCIAL IMPACT REVENUE
├── Climate Enterprise Income
├── Social Enterprise Income
├── Donation Income
├── Fundraising Income
├── Joint Venture Income
├── Endowment Building
└── Volunteer Valuation Income
```

#### Financial Revenue
```
FINANCIAL REVENUE
├── Interest Income
│   └── Climate Impact Bond Interest
├── Investment Income
│   └── Investor Funds
└── Other Financial Income
    ├── Cash Advances
    ├── Advance Payments
    └── Overdrafts
```

### 2. Cost of Goods Sold (COGS)

#### Direct Materials
```
COST OF GOODS SOLD
├── Direct Materials
│   ├── Food Ingredients
│   │   ├── Raw Materials
│   │   └── Packaging Materials
│   └── Other Direct Materials
├── Direct Labor
│   ├── Kitchen Staff
│   └── Service Staff
└── Manufacturing Overhead
    ├── Kitchen Utilities
    ├── Equipment Depreciation
    └── Kitchen Supplies
```

### 3. Operating Expenses (Money Out)

#### Personnel Expenses
```
PERSONNEL EXPENSES
├── Direct Salaries/Wages
├── Payroll Taxes and Benefits
├── Staff Meals
└── Recruitment, Meeting & Conferencing
```

#### Technology & Communication
```
TECHNOLOGY & COMMUNICATION
├── Computer Internet
├── Bank/Mpesa Payment Charges
├── Bank/Mpesa Collection Charges
├── Telephone
└── IT Enabled Services (1% GLS)
```

#### Administrative Expenses
```
ADMINISTRATIVE EXPENSES
├── Office Supplies (Stationery)
├── Printing, Photocopying
├── Business Registration
├── Travel & Accommodation
├── Maintenance
├── Cleaning Materials
└── Hire of Equipment
```

#### Facility Expenses
```
FACILITY EXPENSES
├── Security Expenses
├── Depreciation-Direct
└── Rent + Utilities (5% GLS)
```

#### Business Development
```
BUSINESS DEVELOPMENT
├── Market Activations (5% GLS)
├── Smart Extension Services (5% GLS)
└── Climate-Enterprises (25% GLS)
```

### 4. Government & Regulatory Expenses (GLS)

#### Government Levies (GLS)
```
GOVERNMENT LEVIES (GLS)
├── Loyalty-as-a-Service (LaaS) (15% GLS)
├── Withholding Tax (5% GLS)
├── Trading License (1% GLS)
├── INPL Interest (1% GLS)
├── Teller Operations (10% GLS)
├── Curricula Development (1% GLS)
├── Data-Science (1% GLS)
├── Socio-enterprise Development (1% GLS)
├── Agronomy Services (1% GLS)
├── Climate-Science (1% GLS)
├── Hospital Insurance (15% GLS)
├── Social Enterprises (7% GLS)
└── INPL Smart Advances Repayments
```

### 5. Special Categories

#### Creditors & Rewards
```
SPECIAL CATEGORIES
├── Creditors (Accounts Payable Payments)
└── Rewards (Customer Loyalty Rewards)
```

## Enhanced Income Statement Template

### 1. Database Structure
```sql
-- Enhanced income statement template
INSERT INTO income_statement_template (line_order, line_name, line_type, parent_line_id, calculation_type, pos_accnt_id) VALUES

-- REVENUE SECTION
(1, 'REVENUE', 'header', NULL, 'sum', 1),
(2, 'Core Business Revenue', 'subtotal', 1, 'sum', 1),
(3, 'Sales Revenue', 'subtotal', 2, 'sum', 1),
(4, 'Product Sales', 'account', 3, 'sum', 1),
(5, 'Food Sales', 'account', 4, 'sum', 1),
(6, 'Beverage Sales', 'account', 4, 'sum', 1),
(7, 'Service Revenue', 'account', 3, 'sum', 1),
(8, 'Smart Extension Services', 'account', 7, 'sum', 1),
(9, 'Equipment Rental', 'account', 7, 'sum', 1),
(10, 'Membership Revenue', 'account', 2, 'sum', 1),
(11, 'Other Business Income', 'subtotal', 2, 'sum', 1),
(12, 'Kitchen Salvages', 'account', 11, 'sum', 1),
(13, 'Equipment Rental Income', 'account', 11, 'sum', 1),
(14, 'Wifi Charges', 'account', 11, 'sum', 1),
(15, 'Social Impact Revenue', 'subtotal', 1, 'sum', 1),
(16, 'Climate Enterprise Income', 'account', 15, 'sum', 1),
(17, 'Social Enterprise Income', 'account', 15, 'sum', 1),
(18, 'Donation Income', 'account', 15, 'sum', 1),
(19, 'Fundraising Income', 'account', 15, 'sum', 1),
(20, 'Joint Venture Income', 'account', 15, 'sum', 1),
(21, 'Endowment Building', 'account', 15, 'sum', 1),
(22, 'Volunteer Valuation Income', 'account', 15, 'sum', 1),
(23, 'Financial Revenue', 'subtotal', 1, 'sum', 1),
(24, 'Interest Income', 'account', 23, 'sum', 1),
(25, 'Climate Impact Bond Interest', 'account', 24, 'sum', 1),
(26, 'Investment Income', 'account', 23, 'sum', 1),
(27, 'Investor Funds', 'account', 26, 'sum', 1),
(28, 'Total Revenue', 'total', 1, 'sum', 1),

-- COST OF GOODS SOLD SECTION
(29, 'COST OF GOODS SOLD', 'header', NULL, 'sum', 1),
(30, 'Direct Materials', 'subtotal', 29, 'sum', 1),
(31, 'Food Ingredients', 'account', 30, 'sum', 1),
(32, 'Raw Materials', 'account', 31, 'sum', 1),
(33, 'Packaging Materials', 'account', 31, 'sum', 1),
(34, 'Direct Labor', 'subtotal', 29, 'sum', 1),
(35, 'Kitchen Staff', 'account', 34, 'sum', 1),
(36, 'Service Staff', 'account', 34, 'sum', 1),
(37, 'Manufacturing Overhead', 'subtotal', 29, 'sum', 1),
(38, 'Kitchen Utilities', 'account', 37, 'sum', 1),
(39, 'Equipment Depreciation', 'account', 37, 'sum', 1),
(40, 'Kitchen Supplies', 'account', 37, 'sum', 1),
(41, 'Total Cost of Goods Sold', 'total', 29, 'sum', 1),
(42, 'Gross Profit', 'total', NULL, 'subtract', 1),

-- OPERATING EXPENSES SECTION
(43, 'OPERATING EXPENSES', 'header', NULL, 'sum', 1),
(44, 'Personnel Expenses', 'subtotal', 43, 'sum', 1),
(45, 'Direct Salaries/Wages', 'account', 44, 'sum', 1),
(46, 'Payroll Taxes and Benefits', 'account', 44, 'sum', 1),
(47, 'Staff Meals', 'account', 44, 'sum', 1),
(48, 'Recruitment, Meeting & Conferencing', 'account', 44, 'sum', 1),
(49, 'Technology & Communication', 'subtotal', 43, 'sum', 1),
(50, 'Computer Internet', 'account', 49, 'sum', 1),
(51, 'Bank/Mpesa Payment Charges', 'account', 49, 'sum', 1),
(52, 'Bank/Mpesa Collection Charges', 'account', 49, 'sum', 1),
(53, 'Telephone', 'account', 49, 'sum', 1),
(54, 'IT Enabled Services (1% GLS)', 'account', 49, 'sum', 1),
(55, 'Administrative Expenses', 'subtotal', 43, 'sum', 1),
(56, 'Office Supplies (Stationery)', 'account', 55, 'sum', 1),
(57, 'Printing, Photocopying', 'account', 55, 'sum', 1),
(58, 'Business Registration', 'account', 55, 'sum', 1),
(59, 'Travel & Accommodation', 'account', 55, 'sum', 1),
(60, 'Maintenance', 'account', 55, 'sum', 1),
(61, 'Cleaning Materials', 'account', 55, 'sum', 1),
(62, 'Hire of Equipment', 'account', 55, 'sum', 1),
(63, 'Facility Expenses', 'subtotal', 43, 'sum', 1),
(64, 'Security Expenses', 'account', 63, 'sum', 1),
(65, 'Depreciation-Direct', 'account', 63, 'sum', 1),
(66, 'Rent + Utilities (5% GLS)', 'account', 63, 'sum', 1),
(67, 'Business Development', 'subtotal', 43, 'sum', 1),
(68, 'Market Activations (5% GLS)', 'account', 67, 'sum', 1),
(69, 'Smart Extension Services (5% GLS)', 'account', 67, 'sum', 1),
(70, 'Climate-Enterprises (25% GLS)', 'account', 67, 'sum', 1),
(71, 'Total Operating Expenses', 'total', 43, 'sum', 1),
(72, 'Operating Income', 'total', NULL, 'subtract', 1),

-- GOVERNMENT LEVIES SECTION
(73, 'GOVERNMENT LEVIES (GLS)', 'header', NULL, 'sum', 1),
(74, 'Loyalty-as-a-Service (LaaS) (15% GLS)', 'account', 73, 'sum', 1),
(75, 'Withholding Tax (5% GLS)', 'account', 73, 'sum', 1),
(76, 'Trading License (1% GLS)', 'account', 73, 'sum', 1),
(77, 'INPL Interest (1% GLS)', 'account', 73, 'sum', 1),
(78, 'Teller Operations (10% GLS)', 'account', 73, 'sum', 1),
(79, 'Curricula Development (1% GLS)', 'account', 73, 'sum', 1),
(80, 'Data-Science (1% GLS)', 'account', 73, 'sum', 1),
(81, 'Socio-enterprise Development (1% GLS)', 'account', 73, 'sum', 1),
(82, 'Agronomy Services (1% GLS)', 'account', 73, 'sum', 1),
(83, 'Climate-Science (1% GLS)', 'account', 73, 'sum', 1),
(84, 'Hospital Insurance (15% GLS)', 'account', 73, 'sum', 1),
(85, 'Social Enterprises (7% GLS)', 'account', 73, 'sum', 1),
(86, 'INPL Smart Advances Repayments', 'account', 73, 'sum', 1),
(87, 'Total Government Levies', 'total', 73, 'sum', 1),

-- SPECIAL CATEGORIES
(88, 'SPECIAL CATEGORIES', 'header', NULL, 'sum', 1),
(89, 'Creditors (Accounts Payable Payments)', 'account', 88, 'sum', 1),
(90, 'Rewards (Customer Loyalty Rewards)', 'account', 88, 'sum', 1),
(91, 'Total Special Categories', 'total', 88, 'sum', 1),

-- FINAL TOTALS
(92, 'Total Expenses', 'total', NULL, 'sum', 1),
(93, 'Net Income', 'total', NULL, 'subtract', 1);
```

## Enhanced Income Statement Generation

### 1. Revenue Calculation Service
```java
@Service
public class EnhancedIncomeStatementService {
    
    public IncomeStatementDto generateIncomeStatement(LocalDate fromDate, LocalDate toDate) {
        IncomeStatementDto incomeStatement = new IncomeStatementDto();
        incomeStatement.setFromDate(fromDate);
        incomeStatement.setToDate(toDate);
        
        // Calculate core business revenue
        BigDecimal coreBusinessRevenue = calculateCoreBusinessRevenue(fromDate, toDate);
        incomeStatement.setCoreBusinessRevenue(coreBusinessRevenue);
        
        // Calculate social impact revenue
        BigDecimal socialImpactRevenue = calculateSocialImpactRevenue(fromDate, toDate);
        incomeStatement.setSocialImpactRevenue(socialImpactRevenue);
        
        // Calculate financial revenue
        BigDecimal financialRevenue = calculateFinancialRevenue(fromDate, toDate);
        incomeStatement.setFinancialRevenue(financialRevenue);
        
        // Calculate total revenue
        BigDecimal totalRevenue = coreBusinessRevenue.add(socialImpactRevenue).add(financialRevenue);
        incomeStatement.setTotalRevenue(totalRevenue);
        
        // Calculate cost of goods sold
        BigDecimal costOfGoodsSold = calculateCostOfGoodsSold(fromDate, toDate);
        incomeStatement.setCostOfGoodsSold(costOfGoodsSold);
        
        // Calculate gross profit
        BigDecimal grossProfit = totalRevenue.subtract(costOfGoodsSold);
        incomeStatement.setGrossProfit(grossProfit);
        
        // Calculate operating expenses
        BigDecimal operatingExpenses = calculateOperatingExpenses(fromDate, toDate);
        incomeStatement.setOperatingExpenses(operatingExpenses);
        
        // Calculate government levies
        BigDecimal governmentLevies = calculateGovernmentLevies(fromDate, toDate);
        incomeStatement.setGovernmentLevies(governmentLevies);
        
        // Calculate special categories
        BigDecimal specialCategories = calculateSpecialCategories(fromDate, toDate);
        incomeStatement.setSpecialCategories(specialCategories);
        
        // Calculate total expenses
        BigDecimal totalExpenses = costOfGoodsSold.add(operatingExpenses)
                                                 .add(governmentLevies)
                                                 .add(specialCategories);
        incomeStatement.setTotalExpenses(totalExpenses);
        
        // Calculate net income
        BigDecimal netIncome = totalRevenue.subtract(totalExpenses);
        incomeStatement.setNetIncome(netIncome);
        
        return incomeStatement;
    }
    
    private BigDecimal calculateCoreBusinessRevenue(LocalDate fromDate, LocalDate toDate) {
        // Product sales
        BigDecimal productSales = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4110", fromDate, toDate);
        
        // Service revenue
        BigDecimal serviceRevenue = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4120", fromDate, toDate);
        
        // Membership revenue
        BigDecimal membershipRevenue = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4130", fromDate, toDate);
        
        // Other business income
        BigDecimal otherBusinessIncome = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4200", fromDate, toDate);
        
        return productSales.add(serviceRevenue).add(membershipRevenue).add(otherBusinessIncome);
    }
    
    private BigDecimal calculateSocialImpactRevenue(LocalDate fromDate, LocalDate toDate) {
        BigDecimal climateEnterprise = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4260", fromDate, toDate);
        
        BigDecimal socialEnterprise = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4270", fromDate, toDate);
        
        BigDecimal donations = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4230", fromDate, toDate);
        
        BigDecimal fundraising = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4240", fromDate, toDate);
        
        BigDecimal jointVenture = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4250", fromDate, toDate);
        
        BigDecimal endowment = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4280", fromDate, toDate);
        
        BigDecimal volunteerValuation = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4280", fromDate, toDate);
        
        return climateEnterprise.add(socialEnterprise).add(donations)
                              .add(fundraising).add(jointVenture)
                              .add(endowment).add(volunteerValuation);
    }
    
    private BigDecimal calculateFinancialRevenue(LocalDate fromDate, LocalDate toDate) {
        BigDecimal interestIncome = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4210", fromDate, toDate);
        
        BigDecimal investmentIncome = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4260", fromDate, toDate);
        
        return interestIncome.add(investmentIncome);
    }
    
    private BigDecimal calculateCostOfGoodsSold(LocalDate fromDate, LocalDate toDate) {
        BigDecimal directMaterials = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("5100", fromDate, toDate);
        
        BigDecimal directLabor = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("5120", fromDate, toDate);
        
        BigDecimal manufacturingOverhead = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("5130", fromDate, toDate);
        
        return directMaterials.add(directLabor).add(manufacturingOverhead);
    }
    
    private BigDecimal calculateOperatingExpenses(LocalDate fromDate, LocalDate toDate) {
        // Personnel expenses
        BigDecimal personnelExpenses = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("6100", fromDate, toDate);
        
        // Technology & communication
        BigDecimal technologyExpenses = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("6200", fromDate, toDate);
        
        // Administrative expenses
        BigDecimal administrativeExpenses = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("6300", fromDate, toDate);
        
        // Facility expenses
        BigDecimal facilityExpenses = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("6400", fromDate, toDate);
        
        // Business development
        BigDecimal businessDevelopment = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("6700", fromDate, toDate);
        
        return personnelExpenses.add(technologyExpenses).add(administrativeExpenses)
                               .add(facilityExpenses).add(businessDevelopment);
    }
    
    private BigDecimal calculateGovernmentLevies(LocalDate fromDate, LocalDate toDate) {
        return journalEntryLineRepository
            .sumByAccountTypeAndDateRange("7000", fromDate, toDate);
    }
    
    private BigDecimal calculateSpecialCategories(LocalDate fromDate, LocalDate toDate) {
        BigDecimal creditors = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("8900", fromDate, toDate);
        
        BigDecimal rewards = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("9000", fromDate, toDate);
        
        return creditors.add(rewards);
    }
}
```

### 2. GLS Compliance Service
```java
@Service
public class GLSComplianceService {
    
    public GLSComplianceReport generateGLSComplianceReport(LocalDate fromDate, LocalDate toDate) {
        GLSComplianceReport report = new GLSComplianceReport();
        report.setFromDate(fromDate);
        report.setToDate(toDate);
        
        // Calculate GLS by category
        Map<String, BigDecimal> glsByCategory = calculateGLSByCategory(fromDate, toDate);
        report.setGlsByCategory(glsByCategory);
        
        // Calculate total GLS
        BigDecimal totalGLS = glsByCategory.values().stream()
            .reduce(BigDecimal.ZERO, BigDecimal::add);
        report.setTotalGLS(totalGLS);
        
        // Check compliance status
        List<GLSComplianceItem> complianceItems = checkGLSCompliance(fromDate, toDate);
        report.setComplianceItems(complianceItems);
        
        // Calculate compliance percentage
        long compliantItems = complianceItems.stream()
            .mapToLong(item -> item.isCompliant() ? 1 : 0)
            .sum();
        double compliancePercentage = (double) compliantItems / complianceItems.size() * 100;
        report.setCompliancePercentage(compliancePercentage);
        
        return report;
    }
    
    private Map<String, BigDecimal> calculateGLSByCategory(LocalDate fromDate, LocalDate toDate) {
        Map<String, BigDecimal> glsByCategory = new HashMap<>();
        
        // Loyalty-as-a-Service (15% GLS)
        BigDecimal laas = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("7110", fromDate, toDate);
        glsByCategory.put("Loyalty-as-a-Service (15% GLS)", laas);
        
        // Withholding Tax (5% GLS)
        BigDecimal withholdingTax = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("7120", fromDate, toDate);
        glsByCategory.put("Withholding Tax (5% GLS)", withholdingTax);
        
        // Trading License (1% GLS)
        BigDecimal tradingLicense = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("7130", fromDate, toDate);
        glsByCategory.put("Trading License (1% GLS)", tradingLicense);
        
        // Continue for all GLS categories...
        
        return glsByCategory;
    }
    
    private List<GLSComplianceItem> checkGLSCompliance(LocalDate fromDate, LocalDate toDate) {
        List<GLSComplianceItem> complianceItems = new ArrayList<>();
        
        // Check each GLS category for compliance
        Map<String, BigDecimal> glsByCategory = calculateGLSByCategory(fromDate, toDate);
        
        for (Map.Entry<String, BigDecimal> entry : glsByCategory.entrySet()) {
            String category = entry.getKey();
            BigDecimal paidAmount = entry.getValue();
            
            // Calculate required amount based on revenue
            BigDecimal requiredAmount = calculateRequiredGLSAmount(category, fromDate, toDate);
            
            boolean isCompliant = paidAmount.compareTo(requiredAmount) >= 0;
            BigDecimal outstandingAmount = requiredAmount.subtract(paidAmount);
            
            GLSComplianceItem item = new GLSComplianceItem(
                category, requiredAmount, paidAmount, outstandingAmount, isCompliant
            );
            complianceItems.add(item);
        }
        
        return complianceItems;
    }
    
    private BigDecimal calculateRequiredGLSAmount(String category, LocalDate fromDate, LocalDate toDate) {
        // Get the GLS percentage for the category
        BigDecimal glsPercentage = getGLSPercentage(category);
        
        // Get the base amount for calculation
        BigDecimal baseAmount = getBaseAmountForGLS(category, fromDate, toDate);
        
        // Calculate required GLS amount
        return baseAmount.multiply(glsPercentage).divide(new BigDecimal("100"));
    }
}
```

### 3. Social Impact Analysis Service
```java
@Service
public class SocialImpactAnalysisService {
    
    public SocialImpactAnalysis generateSocialImpactAnalysis(LocalDate fromDate, LocalDate toDate) {
        SocialImpactAnalysis analysis = new SocialImpactAnalysis();
        analysis.setFromDate(fromDate);
        analysis.setToDate(toDate);
        
        // Calculate social impact revenue
        BigDecimal socialImpactRevenue = calculateSocialImpactRevenue(fromDate, toDate);
        analysis.setSocialImpactRevenue(socialImpactRevenue);
        
        // Calculate climate enterprise impact
        BigDecimal climateEnterpriseIncome = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4260", fromDate, toDate);
        analysis.setClimateEnterpriseIncome(climateEnterpriseIncome);
        
        // Calculate social enterprise impact
        BigDecimal socialEnterpriseIncome = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4270", fromDate, toDate);
        analysis.setSocialEnterpriseIncome(socialEnterpriseIncome);
        
        // Calculate donation impact
        BigDecimal donationIncome = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4230", fromDate, toDate);
        analysis.setDonationIncome(donationIncome);
        
        // Calculate volunteer valuation
        BigDecimal volunteerValuation = journalEntryLineRepository
            .sumByAccountTypeAndDateRange("4280", fromDate, toDate);
        analysis.setVolunteerValuation(volunteerValuation);
        
        // Calculate total social impact
        BigDecimal totalSocialImpact = climateEnterpriseIncome.add(socialEnterpriseIncome)
                                                             .add(donationIncome)
                                                             .add(volunteerValuation);
        analysis.setTotalSocialImpact(totalSocialImpact);
        
        // Calculate social impact percentage of total revenue
        BigDecimal totalRevenue = calculateTotalRevenue(fromDate, toDate);
        BigDecimal socialImpactPercentage = totalSocialImpact.divide(totalRevenue, 4, RoundingMode.HALF_UP)
                                                           .multiply(new BigDecimal("100"));
        analysis.setSocialImpactPercentage(socialImpactPercentage);
        
        return analysis;
    }
}
```

## Enhanced Income Statement DTOs

### 1. Income Statement DTO
```java
public class IncomeStatementDto {
    private LocalDate fromDate;
    private LocalDate toDate;
    
    // Revenue Section
    private BigDecimal coreBusinessRevenue;
    private BigDecimal socialImpactRevenue;
    private BigDecimal financialRevenue;
    private BigDecimal totalRevenue;
    
    // Cost of Goods Sold
    private BigDecimal costOfGoodsSold;
    private BigDecimal grossProfit;
    
    // Operating Expenses
    private BigDecimal operatingExpenses;
    private BigDecimal operatingIncome;
    
    // Government Levies
    private BigDecimal governmentLevies;
    
    // Special Categories
    private BigDecimal specialCategories;
    
    // Final Totals
    private BigDecimal totalExpenses;
    private BigDecimal netIncome;
    
    // Analysis
    private BigDecimal profitMargin;
    private BigDecimal socialImpactPercentage;
    private GLSComplianceReport glsCompliance;
    private SocialImpactAnalysis socialImpactAnalysis;
}
```

### 2. GLS Compliance Report DTO
```java
public class GLSComplianceReport {
    private LocalDate fromDate;
    private LocalDate toDate;
    private Map<String, BigDecimal> glsByCategory;
    private BigDecimal totalGLS;
    private List<GLSComplianceItem> complianceItems;
    private double compliancePercentage;
}

public class GLSComplianceItem {
    private String category;
    private BigDecimal requiredAmount;
    private BigDecimal paidAmount;
    private BigDecimal outstandingAmount;
    private boolean isCompliant;
    private LocalDate dueDate;
    private boolean isOverdue;
}
```

### 3. Social Impact Analysis DTO
```java
public class SocialImpactAnalysis {
    private LocalDate fromDate;
    private LocalDate toDate;
    private BigDecimal socialImpactRevenue;
    private BigDecimal climateEnterpriseIncome;
    private BigDecimal socialEnterpriseIncome;
    private BigDecimal donationIncome;
    private BigDecimal volunteerValuation;
    private BigDecimal totalSocialImpact;
    private BigDecimal socialImpactPercentage;
    private List<SocialImpactCategory> impactCategories;
}

public class SocialImpactCategory {
    private String categoryName;
    private BigDecimal amount;
    private BigDecimal percentage;
    private String description;
    private List<String> impactMetrics;
}
```

This enhanced income statement structure provides a comprehensive framework for tracking and reporting the specific business model with detailed revenue streams, government compliance, and social impact analysis.
