# Enhanced Spring Boot APIs - Business-Specific Implementation

## Overview
This document provides enhanced Spring Boot API designs specifically tailored for the business model with detailed cash payment categories, cash receipts, and specialized journal types.

## Enhanced API Structure

### 1. Cash Payment APIs

#### Cash Payment Controller
```java
@RestController
@RequestMapping("/api/v1/cash-payments")
public class CashPaymentController {
    
    @GetMapping
    public ResponseEntity<Page<CashPaymentDto>> getCashPayments(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size,
            @RequestParam(required = false) PaymentCategory category,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate,
            @RequestParam(required = false) String search) {
        // Get paginated cash payments with filtering
    }
    
    @PostMapping
    public ResponseEntity<CashPaymentDto> createCashPayment(@RequestBody CreateCashPaymentRequest request) {
        // Create new cash payment
        // Automatically create journal entry
        // Validate GLS requirements
    }
    
    @GetMapping("/categories")
    public ResponseEntity<List<PaymentCategoryDto>> getPaymentCategories() {
        // Get all payment categories with GLS information
    }
    
    @GetMapping("/gls-summary")
    public ResponseEntity<GLSSummaryDto> getGLSSummary(
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get GLS summary for government compliance
    }
}
```

#### Payment Category Service
```java
@Service
public class PaymentCategoryService {
    
    public List<PaymentCategoryDto> getAllPaymentCategories() {
        return Arrays.asList(
            new PaymentCategoryDto("PURCHASES", "Purchases", null, "Cost of Goods Sold"),
            new PaymentCategoryDto("DELIVERY_COSTS", "Delivery costs", null, "Operating Expense"),
            new PaymentCategoryDto("EXTENSION_SERVICE", "Extension Service costs", null, "Operating Expense"),
            new PaymentCategoryDto("DIRECT_SALARIES", "Direct Salaries/wages", null, "Operating Expense"),
            new PaymentCategoryDto("PAYROLL_TAXES", "Payroll Taxes and Benefits-Direct", null, "Operating Expense"),
            new PaymentCategoryDto("STAFF_MEALS", "Staff meals", null, "Operating Expense"),
            new PaymentCategoryDto("COMPUTER_INTERNET", "Computer Internet", null, "Operating Expense"),
            new PaymentCategoryDto("BANK_PAYMENT_CHARGES", "Bank/mpesa Payment Charges", null, "Operating Expense"),
            new PaymentCategoryDto("BANK_COLLECTION_CHARGES", "Bank/Mpesa Collection Charges", null, "Operating Expense"),
            new PaymentCategoryDto("OFFICE_SUPPLIES", "Office supplies (Stationery)", null, "Operating Expense"),
            new PaymentCategoryDto("HIRE_EQUIPMENT", "Hire of equipment", null, "Operating Expense"),
            new PaymentCategoryDto("SECURITY_EXPENSES", "Security Expenses", null, "Operating Expense"),
            new PaymentCategoryDto("DEPRECIATION_DIRECT", "Depreciation-Direct", null, "Operating Expense"),
            new PaymentCategoryDto("PRINTING_PHOTOCOPYING", "Printing, photocopying", null, "Operating Expense"),
            new PaymentCategoryDto("TELEPHONE", "Telephone", null, "Operating Expense"),
            new PaymentCategoryDto("CREDITORS", "Creditors", null, "Liability Reduction"),
            new PaymentCategoryDto("TRAVEL_ACCOM", "Travel & Accom", null, "Operating Expense"),
            new PaymentCategoryDto("BUSINESS_REGISTRATION", "Business Registration", null, "Operating Expense"),
            new PaymentCategoryDto("MAINTENANCE", "Maintenance", null, "Operating Expense"),
            new PaymentCategoryDto("CLEANING_MATERIALS", "Cleaning materials", null, "Operating Expense"),
            new PaymentCategoryDto("PACKAGING_MATERIALS", "Packaging Materials", null, "Cost of Goods Sold"),
            new PaymentCategoryDto("RECRUITMENT_MEETING", "Recruitment, meeting & Conferencing", null, "Operating Expense"),
            new PaymentCategoryDto("LAAS", "Loyalty-as-a-Service (LaaS)", 15.0, "Tax Expense"),
            new PaymentCategoryDto("WITHHOLDING_TAX", "Withholding tax", 5.0, "Tax Expense"),
            new PaymentCategoryDto("TRADING_LICENSE", "Trading License", 1.0, "Tax Expense"),
            new PaymentCategoryDto("INPL_INTEREST", "INPL Interest", 1.0, "Interest Expense"),
            new PaymentCategoryDto("TELLER_OPERATIONS", "Teller Operations", 10.0, "Operating Expense"),
            new PaymentCategoryDto("IT_ENABLED_SERVICES", "IT Enabled Services", 1.0, "Operating Expense"),
            new PaymentCategoryDto("CURRICULA_DEVELOPMENT", "Curricula Development", 1.0, "Operating Expense"),
            new PaymentCategoryDto("DATA_SCIENCE", "Data-Science", 1.0, "Operating Expense"),
            new PaymentCategoryDto("SOCIO_ENTERPRISE", "Socio-enterprise Development", 1.0, "Operating Expense"),
            new PaymentCategoryDto("AGROMONY_SERVICES", "Agronomy Services", 1.0, "Operating Expense"),
            new PaymentCategoryDto("CLIMATE_SCIENCE", "Climate-Science", 1.0, "Operating Expense"),
            new PaymentCategoryDto("RENT_UTILITIES", "Rent + Utilities", 5.0, "Operating Expense"),
            new PaymentCategoryDto("MARKET_ACTIVATIONS", "Market Activations", 5.0, "Operating Expense"),
            new PaymentCategoryDto("SMART_EXTENSION", "Smart Extension Services", 5.0, "Operating Expense"),
            new PaymentCategoryDto("CLIMATE_ENTERPRISES", "Climate-Enterprises", 25.0, "Operating Expense"),
            new PaymentCategoryDto("HOSPITAL_INSURANCE", "Hospital Insurance", 15.0, "Operating Expense"),
            new PaymentCategoryDto("SOCIAL_ENTERPRISES", "Social Enterprises", 7.0, "Operating Expense"),
            new PaymentCategoryDto("INPL_REPAYMENTS", "INPL Smart Advances Repayments", null, "Interest Expense"),
            new PaymentCategoryDto("REWARDS", "Rewards", null, "Operating Expense")
        );
    }
}
```

### 2. Cash Receipt APIs

#### Cash Receipt Controller
```java
@RestController
@RequestMapping("/api/v1/cash-receipts")
public class CashReceiptController {
    
    @GetMapping
    public ResponseEntity<Page<CashReceiptDto>> getCashReceipts(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size,
            @RequestParam(required = false) ReceiptCategory category,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get paginated cash receipts with filtering
    }
    
    @PostMapping
    public ResponseEntity<CashReceiptDto> createCashReceipt(@RequestBody CreateCashReceiptRequest request) {
        // Create new cash receipt
        // Automatically create journal entry
        // Update cash account balance
    }
    
    @GetMapping("/categories")
    public ResponseEntity<List<ReceiptCategoryDto>> getReceiptCategories() {
        // Get all receipt categories
    }
    
    @GetMapping("/social-impact-summary")
    public ResponseEntity<SocialImpactSummaryDto> getSocialImpactSummary(
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get social impact revenue summary
    }
}
```

#### Receipt Category Service
```java
@Service
public class ReceiptCategoryService {
    
    public List<ReceiptCategoryDto> getAllReceiptCategories() {
        return Arrays.asList(
            new ReceiptCategoryDto("DEBTORS", "Debtors", "Asset Reduction"),
            new ReceiptCategoryDto("MEMBERSHIP_FEES", "Member-ship Fees", "Revenue"),
            new ReceiptCategoryDto("SALES", "Sales", "Revenue"),
            new ReceiptCategoryDto("SMART_EXTENSION_SERVICE", "Smart Extension Service", "Revenue"),
            new ReceiptCategoryDto("INVESTOR_FUNDS", "Investor funds", "Equity"),
            new ReceiptCategoryDto("KITCHEN_SALVAGES", "Kitchen salvages", "Other Income"),
            new ReceiptCategoryDto("HIRE_EQUIPMENT", "Hire of equipment", "Other Income"),
            new ReceiptCategoryDto("OVERDRAFTS", "Over-drafts", "Liability"),
            new ReceiptCategoryDto("CASH_ADVANCES", "Cash advances", "Liability"),
            new ReceiptCategoryDto("ADVANCE_PAYMENTS", "Advance Payments", "Liability"),
            new ReceiptCategoryDto("WIFI_CHARGES", "Wifi charges", "Revenue"),
            new ReceiptCategoryDto("DONATIONS", "Donations", "Other Income"),
            new ReceiptCategoryDto("CLIMATE_ENTERPRISE", "Climate Enterprise Income", "Revenue"),
            new ReceiptCategoryDto("SOCIAL_ENTERPRISE", "Social Enterprise Income", "Revenue"),
            new ReceiptCategoryDto("CLIMATE_IMPACT_BOND", "Climate Impact Bond Coupon Rate", "Interest Income"),
            new ReceiptCategoryDto("FUNDRAISERS", "Fund-raisers", "Other Income"),
            new ReceiptCategoryDto("JOINT_VENTURE", "Joint-venture Income", "Revenue"),
            new ReceiptCategoryDto("ENDOWMENT", "Endowment Building", "Equity"),
            new ReceiptCategoryDto("VOLUNTEER_VALUATION", "Volunteer Valuation Time", "Other Income"),
            new ReceiptCategoryDto("OTHERS", "Others Revenues", "Other Income")
        );
    }
}
```

### 3. Cost of Sales APIs

#### Cost of Sales Controller
```java
@RestController
@RequestMapping("/api/v1/cost-of-sales")
public class CostOfSalesController {
    
    @GetMapping("/products/{productId}")
    public ResponseEntity<CostOfSalesDto> getProductCostOfSales(
            @PathVariable Long productId,
            @RequestParam(required = false) Integer quantity) {
        // Get cost of sales for specific product
    }
    
    @PostMapping("/calculate")
    public ResponseEntity<CostOfSalesCalculationDto> calculateCostOfSales(
            @RequestBody CalculateCostOfSalesRequest request) {
        // Calculate cost of sales for product/service
    }
    
    @GetMapping("/profit-margins")
    public ResponseEntity<List<ProductProfitMarginDto>> getProductProfitMargins(
            @RequestParam(required = false) BigDecimal minMargin,
            @RequestParam(required = false) BigDecimal maxMargin) {
        // Get profit margins for all products
    }
    
    @PostMapping("/update-costs")
    public ResponseEntity<Void> updateProductCosts(@RequestBody UpdateProductCostsRequest request) {
        // Update raw material, labor, or overhead costs
    }
}
```

#### Cost of Sales Service
```java
@Service
public class CostOfSalesService {
    
    public CostOfSalesCalculationDto calculateProductCost(Long productId, Integer quantity) {
        // Get product details
        Product product = productRepository.findById(productId);
        
        // Calculate raw material costs
        BigDecimal rawMaterialCost = calculateRawMaterialCost(productId, quantity);
        
        // Calculate direct labor costs
        BigDecimal laborCost = calculateDirectLaborCost(productId, quantity);
        
        // Calculate overhead allocation
        BigDecimal overheadCost = calculateOverheadAllocation(productId, quantity);
        
        // Calculate total cost
        BigDecimal totalCost = rawMaterialCost.add(laborCost).add(overheadCost);
        
        // Calculate profit margin
        BigDecimal sellingPrice = product.getPrice();
        BigDecimal profitMargin = sellingPrice.subtract(totalCost);
        BigDecimal marginPercentage = profitMargin.divide(sellingPrice, 4, RoundingMode.HALF_UP)
                                                 .multiply(new BigDecimal("100"));
        
        return new CostOfSalesCalculationDto(
            productId, product.getName(), quantity, rawMaterialCost, 
            laborCost, overheadCost, totalCost, sellingPrice, 
            profitMargin, marginPercentage
        );
    }
    
    private BigDecimal calculateRawMaterialCost(Long productId, Integer quantity) {
        // Get recipe/ingredients for product
        List<ProductIngredient> ingredients = productIngredientRepository.findByProductId(productId);
        
        BigDecimal totalCost = BigDecimal.ZERO;
        for (ProductIngredient ingredient : ingredients) {
            BigDecimal ingredientCost = ingredient.getCostPerUnit()
                .multiply(ingredient.getQuantity())
                .multiply(new BigDecimal(quantity));
            totalCost = totalCost.add(ingredientCost);
        }
        
        return totalCost;
    }
    
    private BigDecimal calculateDirectLaborCost(Long productId, Integer quantity) {
        // Get labor time required for product
        BigDecimal laborTime = productLaborRepository.findByProductId(productId).getLaborTime();
        
        // Get hourly labor rate
        BigDecimal hourlyRate = laborRateRepository.findCurrentRate();
        
        return laborTime.multiply(hourlyRate).multiply(new BigDecimal(quantity));
    }
    
    private BigDecimal calculateOverheadAllocation(Long productId, Integer quantity) {
        // Get overhead allocation rate
        BigDecimal overheadRate = overheadAllocationRepository.findCurrentRate();
        
        // Get direct costs for allocation base
        BigDecimal directCosts = calculateRawMaterialCost(productId, quantity)
            .add(calculateDirectLaborCost(productId, quantity));
        
        return directCosts.multiply(overheadRate);
    }
}
```

### 4. Sales Journal APIs

#### Sales Journal Controller
```java
@RestController
@RequestMapping("/api/v1/sales-journal")
public class SalesJournalController {
    
    @GetMapping
    public ResponseEntity<Page<SalesJournalDto>> getSalesJournal(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get sales journal entries
    }
    
    @GetMapping("/profit-analysis")
    public ResponseEntity<SalesProfitAnalysisDto> getSalesProfitAnalysis(
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get profit analysis for sales period
    }
    
    @GetMapping("/products/{productId}/profit-history")
    public ResponseEntity<List<ProductProfitHistoryDto>> getProductProfitHistory(
            @PathVariable Long productId,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get profit history for specific product
    }
    
    @PostMapping("/recalculate-profits")
    public ResponseEntity<Void> recalculateProfits(@RequestBody RecalculateProfitsRequest request) {
        // Recalculate profits for sales period
    }
}
```

### 5. Purchase Journal APIs

#### Purchase Journal Controller
```java
@RestController
@RequestMapping("/api/v1/purchase-journal")
public class PurchaseJournalController {
    
    @GetMapping
    public ResponseEntity<Page<PurchaseJournalDto>> getPurchaseJournal(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size,
            @RequestParam(required = false) Long supplierId,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get purchase journal entries
    }
    
    @GetMapping("/suppliers/{supplierId}/pricing-analysis")
    public ResponseEntity<SupplierPricingAnalysisDto> getSupplierPricingAnalysis(
            @PathVariable Long supplierId,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get pricing analysis for supplier
    }
    
    @GetMapping("/wholesale-vs-retail")
    public ResponseEntity<WholesaleRetailAnalysisDto> getWholesaleRetailAnalysis(
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get wholesale vs retail pricing analysis
    }
    
    @PostMapping("/update-pricing")
    public ResponseEntity<Void> updatePricing(@RequestBody UpdatePricingRequest request) {
        // Update wholesale/retail pricing
    }
}
```

### 6. Bank Deposits APIs

#### Bank Deposits Controller
```java
@RestController
@RequestMapping("/api/v1/bank-deposits")
public class BankDepositsController {
    
    @GetMapping
    public ResponseEntity<Page<BankDepositDto>> getBankDeposits(
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size,
            @RequestParam(required = false) DepositType depositType,
            @RequestParam(required = false) DepositStatus status,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam(required = false) @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get bank deposits with filtering
    }
    
    @PostMapping
    public ResponseEntity<BankDepositDto> createBankDeposit(@RequestBody CreateBankDepositRequest request) {
        // Create new bank deposit
        // Automatically create journal entry
        // Update bank account balance
    }
    
    @GetMapping("/summary")
    public ResponseEntity<BankDepositSummaryDto> getBankDepositSummary(
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate fromDate,
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate toDate) {
        // Get bank deposit summary by type
    }
    
    @GetMapping("/reconciliation")
    public ResponseEntity<BankReconciliationDto> getBankReconciliation(
            @RequestParam @DateTimeFormat(iso = DateTimeFormat.ISO.DATE) LocalDate asOfDate) {
        // Get bank reconciliation report
    }
}
```

## Enhanced Data Transfer Objects

### 1. Cash Payment DTOs
```java
public class CashPaymentDto {
    private Long id;
    private String paymentReference;
    private PaymentCategory category;
    private String description;
    private BigDecimal amount;
    private BigDecimal glsAmount;
    private BigDecimal glsPercentage;
    private LocalDate paymentDate;
    private String accountCode;
    private String accountName;
    private String createdBy;
    private LocalDateTime createdAt;
}

public class GLSSummaryDto {
    private BigDecimal totalGLSPayments;
    private Map<String, BigDecimal> glsByCategory;
    private Map<String, BigDecimal> glsByPercentage;
    private List<GLSComplianceDto> complianceStatus;
}

public class GLSComplianceDto {
    private String category;
    private BigDecimal requiredAmount;
    private BigDecimal paidAmount;
    private BigDecimal outstandingAmount;
    private LocalDate dueDate;
    private boolean isOverdue;
}
```

### 2. Cash Receipt DTOs
```java
public class CashReceiptDto {
    private Long id;
    private String receiptReference;
    private ReceiptCategory category;
    private String description;
    private BigDecimal amount;
    private LocalDate receiptDate;
    private String accountCode;
    private String accountName;
    private String sourceReference;
    private String createdBy;
    private LocalDateTime createdAt;
}

public class SocialImpactSummaryDto {
    private BigDecimal totalSocialImpactRevenue;
    private BigDecimal climateEnterpriseIncome;
    private BigDecimal socialEnterpriseIncome;
    private BigDecimal donationIncome;
    private BigDecimal volunteerValuationIncome;
    private BigDecimal fundraisingIncome;
    private Map<String, BigDecimal> revenueByCategory;
}
```

### 3. Cost of Sales DTOs
```java
public class CostOfSalesCalculationDto {
    private Long productId;
    private String productName;
    private Integer quantity;
    private BigDecimal rawMaterialCost;
    private BigDecimal laborCost;
    private BigDecimal overheadCost;
    private BigDecimal totalCost;
    private BigDecimal sellingPrice;
    private BigDecimal profitMargin;
    private BigDecimal marginPercentage;
    private List<CostComponentDto> costComponents;
}

public class ProductProfitMarginDto {
    private Long productId;
    private String productName;
    private BigDecimal currentMargin;
    private BigDecimal averageMargin;
    private BigDecimal minMargin;
    private BigDecimal maxMargin;
    private Integer salesCount;
    private BigDecimal totalRevenue;
    private BigDecimal totalCost;
}
```

### 4. Sales Journal DTOs
```java
public class SalesJournalDto {
    private Long id;
    private String saleReference;
    private LocalDate saleDate;
    private String customerName;
    private List<SalesJournalLineDto> lines;
    private BigDecimal totalRevenue;
    private BigDecimal totalCost;
    private BigDecimal grossProfit;
    private BigDecimal profitMargin;
}

public class SalesJournalLineDto {
    private Long productId;
    private String productName;
    private Integer quantity;
    private BigDecimal unitPrice;
    private BigDecimal totalPrice;
    private BigDecimal unitCost;
    private BigDecimal totalCost;
    private BigDecimal profit;
    private BigDecimal margin;
}

public class SalesProfitAnalysisDto {
    private BigDecimal totalRevenue;
    private BigDecimal totalCost;
    private BigDecimal grossProfit;
    private BigDecimal profitMargin;
    private List<ProductProfitAnalysisDto> productAnalysis;
    private List<CategoryProfitAnalysisDto> categoryAnalysis;
}
```

### 5. Purchase Journal DTOs
```java
public class PurchaseJournalDto {
    private Long id;
    private String purchaseReference;
    private LocalDate purchaseDate;
    private String supplierName;
    private List<PurchaseJournalLineDto> lines;
    private BigDecimal totalPurchaseCost;
    private BigDecimal totalWholesaleValue;
    private BigDecimal totalRetailValue;
    private BigDecimal totalMarkup;
}

public class PurchaseJournalLineDto {
    private Long productId;
    private String productName;
    private Integer quantity;
    private BigDecimal purchasePrice;
    private BigDecimal wholesalePrice;
    private BigDecimal retailPrice;
    private BigDecimal wholesaleMarkup;
    private BigDecimal retailMarkup;
    private BigDecimal totalPurchaseCost;
    private BigDecimal totalWholesaleValue;
    private BigDecimal totalRetailValue;
}

public class SupplierPricingAnalysisDto {
    private Long supplierId;
    private String supplierName;
    private BigDecimal totalPurchaseAmount;
    private BigDecimal averageMarkup;
    private BigDecimal minMarkup;
    private BigDecimal maxMarkup;
    private Integer purchaseCount;
    private List<ProductPricingDto> productPricing;
}
```

### 6. Bank Deposits DTOs
```java
public class BankDepositDto {
    private Long id;
    private String depositReference;
    private LocalDate depositDate;
    private BigDecimal depositAmount;
    private DepositType depositType;
    private String sourceReference;
    private String bankAccount;
    private DepositStatus status;
    private String description;
    private String createdBy;
    private LocalDateTime createdAt;
}

public class BankDepositSummaryDto {
    private BigDecimal totalDeposits;
    private Map<DepositType, BigDecimal> depositsByType;
    private Map<DepositStatus, BigDecimal> depositsByStatus;
    private List<BankDepositTrendDto> dailyTrends;
}

public class BankReconciliationDto {
    private LocalDate reconciliationDate;
    private BigDecimal bookBalance;
    private BigDecimal bankBalance;
    private BigDecimal difference;
    private List<ReconciliationItemDto> outstandingItems;
    private boolean isReconciled;
}
```

## Business Rules and Validation

### 1. GLS Validation Service
```java
@Service
public class GLSValidationService {
    
    public void validateGLSPayment(CreateCashPaymentRequest request) {
        PaymentCategory category = request.getCategory();
        
        if (category.getGlsPercentage() != null) {
            BigDecimal expectedGLS = request.getAmount()
                .multiply(category.getGlsPercentage())
                .divide(new BigDecimal("100"));
            
            if (request.getGlsAmount() == null || 
                !request.getGlsAmount().equals(expectedGLS)) {
                throw new GLSValidationException(
                    "GLS amount must be " + expectedGLS + " for " + category.getName()
                );
            }
        }
    }
    
    public GLSSummaryDto generateGLSSummary(LocalDate fromDate, LocalDate toDate) {
        List<CashPayment> glsPayments = cashPaymentRepository
            .findByCategoryGlsPercentageNotNullAndPaymentDateBetween(fromDate, toDate);
        
        Map<String, BigDecimal> glsByCategory = glsPayments.stream()
            .collect(Collectors.groupingBy(
                payment -> payment.getCategory().getName(),
                Collectors.reducing(BigDecimal.ZERO, CashPayment::getAmount, BigDecimal::add)
            ));
        
        return new GLSSummaryDto(glsByCategory);
    }
}
```

### 2. Cost of Sales Validation
```java
@Service
public class CostOfSalesValidationService {
    
    public void validateCostOfSales(CostOfSalesCalculationDto calculation) {
        // Validate minimum profit margin
        if (calculation.getMarginPercentage().compareTo(new BigDecimal("10")) < 0) {
            throw new LowProfitMarginException(
                "Profit margin " + calculation.getMarginPercentage() + 
                "% is below minimum threshold of 10%"
            );
        }
        
        // Validate cost components
        if (calculation.getRawMaterialCost().compareTo(BigDecimal.ZERO) <= 0) {
            throw new InvalidCostException("Raw material cost must be positive");
        }
        
        if (calculation.getLaborCost().compareTo(BigDecimal.ZERO) <= 0) {
            throw new InvalidCostException("Labor cost must be positive");
        }
        
        if (calculation.getOverheadCost().compareTo(BigDecimal.ZERO) < 0) {
            throw new InvalidCostException("Overhead cost cannot be negative");
        }
    }
}
```

### 3. Bank Deposit Validation
```java
@Service
public class BankDepositValidationService {
    
    public void validateBankDeposit(CreateBankDepositRequest request) {
        // Validate deposit amount
        if (request.getDepositAmount().compareTo(BigDecimal.ZERO) <= 0) {
            throw new InvalidDepositAmountException("Deposit amount must be positive");
        }
        
        // Validate deposit type
        if (request.getDepositType() == null) {
            throw new InvalidDepositTypeException("Deposit type is required");
        }
        
        // Validate bank account
        if (request.getBankAccount() == null || request.getBankAccount().trim().isEmpty()) {
            throw new InvalidBankAccountException("Bank account is required");
        }
        
        // Validate source reference for certain deposit types
        if (requiresSourceReference(request.getDepositType()) && 
            (request.getSourceReference() == null || request.getSourceReference().trim().isEmpty())) {
            throw new MissingSourceReferenceException(
                "Source reference is required for " + request.getDepositType()
            );
        }
    }
    
    private boolean requiresSourceReference(DepositType depositType) {
        return Arrays.asList(
            DepositType.SALES_REVENUE,
            DepositType.MEMBERSHIP_FEES,
            DepositType.CLIMATE_ENTERPRISE,
            DepositType.SOCIAL_ENTERPRISE
        ).contains(depositType);
    }
}
```

This enhanced Spring Boot API design provides comprehensive support for the specific business model with detailed cash flow tracking, government compliance, social impact monitoring, and specialized journal management.
