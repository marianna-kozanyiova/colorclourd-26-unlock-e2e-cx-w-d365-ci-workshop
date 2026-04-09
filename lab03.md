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
- Use your user ID as a prefix when naming the form, **{{Your user ID}}AllAppUsers**, so if your user is colorcloud01@andrasfordos.onmicrosoft.com, then you name your segment **01**AllAppUsers
- Enter a description that clearly explains the purpose of the segment, for example: Customers who are using ColorCloud app
- Add the following tag:
  - App
- Click on Done in the right bottom corner
- In the right navigation, Attributes tab, expand Telemetry : IotHUB section, select username which will be added to the segment logic builder canvas, change the is logical operator to is not and the equal to logical operator to empty
- At the top of the logic Rule 1 block click on Set relationship path and choose IotHUB_Telemetry > ERP_Product > eCommerce_Transactions > eCommerce_Users > Customer path, click on Done
- At the bottom right corner click on Save, then at the bottom left corner click on Run (in case you get a warning about Segment table being Inactive, activate / run anyway)

**Step 3. Create the ProductShippedAura segment**
- Back in the Segments overview, at the top command bar, click on **+ New** > Build your own
- Click on Edit details next to Untitled segment
- Use your user ID as a prefix when naming the form, **{{Your user ID}}ProductShippedAura**, so if your user is colorcloud01@andrasfordos.onmicrosoft.com, then you name your segment **01**ProductShippedAura
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

**Step 1. Finalize ColorCloud Aura On Its Way Version A Email**
- In CI-J, make sure you are in the Real-time journeys area
- In the left navigation, go to **Channels > Emails**
- Open the ColorCloud Aura On Its Way Version A that is a Draft state, click on drop-down next to Save in the right top corner and select Save as
- In the Quick Create: Email drawer in the right side add your user ID prefix to the Name and delete Copy from the end of the name, so if your user is colorcloud01@andrasfordos.onmicrosoft.com, then you name your email **01** ColorCloud Aura On Its Way Version A, click on Save and Close in the right bottom corner
- Go back to **Channels > Emails** and open the email **{{Your user ID}}** ColorCloud Aura On Its Way Version A you just created
- Click on the drop-down arrows in the email header next to From: and Subject:, place your cursor in the Subject field right before the word your and click on personalization (person with lighting bolt icon) in the right side of the Subject field > + New dynamic text > Choose an attribute > Audience > CustomerProfile > firstname > Save, {{firstname}} should be added right before the word your (this value will be replaced with actual First name value from Customer profile that will be receiving this email)
- In the body of the email, select Get set up in minutes Text, in the icon menu on the right side click on Personalize (person with lighting bolt icon), expand Inline conditions > + Add condition > define Display name as NotAppUser > Update condition to be Make condition on segment membership > Change Is in segment to Is not in segment > Look for your **{{Your user ID}}AllAppUsers** CI-D segment > Save & copy
- Optional: You can check the email elements in the same way you've done in Lab 2, checking the Brand profile, Personalize (should be set to CustomerProfile this time since we are targeting CI-D segment with Customer profile members), Settings (Compliance check where Purpose is Commercial) and Footer content block (should include Unsubscribe since Purpose of the email is Commercial)
- In the right top corner click on Save, once saved, click on Ready to send and make sure that your email is moved to Live state

**Step 2. Verify rest of the Emails**
- Go back to **Channels > Emails**, open the ColorCloud Aura On Its Way Version B email and check that the Subject is not personalized, this is the Version B of the email you just created, but without personalization
- Go back to **Channels > Emails**, open the ColorCloud Aura Accessories, this email will be sent to customers who clicked the Download app link from **{{Your user ID}} ColorCloud Aura On Its Way Version A** email you created if the systems sees that the customer is interacting the most with email which will be determined in the journey via Email channel optimization

**Step 3. Create ColorCloud Aura On Its Way Text message**
- In CI-J, make sure you are in the Real-time journeys area
- In the left navigation, go to **Channels > Text messages**
- In the top command bar click on **+ New**
- Name the Text message **{{Your user ID}} ColorCloud Aura On Its Way** using your user ID prefix same as for the form, emails, journeys and segments elements in the previous labs, exercises and steps
- Choose +15074835080 as Text message sender
- Enter Hi , your ColorCloud Aura 🌈 is on its way 🚚! 📲 Download the app to get started: https://colorcloud.rocks/ Unsubscribe: under Message, then place your cursor right before the comma > Personalization icon > + New dynamic text > Choose an attribute > Audience > CustomerProfile > firstname > Save, {{firstname}} should be added right before the comma, then place your cursor after Unsubscribe:  > Personalization icon > + New dynamic text > Choose an attribute > Compliance > Preference center > Save, {{Preferencecenter}} should be added after Unsubscribe
- Choose ColorCloud Commercial DOI Compliance profile and Commercial Purpose
- In the right top corner click on Save, once saved, click on Ready to send

**Step 4. Verify rest of the Text messages**
- Go back to **Channels > Text message**, open the ColorCloud Aura On Its Way App Users text message, this is the text message that will be sent to customers who are already users of the app
- Go back to **Channels > Text message**, open the ColorCloud Aura Accessories text message, this is the text message that will be sent to customers who are not app users yet and have clicked the Download the app link in the **{{Your user ID}} ColorCloud Aura On Its Way Version A** email

**Expected outcome**

You have finalized **{{Your user ID}} ColorCloud Aura On Its Way Version A** email and verified the rest of the emails to be used in the onboarding & upsell journey. You have created **{{Your user ID}} ColorCloud Aura On Its Way** text message and verified rest of the emails to be used in the onboarding & upsell journey.


# Exercise 3: Build the segment-based post-purchase onboarding and upsell journey
In this exercise, you will create the main segment-based journey that orchestrates onboarding and upsell after Maya’s purchase.

**Step 1. Create a new segment-based journey**
- In CI-J, stay in the Real-time journeys area
- In the left navigation, go to **Journeys**
- In the top command bar select **+ New journey**, in pop up window click on Skip and create from blank in the right bottom corner
- Name the Journey **{{Your user ID}} ColorCloud Aura Onboarding & Accessory Upsell** using your user ID prefix same as for the rets of the elements you were creating
- Choose Segment-based, choose **{{Your user ID}}ProductShippedAura** under Select segments, choose A one-time journey where newly added audience members can start any time under Select the frequency, set the right Time zone and Start, then click on Create in the right bottom corner

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-segment-based-journey?source=recommendations) to learn more about Segment-based journeys

**Step 2. Add A/B test for onboarding email**
- In the journey canvas, click on plus sign, under AI powered actions click on A/B test (Text messages or channels against each other), Version A should be Email and Version B should be Email, click on Create test
- Set up the A/B test under the A/B test section on the right side
    - Under Versions, select **{{Your user ID}} ColorCloud Aura On Its Way Version A** for Version A and ColorCloud Aura On Its Way Version B for Version B (if you get thrown out of the A/B test section, you can always go back by click on the A/B test tile in the journey canvas and you can also choose the emails by clickong on the respective email tiles in the journey canvas)
    - Under Test completion, Winning metric select Open rate
    - Keep the rest of the settings as is, if you want to learn more about A/B test, you can check the [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-ab-tests-in-marketing-journeys) as there are some recommendations on the audience size in order for the test to run smoothly

**Step 3. Add branching based on the “Download the app” link click**
- After the A/B test path, click on the plus sign Add an action in the journey canvas, under Conditions, add Wait for trigger (Response to an audience action or update)
- Set up the branch under the If/then branch section on the right side
    - Select Previous message gets an interaction for Choose a branch condition type
    - Under both Versions A and B, Select trigger Email Link Clicked and choose download-colorcloud-app-for-iosor-android link
    - Under Time limit set 7 days

**Step 6. Set up Email Link Clicked No path of the journey**
- After the If/then branch, click on the plus sign Add an action on the No path, under Conditions, add Attribute branch (Branch based on specific value)
- Enter AllAppUsers as Dsiplay name
- Under Branches click on Branch 1 If Add conditions > Marke condition on segment membership > Is in segment > **{{Your user ID}}AllAppUsers**
- In the journey canvas under Branch 1, click on the plus sign Add an action, under Messages, add Text message (Send a text message (SMS)), choose ColorCloud Aura On Its Way App Users text message (this message only informs the customers who are already using the app that the product was shipped)
- In the journey canvas under Other, click on the plus sign Add an action, under Messages, add Text message (Send a text message (SMS)), choose **{{Your user ID}} ColorCloud Aura On Its Way** text message (this message informs the customers who are not app users yet that the product was shipped and prompts them to download the app)

**Step 7. Set up Email Link Clicked Yes path of the journey incl. AI channel optimization**
- After the If/then branch, click on the plus sign Add an action on the Yes path, under AI powered actions, add Channel optimization (Use AI to select the best channel for each person)
- Choose Email and Text message, click on Optimize
- Under the Channel optimization section on the right side, set up Journey goal > select Send a general notification under The goal of this journey is > select A person clicked on at least one link under This goal is met when > under The number of people needed is enter 1000 and select # (Number of customers to meet the goal) instead of the % (Percent of total customers)
- In the journey canvas click on the Channel optimization tile, scroll down to Default channel and select Email
- In the journey canvas click on the Email tile under Channel optimization and choose ColorCloud Aura Accessories email
- In the journey canvas click on the Text message tile under Channel optimization and choose ColorCloud Aura Accessories text message

**Step 8. Save & publish the journey**
- In the right top corner click on Save, once saved, click on Publish
- Wait until the journey is Live

**Expected outcome**

You have created and published **{{Your user ID}} ColorCloud Aura Onboarding & Accessory Upsell**. The journey starts from the **{{Your user ID}}ProductShippedAura** segment, tests two onboarding email variants, branches on the **Download the app** link click, uses channel optimization for engaged customers to drive accessory upsell and sends a text message reminder to non-clickers depending on their **{{Your user ID}}AllAppUsers** segment membership.


# Lab Summary
In this lab, you extended Maya Novak’s ColorCloud journey beyond the first purchase. You created two CI-D segments to identify shipped-product customers and app users, updated the onboarding email with personalization and conditional content, prepared email and SMS assets, and built a segment-based journey in CI-J.

Consider where this journey fits in Maya Novak’s experience:
- Maya has already subscribed and completed her first purchase
- Her ColorCloud Aura product is shipped
- She enters the onboarding journey through the **ProductShippedAura** segment
- She receives an onboarding email that is part of an A/B test
- Her next step depends on whether she clicked the **Download the app** link
- She can then continue into a more optimized onboarding and upsell experience across email and SMS

You are now ready to continue with the next step of Maya’s experience in [Lab 4: Build Segment-based First Use Feedback Journey](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/blob/main/lab04.md).
