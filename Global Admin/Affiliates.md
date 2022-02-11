# Affiliates

## How to add a record to a table

1. Click Add Affiliates
2. Fill in all required fields
3. Click Confirm

## How to use Affiliates

Launch your browser.
1. Type https://go.rallyup (QA or Staging).com /start?affl=code where the Code you created when adding Affiliates
2. This opens the start page
3. Register a new user
4. Add an Organization to it.
5. Create Campaign
6. Donate to this campaign
7. Ending the campaign 
The Earned value should change in the table.

You specify the percentage of Earned when you create Affiliates.
The collected Tips and Service Fees are added up and multiplied by that percentage.

#10126 is a document that explains the mathematical interaction in more detail. 

## By Column.

ID - Contains Affiliates ID, which is assigned when you add Affiliates to the table

First Name/Last Name - Contains information about the user that the Affiliates were created for

Email - Contains information about Email to which Affiliates were created

Company Name - Contains information about the company name you specified when adding Affiliates to the table.

Date created - Contains information about the date Affiliates were added to the table

Code - Contains the code you specify when adding Affiliates to the table

Rate - Percentage specified when adding Affiliates to the table.

Earned - the total amount that the affiliate has earned from their affiliate-referred users

Paid - the amount that SysAdmin has paid the affiliate (SysAdmin can "pay" affiliates via a "Pay Affiliate" manage menu option, described later)

Owed - this should always be equal to the Earned amount minus the Paid amount, and is shown on this table so that SysAdmin can sort by affiliates that we owe payments to

## Manage Button

Edit Affiliate - This will open the "Edit Affiliate" modal (the same as the Add Affiliate modal), but only the commission fields will be editable

Pay Affiliate - This will open the "Pay Affiliate" modal.
The amount that SysAdmin "pays" in this modal will add to the amount shown in the "Paid" column for the affiliate
After clicking "Pay" in this modal, the modal should have a second "confirmation" state to confirm the SysAdmin's actions

View Campaigns - When this is clicked, we'll open Administration -> Campaigns in a new tab with a special filtering:

Recalculate Earned - Starts a recalculation if old donations are Refunded. Statistics are automatically recalculated for the current month only. Also, recalculation is triggered if Affiliates have changed their characteristics.

## Button Export

If you click on it the export file will be loaded.

