# Filtering Domains 

---

Filtering a Domain allows you to define different traversals through it for common operations, like searching, or different views of the data.

## What is a Filter

A Filter is a pre-defined slice of your Domain. It's a way for you to communicate to others how they should traverse your domain. 

Depending on where your Domain is used, it's possible that Filters may become API or Web Service calls. Maybe they'll become canned reports in a Database. But no matter where they're used, they'll behave consistently because you described what data they should return and where they should start from.

## How to use the Filter Sidebar

1. Click the Filter button in the Toolbar
2. Use the Left and Right arrow buttons to scroll through the available Filters. In the lower right corner of the Sidebar you can see what number Filter you are on, and how many there are in total. These numbers have no meaning, and just make it easier to scroll.
3. In the lower left corner of the Sidebar, you can choose to highlight the Domain based on the current Filter. Highlighting will dim all Classes and connections that aren't part of the Filter. All of the connections between Classes in the Filter will change to a yellow/purple gradient. This indicates the direction of traversal, going from the parent side (yellow) to the child side (purple)

## Creating a new Filter
1. Click the Filter button in the Sidebar
2. If no Filters exist, click the 'Add a Filter' link at the top of the Sidebar
3. Otherwise, click the '+' button in the lower right corner of the Sidebar
4. Type the Name of the Filter. Good Filter names follow these patterns:

> [Action].[Object].[Intent] eg: Initiate.Payment.Request
>
> [EventName] eg: PurchaseRequested

## Writing the Filter

Filters are created using dot notation, starting at a Class and following the Property names till you finish.

Here's an example:

> Organisation.bankAccount.accountIdentification

```jargon
c:ANZIC
c:NameUsages
c:AccountTypes
---
Organisation:
	^abn:Numeric
	industryClassification:Code(ANZIC)
	name:OrganisationName[]
	bankAccount:BankAccount
    employees:Employee[]

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

Employee:
    name:Text
```

1. Choose a Class as the root of the Filter: which is 'Organisation' here. This is where the traversal will begin. Depending on how the Filter is used, this Filter may act on all instances of that Class, or just one after specifying it's Identity.
2. Select which Property of that class you want to traverse: the first one here is 'bankAccount'
3. Keep speficying Properties until you're done. In this example, because we specified 'bankAccount' that traversed to the 'BankAccount' Class. That Class has a Property 'accountIdentification', which is the last segment of this Filter.
4. You can have multiple lines of Filters, which all will all be included in the Filter: eg:

>
> Organisation.bankAccount.accountIdentifier
>
> Organisation.employees
>

5. The ValueObjects of each Class that is traversed will be included in the Filter 
6. If you have turned on Highlighting for the Filter, as you type the diagram will update.

!> The Filter Highlighting will only work when you have a valid Filter


## Deleting a Filter
1. Click the Filter button in the Sidebar
2. Scroll through the Filters usiung the left and right arrows.
3. Click the 'x' in the lower right corner of the Sidebar
