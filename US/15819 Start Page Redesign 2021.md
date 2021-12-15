#15819

# Overview
In this user story, we’ll be redesigning our Start Page with a new and more modern design. This new Start Page also has an improved workflow that better optimizes our onboarding and conversion rate metrics as well as improves our marketing and statistics capabilities.

Before we go into the requirements, we wanted to update you on one thing regarding marketing and positioning on our side. We are categorizing RallyUp’s customers that we target into three main groups: see screenshot.

1. Nonprofits: our main audience, these are nonprofit organizations from a size of $50k annual donations all the way up to $25M+ in donations. See example from our Make-A-Wish client.

2. Groups: includes smaller nonprofits as well as other types of charitable groups like schools and sports teams. See example from our NEFC Soccer client.

3. Corporate (CSR): these are for-profit organizations that run fundraisers to benefit a charity organization. See example from our ExxonMobil client.

This doesn’t really affect the app or our user types of Advocates and Organizations, but we wanted to let you know about how we’re approaching this from the company strategy level. These groups are what we will be targeting and positioning the company around in our marketing, advertising, sales efforts, and more.

In the future, we will be adding additional functionality to better support the unique needs of these specific 3 groups. The first step towards this is our new Start Page, which will ask users directly which of these 3 groups they fall into. By storing that info in our database, it will be hugely helpful to marketing, analytics, and strategy going forward. More detail explained below in the requirements.

# Start Page

## Implement new Start Page design

a. See Figma file: i. Start Page Design

b. See Balsamiq for copy to use for the new Start Page: i. Start Page Balsamiq c. Note how this new design no longer has our app’s Header or Footer on it. This is expected and what we’d like to do, as it creates a cleaner and more focused design. i. The logo in the upper left should use the Header Logo image from Partner Setup, matching the display size shown in the Figma.

d. Field Design: You can see in the Figma our new input field design style. This is the same one that we use in the new On-Page Checkout in #15775.

i. I’ll copy the requirements from #15775 here in case this gets worked on before #15775: ii. New Input Fields: We’ve created a new modern input field design where the placeholder text animates out of the way once the user focuses their cursor into it. You can see this in action in this prototype here: view prototype.

· We aren’t sure how difficult this would be to implement. Let us know your thoughts on this and if you see any issues with this. If needed, we can delay this point to a Phase2. iii. Checkboxes: see Figma Design System File here for the new checkbox style and the selected/unselected state. e. Step 1 – Create Your Login: This step is similar to our current Step 1 on the Start Page. Users will fill out their Login information for their User account.

i. The left sidebar will be customizable in Partner Setup. Additionally, it is entirely optional and can be disabled in Partner Setup. Both of these points will be explained in the Partner Setup section below.

· Note how on mobile and tablet, the left sidebar from desktop is split up and displayed slightly differently: see screenshot.

ii. On the right, we start with an element that shows only if an already-logged-in user accesses the Start Page: see screenshot. This should only show for logged in users. The link should redirect to the My Campaigns (/Campaigns) page. · If the user is not logged in, we have a separate string which shows to allow the user to log in if they have an existing account. When the link in that string is clicked, we should redirect the user to our Login Page.

iii. Next, we have Social Login buttons for Google, Facebook, and Apple. This is explained in more detail in point 2 below.

iv. Below that, we have the same fields we have on our current Start Page Step 1.

· Note that we have a new design for the “error state” of the Email Field for when the user enters an email address that already exists. See here. f. Step 2 – Who Are You?/Organization: this step is a combination of our current Step 2 where users enter the name of the Organization they are fundraising for, and our current Step 3 where we ask users their role (Organization or Advocate).

i. On this new Step 2, we now ask users via a series of dropdown options Who they are and What they’re fundraising for. Depending on their selections here, we can make users either “Organization” or “Advocate” therefore eliminating the need for a separate Step 3 of our onboarding process where we ask users these questions. ii. Country Field: currently, our Country dropdown is just a long scrolling dropdown with no ability for users to type in a name of their country to jump to that position in the list. It means a lot of scrolling and hunting for users to find their country, as they have to manually scroll the entire Country list until they find theirs.

· You may be familiar with other dropdown styles where you can type into your keyboard the first few letters of something and it jumps to that position in the dropdown.

· If this is possible for us to do, we’d like to implement this here for this dropdown.

· Small UX details like this can actually add up to improve overall conversion rates for our onboarding process. · This should still be defaulted to the country set at Partner Setup

iii. You can see in the Balsamiq that we have various dropdowns that can show depending on the user’s selection.

· As it is currently on the Start Page, the “State” dropdown should only show if “United States” is selected as the Country. · For the first dropdown after the country selection, the options shown in the dropdown will vary depending on if US is selected as the Country or not. · For the second dropdown after the country selection, depending on what the user selects in the first dropdown, the second dropdown’s entries will change accordingly to as shown in the Balsamiq.

· Note: if the user selects “Group or organization (non-501c)” OR “501c organization” from the first dropdown, we do not need to show the second dropdown block at all. In other words, the second dropdown block should only be shown if “Other” or “Company or business” is selected in the first dropdown.

· Both dropdowns should be default-selected to the “Select option” choice.

· Note: these dropdowns will only show for the RallyUp Partner. Since Partners don’t have Advocates and they aren’t

using our same marketing positioning, that means these dropdowns aren’t applicable to them so we can just hide them and onboard all of their customers as Organizations like we do now.

iv. Organization vs. Advocate distinction: basically, the user’s choice in the first dropdown will determine whether we onboard them as an Advocate or Organization user type.

· If they select “Other”, we onboard them as an Advocate.

· If they select anything else, we onboard them as an Organization.

· Note that the non-US version of the first dropdown does not have an “Other” option. This means it’s not possible to sign up as an Advocate if you’re outside of the US. This is expected because we currently do not support non-US advocates.

v. Stopping users if they select “Personal cause” in second dropdown: · When users select “A personal cause” in the second dropdown, they should not be able to proceed with creating an account (the “Start fundraising” button should be disabled). We’ll show a message that explains why as well, which you can see here in the Balsamiq.

· We also created a design in the Figma for this state, which you can see here: “Personal cause” Error State Figma

· RallyUp does not currently support personal fundraisers (fundraisers where the money goes to a personal cause) as our app is not set up for it and it’s not a target market we are going after. Personal fundraisers still are submitted on our platform now by users registering fake organizations (e.g, “Kevan’s Organization”) and creating a fundraiser that way, which we then have to decline in CS which frustrates customers.

· By adding this choice to our Start Page and stopping them if they select it, we are hoping this catches these types of users earlier in our funnel.

vi. Organization Name field: this field will display after the user makes a selection in the first dropdown.

· As shown in the Balsamiq, it will not show if “Other” is selected in the first dropdown because “Other” is the equivalent of our Advocate use case and Advocates do not register an Organization (same business logic that we have now for Advocates).

vii. Animations: we’d like to add a fade-in animation to fields that appear as a result of selecting something. For example, when the user makes a selection in the first dropdown, they can see the second dropdown/question fade-in below them smoothly. This small detail point increases professionalism and polish on one of the first impression pages customers have of our company. g. Step 2 – COL Version: For Partners on a COL, we still have a separate version of Step 2 that is identical to our current one. That is, users will select from an organization via typeahead search as they do now. In general, we have no changes to the logic for the COL-version of Step 2 so all we need to do is update it to the new design shown in the Figma.

h. Branding: here are the Partner Setup branding colors we should use on this page: i. Step 1 (Main) ii. Field Selected State and “Account Found” String iii. “Already have an account?” String iv. Step 2 v. Step 2 – COL Version

## Implement social login on Start Page

a. One onboarding improvement we want to make is the ability for users to sign up using social login. This can be faster and more convenient for

users to sign up since they don’t need to manually type in their name, email, password, etc.

b. We will have three Social Login options available: Google, Facebook, and Apple. c. We believe that we can use our existing OneAll integration for this, although we still only want Facebook, Google, and Apple (no Twitter).

d. In checking OneAll’s website, it looks like they support all of these login options: https://www.oneall.com/services/social-network-integration/social-login/

i. Let us know which Developers should be invited to our OneAll account so that you can investigate and work on this integration.

e. Social Login workflow: here is our expected result for how Social Login should work:

i. User clicks on one of the Social Login buttons

ii. User completes social login in the separate window

iii. User returns to RallyUp and we automatically advance them to Step 2 to continue and finish the Start Page process

f. There is one issue/workflow we aren’t sure of the best way to solve, which is the case where the user tries to go back to Step 1 after getting to Step 2 from Social Login.

 i. Let us know what you think is the best way to handle this case.

ii. On the current Start Page, I think we store Start Page data into a separate DB table and then we don’t actually create the “User” entity in our DB until they fully complete the Start Page. This process has worked well because it allows us to create Contacts in ActiveCampaign for these users who have an incomplete Start Page and send them marketing messages if they drop-off.

iii. If the same approach is possible with a Social Login, then we can do the same thing here we think.

iv. If a user who did Social Login is on Step 2 and tries to go back to Step 1, then we can show Step 1 as a “fresh” Step 1 with no data or

anything entered. In order to go to Step 2 again, the user would need to re-login with Social OR sign-up manually with email.

v. Let us know what you think.

g. RallyUp-only: We want to only offer the OneAll Social Login for the RallyUp Partner. Non-RallyUp Partners should have this entire block hidden from the Start Page and should not have Social Login here.

i. This is being done due to limitations and complexities with how OneAll works with different domains. It is a lot of overhead to have every domain for all Partners added manually to our one RallyUp OneAll account.

# Partner Setup

## Add ability to disable left sidebar on Start Page

a. As mentioned above, we’ll have the ability in Partner Setup for each Partner to control whether or not the left sidebar on the Start Page is shown. i. See Figma version for case when left sidebar is disabled b. We’ve added a card in Partner Setup for controlling and customizing this: i. Partner Setup Balsamiq c. Migration: only the RallyUp Partner should have the left sidebar enabled. All other Partners should have it disabled.

## Add ability to customize image and content in left sidebar

a. On the same card described above in Partner Setup, we’ll also have the ability to customize the content in the left sidebar for each Partner. We’ll have the following elements as customizable:

i. Headline

ii. Bullet Point(s)

iii. Image

b. For the RallyUp Partner, it should use the content from the Start Page Balsamiq and the image from the Figma: i. Start Page Balsamiq ii. Figma Image

c. For all other Partners, if the left sidebar is enabled then they can customize the Headline, upload an image, and add bullet points.

i. The headline should be required

1. Character Limit: 40

ii. The image should be optional

iii. We’ll allow a maximum of 4 bullet points and a minimum of 1

1. Bullet Point Character Limit: 150

2. Note: depending on your effort estimate to allow a customizable number of bullets here, we are considering dropping this requirement and instead keeping the number of bullet points constant and required for all Partners.

d. Note: You’ll notice how in the Figma and Balsamiq for the RallyUp Partner, we show parts of the bullet points bolded and others normal. We aren’t sure of the best way to handle this for Partners.

i. For the RallyUp Partner, it’s important for us to have the bolded parts because it improves readability of the left sidebar.

ii. For other Partners, one idea is to use a markdown-style system for the input fields in Partner Setup on these bullet points. That is, users could input asterisks which would translate to bolding the text. For example, entering “*this text*” would translate to being displayed as “this text” on the Start Page.

1. If this is difficult to implement and there is no simple other solution, then we are fine with dropping the bolded requirement for other non-RallyUp Partners.

2. Our main priority is to have the bolded text for the RU Partner, but it’s not as important for other Partners to have this capability.

# ActiveCampaign

## Add new custom fields to Contact object

a. There are two new custom fields we want to pass to ActiveCampaign for the Contact objects. These custom fields correspond to our new dropdown choices on the Start Page.

b. StartPageCustomerType: string. Here is how this value should be populated based on what the user selected in the first dropdown on the Start Page:

i. 501(c) organization = Nonprofit

ii. Group or organization (non-501c) = Group

iii. Company or business (for-profit) = Business

iv. Charitable organization (NGO) = Nonprofit

v. Other = Advocate

c. FundraisingFor: string. Pass the exact value selected by the user in the second dropdown on the Start Page.