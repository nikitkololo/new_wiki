               

Overview

**Quick Overview:** We will be making some onboarding process changes to the [Start Page](http://go.rallyup.com/start) to reduce friction and decrease customer confusion around the choice of [Organization or Advocate](https://share.getcloudapp.com/geuzPryw) during onboarding.

Currently, the first step in the onboarding process for new RallyUp customers on the Start Page is that we ask users whether they are an Organization or an Advocate user. This choice they make determines the user type we set them as and also the overall onboarding process that we provide them.

Over the years, we’ve tweaked the wording of how we present these two choices in an effort to reduce customer confusion and, mainly, reduce the number of customer choosing the wrong option. For example, some customers who are actually Organizations may accidentally choose the Advocate option (or vice versa) which creates headaches down the line for our Support team and to the Customer as further effort is needed to “fix” the customer to the correct user type and their campaigns.

We’ve decided to take a different approach to how we onboard new customers. Rather than asking users first if they are an Organization or Advocate upfront, we will instead start by asking them what _Organization_ they’re trying to fundraise for, which they’ll [select from our typeahead search](https://share.getcloudapp.com/KourEeg4) we have now. Finally, we’ll ask them if they “work for the organization” that they just selected. If they say yes, then we’ll set them to be an Organizational user and finish the process by registering their Organization and creating their User account the exact same way as we do now for Organizational users who are onboarding. Everything from that point on would be the same onboarding process that it is now for Organizations. If they say no to working for the organization, then we’ll set them to be an Advocate user.

To clarify, we’re talking about making a few relatively minor changes to the way we present existing onboarding fields on the Start Page. However, with this new approach, we believe that we have a chance to eliminate customer confusion and friction in our onboarding process.

Start Page

Below, we’ll describe the changes we need to make to the Start Page in order to support this goal:

**1.** **Implement new Start Page markup and workflow**

a. The general new workflow on the Start Page will be as follows:

 i. Step 1: ["Tell us about yourself" step](https://share.getcloudapp.com/d5uEJKpZ)

· This is the User account creation step, the same one we have now.

 ii. Step 2: "Tell us about your org" step

· This is where users select an Organization from the typeahead or create a new one.

· It’s the same existing step we have now for this, but now we let users reach this step _before_ we know if they’re an Organizational or Advocate user – that part is determined in Step 3 below.

· NOTE: For Partners, since they don’t have Step 3, the button on this step should read “START FUNDRAISING” instead of “CONTINUE”.

 iii. Step 3: "Do you work for [orgName]" step

· New Step: this is a new step that replaces our existing [Step 1](https://share.getcloudapp.com/DOuxPO6G) and essentially is used to determine whether we make the user an Organizational user or not.

· I’ll explain more about this step below[[JY1]](#_msocom_1) [[KM2]](#_msocom_2) 

· NOTE: This Step should not appear for Partners, since Partners do not have Advocates. This means that Partners Start Pages will essentially work exactly like they do now, in that they will only have Steps 1 and 2 above.

b. [See Start Page Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r13CD/bB8A4)

2. **Step 1: “Tell us about yourself”**

**a.** Although the user enters their information in step 1, currently their user would not be created until they click the final button in Step 3.

**b.** In this user story we would like to change this so that their user account is created as soon as they complete step 1

 **i.** The reason why we’re doing this is for marketing. In a future user story, we’ll be integrating with marketing systems so that we can track and auto-email customers who proceed to step 2 but don’t complete setting up their account.

c. After completing step 1, the user should be automatically logged in and continue to complete step 2 and 3

3. **Step 2: “Tell us about your org”**

a. This step will remain the same

b. Our existing URL “/register” should land on this step. We’ll potentially be using this link in marketing emails to send to users that completed step 1 but dropped-off before completing step 2.

 i. For example, the marketing email might have a button that links the user right back to Step 2 in the app so that they can continue setting up their account.

4. **Step 3: Do you work for the Organization?**

a. This step essentially works like our existing [Step 1](https://share.getcloudapp.com/DOuxPO6G). The choice they make here will determine whether we make this user an Organizational user or an Advocate user.

b. If they select that they DO work for the Organization, then this means the user will be an Organizational user and all processes that follow once they click “START FUNDRAISING” will be exactly the same as they are now for Organizational users. That is – we register the organization, make that user an Admin on it, etc. There are no changes to that process.

c. If they select that they DON’T work for the Organization, then this means the user will be an Advocate user when they click “START FUNDRAISING”. The process will differ slightly depending on the Organization they selected in Step 2:

 i. If they selected an **existing** Org from the Typeahead search dropdown, then when they click START FUNDRAISING, in addition to the other processes that happen when that button is clicked we want to make it so that the Org they selected in Step 2 will be pre-filled on their first Campaign that they create.

· One idea we had for this would be to store the OrgID of the Org from Step 2 at the User-level somehow. Then, whenever they create their first Campaign, we pre-fill that OrgID as the Beneficiary Organization of their first Campaign. This action would only be done for the first Campaign this user creates.

 ii. If they created a **new** Org (clicked “I couldn’t find the org” checkbox OR chose a non-US country in the Country dropdown), we still can’t allow Advocates to fundraise for an Organization that isn’t already an existing one in the typeahead. This is the same logic we have now for Advocates in Campaign Setup – we prevent them from adding NEW organizations and we require them to select an existing one from the typeahead. If they want to fundraise for a new Organization that’s not already in the typeahead, then they can go the Verified Advocate route and have the Organization register and then invite them.

· So, we’re essentially keeping this same business logic but moving it to the Start Page here.

· When they click START FUNDRAISING we need to show them a modal that explains what their options are: [see screenshot from Balsamiq](https://share.getcloudapp.com/6queXKW7).

· If they click “CONTINUE” in that modal, we’ll just ignore/clear the Organization they selected before in Step 2. They’ll be taken to the Start Guide like any normal Advocate, and then they can create a new Campaign when they want and select a different Organization. This flow will not have any of the pre-fill OrgID logic we mentioned in point i above.

· If they click “CLOSE”, then the modal will just close. From there the user can determine whether they want to go back to Step 2 and select another Org, or not continue.

· The “LEARN MORE” link in that modal should link here in a new tab: [https://community.rallyup.com/t/800mcy](https://community.rallyup.com/t/800mcy)

d. We’d like step 3 to have its own link similar to how step 2 has “/register” for its own link

 i. This link should be “/affiliation”

 ii. We’d like to be able to send this link to users that completed step 2 but dropped-off before completing step 3

 iii. We understand that this may require us to save the draft organization info set in step 2 with the user, since the organization will not be registered until step 3 is completed. Let us know if this is possible already or if it will require significant development effort and we can decide whether or not we want to complete this point as part of this user story

5. **Allow for organization onboarding analytics from database**

a. With this new onboarding flow, we’d like to log some sort of information in the database that allows us to have better analytics into the progress that users have made through the onboarding process on our start page

b. Our goal is to have the ability to run analytics and obtain the following data for a given period of time for a given partner

 i. How many people completed the first step of the start page onboarding process?

 ii. Of the people who completed the first step of the start page onboarding process, how many people completed the second step?

 iii. Of the people who completed the second step of the start page onboarding process, how many people completed the third step? (applicable only to RallyUp partner)

c. You can determine the best way to record this information so that we can retrieve it from queries

d. This is part of our initiative to collect more data on user behavior in the application so we can make better and more strategic decisions around our product and business[[JY3]](#_msocom_3) [[KM4]](#_msocom_4) 

---

We should note that this step does not appear for partners correct? Should we change the button on Step 2 to be "Start Fundraising" on partner apps?  [[JY1]](#_msoanchor_1)

Yes on both, good catches. Fixing... [[KM2]](#_msoanchor_2)

Added this, let me know if you think it's appropriate for this US [[JY3]](#_msoanchor_3)

Love it [[KM4]](#_msoanchor_4)