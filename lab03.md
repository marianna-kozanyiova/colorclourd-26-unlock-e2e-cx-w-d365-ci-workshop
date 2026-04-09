# Lab 3: Build Segment-based Post-Purchase Onboarding & Upsell Journey

# Lab Overview
## Introduction
In this lab, you will continue Maya Novak’s ColorCloud experience after her first purchase. You will begin in Dynamics 365 Customer Insights - Data (CI-D), where you will create two segments that identify customers whose ColorCloud Aura product has been shipped and customers who already use the ColorCloud mobile app. You will then switch to Dynamics 365 Customer Insights - Journeys (CI-J), where you will prepare the required email and text message assets and build a segment-based journey for post-purchase onboarding and upsell.

This journey is designed to support customers after purchase in a more personalized way. Customers whose product has been shipped will first receive an onboarding email which will include an inline condition for Download app section to be dsiplayed if the customer is not an app user yet. The journey will test two subject line variants of this email through an A/B test. It will then branch based on whether the customer clicked the **Download the app** link in the onboarding email or not. Customers who clicked the link will continue into channel optimization for accessory upsell, while customers who did not click the link will be branched out further based being app user or not to receive relevant text message reminder.

## Objectives
By the end of this lab, you will be able to:
- Create CI-D segments for shipped ColorCloud Aura customers and mobile app users
- Update and publish an onboarding email in CI-J
- Create a new onboarding text message in CI-J
- Verify preconfigured email and text message assets that will be reused in the journey
- Build a segment-based journey with an A/B test
- Add branching logic based on a link click
- Use channel optimization and text messaging within the same journey


# Exercise 1: Build onboarding segments in Customer Insights - Data
In this exercise, you will work in Customer Insights - Data to create the audience segments needed for the post-purchase onboarding and upsell journey.

**Step 1. Open Customer Insights - Data**
- Open the Customer Insights - Data environment you verified in Lab 1
- In the left navigation, go to **Segments**

**Step 2. Create the ProductShippedAura segment**
- Select **+ New segment**
- Create a new segment named **ProductShippedAura**
- Enter a description that clearly explains the purpose of the segment, for example:
  - **Customers whose ColorCloud Aura product has been shipped and who should enter the onboarding journey**
- Add the following tags:
  - **Aura**
  - **Onboarding**

**Step 3. Define the ProductShippedAura logic**
- Build the segment so it identifies customers associated with shipped ColorCloud Aura products
- Use the available customer, transaction, order, shipment, or product-related data in your CI-D environment to isolate customers whose purchased product is **ColorCloud Aura** and whose order or shipment status indicates that the product has been shipped
- Review the segment logic and confirm that it represents the intended post-purchase onboarding audience

**Step 4. Save and refresh the ProductShippedAura segment**
- Select **Save**
- Run or refresh the segment so it starts processing
- Wait until the segment reaches a successful status

**Expected outcome**

You have created a CI-D segment named **ProductShippedAura** with a description and the tags **Aura** and **Onboarding**. The segment identifies customers whose ColorCloud Aura product has been shipped.


**Step 5. Create the AllAppUsers segment**
- Still in **Segments**, select **+ New segment**
- Create a new segment named **AllAppUsers**
- Enter a description that clearly explains the purpose of the segment, for example:
  - **Customers who already use the ColorCloud mobile app**
- Add the following tag:
  - **App**

**Step 6. Define the AllAppUsers logic**
- Build the segment so it identifies customers who are already app users
- Use the available app, registration, telemetry, or product activation data in your CI-D environment to isolate customers who have already used or registered in the ColorCloud app
- Review the segment logic and confirm that it represents the intended app-user audience

**Step 7. Save and refresh the AllAppUsers segment**
- Select **Save**
- Run or refresh the segment so it starts processing
- Wait until the segment reaches a successful status

**Expected outcome**

You have created a CI-D segment named **AllAppUsers** with a description and the tag **App**. The segment identifies customers who already use the ColorCloud mobile app.


# Exercise 2: Update the onboarding email in Customer Insights - Journeys
In this exercise, you will switch to Customer Insights - Journeys and update the main onboarding email that will be used in the journey A/B test.

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
