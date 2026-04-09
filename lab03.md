# Lab 3: Build Segment-based Post-Purchase Onboarding & Upsell Journey

# Lab Overview
## Introduction
In this lab, you will continue Maya Novak’s ColorCloud experience after her first purchase. You will begin in CI-D, where you will create two segments that identify customers whose ColorCloud Aura product has been shipped and customers who already use the ColorCloud mobile app. You will then switch to CI-J, where you will prepare the required email and text message assets and build a segment-based journey for post-purchase onboarding and upsell.

This journey is designed to support customers after purchase in a more personalized way. Customers whose product has been shipped will first receive an onboarding email which will include an inline condition for Download app section to be dsiplayed if the customer is not an app user yet. The journey will test two subject line variants of this email through an A/B test. It will then branch based on whether the customer clicked the **Download the app** link in the onboarding email or not. Customers who clicked the link will continue into channel optimization for accessory upsell, while customers who did not click the link will be branched out further based on being an app user or not to receive relevant text message reminder.

## Objectives
By the end of this lab, you will be able to:
- Create CI-D segments for CI-J journeys
- Update an email with personalization and inline conditions
- Create a text message
- Build a segment-based cross-channel journey with an A/B test, branching logic and channel optimization


# Exercise 1: Build the CI-D segments
In this exercise, you will work in CI-D to create the customer segments needed for the post-purchase onboarding and upsell journey.

**Step 1. Open Customer Insights - Data**
- Open the CI-D environment you verified in Lab 1
- In the left navigation, go to Insights > **Segments**

**Step 2. Create the AllAppUsers segment**
- At the top command bar, click on **+ New** > Build your own
- Click on Edit details next to Untitled segment
- Use your user ID as a prefix when naming the form, **{{Your user ID}}AllAppUsers**, so if your user is colorcloud01@andrasfordos.onmicrosoft.com, then you name your form **01**AllAppUsers
- Enter a description that clearly explains the purpose of the segment, for example: Customers who are using ColorCloud app
- Add the following tag:
  - App
- Click on Done in the right bottom corner
- In the right navigation, Attributes tab, expand Telemetry : IotHUB section, select username which will be added to the segment logic builder canvas, change the is logical operator to is not and the equal to logical operator to empty
- At the top of the logic Rule 1 block click on Set relationship path and choose IotHUB_Telemetry > ERP_Product > eCommerce_Transactions > eCommerce_Users > Customer path, click on Done
- At the bottom right corner click on Save, then at the bottom left corner click on Run

**Step 3. Create the ProductShippedAura segment**
- Back in the Segments overview, at the top command bar, click on **+ New** > Build your own
- Click on Edit details next to Untitled segment
- Use your user ID as a prefix when naming the form, **{{Your user ID}}ProductShippedAura**, so if your user is colorcloud01@andrasfordos.onmicrosoft.com, then you name your form **01**ProductShippedAura
- Enter a description that clearly explains the purpose of the segment, for example: Customers whose ColorCloud Aura product has been shipped in the past 30 days
- Add the following tags:
  - Aura
  - Onboarding
- Click on Done in the right bottom corner
- In the right navigation, Attributes tab, expand Product : ERP section, select category which will be added to the segment logic builder canvas, enter Device after equal to and check Ignore case (Hint: you can always check Data > Tables in case you are unsure about which attributes are available from which data sources)
- In the right navigation, Attributes tab, expand Product : ERP section, select name > Add item to > Existing rule > Rule 1 which will be added to the segment logic builder canvas, change the is logical operator to contains, enter Aura after contains and check Ignore case
- In the right navigation, Attributes tab, expand Transactionas : eCommerce section, select Status > Add item to > Existing rule > Rule 1 which will be added to the segment logic builder canvas, enter Shipped after equal to and check Ignore case
- In the right navigation, Attributes tab, expand Transactionas : eCommerce section, select ShippedDate > Add item to > Existing rule > Rule 1 which will be added to the segment logic builder canvas, change the specific date logical operator to within last, enter 30 after within last
- At the top of the logic Rule 1 block click on Set relationship path and choose ERP_Product > eCommerce_Transactions > eCommerce_Users > Customer path, click on Done
- At the bottom right corner click on Save, then at the bottom left corner click on Run

**Step 4. Verify the Status of AllAppUsers and ProductShippedAura segments**
- Back in the Segments overview, make sure that both of your segments have Status Queued or Refreshing or Successful; if successful, verify that you see number of Members for each segment (when you click on a segment you will be able to see Segment members preview at the bottom showing you a preview of Customer profiles that fulfill the segment conditions and are therefore, included)

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/segment-builder-aspects) to learn more about Segments in CI-D

**Step 5. Check CI-D segments availability in CI-J**
- Open the CI-J environment you verified in Lab 1 and used in Lab 2
- In the CI-J app, under Real-time journeys area, Audience section in the left side navigation, click on Segments and verify that you see your Segments under the All Segments view where the Source is Customer Insights - Data

**Expected outcome**

You have created CI-D segments named **{{Your user ID}}ProductShippedAura** of customers whose ColorCloud Aura product has been shipped and **{{Your user ID}}AllAppUsers** of customers who already use the ColorCloud app as well as verified that the segments are available in CI-J.


# Exercise 2: Finalize the CI-J Email and Text messages
In this exercise, you will continue in CI-J to finalize the email and text messages for the onboarding & upsell journey.

**Step 1. Go to Emails**
- In Customer Insights - Journeys, make sure you are in the Real-time journeys area
- In the left navigation, go to **Assets > Emails**

**Step 2. Open ColorCloud Aura On Its Way Version A**
- Locate and open the email named **ColorCloud Aura On Its Way Version A**
- Confirm that the email is based on the ColorCloud branded template structure

**Step 3. Add first name personalization to the subject line**
- Expand the email header
- Update the subject so it includes first name personalization
- Use the personalization panel to insert **First Name** from the contact record into the subject line
- Ensure the subject remains appropriate for a post-purchase onboarding email

**Step 4. Add an inline condition to the “Get set up in minutes” text element**
- In the email body, locate the text element that includes the **Get set up in minutes** content
- Add an inline condition to this text element
- Configure the condition so the content can be shown or adjusted based on whether the recipient is already an app user or not, using the audiences available to you in the environment
- Review the logic and confirm the conditional content supports the onboarding scenario

**Step 5. Save and publish the email**
- Select **Save**
- Run **Check content** if required
- Resolve any issues that prevent publishing
- Select **Ready to send**
- Wait until the email is live

**Expected outcome**

You have updated and published **ColorCloud Aura On Its Way Version A**. The email now includes first name personalization in the subject line and conditional onboarding content in the body.


# Exercise 3: Verify the remaining email assets
In this exercise, you will confirm that the additional email assets needed for the journey are already available and live.

**Step 1. Verify ColorCloud Aura On Its Way Version B**
- In **Assets > Emails**, locate **ColorCloud Aura On Its Way Version B**
- Open or preview the record if needed
- Confirm that the email status is live or ready to send

**Step 2. Verify ColorCloud Aura Accessories**
- In **Assets > Emails**, locate **ColorCloud Aura Accessories**
- Open or preview the record if needed
- Confirm that the email status is live or ready to send

**Expected outcome**

You have confirmed that **ColorCloud Aura On Its Way Version B** and **ColorCloud Aura Accessories** are already available as live email assets for reuse in the journey.


# Exercise 4: Create and verify text messages
In this exercise, you will prepare the SMS assets needed for the journey.

**Step 1. Go to Text messages**
- In Customer Insights - Journeys, stay in the Real-time journeys area
- In the left navigation, go to **Channels > Text messages**

**Step 2. Create ColorCloud Aura On Its Way text message**
- Select **+ New**
- Create a new text message named **ColorCloud Aura On Its Way**
- Use the configured ColorCloud SMS provider
- Add message copy that supports the onboarding scenario, for example by reminding the customer to get started with ColorCloud Aura and download or use the app
- Include any required compliance and personalization settings appropriate for the scenario
- Save the text message
- Publish or make the text message live so it can be used in the journey

**Step 3. Verify ColorCloud Aura Accessories text message**
- In the list of text messages, locate **ColorCloud Aura Accessories**
- Open or preview the record if needed
- Confirm that the text message status is live and ready for use

**Expected outcome**

You have created and published **ColorCloud Aura On Its Way** and confirmed that **ColorCloud Aura Accessories** is already live.


# Exercise 5: Build the segment-based post-purchase onboarding and upsell journey
In this exercise, you will create the main segment-based journey that orchestrates onboarding and upsell after Maya’s purchase.

**Step 1. Go to Journeys**
- In Customer Insights - Journeys, stay in the Real-time journeys area
- In the left navigation, go to **Journeys**

**Step 2. Create a new segment-based journey**
- Select **+ New journey**
- Choose to create the journey from blank
- Select **Segment-based** as the journey type
- Name the journey **ColorCloud Post-Purchase Onboarding & Upsell Journey**

**Step 3. Select the entry audience**
- For the journey audience, select the CI-D segment **ProductShippedAura**
- Review the audience configuration and confirm that the journey targets customers whose ColorCloud Aura product has been shipped

**Step 4. Add the A/B test for the onboarding email**
- In the journey canvas, add an **A/B test** step after the audience entry
- Configure the A/B test to compare two email subject line variants using the two onboarding emails:
  - **ColorCloud Aura On Its Way Version A**
  - **ColorCloud Aura On Its Way Version B**
- Configure the split and winner settings according to the workshop guidance or default settings available in the environment
- Confirm that the A/B test is intended to evaluate subject line personalization performance

**Step 5. Add branching based on the “Download the app” link click**
- After the onboarding email path, add a condition or branch based on customer interaction
- Configure the condition so the journey checks whether the recipient clicked the **Download the app** link in the onboarding email
- Create two branches:
  - **Clicked**
  - **Did not click**

**Step 6. Configure the clicked branch with channel optimization**
- On the **Clicked** branch, add a **Channel optimization** step
- Configure the step according to the options available in your environment so the journey can continue through the optimized channel path for engaged recipients
- Review the setup and confirm this branch is intended for customers who showed interest in app onboarding

**Step 7. Configure the non-clicked branch with a text message**
- On the **Did not click** branch, add a **Text message** step
- Select **ColorCloud Aura On Its Way**
- Confirm that this branch provides a follow-up reminder for customers who did not engage with the app download call to action in the email

**Step 8. Add the upsell follow-up assets**
- Continue the journey design using the preconfigured upsell assets where appropriate
- Use **ColorCloud Aura Accessories** email and/or **ColorCloud Aura Accessories** text message according to the workshop design so the journey supports a relevant accessory upsell after onboarding
- Review the overall flow and confirm it combines onboarding and upsell touchpoints in a single post-purchase experience

**Step 9. Review the journey logic**
- Confirm that the journey includes:
  - Entry audience based on **ProductShippedAura**
  - An A/B test using **ColorCloud Aura On Its Way Version A** and **ColorCloud Aura On Its Way Version B**
  - A branch based on whether the **Download the app** link was clicked
  - A **Channel optimization** path for recipients who clicked
  - A **ColorCloud Aura On Its Way** text message for recipients who did not click
  - The reuse of prebuilt accessory upsell content

**Step 10. Publish the journey**
- Select **Go live** or **Publish**
- Wait until the journey is live

**Expected outcome**

You have created and published **ColorCloud Post-Purchase Onboarding & Upsell Journey**. The journey starts from the **ProductShippedAura** segment, tests two onboarding email variants, branches on the **Download the app** link click, uses channel optimization for engaged customers, sends a text message reminder to non-clickers, and supports follow-up accessory upsell communication.


# Lab Summary
In this lab, you extended Maya Novak’s ColorCloud journey beyond the first purchase. You created two CI-D segments to identify shipped-product customers and app users, updated the onboarding email with personalization and conditional content, prepared SMS assets, and built a segment-based real-time journey in CI-J.

Consider where this journey fits in Maya Novak’s experience:
- Maya has already subscribed and completed her first purchase
- Her ColorCloud Aura product is shipped
- She enters the onboarding journey through the **ProductShippedAura** segment
- She receives an onboarding email that is part of an A/B test
- Her next step depends on whether she clicked the **Download the app** link
- She can then continue into a more optimized onboarding and upsell experience across email and SMS

You are now ready to continue with the next step of Maya’s experience in **Lab 4: Build Segment-based First Use Feedback Journey**.
