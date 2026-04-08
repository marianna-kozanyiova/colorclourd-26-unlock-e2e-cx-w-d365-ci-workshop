# Lab 3: Build Segment-based Post-Purchase Onboarding & Upsell Journey

# Lab Overview
## Introduction
In this lab, you will continue Maya Novak’s ColorCloud journey after her first purchase. You will start in Customer Insights - Data (CI-D), where you will create two customer segments that will later be used for targeting and personalization. Then you will switch to Customer Insights - Journeys (CI-J) to prepare the onboarding and upsell assets across email and text message channels and orchestrate them in a segment-based journey.

This lab introduces a more advanced journey pattern: an A/B test for personalized subject lines, branching based on customer behavior, and channel optimization for follow-up communication. If Maya clicks the **Download the app** link in the onboarding email, she will continue to the next step through channel optimization. If she does not click it, she will receive a reminder by text message instead.

## Objectives
By the end of this lab, you will be able to:
- Create segments in Customer Insights - Data
- Update and publish an email in Customer Insights - Journeys
- Review and reuse preconfigured live marketing assets
- Create a text message in Customer Insights - Journeys
- Build a segment-based journey with A/B testing, branching, and channel optimization


# Exercise 1: Build post-purchase segments in Customer Insights - Data
In this exercise, you will work in Customer Insights - Data to create two segments that represent key moments in Maya’s post-purchase experience. One segment identifies customers whose ColorCloud Aura product has been shipped and who should receive onboarding communication. The second segment identifies customers who already use the ColorCloud app.

**Step 1. Open Customer Insights - Data**
- Open the browser tab where you have Customer Insights - Data available from Lab 1
- If needed, use the Customer Insights connector in CI-J Settings to open the CI-D environment again

**Step 2. Go to Segments**
- In the left navigation of Customer Insights - Data, go to **Customers > Segments**

**Step 3. Create the first segment**
- Click **+ New segment**
- Choose to create the segment from scratch
- Name the segment **ProductShippedAura**
- In the **Description** field, enter a description that clearly explains that this segment is intended for customers whose **ColorCloud Aura** product has been shipped and who should receive onboarding communication
- Add the following Tags:
    - **Aura**
    - **Onboarding**

**Step 4. Define the segment logic for shipped Aura customers**
- Build the segment so that it identifies customers whose purchased product is **ColorCloud Aura** and whose order or shipment status indicates that the product has been shipped
- Use the available unified customer profile attributes and related transactional data in your environment to define the logic
- Review the segment conditions to ensure the audience reflects customers ready for post-purchase onboarding

**Step 5. Save and refresh the segment**
- Click **Save**
- Run or refresh the segment so that the membership is calculated
- Wait until the segment status indicates that it is ready to use

**Step 6. Create the second segment**
- Return to the Segments area and click **+ New segment** again
- Name the segment **AllAppUsers**
- In the **Description** field, enter a description that clearly explains that this segment is intended for customers who are already using the ColorCloud mobile app
- Add the following Tag:
    - **App**

**Step 7. Define the segment logic for app users**
- Build the segment so that it identifies customers who have already used, registered, or activated the ColorCloud app based on the available app or telemetry-related data in your environment
- Review the logic to ensure this segment can later be used for branching, exclusion, or insight purposes

**Step 8. Save and refresh the segment**
- Click **Save**
- Run or refresh the segment so that the membership is calculated
- Wait until the segment status indicates that it is ready to use

**Expected outcome**

You have created two CI-D segments:
- **ProductShippedAura**, tagged with **Aura** and **Onboarding**
- **AllAppUsers**, tagged with **App**

These segments are now available for use in Customer Insights - Journeys.


# Exercise 2: Update and publish the onboarding email
In this exercise, you will switch to Customer Insights - Journeys and update the onboarding email that will be used in the post-purchase journey. You will personalize the subject line with the recipient’s first name and add inline conditional content to the email body.

**Step 1. Return to Customer Insights - Journeys**
- Go back to the browser tab where Customer Insights - Journeys is open
- Make sure you are in the **Real-time journeys** area

**Step 2. Go to Emails**
- In the left navigation, go to **Channels > Emails**

**Step 3. Open the onboarding email**
- Locate and open the email named **ColorCloud Aura On Its Way Version A**

**Step 4. Add first name personalization to the subject**
- In the email header, update the **Subject** so that it includes the recipient’s first name personalization token
- Use the **Personalize** option in the right-side menu to insert the **First Name** value from the Contact record
- Review the subject to confirm it now contains both the original message and the recipient’s first name

**Step 5. Add inline condition to the email body**
- In the email body, locate the text element that contains the heading or message **Get set up in minutes**
- Configure an inline condition for this text element so that its content can be shown conditionally based on the intended workshop logic
- Review the condition setup and confirm that the element is now using conditional content

**Step 6. Save and publish the email**
- Click **Save** in the right top corner
- Then click **Ready to send**
- Wait until the email status confirms that it is live and ready to use in a journey

**Expected outcome**

You have updated **ColorCloud Aura On Its Way Version A** by adding first name personalization to the subject and inline conditional content to the **Get set up in minutes** text element. The email is now published and ready to use.


# Exercise 3: Review the preconfigured live email assets
In this exercise, you will confirm that the remaining email assets required for the journey are already available and live.

**Step 1. Verify onboarding email Version B**
- In **Channels > Emails**, locate **ColorCloud Aura On Its Way Version B**
- Open the record and verify that its status is live or ready to send
- Review the subject and content so you understand how it differs from Version A for the A/B test

**Step 2. Verify accessories email**
- In **Channels > Emails**, locate **ColorCloud Aura Accessories**
- Open the record and verify that its status is live or ready to send
- Review the content and confirm that it is intended for accessory upsell communication

**Expected outcome**

You have verified that the following email assets are available and live:
- **ColorCloud Aura On Its Way Version B**
- **ColorCloud Aura Accessories**

These assets are ready to be used in the segment-based journey.


# Exercise 4: Create and review the text message assets
In this exercise, you will prepare the text message assets used in the journey. You will create the onboarding reminder text message and verify that the accessory upsell text message is already live.

**Step 1. Go to Text messages**
- In Customer Insights - Journeys, go to **Channels > Text messages**

**Step 2. Create a new text message**
- Click **+ New text message**
- Create a new message named **ColorCloud Aura On Its Way**

**Step 3. Configure the text message details**
- Confirm that the correct **SMS provider** is selected
- Set the **Compliance profile** and **Purpose** appropriate for the message based on your workshop setup
- Write the text message so that it reminds the customer to download the ColorCloud app and get started with their new ColorCloud Aura product
- If relevant, include a shortened or workshop-provided link to the app download experience

**Step 4. Save and publish the text message**
- Click **Save**
- Then publish the text message so that it is available for journey use
- Wait until the text message status indicates that it is live

**Step 5. Verify the existing accessories text message**
- Stay in **Channels > Text messages**
- Locate **ColorCloud Aura Accessories**
- Open the record and verify that it is already live
- Review the content so you understand how it supports the upsell step of the journey

**Expected outcome**

You have created and published **ColorCloud Aura On Its Way** text message and verified that **ColorCloud Aura Accessories** text message is already live.


# Exercise 5: Build the segment-based onboarding and upsell journey
In this exercise, you will build the full segment-based journey in Customer Insights - Journeys. The journey starts with customers from the **ProductShippedAura** segment, tests two onboarding email subject lines, checks whether the customer clicked the **Download the app** link, and then continues with either a text reminder or a channel-optimized follow-up.

**Step 1. Go to Journeys**
- In Customer Insights - Journeys, go to **Engagement > Journeys**

**Step 2. Create a new segment-based journey**
- Click **+ New journey**
- In the Create new journey pop up window click on **Skip and create from blank** in the right bottom corner
- Name the journey **ColorCloud Aura Post-Purchase Onboarding & Upsell**
- Choose **Segment-based**
- Under the audience configuration, select the **ProductShippedAura** segment as the entry audience
- Click **Create**

**Step 3. Configure journey entry settings**
- In the right-side configuration menu, open **Entry**
- Set the journey to start according to your workshop timing preferences
- Confirm the correct **Time zone**
- Review repeat settings and leave them configured so the journey behaves appropriately for post-purchase onboarding

**Step 4. Add an A/B test for the onboarding email**
- On the journey canvas, add an **A/B test** step after the audience entry
- Configure the A/B test to compare:
    - **ColorCloud Aura On Its Way Version A**
    - **ColorCloud Aura On Its Way Version B**
- Review the A/B test settings and confirm the split is appropriate for the workshop scenario
- Save your changes

**Step 5. Add the onboarding email path**
- Make sure both A/B branches send the respective onboarding email versions
- Review the journey canvas to confirm the A/B test is correctly wired and both paths continue into the next decision step

**Step 6. Add branching based on link click behavior**
- After the onboarding email step, add a **branch** that evaluates whether the recipient clicked the **Download the app** link in the onboarding email
- Configure the **Yes** branch for customers who clicked the link
- Configure the **No** branch for customers who did not click the link

**Step 7. Configure the Yes branch with channel optimization**
- On the **Yes** branch, add a **Channel optimization** step
- Configure the step so that the system selects the best available channel for the follow-up communication in your environment
- Use the appropriate upsell asset so that the next message promotes relevant ColorCloud Aura accessories
- Review the settings and save the step

**Step 8. Configure the No branch with text reminder**
- On the **No** branch, add a **Text message** step
- Select **ColorCloud Aura On Its Way** as the message to send
- This branch should act as a reminder for customers who did not click the app download link in the onboarding email
- Save the step

**Step 9. Continue the journey with upsell communication**
- After the reminder or channel-optimized step, continue the journey so that recipients can receive the upsell communication for accessories using the available ColorCloud Aura assets
- Review the overall sequence to ensure the onboarding and upsell logic is connected correctly

**Step 10. Review and publish the journey**
- Review the complete journey canvas and confirm that it includes:
    - Segment-based audience entry using **ProductShippedAura**
    - An A/B test for onboarding email subject personalization
    - Branching based on **Download the app** link click behavior
    - A **Channel optimization** path for engaged customers
    - A **Text message** reminder path for customers who did not click
- Click **Publish** in the right top corner
- Wait until the journey is published successfully

**Expected outcome**

You have created and published a segment-based journey named **ColorCloud Aura Post-Purchase Onboarding & Upsell**. The journey starts with customers from the **ProductShippedAura** segment, tests two onboarding email versions, responds to customer engagement based on the **Download the app** link click, and continues with the appropriate follow-up and upsell communication.


# Lab Summary
In this lab, you moved Maya Novak’s ColorCloud experience from acquisition to post-purchase engagement. You created CI-D segments to identify shipped Aura customers and existing app users, updated the onboarding email, prepared text message assets, and orchestrated a richer segment-based journey in CI-J.

Consider where this journey fits in Maya Novak’s experience:
- Maya has already subscribed and made her first purchase
- Her **ColorCloud Aura** product is shipped, placing her into **ProductShippedAura** segment
- She receives an onboarding email through **ColorCloud Aura Post-Purchase Onboarding & Upsell** journey
- If she clicks **Download the app**, the journey continues through channel optimization toward the next best follow-up
- If she does not click the link, she receives **ColorCloud Aura On Its Way** text message reminder
- She then continues toward accessory upsell communication using the prepared ColorCloud Aura assets

You are now ready to continue with the next step of Maya’s experience in [Lab 4: Build Segment-based First Use Feedback Journey](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/blob/main/lab04.md).
