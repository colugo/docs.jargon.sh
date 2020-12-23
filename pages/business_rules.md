# Business Rules

!> Business Rules aren't ready yet, but here is a taste of what we're thinking:


> Only Entities and Aggregates can be the targets of Rules, because they have business identifiers. ValueOjects, which don't, can only be accessed as part of the Aggregate / Entity


**Hours per week are between 0 and 40**
```
Employee
@.conditions.contractedHoursPerWeek BETWEEN {0} AND {40}
```


**All payroll runs must end after starting**

```
PayrollRun
@.end {1} {DAY} AFTER @.start
```

**Or for a PayrollRun from a Organisation with an IndustryCode between 1000 and 2000, payroll runs are monthly**

```
Organisation[@.industryClassification BETWEEN {1000} AND {2000}].payrollRun
@.end {1} {MONTH} AFTER @.start
```

**Payslip pay dates must fall within the payroll run date range**

```
PayrollRun.payslip
@.date BEWTEEN {../.start} AND {../.end}
```

**Termination payslips must be sent after the termination date of the employee**

```
Employee[WITH @.terminationText].payslip
../terminationText BETWEEN {@.start} AND {@.end}
```

**Termination payslips must be sent after the termination date of the employee, only if they're a 'JNR'**

```
Employee[WITH @.terminationText AND @.personDetails.name[@.nameSuffix IS 'JNR']].payslip
@.terminationPayment TRUE
```

```jargon
c:ANZIC
c:NameUsages
c:AccountTypes
---
Organisation:
	^abn:Numeric
	industryClassification:Code(ANZIC)
	name:OrganisationName[]
	payrollRun:PayrollRun[]
	bankAccount:BankAccount
	employee:Employee[]

OrganisationName:
	name:Text
	type:Code(NameUsages)

BankAccount:
	name:Text
	type:Code(AccountTypes)
	accountIdentification:AccountIdentification

AccountIdentification:
	^iban:Numeric
	^bban:Numeric
	^bsb:Numeric
	^accountNumber:Numeric

PayrollRun:
	endDate:Text
	startDate:Text
	^posted:Text
	payslip:Payslip[]

Employee:
	^id:Numeric
	employmentStartText:Text
	personDetails:Person
	^tfn:Numeric
	terminationText:Text
	terminationReason:Text
	conditions:EmploymentConditions
	activityDetail:WorkActivityDetail[]
	taxationPlan:TaxationPlan
	wage:WagePlan[]
	allowance:AllowancePlan[]
	super:SuperannuationPlan[]
	deduction:DeductionPlan[]
	leaveEntitlement:LeaveEntitlement[]
	payslip:Payslip[]

Payslip:
	expenseReimbursement:Numeric
	gross:Numeric
	net:Numeric
	^date:Text
	paymentMethod:Code
	terminationPayment:Indicator
	ytdGross:Numeric
	ytdNet:Numeric
	wage:WageItem[]
	allowance:AllowanceItem[]
	super:SuperannuationItem[]
	deduction:DeductionItem[]
	leave:LeaveItem[]
	tax:TaxationItem[]
```


---

