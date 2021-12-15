# Organization user
 ##  How to register an org user
 
 1. Go to the start [page](https://go.rallyupqa.com/start)
 2. Fill all fields and go to the next step
 3. Select country
 4. Select other options
 5. Complete the registation
 6. After registration org user should be redirected to /org page (Start guide)

[[16373 Start Guide Redesign]]
 
 ## How to approve organization
 On the /org page (Start guide) you'll find "Finish account setup section". This section will redirect to account setup process.
 
 [[14205 New Organization Verification Process with Stripe Identity and GuideStar]]
 
 ## USA/non-USA
 - USA organizations are able to register 501(c), non-501(c)
 - Australian organizations can not create raffles
 - UK organizations can add gift aid to campaign
 - Canadian organizations have canadian tax receipt
 
 ## 501(c), non-501(c)
For organizations from America, it is possible to create a 501 (c) or non-501(c) organization. A 501 (c) allows you to create a Raffle
 
 ## Managed Funds, direct funds
 ### Direct funds
 User adds personal Stripe account for payments
 
 ### Managed funds
Do Charity is a separate non-profit 501c organization that RallyUp created to simplify the administrative process of payouts to organizations. Do Charity operates similarly to Deferred Funding in that it is our option for people to have _RallyUp_ collect the funds in our Stripe account and then pay out to the organization later when their Campaign ends.

The key difference is that a separate organization – Do Charity – will be the one issuing the payouts and tax receipts for donations, not RallyUp. The funds raised from Campaigns on Do Charity will also go to a separate (new) Stripe account from our current Deferred Funding one.

Since the process for users within the app is so similar to Deferred Funding (i.e., users still need to submit a fund request for their campaign and wait for us to pay it out to them), the main task within this user story for Do Charity is to implement the new naming in strings throughout the app, handle migration for customers currently on Deferred Funding, and link up the new Do Charity Stripe account to the system.

[[14205 New Organization Verification Process with Stripe Identity and GuideStar]]
 
 ## Add staff and admins
- The organization user can invite campaign staff and administators. This can be done on the **left-side menu -> Users page **

- The user can also add an administrator for a specific campaign. To add campaign administrator go to **campaign setup -> Advanced options -> Experience options**
 
 ## Banned States for Raffle creation
-  Alabama
-  California
-  Hawaii
-  Kansas
-  Utah

https://rallyup.tpondemand.com/restui/board.aspx?#page=userstory/10111

