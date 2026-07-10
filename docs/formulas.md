# Formula Notes

All formulas are simplified and intended for education and scenario exploration.

## Units

The model uses PHP billions internally.

```text
₱30.8 trillion = 30,800 PHP billions
```

## Corporate Tax Revenue

```text
Corporate Output = GDP × Corporate Output Share
Corporate Taxable Surplus = Corporate Output × Taxable Surplus Share
Corporate Tax Revenue = Corporate Taxable Surplus × Corporate Tax Rate × Compliance Rate
```

## Elite / Tycoon Tax Revenue

```text
Elite Tax Revenue = Elite Income × Elite Tax Rate × Elite Tax Exposure × Compliance Rate
```

## Private Capital Recycling

```text
Tycoon Equity = retained post-tax corporate/elite wealth
Private Investment = Tycoon Equity × Reinvestment Rate
Luxury Consumption = Tycoon Equity × Luxury Consumption Rate
Assets / Offshore = Tycoon Equity × Asset or Leakage Rate
Capital Tax Capture = Tycoon Equity × Capital Tax Capture Rate
```

## Middle-Class Income

```text
Middle Total Income = GDP × Middle Income Share + OFW Remittances × Middle OFW Share
Middle Income Tax = Middle Domestic Income × Middle Tax Rate × Compliance Rate
Middle VAT = Middle Spendable Income × VAT Rate × VAT Exposure × Collection Efficiency
Middle Net Income = Middle Total Income - Middle Income Tax - Middle VAT
```

## Working-Poor Income

```text
Poor Total Income = GDP × Working-Poor Income Share + OFW Remittances × Poor OFW Share
Poor VAT = Poor Income × VAT Rate × VAT Exposure × Collection Efficiency
Poor Net Income = Poor Total Income - Poor VAT
```

## Treasury Revenue

```text
Treasury Revenue =
Corporate Tax
+ Elite Income Tax
+ Middle Income Tax
+ Middle VAT
+ Poor VAT
+ Other Government Revenue
+ Capital Tax Capture
```

## Budget and Borrowing

```text
Borrowing = max(0, Target Budget - Treasury Revenue)
New Debt Stock = Previous Debt Stock + Borrowing
Debt / GDP = National Government Debt ÷ GDP
```

## Household Reality Indicators

### Rice

```text
Rice Price = Base Rice Price × (1 + VAT Rate × Rice VAT Pass-Through) × Price Stress
```

### Electricity

```text
Electric Bill = Base Electric Bill × (1 + VAT Rate × Power VAT Pass-Through) × Price Stress
```

### ER Wait Time

```text
ER Wait Time = Reference ER Wait Time × (Reference Social Share ÷ Current Social Share)
```

### Public School Class Size

```text
Class Size = Reference Class Size × (Reference Social Share ÷ Current Social Share)
```

### Estimated Aid

```text
Estimated Aid = Reference Aid × (Current Social Share ÷ Reference Social Share)
```

## Synthetic Inequality

The app approximates a Lorenz curve using simplified population groups:

```text
70% working poor
29% middle class
1% elite
```

Synthetic Gini concept:

```text
Synthetic Gini = Area between equality line and Lorenz curve ÷ Total area under equality line
```

This is not an official inequality statistic.
