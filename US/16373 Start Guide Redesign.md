               

[#16373] Start Guide Redesign

**Requirements Written By:** **RallyUp Product Team**

Overview

 In this user story, we are applying a new design to [our Start Guide page](https://share.getcloudapp.com/geuAZNzj). This new design is more modern and matches our new design language established first with the Experience Page update. Additionally, it contains some new features which will help improve our retention rates for new customers.

New Start Guide

# **New Start Guide design**

a. [**Start Guide Figma**](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/?node-id=44%3A824)

b. [**Start Guide Balsamiq**](https://balsamiq.cloud/su8ul/pks9l/r1F4A/b3F05)

c. The core logic of the Start Guide remains largely the same with this new design. We still have the two main options to “Create an Experience” and “Finish account setup”, and we still have the same incomplete/complete states for them. I’ll walk through each of the elements on this design and how they should work:

d. [Headline](https://share.getcloudapp.com/8Lu5dbKZ): As shown in the Balsamiq, this line should use the [PartnerName] and the user’s [FirstName] in this string

e. [Create Experience card](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=44%3A860): The button on this card will open Experience Setup, just like it does now.

 i. Complete State trigger: this card will go into the Completed state once the user has at least 1 _published_ experience

f. [Finish account setup](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=44%3A870): This card will open the Account Setup page just like it does now. 

 i. Completed State trigger: this card will go into the Completed State by the same trigger that it does now, which is when the user successfully finishes Account Setup by clicking on the [“Finish Setup” button](https://share.getcloudapp.com/NQuYblE4).

 ii. For the Completed State, the “Finish account setup” button on the Start Guide should be switched to the disabled state so that users can’t click on it anymore. This is similar to what we do now.

g. [Invite your teammates card](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=44%3A879): [[TG1]](#_msocom_1) [[KM2]](#_msocom_2) The button on this card will open the new Invite Teammates modal, which is described in full detail in point 2 below.

 i. Completed State Trigger: this card will go into the Completed State if either of the below conditions is met:

· The user has invited at least 1 user to the Organization other than themselves **OR**

· They click the “Skip” button in the Invite your teammates modal

h. [Completed state](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=47%3A1530): In the new Completed state, the “Takes about XX minutes” string gets replaced with a new string and icon that tells the user that they’ve completed this step: [see screenshot](https://share.getcloudapp.com/NQuYdoRL).

i. [Help Center link](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=44%3A888): This link should open the [“Help Center” URL](https://share.getcloudapp.com/z8urqQ5K) from Partner Setup _in a new tab_.

j. [Advocate version](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=47%3A1534):

 i. The Advocate version of the Start Guide is exactly the same as the Organizational one except the following:

· The “Finish account setup” and “Invite your teammates” cards are hidden, because they aren’t applicable to Advocates

· There is an extra string here that lets the Advocate user switch to an Organizational one: [see Figma](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=47%3A1534). This should redirect the user to the /Register page to register an organization. 

k. Branding:

 i. [See screenshot for branding colors](https://share.getcloudapp.com/xQu6vWJY)

# **Invite your teammates modal**

a. [**Invite your teammates Figma**](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=47%3A1528)

b. [**Invite your teammates Balsamiq**](https://balsamiq.cloud/su8ul/pks9l/r1F4A/b3F05)

c. This modal will allow users to invite Users (Admin or Staff) to the Organization. It is the same functionality that our [existing “Add Users” modal](https://share.getcloudapp.com/rRubENBL), just has a new design.

d. By default when this modal is opened, it should have 3 separate email fields shown as you can see in the Balsamiq and Figma.

 i. For validation when the user clicks “Send invites”, we only need to check that they’ve entered at least 1 email. If the other 2 open fields are blank, they should not receive errors about them

 ii. The user can then click “Add another teammate” to create a new row to add another.

e. Next to the “Role” label, we have an info icon: [see screenshot](https://share.getcloudapp.com/geuA0dez). Hovering on this icon will show a tooltip with the content shown in the Balsamiq.

 i. That tooltip should use the Titled version of our new tooltip design, as described in point 3 below.

f. After the user clicks “Send invites” and the invites are successfully sent and the modal closes, we’d like to show a toast message in the lower left with the following content:

 i. Invites sent successfully

g. If it doesn’t require too much effort, we also want the Completed State to be engaged immediately on the Start Guide for the “Invite your teammates” card without the user needing to manually refresh the page

h. We want this new modal to replace our existing one. So this new modal should be used when the user clicks on [“Add Users”](https://share.getcloudapp.com/YEuO8kkK) from the Users page as well.

 i. The only difference is that we don’t need the “Skip this step” button on the one on the Users page, since “Skip this step” is a button related specifically to marking one of the steps of the Start Guide as Completed.

i. Branding:

 i. [See screenshot for branding colors](https://share.getcloudapp.com/2NulA5J1)

**3.** **Implement new tooltip design globally**

a. Currently, we have a global tooltip design that looks like this: [see screenshot](https://share.getcloudapp.com/bLuqJKqv).

b. We want to update the design for this globally to the new design you see in the Figma below:

 i. [New Tooltip Design Figma](https://www.figma.com/file/oQTWwGI0fFsRAP2x8Uq5Dq/VE-Design-System-v1.0?node-id=1%3A1140)

c. Note that we have two versions of the tooltip:

 i. [Tooltip with Title](https://www.figma.com/file/oQTWwGI0fFsRAP2x8Uq5Dq/VE-Design-System-v1.0?node-id=1%3A1141)

 ii. [Tooltip without Title](https://www.figma.com/file/oQTWwGI0fFsRAP2x8Uq5Dq/VE-Design-System-v1.0?node-id=1%3A1154)

d. All tooltips in the app now don’t have titles, so when updating them all to the new design they should use the “without Title” version.

e. We’ll use Titled Tooltips in the future as defined in PRDs, such as in point 2e above.

f. Branding: [https://share.getcloudapp.com/6quYov7j](https://share.getcloudapp.com/6quYov7j) 

# **Changes to login redirect behavior and left navigation menu once all Start Guide steps are “Completed”**

a. Currently, once a user completes both steps (“Create an Experience” and “Finish Account Setup”) on the Start Guide, we change our login redirect behavior so that the user goes to My Campaigns upon login.

 i. This is done because the Start Guide is not useful or necessary for the user once they’ve completed all steps on it.

 ii. This behavior will remain with this new Start Guide, but it should also include our new “Invite your teammates” card as one of the required completion steps.

 iii. So this means that all 3 steps on the Start Guide must be completed in order for this logic to take effect

b. Additionally, once the entire Start Guide “Completed”, we want to hide it from the Left Navigation Menu: [see screenshot](https://share.getcloudapp.com/4gul5PBo).

c. So to summarize, once all 3 steps on the Start Guide are “Completed”, we should:

 i. Change the login redirect behavior so that users are taken to My Campaigns – instead of Start Guide – once they login **AND**

 ii. Hide “Start guide” from the left navigation menu

**5.** **New app navigation menu design**

a. The design for the left side Navigation Menu has been updated, see Figma:

 i. [**New Left Navigation Menu Figma**](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=44%3A826)

 ii. [**New Left Navigation Menu Balsamiq**](https://balsamiq.cloud/su8ul/pks9l/r0E71)

b. The functionality of it is the same with no logic changes, so this is purely a design update.

c. Branding:

 i. [See screenshot](https://share.getcloudapp.com/JruxX5yl)

**6.** **New sticky banner design**

a. Currently, we have this design for these sticky banners in the app: [see screenshot](https://share.getcloudapp.com/jku4J876).

b. We’d like to update the design for this to the new one you see here in the Figma:

 i. [New Sticky Banner Figma](https://www.figma.com/file/bO4CkdbpPySBl95xcYTZ5f/Start-Guide?node-id=74%3A1257)

 ii. [Sticky Banner Balsamiq](https://balsamiq.cloud/su8ul/pks9l/r1F4A/b3F05)

c. This sticky banner should display in all the same places and under the same conditions that it does now. That includes not displaying on the Start Guide page itself, just like the current behavior.

 i. The “Finish account setup” button in the banner should take the user to Account Setup

d.  Branding:

 i. [See screenshot](https://share.getcloudapp.com/qGuRwedO)[[KM3]](#_msocom_3) 

---

Updated CTA for this on the Balsamiq to say "Invite Teammates" bc it said "Set up Funding now."[https://share.getcloudapp.com/GGup0RRmhttps://share.getcloudapp.com/GGup0RRm](https://share.getcloudapp.com/GGup0RRmhttps:/share.getcloudapp.com/GGup0RRm)  [[TG1]](#_msoanchor_1)

 [[KM2]](#_msoanchor_2)Thanks!

 [[KM3]](#_msoanchor_3)Finish [[KM3]](#_msoanchor_3)