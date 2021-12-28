 # Overview

## Cart

a. The Cart is logically the same in this new Checkout process and we haven’t made any significant changes to it. Users will add items to their Cart in the same way as they do now, and the items will display in the same way inside the cart (including the [image, title, and price](https://share.getcloudapp.com/12uAoj6W)). ^cdb0d8

b. [**See Cart Figma**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4418%3A252049)

c. With that said, there are a small number of minor changes:

 -  **New Component Name headings**:
     - To add better categorization to the cart between item types, we’ve added some headings to group items of the same type under specific headings for that component.
    - So for example, Event Tickets will display under the “Event” heading and Raffle Tickets will display under the “Raffle” heading.
    - There should be one heading for each of our [Components](https://share.getcloudapp.com/NQuwJ9eW).

### 16661 [#15775][IMPROVE] Cart component headings - Design
Created per discussion in TP-16403.

Figma: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4478%3A273036](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4478%3A273036)

-----

d. These headings should use the Component Terminology for that Component from here: [see screenshot](https://share.getcloudapp.com/5zuBAoye). So for example, “[Raffle]”, “[Event]”, and so on.

e. When the user clicks the “Checkout now” button, this should take the user to the new on-page Checkout slideout (described later). We’d like the transition between Cart and Checkout to be smooth (i.e., if a load time is required then we can show loading spinners on the button or elsewhere and the Checkout should have a slideout animation when it appears).

### 17152 [#15775][IMPROVE] Cart markup updates

This task is created from comments in [#17038 [Staging][#15775] Cart markup issues](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=bug/17038&appConfig=eyJhY2lkIjoiIn0= "Bug #17038 [Staging][#15775] Cart markup issues") 

Here are new Figmas that show final design and positioning of elements for the Cart: [https://www.figma.com/file/oQTWwGI0fFsRAP2x8Uq5Dq/RU-Design-System-v1.0?node-id=290%3A912](https://www.figma.com/file/oQTWwGI0fFsRAP2x8Uq5Dq/RU-Design-System-v1.0?node-id=290%3A912)

Branding: [https://share.getcloudapp.com/04u5eBLR](https://share.getcloudapp.com/04u5eBLR)

Let us know if you have any questions about this design or its implementation. Thanks!

---

### 16636 [#15775][IMPROVE] Change cart button text

The two buttons in the cart have been changed to "Checkout now" and "Checkout later". 

This change is reflected in the Balsamiq: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

If cart is empty, we currently have one button which just closes the cart: [https://share.getcloudapp.com/o0uPJdyR](https://share.getcloudapp.com/o0uPJdyR)

When cart is empty, this button should read:

-   Close cart

---

## New On-Page Checkout

a. The new Checkout process will be very similar to how it is now in the current Checkout. The main changes will be to the design, and the fact that it’s displayed as a slideout from the right side of the page (instead of a separate Checkout page like we have currently.

b. See below for new Checkout design and Balsamiq:

- [**New Checkout Balsamiq**](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)
- [**New Checkout Design Figma**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120711)

c. You’ll notice in the Figma/Balsamiq how within each Timeline section, we have organized the “cards” into these [collapsible tabs](https://share.getcloudapp.com/RBuYrJvp). The intent of these collapsible sections is to improve donor UX and navigation by categorizing the cards into more manageable “chunks” and reducing length and scrolling of this Checkout Slideout.

- I will explain the logic for these Collapsible Tabs in more detail later in this point. 

d. [**New Input Fields**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120707)**:** We’ve created a new modern input field design where the placeholder text animates out of the way once the user focuses their cursor into it. You can see this in action in this prototype here: [view prototype](https://www.figma.com/proto/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?page-id=1132%3A114097&node-id=1226%3A141304&viewport=-4137%2C-5791%2C0.4917929768562317&scaling=min-zoom&starting-point-node-id=1226%3A141304).

 - [**See Design System with All States**](https://www.figma.com/file/oQTWwGI0fFsRAP2x8Uq5Dq/VE-Design-System-v1.0?node-id=580%3A16008)

 - We aren’t sure how difficult this would be to implement globally on this new Checkout/Experience Page. Let us know your thoughts on this and if you see any issues with this. If needed, we can delay this point to a Phase2.

e. Several elements have received updated designs. All of these panels are labeled and marked in the Figma files above, but I’ll create a list here so you have them:

- [New “Forgot password” message](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A123737)
- [Logged-in user state](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A123737)
- [New tooltips](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A149804)
- [Donation Credit radio buttons](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120731)
- [Tip/Bonus Entry Card](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A131573) (see bottom of section)
- [Payment Method buttons and Stripe Card Fields](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A132410)
- [Card Info – Saved State](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120687)

f. [Flat Donation Pop-Up](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A160663): similar to how we’ve moved A-Thon pledging out of the Checkout process and into a pop-up where people add pledges to their cart, we’re also doing the same for Flat Donations. This allows us to not need a [separate “Donation” section](https://share.getcloudapp.com/jkuLP5Zq) in Checkout like we have now.

- The design for this pop-up can be found in the Experience Page Figma mockup, here: [**Flat Donation Pop-Up Figma Design**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A160663).
- We’ve moved all of that existing functionality to this new Flat Donation Pop-Up.
    - [See Flat Donation Pop-Up Balsamiq](https://balsamiq.cloud/su8ul/pdrj7d2/r2278)
- This pop-up should replace all uses of the existing “Donation” section in Checkout. We believe this only includes Crowdfunding w/o Perks campaigns, and also all instances of this [“Donate Without Buying Items” button](https://share.getcloudapp.com/Z4uoKgyY).

- When users click “ADD TO CART”, their flat donation will be added to their cart (similar to how flat donations for A-Thons are).

- In the cart, these flat donation should show like this:

    - For non-recurring: Show title as “Flat [Donation]”, and amount as the donation amount

    - For recurring: Show title as “Recurring [Donation]” and amount as “$XX per-[week/month/quarter/year]”

g. The new Checkout is comprised of these possible sections:

 i. **Your Information**: this section contains exactly the same cards and fields as our current Your Information section, so the logic for when we show fields and how they work (like the Auction Bid Lookup cards) should work exactly the same as they do now. ^e74d3e

- The only **new card** in this section is that we’ve also moved our [existing “Select Members/Teams” step](https://share.getcloudapp.com/yAuDDZq6) to Your Information as well, so we no longer have a need for a separate step for that: [see screenshot](https://share.getcloudapp.com/llu55nLz).

 ii. [**Event Tickets**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120763)**:** This section is similar to our existing Event Tickets section in Checkout. It comes _after_ Your Information and only shows in Checkout if their Transaction contains Event Tickets (same logic we have currently).

- This section has the same collapsible tab logic that we described below in point g.

 ~~iii.~~ [**Bids**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120759): this section allows the user to review/enter their bid amount if their Transaction contains bids. ~~Since users already enter their Bid amounts on the Campaign Page when they add them to their cart, that means we only want this section to only show in Checkout when necessary. We already implemented logic for this in~~ [~~#14591~~](https://rallyup.tpondemand.com/entity/14591-12486improve-changes-to-behavior-of-bids) ~~that we want to retain and carry over to this new Checkout.~~

- ~~Note: I think per #14591, we always show the Bids section in Checkout for Proxy Bids still. If there is a clean way to not show the Bids section initially even for Proxy Bids (just like we do for English Auctions), that would be great. Let us know.~~

### 16841 [#15775][IMPROVE] Migrate "Update Bid" workflow to use new Checkout Slideout

See comments in [#15775 On-Page Checkout](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=userstory/15775&appConfig=eyJhY2lkIjoiIn0= "User Story #15775 On-Page Checkout"): [https://share.getcloudapp.com/nOuv7yz2](https://share.getcloudapp.com/nOuv7yz2)

This task would be to update our "Update Bid" workflow to use the new Checkout design and slide out. 

The workflow for updating a bid using the new Checkout would be very similar to the current one, except it just uses the new Checkout slide out and design. The steps for the user would be: 

1.  User clicks on any link that takes them to the Update Bid workflow (e.g., clicking link in "Outbid" email or SMS)
2.  User is taken to Experience Page and is asked to login via Login Page (if necessary)
3.  Checkout Slideout opens right to "Bids" section and shows the related Auction Item (Bid): [https://share.getcloudapp.com/geuA7mBN](https://share.getcloudapp.com/geuA7mBN)
4.  User enters their bid amount 
5.  User proceeds to Review & Pay section and submits

----

### 16915 [#15775][IMPROVE] Update markup on Your Information section to new Figmas
See comments in [#16780 [#15775][IMPROVE] Changes to collapsible section and navigation/validation logic in On-Page Checkout](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=task/16780&appConfig=eyJhY2lkIjoiIn0= "Task #16780 [#15775][IMPROVE] Changes to collapsible section and navigation/validation logic in On-Page Checkout")

[https://share.getcloudapp.com/yAuyqpDd](https://share.getcloudapp.com/yAuyqpDd)

See updated PRD: [https://share.getcloudapp.com/xQu65ZLY](https://share.getcloudapp.com/xQu65ZLY)

See updated Figmas: 

-   1366px and above: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5904%3A260580](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5904%3A260580)
-   768px: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5975%3A268034](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5975%3A268034)
-   414px: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=6257%3A257500](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=6257%3A257500)

---
### 16933 [#15775][IMPROVE] Remove "Create Account" and "Login" buttons from Your Information section
Currently, we have a separate "Create Account" and "Login" button in Checkout for our Auction Bid use case when the user is either logging into their existing account or creating a new one: [https://share.getcloudapp.com/Apu92bZ6](https://share.getcloudapp.com/Apu92bZ6)

This is a bit odd looking and strange UX to have two call-to-action buttons in this section that both do essentially the same thing. In our testing, we found that clicking the "Continue" button does the same thing as clicking "Create Account" or "Login" (let us know if we are incorrect in that). 

With that said, it seems to make sense to just remove those separate "Create Account" and "Login" buttons and just have our "Continue" button like we have in all sub-sections on Your Information. The user will just click that to validate and go to the next step, instead of being confused about what button they need to press here and in what order. 

Let us know if you have any questions or concerns about this. We will update the Balsamiq to remove these buttons once we get confirmation from you that this change should be okay. Thanks!

---

 iv. [**Review & Pay**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120735): this section is similar to our existing Review & Pay section where the user will review their transaction, enter card information, and submit their transaction.

- There are two existing cards that we’ve _moved_ from Your Information to this section:
    - [Payment Method card](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A132485): So the user selects Payment Method on this section now
    - [Notice](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A132522)

- Our current Review & Pay page has a lot of information on it, so in this new design we’ve found ways to simplify it to only the essential info and hide away more detailed info behind “View more” controls.

- ~~The main way we accomplished this is with~~ [~~Collapsible Sections~~](https://share.getcloudapp.com/Jru4e9Ov). You can see in the Figma/Balsamiq that we have our Payment Summary section, which is the same core component as this current one in our current Checkout: [see screenshot](https://share.getcloudapp.com/z8u6b2mO). We still have three separate possible sections/cards here in the Payment Summary section: one for the General components, one for Bids, and another for Pledges.

- For the title of the General card here, we want to use a different title depending on what items are in their transaction. [See spreadsheet showing titles we’ll use](https://rallyup.sharepoint.com/:x:/s/fileshare/EW_DPvlsKSNIh9Hays1wCMYBtxrg8M6MBR3rldmh1SpVLw?e=JeSD3w).

-  ~~The difference in this new design is that we are only showing the final “Total”/”Charged Later” line by default:~~ [~~see screenshot~~](https://share.getcloudapp.com/NQuwpGW5)~~. This makes it simpler to users to just see their final amounts due, rather than being overloaded with information and line items and tables about everything they bought.~~

- When the user clicks “[View details](https://share.getcloudapp.com/YEuR406X)” on any of these cards, that card will expand to show additional information. That additional information that shows is [the same line items we currently have](https://share.getcloudapp.com/geubPXQ9) in the full Donation Summary section – no changes should be made to these line items, as we want to just carry them over directly from the old Checkout. [See Figma here where this is shown](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120695).

- You’ll note that we don’t have [these tables](https://share.getcloudapp.com/eDujE46w) in use anywhere on this, which is correct as we’ve removed them for simplification. These tables will still be shown on the Confirmation Page exactly as they are now, so we’re not making any changes to them there.

- We also use [Collapsible Sections](https://share.getcloudapp.com/5zuBO6yX) for things like the Gift Aid/Delivery/Registration Information/Your Information cards. [See in the Balsamiq](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6) that we’ve grouped these under collapsible sections. 

- Generally, the logic for what sections, strings, and fields we show here, along with the “Pay” button logic, is exactly the same as the current Review & Pay section – the main change is just to put everything in the new design that you see in the Figma file above.

### 16931 [#15775][IMPROVE] Add "Saved Payment Info" to the "Review & Payment" Tab

We'd like to add an improve task for the "Saved Payment Info" State for Auction bids. Currently, with On-Page Checkout, if the user has payment information saved there is no communication of this anywhere within Checkout. So if you have an existing auction bid and you go to make another, the Review & Pay section just shows no payment info at all: [https://share.getcloudapp.com/2NulOkNR](https://share.getcloudapp.com/2NulOkNR)  . We realized some users may be confused by this and think that they didn't pay for their bids (even though behind the scenes, we do have their payment info saved). 

Therefore, we'd like to implement the following: 

"Saved Payment Information" State

[See Figma](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences---Essential-Documentation?node-id=7883%3A298321)

[See Balsamiq](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

[See Balsamiq Screenshot](https://share.getcloudapp.com/8Lu9Z0D4)

If the user has payment information saved, then when they go to place another Auction bid, then they should see the "Saved Payment Information" state. This should appear exactly where the card input area would is shown [here](https://share.getcloudapp.com/xQu68X4k). We are not adding the full functionality seen on the Balsamiq or the Figma in this improve task. 

Instead, we are only adding the string "Your saved payment information" and the card that shows the string "Ending in XXXX" and the credit card brand logo. ([See Screenshot](https://share.getcloudapp.com/Z4uj8RE6))

The copy within this card [here](https://share.getcloudapp.com/04uxwjjK) should say "Ending in XXXX" where 'XXXX' is the last four digits of the user's card. The logo at the [end of the card](https://share.getcloudapp.com/qGuJLWez) should show the logo of the corresponding brand of the card the user used. We believe it is possible to get these logos directly from Stripe depending on the type of card used, but let us know if this is not possible and we will ask our designer to get the files. 

Please note that we are not adding the ability for the user to edit nor remove their card information within on-page checkout at this time. We are only adding the ability to see their saved card info so they know it's still in the system.

**Note:** This is only for Auction bids as we do not save card information for any other Activity type at the moment. Let us know if you have any questions!

---

 v. [**Confirmation**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120747): we’ll consider this Confirmation screen in the new on-page Checkout to be our “Simple Receipt”, because it doesn’t contain everything from [our Full Receipt](https://go.rallyupqa.com/checkout/ContributionConfirmation/04bedec5-228b-45c9-a537-a0d6408a52eb) and instead only has a brief summary with the important info the user needs to know. We’ll still keep our existing Full Confirmation and Payment Receipt pages exactly as-is because they’ll still be used, as described below.

- **Payment Summary**: this section should display our [existing table(s)](https://share.getcloudapp.com/04uAALoo) we have for this section on the Full Confirmation Page, including the Charged Now/Charged Later lines when applicable, per the existing logic on those strings on the Full Confirmation Page.

    - The only difference is that we don’t want to show the Column Headers on the Confirmation Page, as you can see here: [see screenshot](https://share.getcloudapp.com/RBuYJxDZ).

    - Also, the “Total” line we have now is broken out like this: [see screenshot](https://share.getcloudapp.com/qGuE6e06).

- [**Outbid Proxy Bids**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A120751): this section will show if the user’s Transaction contains Outbid Proxy Bids. Since it’s only possible to know if the user will be outbid by a Proxy Bid _after_ they submit their Transaction, that’s what this table communicates. If they’re outbid, it also gives them an explanation and a button to “Bid again”.

    - That “Bid again” button should take the user to the Bids section (described above) to let them re-enter new bid amounts for all of their “Outbid” items and let them try to submit new bids again. This is a similar process we have now for when users make another proxy bid after their first one: [see video](https://share.getcloudapp.com/Jru4DoNj).

- ‘**View Full Receipt’ button**: this button should open [the Contribution Confirmation page](https://go.rallyupqa.com/checkout/ContributionConfirmation/e2f9fbc7-83c8-4ba9-abf4-108ff89c1df7) (aka “Full Receipt”) for this transaction **_in a new tab_**.

- **“Return to Campaign Page” button**: this should simply close the Checkout Slideout.

- **“Leave a comment” button**: this will take the user to a new section of Checkout where they can leave a comment for the Campaign Page. This is basically a new section that has the same functionality that our existing [Comment Card](https://share.getcloudapp.com/Blu44db1) has. I’ll explain this section in a bit more detail in a later point.

### 17233 [IMPROVE][17156] OPC Confirmation

Created from [#17156 [PROD][#15775] SSO Partners should be required to login before accessing checkout when bidding](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=bug/17156&appConfig=eyJhY2lkIjoiIn0= "Bug #17156 [PROD][#15775] SSO Partners should be required to login before accessing checkout when bidding") conversation [https://share.getcloudapp.com/4guPxYzZ](https://share.getcloudapp.com/4guPxYzZ) :

_**Kevan Mann:**_

_The distinction between these receipt types from AIO, thanks for the detailed explanation as well._ 

_Regarding the change here, we actually don't think we need to change anything about **PaymentConfirmation** or **ContributionConfirmation** pages at all because those pages are working fine now. The issue in point 2 was specifically with **OPC Confirmation section** – we believe this should only show bids made within the current checkout session mainly because each OPC session is unique and not necessarily related to previous OPC sessions._ 

_Let's take our 3 receipt types now:_ 

1.  _OPC Confirmation (referred to in PRD as 'Simple Confirmation')_
2.  _ContributionConfirmation_
3.  _PaymentConfirmation_

_ContributionConfirmation is fine as-is with showing all bids ever made, and we don't want to change it. The reason why is because the user can only get to that page by clicking "View Full Receipt" button either on OPC Confirmation or from within the Confirmation **email**. In both cases, since the button says "View Full Receipt" it would be expected that the user should see a receipt containing every bid they ever made (ContributionConfirmation) because that receipt is for the entire transaction._

_Likewise, PaymentConfirmation is perfect for seeing a receipt for a specific Payment that is related to some original Transaction. Since AIO we have the ability to split a single Transaction into multiple Payments, the PaymentConfirmation is a way for the user to view a receipt on a per-payment basis (whereas ContrbutionConfirmation is a per-transaction receipt that can contain info that was split into multiple payments)._ 

_And finally, if we think of the OPC Confirmation Section in the context of OPC, each OPC session is specific to the items in the current session (transaction). That's why it seems to make sense to keep OPC Confirmation only showing bids made within current OPC Checkout session, but all other pages can remain as-is with no changes because they are for separate purposes as I outlined above._ 

_Hope this all makes sense and I didn't cause any more confusion. Let me know if anything is unclear still._

---

### 16806 [#15775][IMPROVE] Use "Subject Line" field on Simple Confirmation Page headline

Instead of a fixed "Transaction confirmed" here on the Simple Confirmation page's headline, we'd like to use the same "Email Subject" field from Experience Setup: [https://share.getcloudapp.com/Z4uj294k](https://share.getcloudapp.com/Z4uj294k)

This is the same thing we do on the Full Confirmation Page and Confirmation Email currently too, so this just makes it consistent on the new Checkout too: [https://share.getcloudapp.com/v1u0B7rQ](https://share.getcloudapp.com/v1u0B7rQ)

The Balsamiq has been updated: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

---

h. **Collapsible Tabs Logic:** As mentioned above, we are organizing Checkout cards into [collapsible sub-sections](https://share.getcloudapp.com/RBuYrJvp) within each timeline step. Here’s how they work:

- [**See Figma Prototype Link which shows Collapsible Tab behavior**](https://www.figma.com/proto/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?page-id=5668%3A257487&node-id=5671%3A259039&viewport=501%2C48%2C0.2&scaling=min-zoom&starting-point-node-id=5671%3A259039)

- [**See Figma Design for Collapsible Tabs**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5904%3A260580)

- **Design Requirements**: You can see how each sub-section is displayed on its own card: [see screenshot](https://share.getcloudapp.com/Wnu0nKr4). Here are the various states for it:

    - For future sections that have not been completed yet, the titles of those sections are slightly dimmed with an opacity mask: [see screenshot](https://share.getcloudapp.com/nOuvOw1Q). The opacity of these titles is **75%**.

- Branding:

    - [Main Sub-Sections](https://share.getcloudapp.com/2NulDR4z)

    - [“Save” Buttons](https://share.getcloudapp.com/YEuOEm7J)

    - [“Next Step” Buttons](https://share.getcloudapp.com/P8uGqgZj)

 v. **Tab Title:** In the [Balsamiq](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6), you can [see the title](https://share.getcloudapp.com/WnuYmv9O) we have for each Tab as well as what cards are grouped under each Tab. Note that the actual cards/field _within_ the Tabs are the same as what we have now.

 vi. **Default-Opened Tab Logic**: When the Your Information section is first opened, we should auto-open [the first tab](https://share.getcloudapp.com/Koud9Non) so that users don’t need to manually click into it.

 vii. **“Continue” button to move to next Sub-Tab**: Within each Tab, there will be a button that reads “Continue”. This will validate the data in the current tab, save it if successful (or show errors if there’s a problem), and then advance the user and auto-open the next tab in the list.

- As described in [Improve Task #16780](https://rallyup.tpondemand.com/entity/16780-15775improve-changes-to-collapsible-section-and), all data within the current sub-section must be validated before we allow the user to advance to the next sub-section. We don’t want to allow user to advance to the next sub-sections without completing the current section they’re on. This is what creates a linear and guided checkout process.

- Users should be allowed to _go back_ to any previously-“Completed” sub-section if they want, as this allows them to edit something within that section. The “Edit” state for Completed tabs is described below.

- Once the user is on the **_last_** sub-section on the Your Information section, the button [moves to the right side](https://share.getcloudapp.com/2Nul9JA8) and when clicked it will advance them to the next _overall_ section of Checkout itself.

    - The button text for this final button should be: “Next step: [Next Section Title]” where “Next Section Title” is the title from the Timeline of whatever the next section in the Checkout Timeline is. E.g., “Next step: Review & Pay”.

    - So for example, [if “Causes” is the last step in Your Information](https://share.getcloudapp.com/L1ur8L4E), when the user clicks the “Next step: Review & Pay” button in that sub-section it should close that sub-tab and then navigate them to the next Timeline section of Checkout (e.g., “Review & Pay”).

    - This just makes it so that the user doesn’t need to click a second button after closing the last sub-section in order to advance to the next Checkout section. 

 viii. **“Completed” state for Collapsible Sub-Tabs**: You’ll note how in the Figma, the tabs have a “Completed” state for the sub-tabs: [see Figma](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5904%3A264083). Here’s the logic for how those should work:

- Since as per point h above the user can’t proceed to the next sub-section until the data is 100% valid and complete within the current sub-section, this means that once they complete a sub-section and proceed to the next one we will engage the “Completed” status indicator for that tab.

- In the “Completed” state, they will be able to click an “Edit” button to edit the data within that tab and re-save if they want using the “Save” button: [see screenshot](https://share.getcloudapp.com/geuABx28).

- [**See Figma showing Completed state for tabs**](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5904%3A264083)

i. **Timeline:** The timeline control at the top of checkout has four possible states: Completed, Active, Not Active, and Error.

 - [See screenshot showing the first 3 states](https://share.getcloudapp.com/NQuYEEAd)

- Regarding the progress bar itself, we don’t need partial progress like we have in Experience Setup. We can just have 2 states: completed/not completed.

### 16860 [#15775][IMPROVE] Timeline missing from Simple Confirmation section

**Campaign URL**:  [https://go.rallyupqa.com/gated-livestream/Event](https://go.rallyupqa.com/gated-livestream/Event)
**Actual Result:** 
The Timeline is missing from the Simple Confirmation section: [https://share.getcloudapp.com/7KuEnKeR](https://share.getcloudapp.com/7KuEnKeR)
**Expected Result:** 
As shown in the Figma, we still want the Timeline to show on the Confirmation Page. It will have all steps in the "Completed" state as shown in the Figma.
The purpose for having the Timeline on the Confirmation too is that it's just another good visual indicator to the user that they have reached the end of the process

-   Figma: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4478%3A266314](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4478%3A266314)
-   Balsamiq: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

-----

### 16905 [QA][IMPROVE][#15775] Padding adjustment for Timeline titles

Currently, the Checkout Timeline wording too tight in worst case when all possible sections are showing: [https://share.getcloudapp.com/yAuyqo1Q](https://share.getcloudapp.com/yAuyqo1Q)

We already drop the titles to 2 lines when necessary, but in order to fix the "too tight" issue, our designer says that we just need to have **4px** of spacing in between all title text containers here: [https://share.getcloudapp.com/rRubRkRO](https://share.getcloudapp.com/rRubRkRO)

Designer notes: 4px is the breaking point, so 5px would be before the "break".

---

j. **Navigation Buttons**: at the bottom of the Checkout Slideout, there’s some buttons to let the user navigate forward and backwards between Checkout sections. These are similar to our “NEXT/PREV” buttons we have now.

- [“Back” button](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A148388): on all steps except the Your Information step, the button to go back to the previous step will just read “Back”.

- We won’t have a “Back” button on the “Your Information” section since that’s the first section of Checkout and there is nothing to go back to.

 iii. [“Next step” button](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A148824): this button lets the user go to the next step of Checkout

- The text on this button will be in the same format as described above in point h. That is: The button text for this final button should be: “**Next step: [Next Section Title]**” where “Next Section Title” is the title from the Timeline of whatever the next section in the Checkout Timeline is. E.g., “Next step: Review & Pay”.

- See h above for a description of how the “Continue” button logic will work on the Your Information section in particular, which has special requirements given the collapsible tabs that are on that section.

 iv. [“Pay/Submit” button](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A148388): on the Review & Pay section, this button submits the transaction. The logic for what the button text reads should be the same as implemented in [#15193](https://rallyup.tpondemand.com/entity/15193-12486improve-change-button-text-on-submit) (AIO).
 
 ### 16281 [#15775][IMPROVE] Change Checkout Submit button text for "Free" case
  Currently, we noticed that the final Submit button in Checkout reads as "PAY FREE" for the case when the transaction contains only "Free" P2P Registrations: [https://www.screencast.com/t/QKyti0SdHR8Z](https://www.screencast.com/t/QKyti0SdHR8Z)  . I'm assuming this also happens for other cases of "Free" transactions, like when a Promo Code is used. 

The "Pay Free" wording is strange and confusing, so we'd like to change it to instead read:

-   Submit

This is the same wording we already use for the per-unit pledge and bid case, as implemented in [#15193 [#12486][IMPROVE] Change button text on "Submit" button in Checkout](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=task/15193&appConfig=eyJhY2lkIjoiIn0= "Task #15193 [#12486][IMPROVE] Change button text on "Submit" button in Checkout").

---

k. **Close Checkout button**: In the upper right side of the Checkout Slideout, there’s an [“X” icon](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A132533) which should act like a “Cancel Checkout” button: [see screenshot](https://share.getcloudapp.com/6qu8r0lN). When the user clicks this, we’ll show a confirmation modal to let them confirm whether they want to cancel their transaction:

 - **TITLE**: LEAVE CHECKOUT

 - **BODY**: Are you sure you want to leave checkout?

- **BUTTONS**: [CLOSE] [LEAVE CHECKOUT]

- When the user clicks “Cancel Checkout”, their transaction should be cancelled and the Checkout Slideout should close.

l. **Return to Cart button**[[KM1]](#_msocom_1) : (ADDED 9/14/2021) In the upper left side of Checkout Slideout, we’ll have a button that returns the user to the Cart: [see screenshot](https://share.getcloudapp.com/Wnu0XekJ).

- This will invoke the “Leave Checkout” modal described above in point k, and will then return them to the Cart once they confirm in that modal.

- Branding: the text and arrow icon should be colored **Link Text** color

## New “Leave a comment” section of Checkout

a. As mentioned above in point 2, we have a [new “Leave a comment” section](https://share.getcloudapp.com/Z4uoo1Nq) of Checkout. This section is opened after the user clicks the “Leave a comment” button on the Confirmation section: [see screenshot](https://share.getcloudapp.com/YEuRRB6G). This is also part of the same Slideout interface that we’re using for the main Checkout.

b. When the user clicks “Finish”, the comment should be posted.

- If it doesn’t require too much effort, we’d also like the user to be taken to and auto-scrolled to the Comments section of the Campaign Page automatically so that they can see the comment they just posted on the page.

- If that will require a lot of complex logic to do, then the “Finish” button can simply post the comment and just close the Leave a comment panel.

c. The “Go back” button should take the user back to the Confirmation step of Checkout.

## Merge “Campaign Updates Opt-In” checkbox with “Marketing Opt-In” checkbox

a. Currently, we have two checkboxes that act as an “Opt-in” for donors to receive communications from the organizer about the Campaign:

- [Campaign Updates Opt-In Checkbox](https://share.getcloudapp.com/v1ubbEOK): this is located on the Confirmation Page currently. It is always there, can’t be disabled, and can’t be customized by the organizer.

- Marketing Opt-In Checkbox](https://share.getcloudapp.com/GGuQQJ5g): this is an optional checkbox that can be enabled by organizers and customized to say whatever they want: [see screenshot](https://share.getcloudapp.com/wbuwwvL1).

b. We don’t need both, and we realized we can deprecate the existing Campaign Updates Opt-In Checkbox and instead just have the Marketing Opt-In Checkbox in Checkout. It’s better for it to be in Checkout rather than the Confirmation Page too, since it can be easily missed by donors on the Confirmation Page.

c. For the Marketing Opt-In Checkbox, we want to make the following changes:

- Enable this checkbox in Campaign Setup by default. This can be enabled even for existing Campaigns that are live now.

- Set [default wording](https://share.getcloudapp.com/nOuoo1Ow) for this checkbox to the following:

    - Receive emails with updates about this [campaign]

d. As for the Confirmation Page, we want to retain this [Notification Preferences card](https://share.getcloudapp.com/4gu22NAW) but it should now control the Marketing Opt-In Checkbox field instead. We have no plans to use the Campaign Updates Opt-In field anymore as we will only need the Marketing Opt-In field from now on.

- Users can update whether they are opted in or out from the Confirmation Page via that checkbox after they’ve submitted their donation.

- Currently, we know this Campaign Updates checkbox controls whether or not opted-in donors receive emails when the Organizer posts an Update on the Updates tab.

- We want to retain this behavior, but now it should be tied to the Marketing Opt-In Checkbox. So in other words, only donors who have selected that Marketing Opt-In Checkbox should receive those [Campaign Update emails](https://share.getcloudapp.com/9ZuxxK2O).

e. To clarify our expected behavior here using an example ([see discussion](https://share.getcloudapp.com/6quryjy6) with Vlad in [#15775 comments](https://rallyup.tpondemand.com/entity/15775-on-page-checkout)):

- For a Donor: the "Marketing" checkbox will also be displayed on [Checkout > Your Information](https://share.getcloudapp.com/4gunoP8G) and also on the [Confirmation Page > Notification Preferences card](https://share.getcloudapp.com/d5uAomGq).

- For the organizer: these checkboxes are enabled in the same place in Experience Setup and are dependent on each other: [see screenshot](https://share.getcloudapp.com/wbuwwvL1).

- If the Donor has checked the checkbox in Checkout > Your Information, it will be enabled on the Confirmation Page > Notification Preferences card too.

- If the Donor has unchecked the checkbox on Checkout > Your Information, it will be unchecked on the Confirmation Page > Notification Preferences card too.

## Remove “Already have a RallyUp account?” string

a. We have received feedback that some donors are put off [by this string](https://share.getcloudapp.com/yAuDr1ON) in our Checkout process because it makes them think it’s required that they create an account to donate (even though it’s not).

b. We realized there’s not really a need to have this string here anyways, since even if the user has an existing account, they don’t need to sign in to have their donation attributed to their existing account (since we automatically do that just based on the Email Address).

c. As such, we’ve removed this string from the Balsamiq for Checkout.

## Hide some donation preference checkboxes when Donation Feed is disabled

a. Currently, we s[how these checkboxes](https://share.getcloudapp.com/d5uAoN8J) regarding how to display the donation on the Experience Page in Checkout regardless of whether Comments and/or Donations Feed are enabled or disabled: [see video](https://share.getcloudapp.com/o0u6L1y5).

 i. This doesn’t really make sense in all cases though, because if the Donation Feed is disabled then there’s no reason to show the checkbox “Hide the amount of my donation from the Experience Page” because it wouldn’t be shown anyways due to the Donation Feed being disabled.

b. To address this confusion, all we want to do is change the display condition for these checkboxes in checkout: [see screenshot](https://share.getcloudapp.com/JruD2GN7).

 i. The [Balsamiq has been updated](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6) with this conditional too. 

## Branding

a. Here are the branding colors to use throughout Checkout:

- [Timeline](https://share.getcloudapp.com/Z4ujG08B)

- [Main Sub-Sections](https://share.getcloudapp.com/2NulDR4z)

- [“Save” Buttons](https://share.getcloudapp.com/YEuOEm7J)

- [“Next Step” Buttons](https://share.getcloudapp.com/P8uGqgZj)

- [Bonus Entry Card](https://share.getcloudapp.com/5zuNq755)

- [Review & Pay](https://share.getcloudapp.com/OAuP7jXb)

- [Confirmation](https://share.getcloudapp.com/xQubNxrv)

- [Logged-In State](https://share.getcloudapp.com/yAuDnQpJ)

- [Collapsible Tabs](https://share.getcloudapp.com/04uxRGxv) (ADDED 9/14/2021)

## Member/Team Registration Checkout

a. As you know, currently our Member/Team Registration workflow re-uses our current Checkout workflow: [see screenshot](https://share.getcloudapp.com/E0uYAyeb).

b. In #14288, we plan to implement a brand-new Member/Team Registration Process that _does not_ use our main donor checkout anymore. However, that US isn’t planned until later in 2021 so it will not be done now with this US.

c. Our question is: is it possible to keep the “old” Checkout but only for Member/Team Registrations like it currently is? We’re not sure if it would be a lot of work and overhead to keep the old and new checkout systems in operation at the same time, so we wanted to see what you thought.

d. If you think that will be difficult, then the alternative is that we move Member/Team Registration to use the _new_ on-page Checkout Slideout too – so we’d get rid of the “old” checkout entirely.

e. Based on your response to this point, we will update requirements accordingly to provide more detail about how this should work. Thanks!

### 16836 [#15775][IMPROVE] Wording changes on Select Participants/Teams section in Checkout
We've made a few wording changes on the Select Participants/Teams section of Checkout. See Balsamiq: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

Here's screenshot showing changed areas: [https://share.getcloudapp.com/o0uPLlEW](https://share.getcloudapp.com/o0uPLlEW)

Basically, we made two changes: 

1.  Removed all usages of "(s)"
2.  Changed "Choose another" button to "Add another"

----

### 16855 [#15775][IMPROVE] Changes to Edit/Delete button style on "Select Participants/Teams" section

We've changed the design of the Edit/Delete buttons here to make them more distinct (two separate colors): [https://share.getcloudapp.com/lluoA6ko](https://share.getcloudapp.com/lluoA6ko)

See Figma: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5898%3A258599](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5898%3A258599)

Branding: [https://share.getcloudapp.com/xQu6Jzz2](https://share.getcloudapp.com/xQu6Jzz2)

---

### 16832 [#15775][IMPROVE] Changes to field placement on Select Participants/Teams section of Checkout
Currently, when you select one of these radio buttons in Checkout on the Select Participants/Teams section, the fields related to that choice appear _in between_ the radio buttons. See video: [https://share.getcloudapp.com/DOuBE1Yq](https://share.getcloudapp.com/DOuBE1Yq)

This was a design error on our part that we missed in the peer review process. We want to change this so that the fields appear _beneath_ the radio buttons as this is standard practice (you don't want to insert fields in between radio buttons in a group)

This is already reflected in the Balsamiq with the layout of fields here: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

The Figma is updated too: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5893%3A258595](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=5893%3A258595)

---

### 16204 [#15775][IMPROVE] Change "Donate" button on Donation Pages to match Checkout format

Currently, the "Donate" button at the bottom of Donation Pages reads like this: [https://share.getcloudapp.com/X6uA57oZ](https://share.getcloudapp.com/X6uA57oZ)

We'd like to change the text format on that button to match the same logic we implemented in [#15193 [#12486][IMPROVE] Change button text on "Submit" button in Checkout](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=task/15193&appConfig=eyJhY2lkIjoiIn0= "Task #15193 [#12486][IMPROVE] Change button text on "Submit" button in Checkout"). That is – it should read "Pay [$XXX]" where $XXX is the amount of the user's payment that's about to be charged.

### 16251 [#14466][IMPROVE] Update design of "View more" loading control on Experience Page

We've received some feedback from customers that our current "View more" loading control is hard for users to see and not very obvious: [https://share.getcloudapp.com/Z4uKp86d](https://share.getcloudapp.com/Z4uKp86d)

We can definitely see what customers mean – it's small, not a full-size button, and easy to miss. 

We addressed this feedback by changing the design of that button, which you can see in the Figmas: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=326%3A67862](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=326%3A67862)

Branding:

-   This default state for the button and text should use Secondary Button color
-   The hover state (which you can see in the Figma, as a filled button) should use Secondary Button + Secondary Button Text color

This design update should only be applied to these "View more" loading buttons at the bottom of the item lists. Other "View more" buttons on the Experience Page (like on the item cards themselves) should not be changed here.

### 16686 [#15775][IMPROVE] Add "Tax Receipt Number" column to View Donations page/report

For Canadian Customers using our Canada Tax Receipt functionality, they need to have this "Receipt Number" column displayed in their View Donations report: [https://share.getcloudapp.com/9ZuQxZLl](https://share.getcloudapp.com/9ZuQxZLl)

We'd like to add a column to the View Donations page for this. The column can be called "Tax Receipt Number" and it should display that ID number in the screenshot above. This column should be added to the following places: 

1.  View Donations CSV Export
2.  View Donations > View Details modal

We do not need to add this column to the table on the View Donations page itself.

### 16702 [#15775][IMPROVE] Change logic for editing Tip Amount on Auction Bids

Currently, we don't have a way for Bidders to change the amount of their tip after they submit their first bid. During Bid Checkout, we only show the [Tip Card](https://share.getcloudapp.com/KouJ42qX) for the first bid checkout and we hide the Tip Card all subsequent bid checkouts. If the user decides later that they want to change their tip amount (for example, decrease it) there is not any way to do this now as far as we know. See video: [https://www.screencast.com/t/3pD7h7c8F5S](https://www.screencast.com/t/3pD7h7c8F5S)

To resolve this UX issue, we will making the following changes to our display condition for the Tip Card in Checkout: 

1.  **From My Account**: If the user clicks "Edit Bid" from My Account, show the Tip Card on the Bids section so the user can change their tip percentage there: [https://share.getcloudapp.com/7KuEo9mY](https://share.getcloudapp.com/7KuEo9mY)
    -   Even though the user can only edit a bid for 1 item at a time from My Account, the percentage selected here would apply to all Bids for all Items for that Experience
2.  **Show Tip Card in Checkout if all bids for a user have been Cancelled**
    -   Currently, if all bids for a specific user are "Cancelled" and the user goes to re-make their bid, we still don't show the Tip Card in Checkout that time. It looks like the original Tip Amount they selected is retained and re-used, despite having all of their bids cancelled. See video showing this: [https://share.getcloudapp.com/KouJ42qX](https://share.getcloudapp.com/KouJ42qX)
    -   If all bids for a bidder are cancelled, we don't want to retain their previous Tip Amount either. This means that if that bidder was to make a bid again _after_ having all their bids cancelled, we should treat them as a new bidder and show the Tip Card again

### 16875 [#15775][IMPROVE] Edit SMS Auction Outbid Message Text

We want to change the message text used for Outbid SMS messages on Auction Campaigns. Right now, our message uses the following text format:

_“You’ve been outbid! The new highest bid on [item name] is [amount]. Tap the link to bid again! [https://go.rallyup.com/checkout/updatebid?itemId=213115](https://go.rallyup.com/checkout/updatebid?itemId=213115)”_

We would like to change this message to:

_“You’ve been outbid on an item! Tap the link to place a new bid on the item [Checkout update bid link]"_

Basically, we want to remove the Auction item name and the new bid amount from the SMS message. The reason for this change is because Twilio sent us an email warning us that an Auction item [had cbd in the its name](https://share.getcloudapp.com/Z4uj972l). This change will help us circumvent future warnings.

### 16977 [#15775] [IMPROVE] The text of the button in the section "Would you like to make an additional donation?" is moved

Campaign URL:  https://go.rallyupqa.com/1d52e2/Sale
Steps to Reproduce:  

    Add any item to cart and proceed to checkout
    Check Additional donation section in the Your information step

Actual Result:  
The text of the button is not on one line
Expected Result:  

Info:  
4k resolution
Full HD resolution

Hello! Actually, that amount input field should display on a new line instead of on the right of the radio button itself. I fixed the Balsamiq to reflect this: https://share.getcloudapp.com/YEuO99Oy
https://balsamiq.cloud/su8ul/pdrj7d2/r05E6


### 17106 [#15775][IMPROVE] Tips should not be included in Check transactions

**Campaign URL**:  Any campaign with "Check" payment method available, like [https://demos.dojiggy.io/funrundemo/Campaign/Details](https://demos.dojiggy.io/funrundemo/Campaign/Details)

****Steps to Reproduce**:** 

1.  Go to checkout and add a Tip to transaction on Your Information section
2.  On next section Review & Pay, select "Check" as payment method
3.  Tip still included in transaction
4.  transaction submitted successfully with Tip
5.  Tip has no way to be collected since this is a Check transaction

****Actual Result**:** 

See video: [https://share.getcloudapp.com/wbu8o7O6](https://share.getcloudapp.com/wbu8o7O6)

****Expected Result**:** 

This issue is part bug, part our fault for not specifying how this should work since OPC moved position of payment method card. If you want to convert this to an improve task that's fine with us. 

We discussed and here's how we think this should work: 

1.  If a Tip is added and then "Check" is selected later as a payment method, the Tip should be removed and not included in the Transaction
    -   Our current position of the payment method card (after tipping and near the card fields) is much better than the old Checkout, so we don't want to change that just because Checks are the only non-tip-supported payment method. “Check” usage is relatively low too, so that's why we're okay with this mild UX tradeoff here for Check users.
2.  If the user then switches _back to_ a non-Check payment method (like Card), then the Tip should be restored back how it was

Essentially, we just remove the Tip if Check is selected as their payment method

### 17107 [PROD][IMPROVE][#15775] Calculated Tip Amounts not shown in Tip Dropdown

**Campaign URL**:  [https://demo.rallyup.com/autism/Campaign/Details](https://demo.rallyup.com/autism/Campaign/Details)

****Actual Result**:** 

Our Tip dropdown always only shows the percentage amount of the tip without ever showing the calculated amount next to that percentage: [https://share.getcloudapp.com/E0uK54mA](https://share.getcloudapp.com/E0uK54mA)

****Expected Result**:** 

In our old Checkout on the old tip card, this dropdown would also include a calculated tip amount in addition to the selected percentage. You can see this in the Balsamiq too: [https://share.getcloudapp.com/7KuAebZj](https://share.getcloudapp.com/7KuAebZj)

That calculated amount has a big benefit to tipping UX, because it shows the user what the amount of their tip will be right from the dropdown before they even select it. With just the percentage, it's hard for the user to select an appropriate tip percentage because they don't know what the actual tip amount will be yet. So for example if you have $10 worth of things in your cart, the dropdown would show "10% ($1.00)" and so on. 

We didn't have any requirements to remove this tip calculation logic in the dropdown so we want to restore it back to how it was before

Note: I know that for things like per-unit pledges and bids where we do not know the final amount of the tip at the time of the transaction, we can't show a calculated tip amount. That's fine for those cases where the transaction contains Bids or Per-Unit Pledges, but in all other cases we should be able to show a calculated tip amount based on their transaction total right in the dropdown.   
There is a previous issue posted about this too, see [#15570 [Prod][Blocking] Tips aren't optional for A-Thon Campaign](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=bug/15570&appConfig=eyJhY2lkIjoiIn0= "Bug #15570 [Prod][Blocking] Tips aren't optional for A-Thon Campaign") for additional context

### 17105 [#15775][IMPROVE] Add "Livestream Access Code" block to Simple Confirmation Page

Copied from comment in [#15775 On-Page Checkout](https://rallyup.tpondemand.com/RestUI/Board.aspx#page=userstory/15775&appConfig=eyJhY2lkIjoiIn0= "User Story #15775 On-Page Checkout"): [https://share.getcloudapp.com/04u5b8BN](https://share.getcloudapp.com/04u5b8BN)

Sorry for our delayed response here! We discussed this over the past few days. The short answer is that we have decided we'll add a string to the Simple Confirmation section that tells the user about where to find their Livestream Access Code: [https://share.getcloudapp.com/z8u1DWk6](https://share.getcloudapp.com/z8u1DWk6)

See Balsamiq: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

-   The "Livestream Access Code" headline can use same text styling as this: [https://share.getcloudapp.com/DOu6RydZ](https://share.getcloudapp.com/DOu6RydZ)
-   The text below the headline can use same styling as this: [https://share.getcloudapp.com/JrunPY8D](https://share.getcloudapp.com/JrunPY8D)

Here's some more background context as well as to how we've approached the separation between the Simple Confirmation and "Full Confirmation":

-   Our goal with Simple Confirmation was to keep it really focused to just showing only essential info that users _need_ _to know_ right after completing their transaction. We have Payment Summary tables now as the main thing, and an "Outbid" state for the case of them having Proxy Bids that are outbid, since those are both "need-to-know" things at that step in their user journey. 
-   So following this concept, that means we put "need-to-knows" on the Simple Confirmation and "optional stuff that can be looked at later" on the Full Confirmation Page. 
-   The "Livestream Access Code" is a good example of something that's a "need to know", especially while the Livestream is currently ongoing (such as if the user buys a ticket while the livestream is happening).

### 17178 [IMPROVE][15775] Change redirect logic for Widgets for solo CF campaigns

_Created from 15775 conversation with Kevan_

Kevan Mann:

I haven't used Widget functionality in a long time so I just tested it on Prod. It looks like I'm right (links to EP) for all cases **except** Solo Crowdfunding without Perks, in which case it links right to Checkout.

Here's how we think it should work now with OPC:

-   For Solo Crowdfunding without Perks, link to EP and auto-open the Flat Donation Modal for the user to select their donation amount: [https://share.getcloudapp.com/yAu0GKpK](https://share.getcloudapp.com/yAu0GKpK)  . They then can add it to their cart and proceed to Checkout normally.
-   Else in every other case, just link to the Experience Page rather than directly into Checkout (like current behavior) 

Let me know if you see any issues with this proposed solution!

### 17327 [#15775][IMPROVE] Change "Sale [Items]" text in Checkout to just "[Items]"

Experience URL: [https://go.rallyup.com/80a620/Sale](https://go.rallyup.com/80a620/Sale)

Currently, on our Confirmation Pages we use the text "Sale [Items]" here: [https://share.getcloudapp.com/WnukBN9g](https://share.getcloudapp.com/WnukBN9g)

Since on the Tom Holland experience we have changed "[Item]" terminology to "Contest Entries", this means it reads weirdly as you can see in the screenshot above because it says "Sale Contest Entries". 

To fix this, we need to do the following: 

1.  **Remove fixed terms before terminology in these lines of text**
    -   We want to drop the "Sale" from this line of text. 
    -   The Balsamiq has been updated: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)
    -   We also updated it for other item types too which had a fixed term before the custom terminology, so now the entire line of text is just terminology for those too: [https://share.getcloudapp.com/ApuERr0K](https://share.getcloudapp.com/ApuERr0K)
2.  **Update Full Receipt and Payment Receipt pages with same changes**
    -   These same changes should be made to the tables on our Full Receipt and Payment Receipt pages too: [https://share.getcloudapp.com/z8u1PX06](https://share.getcloudapp.com/z8u1PX06)
    -   Balsamiq updated there too: [https://balsamiq.cloud/su8ul/pdrj7d2/rCA03](https://balsamiq.cloud/su8ul/pdrj7d2/rCA03)

### 15704 [#12486][IMPROVE] Change "ConfirmationID" to "PaymentID" in "View Details" modal

[https://go.rallyupstaging.com/Account/Organizer/Contributions/d5013a?tab=Donations](https://go.rallyupstaging.com/Account/Organizer/Contributions/d5013a?tab=Donations)

Currently, the "View Details" modal on the View Donations page shows this ID as "ConfirmationID": [https://share.getcloudapp.com/jkuLjPLL](https://share.getcloudapp.com/jkuLjPLL)

However, that ID is actually the PaymentID so I think it's just mis-labeled in this View Details modal incorrectly as "ConfirmationID" since on the receipt and in reports, it's correctly showing "PaymentID":

-   Receipt showing PaymentID 100621: [https://go.rallyupstaging.com/checkout/confirmation/638a5045-3316-4660-b717-d34e737d1191](https://go.rallyupstaging.com/checkout/confirmation/638a5045-3316-4660-b717-d34e737d1191)
-   Exports showing PaymentID 100621:  [https://share.getcloudapp.com/jkuLjPLL](https://share.getcloudapp.com/jkuLjPLL)

As such, we just want to update that label in the View Details modal to "PaymentID" so that it's correctly and accurately describing the actual ID being shown there. We still want to show the PaymentID as we do now, so this is just correcting the label within this modal.

### 16164 [#15775][IMPROVE] Copy changes on Canadian Tax Receipt page

It was recently brought to our attention that two aspects on our Canada Tax Receipt are not accurate and correct per Canada government requirements. These are two small updates we need to make to make our Canadian Tax Receipts compliant again:

See updated Balsamiq: [https://balsamiq.cloud/su8ul/pvt2i/r4E5E](https://balsamiq.cloud/su8ul/pvt2i/r4E5E)

Test Prod tax receipt: [https://go.dojiggy.io/checkout/taxreceipt/a021cc4f-567d-446e-abb2-35fd240e7db6](https://go.dojiggy.io/checkout/taxreceipt/a021cc4f-567d-446e-abb2-35fd240e7db6)

1.  **Update line of text here: [https://share.getcloudapp.com/jkuPv2Z0](https://share.getcloudapp.com/jkuPv2Z0)**
2.  **Add "Issued Date" line: [https://share.getcloudapp.com/Wnux7vgJ](https://share.getcloudapp.com/Wnux7vgJ)**
    -   Canada requires you display separate dates on the receipt for the date of the donation and the date at which the receipt was issues. Although these two dates will always be the same on our end since the receipt is generated at then exact moment of the donation, we still are required to display both dates. 
        -   I believe we use "Paid Date" for the "Donation Date" field now, but if we don't then we should use that for both the Donation Date and Issued Date field. 
    -   I don't have an updated design for this added string, but I was thinking we have room for it here if we reduce spacing between the other parts: [https://share.getcloudapp.com/nOuPXxqJ](https://share.getcloudapp.com/nOuPXxqJ)  . Let me know if that doesn't work.

### 16208 [#15775][IMPROVE] Change "Check" payment method availability logic

Currently, the availability of the "Check" payment method in Campaign Setup depends on which Campaign Types you enable: [https://share.getcloudapp.com/12u4RjBj](https://share.getcloudapp.com/12u4RjBj)

This means that if you enable Auction, that checkbox is hidden (Because we don't support Check payments on Auctions) but this is also the case if you have a multi-component campaign where Auction is only one of the components (e.g., Auction + Raffle). This means that on an AIO campaign like that (Auction + Raffle), you can't accept Checks for the raffle component of your campaign.

We'd like to improve this logic so that we allow Check be enabled for AIO campaigns, but just disallow it at the Transaction-level in Checkout if the transaction contains any of our Check-restricted item types. That includes: 

-   Auction Bids
-   Per-Unit Pledges

So if the Transaction does not contain either of those two things, then the "Check" option should be available for the user in checkout. 

Note: We should still hide the Check option in Campaign Setup for Solo Auction campaigns as we do now, because that is one use case in which checks are not applicable given that they can't be used for auction bids.

### 16273 [#15775][IMPROVE] Headline changes on Flat Donation Pop-Up

We've made a slight design edit to the number of headlines we have on the Flat Donation pop-up: [https://share.getcloudapp.com/OAuQN2NN](https://share.getcloudapp.com/OAuQN2NN)

Instead of 2 there, we simplified to just one. You can see this in the Figmas: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A160663](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=1226%3A160663)

Balsamiq also updated: [https://balsamiq.cloud/su8ul/pdrj7d2/r2278](https://balsamiq.cloud/su8ul/pdrj7d2/r2278)

### 16276 [#15775][IMPROVE] Change "Card Background" branding color for RallyUp Partner

We'd like to make one change to the "Card Background" color used for RallyUp Partner's Branding colors: [https://rallyup.sharepoint.com/:x:/s/fileshare/EckzKg0k8AxFkAlvlNNaVB4BZOzMGB2IRaMrNANyKUrXfQ?e=73jcvS](https://rallyup.sharepoint.com/:x:/s/fileshare/EckzKg0k8AxFkAlvlNNaVB4BZOzMGB2IRaMrNANyKUrXfQ?e=73jcvS)

Old Color: FBFBFB

New Color: FAFBFD

### 16639 [#15775][IMPROVE] Update design of Promo Code block in Checkout

We've updated the position and design of the way users input Promo Codes in Checkout. Currently, this is handled via a small string below the Card Info field but with the new OnPage Checkout we've realized it's more intuitive to place this closer to where the user is shown their Total Amounts that they'll be paying. See screenshot: [https://share.getcloudapp.com/kpunbexk](https://share.getcloudapp.com/kpunbexk)

Here is the Figma showing all of the possible states for this: [https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4487%3A228221](https://www.figma.com/file/eD6wze2YSaYCN0CclY7Liu/Virtual-Experiences-Essential-Documentation?node-id=4487%3A228221)

Balsamiq updated too: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

Branding screenshot: [https://share.getcloudapp.com/xQu6JbwQ](https://share.getcloudapp.com/xQu6JbwQ)

This Promo Code card should only display under the same conditions that our current string display. That is, it should only display if there is at least 1 promo code created on the Experience.

### 16780 [#15775][IMPROVE] Changes to collapsible section and navigation/validation logic in On-Page Checkout

After some initial testing in these first few days of OnPage Checkout (OPC), we realized some flaws in our design for how navigation and collapsible sections work. Currently, our OPC navigation is non-linear in the fact that users can click into any of the sub-sections out of order and jump around: [https://share.getcloudapp.com/8Lu56vnA](https://share.getcloudapp.com/8Lu56vnA)  . That makes it hard for users to know what to do or what the process is to complete checkout, because there isn't a guided process that walks them through in order.

This was a mistake on our side with our initial design for this, and it was unfortunately not caught during our peer review process for the PRD. We have made changes to our PRD and design review process recently that will make it so we catch these UX issues earlier, before Development starts. Unfortunately this PRD was written well before that process was in place. 

With that said, to solve the issue now we have come up with a few changes to this logic that should really improve things and make the overall process more linear, guided, and intuitive for users. The summary of the changes are: 

1.  **Change our validation to be per-sub-section validation**
    -   This means that in order for a user to save and continue from one sub-section to another, we must validate all data within that sub-section before letting them proceed. 
    -   If there are errors within a sub-section, we'll show those errors to the user and ask them to correct them before continuing. 
    -   So for example, if the user is on the "Mailing address" subsection, they need to fill out all required fields with valid data before they are allowed to continue to the next sub-section
    -   This is the main change that will help the process feel more guided and linear to users. After this change, users won't be able to skip ahead to future sections if their current section is incomplete/invalid
    -   We'll still have a button within each sub-section for saving/validating/continuing, but see the PRD for full new requirements on this button.  
2.  **Design changes to** collapsible **tabs and "Completed" state**
    -   Since the process is more linear now, we're making some design changes to the collapsible tabs themselves to be more intuitive for this process. These are purely visual and not logical changes. We will still have a "Completed" state for the tabs which will be engaged once the user successfully saves/validates the current sub-section after clicking on the "Next" button within that sub-section. 
    -   The user will be able to enter an "Edit" state for any of the tabs, which is just opening the collapsed tabs for edits and then having a "Save" button to save those edits and close the tab again. 
    -   See PRD for full requirements on this
    -   The Figma is in process now and will be updated soon
3.  **Moving the "back to cart" button to the upper left side of Checkout**
    -   Figma coming soon to show new position. This is described in point 2L in the PRD. 

The PRD has been updated with all of these changes. See yellow-highlighted portions of PRD in point h and j: [https://share.getcloudapp.com/04uxd7P6](https://share.getcloudapp.com/04uxd7P6)

Let us know if you have any questions about the proposed changes, and thank you for your patience with us as we iterate our design to make this the best possible Checkout we can.

### 16802 [#15775][IMPROVE] Remove "View more" controls on Payment Summary cards on Review & Pay

After some internal UX testing, we decided to get rid of these View more/View less controls here on Review & Pay: [https://share.getcloudapp.com/yAuyBeXA](https://share.getcloudapp.com/yAuyBeXA)

We just want those cards to be shown in their expanded states all the time without any control to expand/collapse them. Initially we added these in an attempt to make checkout shorter and have less scrolling, but we realized that the majority of use cases won't have that many line items in there and it's best practice to let people review their transactions line-by-line on a Review section like this. 

These controls have been removed from the Balsamiq: [https://balsamiq.cloud/su8ul/pdrj7d2/r05E6](https://balsamiq.cloud/su8ul/pdrj7d2/r05E6)

The Figma will be updated soon.

### 16818 [#15775][IMPROVE] Event tickets behaviour
Created from converstation in [TP - 15775](https://share.getcloudapp.com/kpunZ9AY)

1.  Only allow 1 Ticket to be opened at a time
    -   So just like on Prod, if you click on another ticket it should close the currently-open one: [https://share.getcloudapp.com/Wnu0Xmdz](https://share.getcloudapp.com/Wnu0Xmdz)
2.  Auto-open first Ticket in list, so that user doesn't need to manually click into the first one when they land on the Event Tickets section
    -   This is also how it currently works on Prod/Staging

So basically, we want to carry these two behaviors from our old Checkout to the new Checkout and use them here on Event Tickets section.

### 16831 [#15775][IMPROVE] Donation Preferences section changes

There's a few small markup changes we'd like to make to the Donation Preferences section: 

1.  Remove View More/View Less control here so that all options are available without needing to click to expand/collapse it: [https://share.getcloudapp.com/nOuv729n](https://share.getcloudapp.com/nOuv729n)
2.  Don’t show “Name” field unless checkbox for it is selected: [https://share.getcloudapp.com/P8uGr5bD](https://share.getcloudapp.com/P8uGr5bD)

### 16885 [#15775][IMPROVE] Review&Pay, multiple selection of stripe connected account

Missed part for Review & Pay section. If Partner on PLF and added secondary stripe account, a supporter can choose primary or secondary connected account before paying.

### 17160 [#15775][#14466][Improve] Implement functionality from #14466
Need to add related functionality between the two US - 14466, 15775

1.  The Donate Button will always be shown during Streaming Mode
2.  The button text on the donate button will be fixed to read “Donate”
3.  If there is not a featured donation-level active, then this button should open up the same [Flat Donation Pop-Up](https://share.getcloudapp.com/p9uAz5rp) that allows the donor to select their donation amount
    1.  Normally the user would add the donation amount to their cart, and then they can choose to keep browsing or checkout
    2.  In the case where the user clicks this “Donate” button during the livestream, they should be taken directly to the on-page checkout process after selecting their donation amount
4.  If a featured donation-level is made active, the button should change to read “Donate $[ Featured Amount ]”
    1.  This button should take the user directly to the on-page checkout process with the Featured Amount as the amount of their donation





