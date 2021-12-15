               

Overview

**Quick Overview:** We are greatly simplifying the user onboarding process by eliminating verification wait times and increasing clarity for users about how to get started with RallyUp.

We have made a lot of improvements to our User Onboarding and Approvals process in user stories like [#11706 Approvals 2.0](https://rallyup.tpondemand.com/entity/11706-approvals-20) and [#13717 Organization/Advocate Onboarding Changes](https://rallyup.tpondemand.com/entity/13717-organizationadvocate-onboarding-changes). These changes are well received by customers and have gone a long way in making our processes smoother.

In the months since Approvals 2.0 has launched, RallyUp has experienced a lot of growth. As we look to experience exponential growth in 2021 and beyond, we have come to understand that three main pain points still exist in our onboarding process:

1. **Onboarding:** When users land in the app on our [current Getting Started Page](https://share.getcloudapp.com/GGurddZd), they are overwhelmed with potential options and next steps they can take. There are only two things they _need_ to do (Create Campaign and Verify Account), but that’s not clear and they aren’t guided through the process well.

2. **Verification**: it is still cumbersome from the user’s perspective, and difficult to do at scale from the Support team’s perspective.

3. **Funding Setup:** Stripe Standard accounts are too time consuming to set up, and frequently have wait times on the Stripe-side where customers must wait for Stripe to approve their Stripe Account before they can start fundraising on RallyUp.

In this user story, we will address #1 and #2. For #1, we have created some new Onboarding pages and processes in the app that will resolve the described issues. For #2, we have come up with a way to integrate with some 3rd party verification services to completely automate our Organization approval process – meaning that RallyUp Staff no longer will need to do approvals at all of any kind.

For #3, we have a separate user story [#14048 Stripe Express](https://rallyup.tpondemand.com/entity/14048-stripe-express) which will add Stripe Express as our primary funding method instead of Stripe Standard. Stripe Express has several benefits over Stripe Standard, with the main ones being simpler setup on behalf of the user and instant approval of the account (because RallyUp is the one provisioning the accounts with Stripe Express, versus Stripe provisioning them with Stripe Standard). More details will be included in that user story.

# New Onboarding and Verification Process

## Implement new RallyUp Organization Verification process

a. We are replacing our existing [Verify Account process](https://share.getcloudapp.com/NQu19LRY) with a new verification process. The new verification process ditches [Website and File Upload methods](https://share.getcloudapp.com/Z4uyEAkq) as our two current ways of verification in favor of two new methods:

- Email Verification via GuideStar API
 - ID Verification via Stripe Identity

b. We’ll refer to this verification process as the “RallyUp Verification Process” throughout the PRD.

c. **Email Verification (via GuideStar):** [GuideStar](https://www.guidestar.org) is a 3rd party service that provides a comprehensive and trusted database on every 501c nonprofit in the United States. Using it, we can verify that the person registering an organization on RallyUp is affiliated with the organization they are registering.

 - The way we will do this is by asking the user to enter an email address from the organization’s official website domain. We’ll then send a verification email to that email address which will contain a randomized numerical code. The user will then enter that code into the system to verify they have access to that email, which finally will confirm their organization as verified.

 - This system ensures that only someone with access to an email address at one of the organization’s official domains is able to verify the organization.

 - GuideStar’s database only contains US organizations with 501c status. Additionally, this verification method only works if GuideStar’s database is able to find a website/email domain for a given organization.

 - With this said, for any case where GuideStar is not applicable or returns no results for an organization, users will use an the ID Verification method described below.

d. **ID Verification:** Since GuideStar is only applicable for US organizations where GuideStar is able to find a website domain for the Organization with the API, this ID Verification method is our alternate method for completing organization verification.

 - We will be using [Stripe Identity](https://stripe.com/docs/identity) for this (explained in more detail later).

 - Stripe Identity has the user to upload a government-issued ID (passport, driver’s license, etc.) with a secure 3rd party service.[[RV1]](#_msocom_1) [[KM2]](#_msocom_2) 

 - By having their ID uploaded, this provides RallyUp enough protection against fraudulent fundraising activity. In the event that fraud happens, we have the ability to pass the user’s ID along to the appropriate authorities. 

e. Now when the user completes verification via either of these two methods, the Organization will automatically be put into “Approved” status. This automated process using these 3rd party services is what removes the need for RallyUp Support staff to manually review verification and manually approve Organizations, as they do now.

 - More specifics on the process will be explained later.

f. More details about GuideStar and Stripe Identity APIs and the integrations with those services will be explained later.

g. The RallyUp Verification Process will be optional and will be enable-able at the Partner-level.

 - For the initial rollout of this user story, only the “RallyUp” Partner will use the RallyUp Verification Process.

 - All other Partners will have it disabled and will use a separate process (explained later).

 - The reason for this is because GuideStar is expensive and is not a cost we want to take on for our Partners, and most Partners won’t want to pay for it themselves.

· Additionally, Stripe Identity may be considered too much of a barrier to entry for some of our Partners.

· Because of these variations in needs from our Partners, we’re implementing a separate (more simple) verification process for them.

# Implement new Partner Organization Approval Process

a. As mentioned above in point 1g, the RallyUp Verification Process (described in point 1) is going to be optional and enabled at the Partner-level. For the initial deploy of this user story, only the RallyUp Partner will use it.

b. For all other Partners, they will use a more simple Organization Approval Process that does not require users to submit verification.

c. Instead, Partners will have two options for how Organizations submitted under their Partner are approved:

 - **Auto-Approved**:[[RV3]](#_msocom_3) [[KM4]](#_msocom_4)  organizations submitted under a Partner with this option will automatically go to “Approved” status. All Campaigns submitted for that Organization will therefore be able to start fundraising immediately (because they are in Approved status).

 - **Manual Approval:** organizations submitted under a Partner with this option will go to a new status called “Pending Approval”. Campaigns will not be able to start fundraising when the Organization is in this status. The organization will need to be “Approved” by the Partner Admin/SysAdmin in order for Campaigns under that Organization to start fundraising.

d. You can see this shown in the Lucidchart below: [see screenshot](https://share.getcloudapp.com/d5upoRN9)

 - [RallyUp Onboarding Process Lucidchart Diagram](https://lucid.app/invitations/accept/03233e31-705a-4a7c-adc0-eaad8f5f4a93)

e. In Partner Setup, we’ve added the [settings for these options](https://share.getcloudapp.com/04uOB5yv). See Balsamiq:

 - [Partner Setup Balsamiq](https://balsamiq.cloud/su8ul/pks9l/rF651)

# Implement new Organization Submission Notification Email field in Partner Setup

a. We’ve added a [new card](https://share.getcloudapp.com/llu2q6Ob) in Partner Setup for defining an email address that should receive notification emails each time an Organization is registered under a specific Partner. See Balsamiq:

 - [Partner Setup Balsamiq](https://balsamiq.cloud/su8ul/pks9l/rF651)

b. This field should be optional.

c. If an email is added, then for each Organization that is registered under this Partner, we should send the new email “Organization Submitted Notification”, which is described later in the Emails section.

d. If an email is not added, then that notification email should not be sent.

e. This lets Partners be notified in their Support systems for each Organization that is submitted. Using this, they can have more instant notifications for new customers signing up on their platform.

# Implement new Account Setup workflow page

a. Under the RallyUp Verification Process, after an Organizational User signs up for a RallyUp account, there are 2 things they are required to setup for their Organization before they can publish and go live with any Campaigns:

 - **Verify Account**: users need to submit verification for their Organization using one of the two verification methods mentioned above in point 1

- **Funding Setup:** users need to choose where the funds raised on their Campaigns should go. They have a choice between Do Charity (Internal Funding), Stripe Express (External Funding), or Stripe Standard (External Funding)

· More will be explained about Do Charity later (which is essentially the same as Deferred Funding but with a new name and new Stripe account).

· Note: Stripe Express is being implemented in a separate PRD. If this PRD is worked on and deployed before Stripe Express, then we will only offer Do Charity and Stripe Standard for this user story.

 - For Partners not using the RallyUp Verification Process, they do not need to submit verification so the only thing they need to do is **Funding Setup** from the above.

b. We created a new workflow interface that walks the user through completing these two steps. We call it the Account Setup page. See the Balsamiq, XD Design, and LucidChart process diagram below:

- [Account Setup Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r0354)

- [Account Setup XD](https://app.box.com/s/k9801ti6sdgm8jdsq11z0i9h3xal0iea)

- [RallyUp Onboarding Process Lucidchart Diagram](https://lucid.app/invitations/accept/03233e31-705a-4a7c-adc0-eaad8f5f4a93)

c. Currently, we require that Organizations set up Funding prior to publishing their first Campaign. Now, we’ll require that they set up Funding **and** submit verification for their Organization. They will do both of those things on this one Account Setup page.

d. **Step 1: Verification - Email**

 - The first step of Account Setup is Verification, which is what allows us to verify a user’s affiliation with an organization and prevent fundraising fraud by unauthorized individuals trying to fundraise on behalf of an organization.

 - As mentioned in point 1 above, there are two ways users can submit Verification: Email and ID. In the Balsamiq, you’ll see that we have two versions of the card depending on whether the user is doing Email or ID Verification.

- Email Verification is the “primary” method of verification that we’ll show first on this step when applicable since it is fastest and easiest to the user. 

- Email Verification relies on returning a successful result from our API call to GuideStar. Since GuideStar’s database of Organizations only contains US 501c’s, this means Email Verification should only show on this page as an option if the Organization is a 501c.

· Additionally, even if the organization is 501c, we should only provide Email Verification as an option if our API call to GuideStar returns a successful result with at least one email address domain for that organization. [[RV5]](#_msocom_5) [[KM6]](#_msocom_6) [[RV7]](#_msocom_7) [[KM8]](#_msocom_8) 

· You can see this [conditional explained in the Balsamiq](https://share.getcloudapp.com/2NujoL28).

 - If Email Verification is available for an Organization, the way it will work is that the user will be required to enter an email address that is at one of the domain(s) that was returned by the GuideStar API.

· For example, if [@wish.org](http://@wish.org) and [@makeawish.org](http://@makeawish.org) were returned as valid domains for the organization from GuideStar, then the user would be required to enter an email address like [Stephanie@wish.org](mailto:Stephanie@wish.org) as their verification email. An email like [john@gmail.com](mailto:john@gmail.com) would not be accepted as a valid verification email because “@gmail.com” is not a valid domain. 

· Once they enter a valid verification email we’ll then send a verification email to that email address with a randomized numerical code.

· The user then needs to go check that email and enter the correct code from the email in order to continue and successfully submit Verification for their account.

- **Accepted Emails**: the user should only be able to send a verification email if they enter an email address from one of the domains returned by GuideStar. The “Send Verification Email” button should be disabled until they do.

· If they enter an email address [in the field](https://share.getcloudapp.com/NQu19QLb) that is **not** from one of the domains returned by GuideStar, we should show an error message ([per the XD](https://share.getcloudapp.com/X6udjwJr)) with the text in the Balsamiq. 

- **Verification Email**: when the user clicks “Send Verification Email”, we should send the user a verification email to that email address with a randomly generated numeric code for them to enter.

· Given the nature of this email, we need it to be sent immediately via direct SendGrid API call rather than queued with our Windows Service. Users won’t want to wait to receive a verification code.

a. Let us know if this is possible, or if we could prioritize the email higher than other emails we send through the SendGrid API

· Typically, we see verification codes like this be between 4 and 8 characters long. You can let us know what would be best. We would like to keep it as numeric only since it makes it easier on the user’s end to enter a numerical code.

· The email content for this Verification Email is found below in the “Emails” section.

· Regarding the verification codes themselves, we want to implement a 48 hour expiration time on each of them.

· We want to allow users to potentially leave the Account Setup page, come back later, and successfully enter any Verification Code that has not expired. [[RV9]](#_msocom_9) 

a. This system is also what allows the user to send the Verification Email to someone else within their Organization, wait until that person receives and forwards the Verification Code to the person setting up the Account in RallyUp, and then finally they verify the account with that code.

- **Entering Verification Code:** when the user clicks ‘Send Verification Email’, that is when we’ll show the [“Enter verification code” field](https://share.getcloudapp.com/RBuWRGoQ).

· This field should only accept numbers, per point vii above.

· The “CONTINUE” button should be disabled until they enter a verification code.

· The Balsamiq shows error strings for if they enter an invalid Verification Code.

· If the verification code is valid, the user should be successfully taken to Step 2 (Funding).

 ix. In terms of when we do the API call to GuideStar for the Organization, we believe it may be best to do this when the Organization is first registered from the Start Page (or /Register page). Then, we can store the email address domains retrieved from GuideStar with the Organization so that we can show them immediately upon the user opening the Account Setup page.

· Ultimately, you can determine if there is a better place to make the API call to GuideStar or if there’s a better way of doing this. The goal is just for the user to be able to open the Account Setup page and immediately be able to proceed with whichever of the two Verification options is available to them based on their Organization.

· More details about the API call to GuideStar will be explained below.

e. **Step 1: Verification – ID**

- If Email Verification is not available due to the Organization not being a 501c OR GuideStar returning no email address results from our API Call, then the “fallback” Verification method will be ID Verification.

- This method will invoke a Stripe Identity’s interface that lets a user upload a photo of their government-issued identification (e.g., passport, driver’s license, etc.). More details about the specifics of Stripe Identity and how it works is described in point 6.

- In terms of the Account Setup page, users will click the ‘START ID VERIFICATION’ button to invoke the Stripe Identity interface.

· The “CONTINUE” button on this step should remain disabled until the user successfully completes the ID Verification process via Stripe Identity.

 - Once users have successfully uploaded ID Verification via Stripe Identity and have returned back to the Account Setup page, we’ll show a string on the card confirming each of the 3 possible statuses that can be returned from Stripe after closing the ID Verification modal:

· **In Progress**: while verification is still in progress and we are waiting for a success/fail response from Stripe, we should show this string with a loading spinner: [see scre](https://share.getcloudapp.com/5zuwzGqj)enshot. Note that for the loading spinner, we should just use our standard MDB Loading Spinner component. [[RV10]](#_msocom_10) [[KM11]](#_msocom_11) [[RV12]](#_msocom_12) 

· **Success**: If ID Verification is successful, we’ll show this string: [see screenshot](https://share.getcloudapp.com/NQu1m4Gn).

· **Failed**: if ID Verification is failed, we’ll show this string: [see screenshot](https://share.getcloudapp.com/Z4uyBmRg).

· More details about these statuses of the verification are provided later in the section regarding implementation of Stripe Identity

· Only one of these strings should be showing at a time, depending on the status of the Stripe Identity result.

· See Balsamiq for final content to use for each state. 

 v. Verification Wait Times: in testing Stripe Identity, we found that it takes about 5-10 minutes for Stripe to complete verification on their end and send us back the verification result. We will let users continue to the next step even when verification is still “In Progress.

· We’ll also let users publish campaigns and start fundraising even if their Stripe Identity verification is still “in progress”. [[RV13]](#_msocom_13) 

· In most cases, we expect a successful response from Stripe. However, if a “Failed” response is eventually returned, we’ll handle this by Freezing the organization (and their campaigns) and sending the user an email. This is explained more below in point 6.

f. **Step 2: Funding**

- Step 2 of the Account Setup page is where the user will choose their Funding option for their Organization. This is similar to how we currently require users choose Direct or Deferred Funding for their Organization.

- There are three possible options:

· **Do Charity**: This is essentially a rebranded version of Deferred Funding that will use a different Stripe account (described later in Do Charity section). In terms of the logic in the app, when an organization selects Do Charity it will work the same as how Deferred Funding works now including Fund Requests.

· **RallyUp Pay**: This will be used for our upcoming Stripe Express integration as the new primary funding option for External Funding. As mentioned in the Overview, Stripe Express will be implemented in #14048.

· **Stripe Standard**: for users with an existing Stripe account, we will allow them to sign in with it. We will no longer support _creating_ new Stripe Standard accounts under our Stripe Platform account from RallyUp once we have Stripe Express developed.

- Since the RallyUp Pay option is dependent on #14048 Stripe Express PRD, we’ve mocked up a [separate version](https://share.getcloudapp.com/6quPp10n) of this card that doesn’t have RallyUp Pay and instead has just Direct Funding and Do Charity.

· This will essentially work exactly like our existing [Payment Processing card](https://share.getcloudapp.com/rRuoKANn).

· Depending on the status of #14048 PRD at time of development here, you can choose which version to implement now within this user story.

- Do Charity is only available under the same conditions that Deferred Funding is available now. That is to say that Do Charity will **not** be available for:

· Partners

· Non-US Organizations

 - When Do Charity is not available as an option, we have a separate variation of the Funding card that doesn’t show the two boxes for choosing between the funding options. We have mocked it up in the Balsamiq: [see screenshot](https://share.getcloudapp.com/2NujeOnW).

 - The overall logic for elements on this card can mirror what we already do on the existing Payment Processing card.

· The “Have a Stripe account already?” string should be hidden once the user has linked a Stripe account, similarly to how we do now.

· If they select RallyUp Pay/Direct Funding and don’t link an existing account, the button at the bottom of the card will redirect them to Stripe to set up their Stripe account (just like our [“CREATE STRIPE ACCOUNT” button](https://share.getcloudapp.com/JrugYQ7r) does now).

a. Once a Stripe account is linked, then the button will read “FINISH SETUP” and will just complete the Account Setup process. 

· If they select Do Charity, we want to collect the Digital Check Email Address and Payable-To Name on this card (the [same fields here](https://share.getcloudapp.com/GGur1qGm) from the Payment Processing page). Additionally, they’ll be required to acknowledge the [Do Charity limits checkbox](https://share.getcloudapp.com/rRuoKdWx) before they can complete Account Setup.

 vii. Note that we have a “COMPLETE THIS STEP LATER” button on Step 2. This allows the user to leave Account Setup after completing Verification and come back later to complete Funding setup if they want.

· This button should redirect them to the Getting Started Guide.

· Once they return to the Account Setup page after having completed Step 1: Verification, they should be taken right away to Step 2: Funding.

· Users should not be allowed to return back to Step 1: Verification after completing it.

g. **Completing Account Setup:** Once the user completes both steps of Account Setup and clicks the final “FINISH SETUP” button on Step 2, a series of steps will take place in the backend.

 i. Each of these are explained in the [Account Setup Lucidchart Diagram](https://lucid.app/invitations/accept/03233e31-705a-4a7c-adc0-eaad8f5f4a93). [See screenshot here](https://share.getcloudapp.com/OAuJdjqL).

 ii. **Redirect Logic:** In terms of where the user should be redirected after completing Account Setup, we see three possibilities:

· If by completing Account Setup they have completed **both** steps on the Getting Started Page (point 3 below), then redirect the user to My Campaigns

· If by completing Account Setup they still have the “Create Your Fundraiser” step incomplete on the Getting Started Page, then redirect the user to the Getting Started Page

· If the user came to Account Setup in the first place _from_ Campaign Setup (because our [check when Publishing](https://share.getcloudapp.com/OAuJdjo0) required the user to complete Account Setup first), then we should redirect them back to Campaign Setup so that they can continue with publishing their Campaign. This is similar to our [existing logic](https://share.getcloudapp.com/llu2edA0) we have which requires users set up Funding before publishing their campaign.

 iii. In each case when they’re redirected, we want to show a success toast message confirming that the process is complete. That toast success message should have the following content:

· Your account setup is complete!

h. **Partners**: since Partners will not be using the RallyUp Verification Process, their organizations do not need to submit verification in the app. This means the Account Setup page for Partners should only have 1 step: Funding Setup.

 i. We’ve mocked up this [Partner version](https://share.getcloudapp.com/Blu19olk) of the Account Setup page in the Balsamiq:

· [Partner Version – Account Setup Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r0354)

i. **Branding:**  We should apply the following Partner Branding colors to this page:

 i. [Timeline Numbers](https://share.getcloudapp.com/JrugB0Pd)

 ii. Raised Buttons: Primary Button Color + Primary Button Text

 iii. Link Text Buttons: Link Text Color

## Implement new Getting Started page design

a. We have implemented a new design for the Getting Started page for both Organizations and Advocates. See Balsamiq and XD files below:

- [Getting Started Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r1F4A)[[KM14]](#_msocom_14) 

 - [Getting](https://app.box.com/s/vt5xt0o8jr2cwz3e1zz1e12mbkzv7sy4)[[RV15]](#_msocom_15)  Started XD[[KM16]](#_msocom_16) 

b. Changes have been made to both the Advocate and Organization versions of this Getting Started page, so I’ll explain both.

c. Organization Version: this version has been redesigned to more clearly convey the two things that new users can do when they sign up for RallyUp: Finish Account Setup or Create A Campaign.

 - If the user clicks “Create A Campaign”, they should simply be redirected to Campaign Setup.

- If the user clicks “Finish Setup”, they should be redirected to the Account Setup page per point 2 above. [[RV17]](#_msocom_17) [[KM18]](#_msocom_18) 

 - Note that the XD shows a [“Completed” state checkmark](https://share.getcloudapp.com/X6udjv6L) on the cards. [[RV19]](#_msocom_19) 

· The “Create Your Fundraiser” card should be marked as completed once the user has at least one Campaign that they are an Organizer or Campaign Administrator on.

· The “Finish Your Setup” card should be marked as completed only when the user completes **both** steps (Verification and Funding) on the Account Setup Page. The “FINISH SETUP” button on the card should also become disabled so that users cannot access Account Setup once it is completed.

· For both of these, once they are marked as completed we should [hide this time string](https://share.getcloudapp.com/geuqKKw4).

 iv. For the string on the “Finish Your Setup” card that says “2 steps left”, this should update as the user completes the 2 steps on the Account Setup page.

· Once they’ve completed the Verification step but not the Funding step, it should read “1 step left”

· For Partners, since they do not need to submit verification and only need to do Funding Setup, this will start out reading “1 step left”.

d. Advocate Version: this version has just received a design update. The logic on the page itself has not changed and it still has all of the same links and buttons it does now.

 i. Please reference the Balsamiq above, as it has new copy for the campaign type cards to make it so that each campaign type’s description only takes up 3 lines in the design.

~~e.~~ (UPDATED 2/19/2021, see [#14988](https://rallyup.tpondemand.com/entity/14988-14205improve-left-nav-menu-should-not)) ~~Nav Menu: one change we want to make is to hide the left Nav Menu by default on the Getting Started Page, similar to how it is hidden by default on the Campaign Page and users must click the icon in the header to open it.~~

 i. ~~This helps us keep the initial first impression experience for users focused on the two cards without the distraction of the menu options in the left Nav Menu.~~

f. Branding: The following Partner-level Branding colors should be used on this page:

 i. [Info Icon](https://share.getcloudapp.com/kpuwx0Bx): Header Text Color

 ii. [Checkmark](https://share.getcloudapp.com/4guJEdYG): Selected Elements color

 iii. Buttons: Primary Button + Primary Button Text

 iv. [Text Link](https://share.getcloudapp.com/wbuPg2N8): Link Text Color

 v. [Hover on Links](https://share.getcloudapp.com/Blu1Ak0d): Selected Elements Color

## Implement new Start Page onboarding process

~~a.~~ See [#14749](https://rallyup.tpondemand.com/entity/14749-12405improve-start-page-conversion-rate-optimizations) for changes to Start Page.

~~b.~~ ~~The Start Page is largely unchanged in terms of onboarding procedures from what was implemented in~~ [[13717 Organization and Advocate Onboarding Process Improvements on Start Page]]

~~c.~~ ~~The only change we have is to the flow where users select an Organization that already has been registered and has Administrators.~~

 ~~i.~~ ~~Currently in this workflow, we stop the user entirely from proceeding with this message:~~ [~~see screenshot~~](https://share.getcloudapp.com/X6udG5oy)~~.~~

 ~~ii.~~ ~~We will be changing this so that users who fall under this case are able to proceed still and be added as an Org Admin on that already-registered Organization, but before doing so, they will be required to submit Verification on the Start Page~~~~[[RV20]](#_msocom_20)~~ ~~[[KM21]](#_msocom_21)~~ ~~. We will only do this on the _RallyUp Partner_.~~ ~~[[RV22]](#_msocom_22)~~ ~~[[KM23]](#_msocom_23)~~ ~~[[RV24]](#_msocom_24)~~ ~~[[KM25]](#_msocom_25)~~ 

~~·~~ ~~For non-RallyUp Partners, we still want to “stop” them under this flow by showing them~~ [~~this message~~](https://share.getcloudapp.com/7Ku8l51x) ~~(as was implemented in #13717).~~

~~d.~~ ~~See the RallyUp Onboarding Diagram from Lucidchart below where this is shown:~~

 ~~i.~~ [~~RallyUp Onboarding Process Lucidchart Diagram~~](https://lucid.app/invitations/accept/03233e31-705a-4a7c-adc0-eaad8f5f4a93)~~[[KM26]](#_msocom_26)~~ ~~[[JY27]](#_msocom_27)~~ ~~[[KM28]](#_msocom_28)~~ 

 ~~ii.~~ [~~See screenshot of specific part~~](https://share.getcloudapp.com/QwukywZn)~~.~~

 ~~iii.~~ ~~Note how the user is added as a “Staff” or “Admin” role on the Organization depending~~

~~e.~~ ~~In terms of _how_ users under this case will submit verification, we mocked it up in the Balsamiq as taking place on Step 3 of the Start Page:~~ [~~see screenshot~~](https://share.getcloudapp.com/yAulg9O8)~~.~~

 ~~i.~~ [~~See Start Page Balsamiq~~](https://balsamiq.cloud/su8ul/pks9l/r13CD)

~~f.~~ ~~If you believe that it would be cleaner to redirect the user to some separate page where they can complete verification, let us know. The business logic/goal here is just that we cannot let this user have access to the app and be an Admin on that Organization until they successfully submit Verification.~~

~~g.~~ ~~The actual UI markup for Email Verification and ID Verification is exactly the same as it is on the Account Setup page, per point 2 above.~~

**7.** **Integrate GuideStar API for Email verification process**

a. When a user reaches the Verification Step for the first time, we need to make an API call with Guidestar to facilitate our Email Verification process

b. NOTE: Please keep in mind that we are limited in the number of API calls that we can make with Guidestar due to cost

 i. This means that we should be careful during testing not to test large quantities of calls (our limit for test calls should be around 500)

 ii. This also means that when the GuideStar API is not available for any reason, we should fall back on the ID Verification method and we should log the info or notify RallyUp Staff so that we may work with Guidestar to resolve the issue

c. We’ll be using [Guidestar’s POST Essentials v2 API call](https://apiportal.guidestar.org/docs/services/microservices.api.search/operations/5c471f485d8d8981bbd8bc9f?) to retrieve information about the organization the user selected

 **i.** More information about this call can be found [here](https://apiportal.guidestar.org/api-static-documentation-v3#api-essentials)

 **ii.** Authentication for this API call is done by setting the ‘Subscription-Key’ in the header to be:

· Prod: c6cdfe40b75d4488993a45651c7d8467

· Testing: 9abbe6a6a5e043a18edacde6944dfc45

d. When making the API call, we want the request body to just included the “search_terms” parameter with the EIN as the value

 **i.** [See their example](https://share.getcloudapp.com/xQuAXbpK)

e. The response should contain a list of organizations (seems most cases it will be 1 organization, but we’d like to be able to handle if multiple organization are returned) that have a matching EIN

f. Within the organization objects are fields labeled ”website_url” and “contact_email”

 **i.** We’d like to parse these strings and extract just the domain part of the url/email

· For example, if “website_url” is [www.guidestar.org](http://www.guidestar.org), we’d like to just retrieve the “guidestar.org” portion

· If an email is [jimmy@guidestar.org](mailto:jimmy@guidestar.org) we’d like to just retrieve the “guidestar.org” portion

 **ii.** These domains are what we’ll be using when asking users if they have an email at that domain

 **iii.** If the extracted domain is the same from the “website_url” and “contact_email”, then we will only show one email domain in [this section](https://share.getcloudapp.com/eDuP4jBj)

 **iv.** If the extracted domains are different, then we will show both and they can verify with either an email address at either of the domains

 **v.** If we are unable to extract any domain from GuideStar (e.g., both website_url and contact_email are null, GuideStar cannot find an organization with the EIN the user provided, the Guidestar API returned an error, etc.), then Email Verification is not possible and the user would have to proceed with ID verification

 **vi.** The domains should be extracted for every organization returned that matched the EIN search_term and each should be available to be used for email verification

g. When a user submits an email address for Email Verification, we’ll check the domain of the email address and see if it matches the domain of either domains extracted from the “website_url” and “contact_email”

**8.** **Integrate Stripe Identity for ID verification process**

a. As mentioned earlier, we’ll be using Stripe Identity for our ID verification method

 **i.** This [page](https://stripe.com/docs/identity) contains a brief overview and examples of how Stripe Identity works

b. The below Stripe API calls should use the credentials of the Stripe platform account set on the partner in context

c. When a user clicks the [“Start ID Verification” button](https://share.getcloudapp.com/5zuwEXWY) on the Start Page, we want to initiate the Stripe Identity verification process, described below:

 **i.** Call [Create a VerificationIntent](https://stripe.com/docs/api/identity/verification_intents/create) with the following parameters to obtain a “verification link”:

· Requested_verifications should only contain “identity_document”

· Refresh_url is used to handle cases where a user accesses a “verification link” that is expired. The Refresh URL should be a URL in the application that is available only to a logged-in user. This page should call Retrieve VerificationIntent for the VerificationIntent that the user created initially, then redirect them to the newly refreshed “verification link”. See [Stripe’s Refresh URL Handler page](https://stripe.com/docs/identity/refresh-url) for more info.

· Return_url is used to handle users that finish the verification process in Stripe and are redirected back to the application. The return_url should take the user back to the ID verification step on the Start page (where they were before they were directed to Stripe). See [Stripe’s Return URL Handler page](https://stripe.com/docs/identity/return-url) for more info.

- Direct users to the URL provided in ”redirect_to_url” returned from the VerificationIntent object

- Handle users that come back to the application via the return_url

· As recommended by Stripe, we should call RetrieveVerificationIntent when the user is returned to the app via the return_url and check the status of the VerificationIntent

· If the card for ID verification on the Start Page should show different text based on the status of the VerificationIntent:

· [See Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r13CD/b2889)

· If the Verification succeeded, we’ll show the [verified text](https://share.getcloudapp.com/X6ud1N8p)

· If the Verification is “processing”, we’ll show the [proccessing text with a loading spinner](https://share.getcloudapp.com/7Ku8GL6E)

· If the Verification is “requires_action” and the “last_verification_error” is not null, then we’ll show the error section

- While the VerificationIntent is “processing”, or “requires_action” (and “last_verification_error” is not null), then we should subscribe to the verification_intent.updated webhook and inspect the statuses when the VerificationIntent is updated

· The ID verification card on the Start Page should be updated based on the new status of the VerificationIntent when it is updated

d. When a VerificationIntent is in “require_action” status, the app should treat the user as if they have not completed verification at all

 **i.** That is to say they should face the same restrictions as users that have not tried gone through the verification process

e. When a VerificationIntent is in “processing” status, we should consider the user as if they completed verification and allow them to continue through the application as if they were verified

-If the webhook updates and we find that their VerificationIntent is successful, then no changes are needed and they can continue as verified

f. If the webhook updates and we find that their VerificationIntent status is “requires_action”, then we should restrict the user back to as if they were unverified until they verify again. This means we should:

- Freeze their organization if they were the one that registered it

- Freeze any campaigns they created for the organization

- If they were trying to register an existing organization and were added as staff on the organization after doing ID verification, we don’t need to freeze the organization but we should remove them as staff

## Migration and Organization Statuses

a. For any Organization that has not yet submitted verification and is in “Pending Verification” status, we want to keep them in this status. They will submit Verification on the new Account Setup page.

 - If they have already set up Funding but haven’t submitted Verification, then when they get to the Account Setup page, Step 2: Funding should just be pre-selected with whatever funding choice they had chosen previously. They can change it if they want, or continue with the same one and complete the Account Setup process.

b. Our new [Onboarding Process](https://lucid.app/invitations/accept/03233e31-705a-4a7c-adc0-eaad8f5f4a93) as described in the above points means that we no longer have our intermediate Organization status of “Verification Submitted” since all Organizations will go right to “Approved” status after they complete the two steps on the Account Setup page.

 - In terms of migration, any existing Organizations in “Verification Submitted” status can remain in that status so that our team can complete the review of those last organizations.

- Since no Organizations going forward will use this status, we expect the number of Orgs in this status to eventually reach zero.

 - Let us know if you think there is a better way to handle this migration.

c. Approving Orgs in “Pending Verification” status: we currently allow SysAdmin to manually approve any Organization that hasn’t submitted verification yet and is in “Pending Verification” status. Just noting that we want to retain this functionality.

Campaign Submission Process

A few changes will be made to the Campaign Submission Process in order to support the new workflows laid out above.

**1.** **Update Campaign Submission Process**

a. See Campaign Submission Process diagram below:

 i. [Campaign submission process lucidchart diagram](https://lucid.app/invitations/accept/60ba511e-a71f-46ce-a780-6e92c0fb8a1d)[[KM29]](#_msocom_29) [[JY30]](#_msocom_30) 

b. Because of our new automated verification process with GuideStar and Stripe Identity, all Organizations will need to be in “Approved” status for their campaign to be published. There is no longer this intermediate status of “Verification Submitted” that we have now.

 i. Additionally, you can see that we added a check at Publish to see if the user has completed the Account Setup page: [see screenshot](https://share.getcloudapp.com/Z4uy4bxN).

 ii. If they haven’t, we should show a modal when they publish that explains to them that they need to complete Account Setup before publishing. This is similar to our [“Set Up Funding” modal](https://share.getcloudapp.com/llu2edA0) we have currently, but this new modal replaces that one. 

 iii. See [Finish Account Setup Modal Balsamiq](https://balsamiq.cloud/su8ul/pk42v66/r7597) for this.

· [See screenshot](https://share.getcloudapp.com/Kouw6xrX).

c. For Partners using [Manual Approval](https://share.getcloudapp.com/wbuPGzrd) for their Organizations, there is also a check for if the Organization’s status is “Pending Approval”: [see screenshot](https://share.getcloudapp.com/Z4uyg7w7).

 i. If it is, then the Campaign will not be able to start fundraising until the Organization is Approved (the buttons on the Campaign Page will be disabled).

 ii. Once the Organization is Approved, the Campaign should automatically be able to start fundraising

d. **Raise Limits and Soft-Approval**: Because of this, it also means that we no longer have any need for the Soft-approval or Raise Limits system we implemented in #11706. Since the Organization itself will always be in “Approved” status when the Campaign is published, it means that they can be auto-approved without any raise limits.

 i. This is shown in the updated diagram above: [see screenshot](https://share.getcloudapp.com/X6ud6qW7).

 ii. The only time we need a Raise Limit still after these changes is for Raffles and Sweepstakes on Do Charity. This is similar to our $5000 Deferred Funding Raise Limit for Raffles and Sweepstakes. [See screenshot](https://share.getcloudapp.com/2NujDdkz).

 iii. This will be explained more in the Do Charity section below.

2. **Update Raise Limit for Raffles and Sweepstakes on Do Charity**

a. Currently, our raise limit for Raffle and Sweepstakes on Deferred Funding is $5000.

b. With Do Charity, we will still have a Raise Limit for Raffles and Sweepstakes but we’d like to increase the Raise Limit from $5000 to the following:

 i. $10,000[[KM31]](#_msocom_31) [[JY32]](#_msocom_32) 

c. Note that we still want the existing override for this limit on the Organization-level that we have now: [see screenshot](https://share.getcloudapp.com/jkuDkdEK).

 i. This allows us to grant specific organizations an exception to our raise limits on Do Charity Raffles/Sweepstakes.

 ii. We’ve updated the copy in this modal to reference Do Charity instead of Deferred Funding, [see Balsamiq](https://balsamiq.cloud/su8ul/p9m807u/rDA2B).

Partner Administration

**1.** **Add “Approve” and “Decline” functions to Partner Administration for Organizations for Manual Approval**

a. If the Partner is using the [Manual Approval option](https://share.getcloudapp.com/2Nuj4zyn) for Organizations, then they will need a way to Approve and Decline organizations.

b. To handle this, we want to give Partners access to the exact same [“Approve Organization” and “Decline Organization” functions](https://share.getcloudapp.com/NQu16NKZ) we have now on the RallyUp Partner.

c. These should be added into the “MANAGE” menu in Partner Administration > Organizations here: [see screenshot](https://share.getcloudapp.com/12urWg46).

Start Page

**1.** **Improvements to Organization Typeahead search**[[KM33]](#_msocom_33) 

~~a.~~ ~~We want to make two improvements to the organization typeahead search on the Start Page.~~

 ~~i.~~ ~~Allow entering dashes with the EIN when searching by EIN~~

~~·~~ ~~We currently allow users to search for organizations by Name or EIN. The official format for EINs is that they have a dash after the first two digits (e.g., 55-1235678)~~

~~·~~ ~~Right now, if you enter the dash like that when searching, no results are returned. You have to enter the EIN without the dash.~~

~~·~~ ~~We want to improve this so that entering a dash is supported when searching by EIN. So “55-555555” and “55555555” should return the same result.~~

 ii. Load more results in typeahead as you scroll[[RV34]](#_msocom_34) [[KM35]](#_msocom_35) 

· Currently, the typeahead shows 10 results.

· If you’re looking for an organization where there are many chapters with a similar name but for different cities/states (e.g. Make A Wish Phoenix vs Make A Wish Philadelphia) it can be hard to find the one you’re looking for when only 10 results are shown: [see screenshot](https://share.getcloudapp.com/YEuyEn7l).

· We’d like to see if it’s possible in our current typeahead to implement a “Load more results as you scroll” system. Meaning, when the user scrolls to the bottom of the 10 results in the dropdown, we load 10 more results and so on.

· If this is difficult or won’t be possible without a big refactor to our plugin, we’d instead like to increase the number of results shown from 10 to 25. 

Settings Page

**~~1.~~** **~~Implement new “Settings” page~~**

~~a.~~ ~~In an effort to reduce the number of menu options in our left menu and make it less overwhelming, we have created a new singular “Settings” page that has separate links to all of our Organization-level Settings pages on it. This is more consistent with best practices for other SaaS apps.~~

~~b.~~ ~~See XD and Balsamiq below:~~

 ~~i.~~ [~~Settings Page XD~~](https://rallyup.sharepoint.com/:u:/s/fileshare/EbYqRmu5ZppAgyj3-5Uv94oB_1-ExXJXIOet06LaNkK6ZA?e=0nh4vI)

 ~~ii.~~ [~~Settings Page Balsamiq~~](https://balsamiq.cloud/su8ul/pks9l/r0E71)

**2.** **Update Navigation Left Menu Layout**

a. The ordering and layout of the menu options in our Navigation Menu has been updated. You can see the [new design](https://share.getcloudapp.com/GGurgYpg) and layout in the files below:

 i. [New Nav Menu XD](https://app.box.com/s/693gzd85s4ng259fg03bbuvl7z7w7424)[[KM36]](#_msocom_36) 

 ii. [New Nav Menu Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r0E71)

~~b.~~ ~~The separate “Settings” button should link to the new Settings page above~~

Payment Processing Page

**1.** **Payment Processing page changes**

a. The Funding card on the Payment Processing page has been updated with a new design that is similar to the one we implemented on the Account Setup page. The overall logic on this card has not changed in terms of elements that display, but they have moved around to support the fact that the payment options are presented first. See Balsamiq:

 i. [Payment Processing Balsamiq](https://balsamiq.cloud/su8ul/p9m807u/rC31E/b0DF4)

b. The Balsamiq contains three versions of this card:

 i. With Stripe Express: [see screenshot](https://share.getcloudapp.com/JrugBROX).

 ii. Without Stripe Express and Direct Funding instead: [see screenshot](https://share.getcloudapp.com/X6ud618L).

· Stripe Express is being implemented in #14048, so please implement either this one or the Stripe Express version per when this user story is developed

 iii. When Do Charity is Unavailable and Direct Funding (External Funding) is the only option: [see screenshot](https://share.getcloudapp.com/Kouw6X7Q).

· This is for non-US Organizations OR Partners

**2.** **Create Separate Card for Statement Descriptor and Payment Processing fee rates**

a. We have created a [separate card](https://share.getcloudapp.com/L1uQwm5n) for our existing statement descriptor and payment processing fee rate fields. See Balsamiq:

 i. [Payment Processing Balsamiq](https://balsamiq.cloud/su8ul/p9m807u/rC31E/b0DF4)

**3.** **Remove Check option on Payment Processing page**

a. We currently have an option at the Organization-level on the Payment Processing page that lets people enable Check as a payment method for all of their organization’s campaigns: see screenshot.

b. This setting is unnecessary and adds confusion to the process, since users should just be able to enable Check on the Campaign-level for each Campaign they run. We do not have a need to have an Organization-level setting for this.

c. As such, we’d like to remove this setting from the Payment Processing page. The “Check” option should just be available in Campaign Setup for all Campaigns where it is currently eligible (e.g., not Auctions, etc). Users can then choose on a per-Campaign basis to enable or disable it there.

d. This card has been marked out of the [Balsamiq](https://balsamiq.cloud/su8ul/p9m807u/rC31E).

## Do Charity Funding

Do Charity is a separate non-profit 501c organization that RallyUp created to simplify the administrative process of payouts to organizations. Do Charity operates similarly to Deferred Funding in that it is our option for people to have _RallyUp_ collect the funds in our Stripe account and then pay out to the organization later when their Campaign ends.

The key difference is that a separate organization – Do Charity – will be the one issuing the payouts and tax receipts for donations, not RallyUp. The funds raised from Campaigns on Do Charity will also go to a separate (new) Stripe account from our current Deferred Funding one.

Since the process for users within the app is so similar to Deferred Funding (i.e., users still need to submit a fund request for their campaign and wait for us to pay it out to them), the main task within this user story for Do Charity is to implement the new naming in strings throughout the app, handle migration for customers currently on Deferred Funding, and link up the new Do Charity Stripe account  to the system.

In a separate upcoming user story, we will improve the fund request process itself to make it easier for both users and our Admin staff to handle payouts to these people via Do Charity. We do not need to make any changes to Fund Requests within this user story.

1. **Do Charity migration from Deferred Funding**

a. For Campaigns currently running on Deferred Funding, we want to let them continue raising funds on the current Deferred Funding Stripe account. We do not want existing campaigns on Deferred Funding to switchover to Do Charity’s Stripe account when this user story is deployed.

b. If an Organization is currently using Deferred Funding, it should be switched to Do Charity.

 i. For all future campaigns they create from that point on, they should use Do Charity funding.

 ii. This is what allows existing running Campaigns to continue with using Deferred Funding, but any unpublished campaigns and campaigns created in the future should be switched to Do Charity.

**2.** **Link new Do Charity Stripe account**

a. Contact us at the appropriate time during Development and we will provide you Testing and Production credentials for new Stripe accounts for Do Charity.

**3.** **Do Charity tax receipt**

a. Since Do Charity itself is a 501c, that means that tax-deductible receipts will be issued from them (rather than from the organization running the campaign).

b. To handle this in the app, we need to implement a new email to be sent when certain “Eligible Donations” are made on any given Campaign that is using Do Charity funding. This email will be the Do Charity Tax Receipt Email for any Campaign that uses Do Charity Funding.

c. We define “Eligible Donations” as any donation that does not contain items. This is essentially the same as our Eligible Donation criteria that we implemented in [#9883 Canada Tax Receipts](https://share.getcloudapp.com/rRuoeoNd).

 i. Note: our intention is for this to send along with the normal Donation Confirmation Email so that users receive both emails at roughly the same time.

 ii. However, for per-unit pledges, the Do Charity Tax Receipt should only be sent when that donation is actually charged and in “Paid” status.

 iii. For recurring donations, we should send one Do Charity Tax Receipt for each recurring payment.

d. The email content for the Do Charity Tax Receipt Email is below:

# Do Charity Tax Receipt Email

**SEND TRIGGER**: (UPDATED 2/3/2021) When an Eligible Donation is submitted on an **Advocate Campaign** that is using Do Charity Funding. This email should **not** send if the Campaign is _not_ using Do Charity Funding, and also not if it’s a non-Advocate Campaign using Do Charity Funding.  
**SENT TO**: The email address of the donor.  
**SUBJECT**: Your donation tax receipt for “[Campaign Title]”  
**HEADLINE**: Your official tax receipt for your donation to “[Campaign Title]”  
**BODY**:

Hi [First Name] [LastName],

Thanks for your generous donation to [Organization.CommonName]! Your payment is made to **Do Charity**, a public charity (Federal Tax ID: 82-4967842) in partnership with RallyUp, who will process your donation so it can be granted to your chosen charity. More details about Do Charity can be found below.

Your donation summary:

**Transaction ID**

**Donor Name**

**Date & Time**

**Total Payment**

**Tax Deductible Amount**

[TransactionID]

[FirstName] [LastName]

MM/DD/YYYY at HH:MM [PST]

[Total Amount Paid in Transaction]

[Before Fees Donation Amount]

  
This is an official tax receipt, so please save this receipt for tax purposes. We attest that no goods or services were provided to you in exchange for this gift.

**About Do Charity**

Your donation has been made to Do Charity, a US 501(c)(3) charity (Federal Tax ID: 82-4967842). Do Charity will then directly send funds to the charity 90 days after the Campaign you donated to ends.

If, after reasonable efforts, Do Charity cannot deliver donations to this charity, the funds may be donated to another related charity per Do Charity’s policies.

Campaign Page

**1.** **Add “Verified” badge on Campaign Page for Organizations that verified using the Email Verification method**

a. In order to improve donor confidence about the campaign they’re donating to, we’d like to add a new “Verified” badge that displays next to the Organization Name on the Campaign Page.

 i. This is similar to how you see a “Verified” badge on various social media sites.

 ii. It helps donors have more confidence that the campaign they’re donating to is actually associated with the official organization (versus created by an unaffiliated or perhaps illegitimate party)

b. We’ve added this [Verified badge](https://share.getcloudapp.com/2NujDOom) to the Campaign Page[[RV40]](#_msocom_40) [[KM41]](#_msocom_41)  XD (both the AIO Campaign Page and the “old” Campaign Page):

 i. [Verified Badge (AIO Campaign Page)](https://app.box.com/s/xo0qdb9a34c9bpkq9pa5gqk53vtrjnn2)

 ii. [Verified Badge (Old Campaign Page)](https://app.box.com/s/030x0yfkxpyq8bjjiegdhhvw3insd79o)[[KM42]](#_msocom_42) 

c. Display Conditions: This badge should only display on the Campaign Page if the Organization has been successfully verified _via the Email Verification method_

 i. We do not want to show it if the Organization was verified via ID Verification. The reason why is because that method does not allow us to verify the person’s affiliation with the organization itself – only the person themselves.

 ii. It should not display on any Advocate campaign.

d. Campaign Setup Option: Additionally, for Organizations that have the Verified badge, it should display by default on their Campaign Pages but we want to let them disable it on a per-Campaign basis in Campaign Setup if they’d like. We’ve added a [checkbox](https://share.getcloudapp.com/OAuJyKR1) for this in the Page Design section of the Balsamiq:

 i. [Page Design Balsamiq](https://balsamiq.cloud/su8ul/pk42v66/r4D70)

e. Hover Tooltip: when users hover over the verified badge, we want to show a tooltip with the following content:

 i. This campaign has been verified by [RallyUp] as an official campaign created by employees or volunteers of this organization.[[KM43]](#_msocom_43) 

f. Branding: this icon should use Header Text color from the Partner/Organization

New Emails

# Verification Code Email

**SEND TRIGGER**: When “Send Verification Email” is clicked on the Account Setup page  
**SENT TO**: The email address entered on the Account Setup page [here](https://share.getcloudapp.com/9ZuBpeKY).  
**SUBJECT**: Your account verification code  
**HEADLINE**: Complete your verification by entering the code below  
**BODY**:

Hi [First Name],

Please enter the following verification code on the [Account Setup page] to complete verification for your account:

· **[Verification Code Here]**

[ENTER VERIFICATION CODE](dev not: link this button to the Account Setup page for this Organization)

This code will expire in 48 hours.

[Support String]

# Verification Completed Email

(ADDED 2/24/2021, see #[15401](https://rallyup.tpondemand.com/entity/15041-14205improve-add-email-for-when-stripe))

**SEND TRIGGER**: When Stripe Identity verification is successful (goes to “Completed” status). The purpose is to notify users when their verification that they uploaded via Stripe Identity has been successfully approved.  
**SENT TO**: The email address of the user that submitted verification.  
**SUBJECT**: Your account is verified  
**HEADLINE**: Account Verified  
**BODY**:

Hi [First Name],

This email is an update to let you know that the verification you provided is now approved – your account is all set!

[Support String]

# ~~Notifying Existing Org Admins about new Admin~~

Removed, see comments in [#14269](https://rallyup.tpondemand.com/entity/14269-14205req-new-emails)

**~~SEND TRIGGER~~**~~: When an Org Admin is added to an already-registered Organization that has Admins,~~ [~~per this flow~~](https://share.getcloudapp.com/QwukrgAd) ~~in the~~ [~~Onboarding Diagram~~](https://lucid.app/invitations/accept/03233e31-705a-4a7c-adc0-eaad8f5f4a93)~~.~~  
**~~SENT TO~~**~~: All existing Org Admins and Staff on the Organization.~~  
**~~SUBJECT~~**~~: Someone just verified and added themself to your organization’s account~~  
**~~HEADLINE~~**~~: An update on your organization’s account~~  
**~~BODY~~**~~:~~[[KM44]](#_msocom_44) 

~~Hi [First Name],~~

~~Someone just tried to add themselves to your organization on [RallyUp]. Since you’ve already registered your organization with us, we required them to submit verification before we added them to your account.~~

~~Here’s who was added to your account just now:~~

**~~Name~~**

**~~Email~~**

~~[First Name] [Last Name]~~

~~[Email Address~~

~~If this is someone you know, then there’s no further action you need to take.~~

~~If you believe this person should not have access to your account, you can remove them here:~~

~~[MANAGE USERS ON YOUR ACCOUNT]~~~~(def note: link to Manage Users page for this Organization)~~

~~[Support String]~~

# ID Verification Failed – Organization Frozen

**SEND TRIGGER**: When Stripe Identity verification FAILS on an Organization who submitted it via the Account Setup page.  
**SENT TO**: All existing Org Admins and Staff on the Organization.  
**SUBJECT**: We were unable to verify your identification  
**HEADLINE**: An update on your verification status  
**BODY**:[[KM45]](#_msocom_45) 

Hi [First Name],

Unfortunately, we were unable to successfully verify the ID you submitted for the following reason:

· [[details_code reason from Stripe API response](https://share.getcloudapp.com/geuqG07Q)]

Because of this, we have temporarily frozen your account and any live fundraisers.

You can try verifying again by clicking the button below:

[TRY VERIFYING AGAIN](dev note: link to Account Setup > Step 1 Verification for this Organization so that they can retry ID verification via Stripe)

Once your new verification is successfully approved, your account will automatically be restored and any fundraisers will automatically continue. We’ll email you when this happens.

Need help? Get in touch with us by emailing [partnerSupportEmail].

# ~~ID Verification Failed – Org Admin Removed~~

Removed, see comments in [#14269](https://rallyup.tpondemand.com/entity/14269-14205req-new-emails)

**~~SEND TRIGGER~~**~~: When a _user’s_ Stripe Identity verification FAILS where that user was initially added as an Org Admin to an existing organization~~ [~~via this flow~~  
](https://share.getcloudapp.com/X6ud14Nq)**~~SENT TO~~**~~: The user who submitted ID verification (the Org Admin who was removed)~~  
**~~SUBJECT~~**~~: We were unable to verify your identification~~  
**~~HEADLINE~~**~~: An update on your verification status~~  
**~~BODY~~**~~:~~[[KM46]](#_msocom_46) 

~~Hi [First Name],~~

~~Unfortunately, we were unable to successfully verify the ID you submitted for the following reason:~~

~~·~~ ~~[~~[~~details_code reason from Stripe API response~~](https://share.getcloudapp.com/geuqG07Q)~~]~~

~~Because of this, we have removed you from the organization’s account.~~

~~If you believe this was done in error, please get in touch by emailing [partnerSupportEmail].~~

~~[Support String]~~

# ID Verification Successful after First Failed

**SEND TRIGGER**: When an organization’s Stripe Identity verification failed the first time, but has now become successful due to retrying verification.  
**SENT TO**: All existing Org Admins and Staff on the Organization  
**SUBJECT**: Your verification has been approved  
**HEADLINE**: An update on your verification status  
**BODY**:[[KM47]](#_msocom_47) 

Hi [First Name],

We’re just letting you know that the verification you submitted has been approved. Your account is no longer frozen and your campaigns can continue fundraising.

[Support String]

# Organization Submitted Notification

**SEND TRIGGER:** When an organization is registered on a Partner  
﷟**SENT TO:** The email address set in Partner Setup for this: [see screenshot](https://share.getcloudapp.com/bLuwExd9).  
**SUBJECT:** Organization [OrgID] ([Org.CommonName]) Submitted  
**HEADLINE:** Organization [OrgID] ([Org.CommonName]) Submitted  
**BODY:**

Hi there,

The following organization was just submitted on your platform:

**ID**

**Name**

[Org ID]

[Organization.Common Name]

Click the button below to view it in the app:

[VIEW ORGANIZATION](dev note: link to Partner Administration, filtered to show just this Org)

Changes to Existing Emails

Remove Emails: the following emails should be removed as they will no longer be needed due to the changes with the new verification process

a. [Submit Verification Confirmation](https://share.getcloudapp.com/geuqexX5)

b. [Verification Reminder – 2 Days](https://share.getcloudapp.com/5zuwq8Ee)

c. [Verification Reminder – Nearing Limits](https://share.getcloudapp.com/X6ud6k1o)

d. [Organization Approval](https://share.getcloudapp.com/8LurKGAg)

2. Update Emails: the below emails need to be updated with new content

# Internal Funding Limit Approaching

[This existing email](https://share.getcloudapp.com/yAulqOgQ) should be updated per the below content.

**SEND TRIGGER**: When the campaign reaches 80% of the Internal Funding Limit on their Raffle/Sweepstakes  
**SENT TO**: All Organization Administrators of the organization  
**SUBJECT**: Action Required: switch to Direct Funds to continue fundraising  
**HEADLINE**: Managed Funds limit almost reached  
**BODY**:

Hi [First Name],

You chose to start your [raffle/sweepstakes] using the Managed Funds funding method. Your campaign is limited to raising $[X,XXX] using this funding method.

**Please set up Direct Funds to continue fundraising without limits.**

Setting up Direct Funds just takes about 5 minutes and allows you to receive the funds you raise on a more immediate basis. 501(c)(3) nonprofits may also qualify for lower processing rates from Stripe.

[SET UP DIRECT FUNDS](Dev note: this should be a raised button that redirects to the organization’s “Payment Processing page” page)

Once you complete the setup of your Direct Funds account with Stripe, the raise limit on your campaign will be removed and you can fundraise without limits.

[Support String]

# Internal Funding Limit Reached

[This existing email](https://share.getcloudapp.com/xQuA5r14) should be updated with the following new content:

**SEND TRIGGER:** When the Internal Funding Limit is reached on a Raffle/Sweepstakes **SENT TO:** All Organization Administrators of the organization  
**SUBJECT:** Action Required: Your fundraising limit was reached  
**HEADLINE:** Your fundraising has been paused  
**BODY:**

Hi [First Name],

You chose to start your [raffle/sweepstakes] using our Managed Funds method. Your campaign was limited to raising $[X,XXX] using this funding method, and that limit has been reached.

**Please set up Direct Funds now to continue fundraising.**

Setting up Direct Funds just takes about 5 minutes and will allow you to continue fundraising. 501(c)(3) nonprofits may also qualify for lower processing rates from Stripe.

[SET UP DIRECT FUNDS](Dev note: this should be a raised button that redirects to the organization’s “Payment Processing” page)

Once you complete the setup of your Direct Funds account with Stripe, the $[XXXX] raise limit on your campaigns will be removed and you can fundraise without limits.

[Support String]

# Organization Approval Notification for Partners

[This existing email](https://share.getcloudapp.com/8LurKGAg) should be updated so that it is only sent for Partners that are using the [Manual Approval process](https://share.getcloudapp.com/04uOB5DE) for Organizations. New content below:

**SEND TRIGGER**: When the organization is approved on a Partner using the Manual Approval process  
**SENT TO**: All Administrators on the Organization  
**SUBJECT**: Your account has been approved!  
**HEADLINE**: Your account is ready for use  
**BODY**:

Hi [First Name],

We’ve verified and approved your account - you’re all set! This means that all of your campaigns can now start fundraising.

Happy fundraising!

The [RallyUp] Team

[Support String]

---

Does Stripe handle the uploading process for verification documents and files? Do we need to specify file size limits for document uploads like we do now or does this information never pass through our platform?  [[RV1]](#_msoanchor_1)

 [[KM2]](#_msoanchor_2)It’s all handled through Stripe and the info never passes through our platform, similarly to how the credit card numbers never pass through our platform.

[@Kevan Mann](mailto:kevan@rallyup.com) How does this process work? Does the partner take on the liability if their Orgs are not submitting verification?  [[RV3]](#_msoanchor_3)

 [[KM4]](#_msoanchor_4)Yes, exactly. When discussing, we decided that smaller partners will be okay with this because they are targeting a specific smaller customer base, rather than the masses, so it is easier to control.

Is there a way to set API call limits to GuideStar as a security precaution? Something like only 100 calls allowed every 5 minutes?  [[RV5]](#_msoanchor_5)

 [[KM6]](#_msoanchor_6)If I’m understanding correctly and this is about controlling API call costs, I think we don’t need this because we’ll only ever do one API call per organization – and only if that organization is a 501c. Let me know if you were thinking about something else.

I was thinking per timed session. I don't think this is applicable in our case after further review. I was initially thinking like if bots spam sign up process and we get an absurd number of sign up attempts within a set period of time.  [[RV7]](#_msoanchor_7)

 [[KM8]](#_msoanchor_8)We’d catch bots with our Google CAPTCHA on the Start Page J

What about the use case where the user is sent multiple verification codes? Should the new codes sent replace the old codes?  [[RV9]](#_msoanchor_9)

I feel like we should notify the user somewhere on this page that the identity verification wait time may be between 5-10 minutes. Else they might suspect a bug and exit page.  [[RV10]](#_msoanchor_10)

Screenshot updated. Check out the wording.  [[KM11]](#_msoanchor_11)

Nice! Looks good [[RV12]](#_msoanchor_12)

How does this work? Will users be able to raise funds to their account without actually being in verified status?  [[RV13]](#_msoanchor_13) [[RV13]](#_msoanchor_13)

Content needs to be reviewed and finalized.  [[KM14]](#_msoanchor_14) [[KM14]](#_msoanchor_14)

The link for the XD file did not work for me. Here is the link I got for the Get Started page from Box instead https://app.box.com/s/vt5xt0o8jr2cwz3e1zz1e12mbkzv7sy4 [[RV15]](#_msoanchor_15)

To add [[KM16]](#_msoanchor_16) [[KM16]](#_msoanchor_16)

For this card, I might change the wording for "Finish Your Setup"  [[RV17]](#_msoanchor_17) [[RV17]](#_msoanchor_17)

Sounds good, I"ll make that change.  [[KM18]](#_msoanchor_18)

Nice touch [[RV19]](#_msoanchor_19)

So the only change here is that we're allowing users to proceed further in the setup process. We just require them to submit verification on the Start Page so that in the event somebody is an imposter, we have their information.  [[RV20]](#_msoanchor_20)

 [[KM21]](#_msoanchor_21)Exactly!

Why is this the case? Because their Org has already been verified and we collect their verification information?  [[RV22]](#_msoanchor_22)

Since the org is already registered and verified, this would be for someone who doesn't know that their organization is already registered on RallyUp (maybe it's a big organization with a lot of employees) so they try to register it. We tell them that someone else already registered it, but they can add themselves to that existing account just by completing this verification step for themselves.  [[KM23]](#_msoanchor_23)

In this case it's more of verifying the person trying to be added to this existing Org account, rather than verifying the Organization overall.

Let me know if this doesn't make sense.

If somebody joins an existing Org, we still notify other Org members about the new member correct?  [[RV24]](#_msoanchor_24)

 [[KM25]](#_msoanchor_25)Correct, you’ll see the email I added for that in the “Emails” section of the document below.

[@Jimmy Yao](mailto:jimmy@rallyup.com) When reviewing, please review this one last time to make sure I didn't miss any logic cases.  [[KM26]](#_msoanchor_26)

I get page not found link, can you fix?  [[JY27]](#_msoanchor_27)

 [[KM28]](#_msoanchor_28)[@Jimmy Yao](mailto:jimmy@rallyup.com) Fixed!

 [[KM29]](#_msoanchor_29)[@Jimmy Yao](mailto:jimmy@rallyup.com) Double check my logic in here, please [[KM29]](#_msoanchor_29)

Looks good [[JY30]](#_msoanchor_30)

 [[KM31]](#_msoanchor_31)Jimmy to provide new number here based on criteria below [[KM31]](#_msoanchor_31)

I ran the query and the 90th percentile for amount raised for raffles over the last 3 years is $9,681, and for sweepstakes is $13,652. [[JY32]](#_msoanchor_32) [[JY32]](#_msoanchor_32)

With this info we could raise the limit to $10k or $15k or so.

 [[KM33]](#_msoanchor_33)Finish [[KM33]](#_msoanchor_33)

I don't know if this is something we can control on our end but it would be cool if we could clean up the capitalization for Organizations that appear in the search. It looks a little off when some Org names are all caps, some all lowercase, and some in between.  [[RV34]](#_msoanchor_34)

 [[KM35]](#_msoanchor_35)I agree, I’ve always wanted to do something about this. When we import them into the system from the IRS, unfortunately the way the IRS provides them to us is with all capitals.  
  
We thought a while ago about converting them all to Title Case, but that also doesn’t work because you have organization names like “Make-A-Wish Southern Florida” and I think if we title cased orgs like that, they’d show up weird like “Make-a-wish Southern Florida”.  
  
Another example would be any org names with words like “McDonald”. They would read like “Mcdonald” if we title cased them, which isn’t correct.  
  
Let me know what you think or if you see a solution. But this is why we left them as all caps for now because we couldn’t think of another solution.

To add [[KM36]](#_msoanchor_36) [[KM36]](#_msoanchor_36)

Need to ask team how this should work [[KM37]](#_msoanchor_37) [[KM37]](#_msoanchor_37)

The Do Charity Stripe account is still a Platform Stripe Standard account correct?  [[RV38]](#_msoanchor_38)

 [[KM39]](#_msoanchor_39)Correct. Right now, all Deferred Funding funds go to one Stripe account that RallyUp created. We just need to link the new Do Charity one and have all funds from Do Charity Campaigns go to that new Stripe account 👍🏻

I know it is late to mention this but the badge seems very small on the Campaign Page.  [[RV40]](#_msoanchor_40)

 [[KM41]](#_msoanchor_41)Not too late! I posted this in the Product channel for feedback too. I agree it doesn’t look amazing. Let me ping again in Teams to see the team’s thoughts.

 [[KM42]](#_msoanchor_42)Add [[KM42]](#_msoanchor_42)

Copy needs review [[KM43]](#_msoanchor_43)

 [[KM44]](#_msoanchor_44)Finish [[KM44]](#_msoanchor_44) [[KM44]](#_msoanchor_44)

Finish [[KM45]](#_msoanchor_45)

Finish [[KM46]](#_msoanchor_46)

Finish [[KM47]](#_msoanchor_47)