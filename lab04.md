# Lab 4: Build Segment-based First Use Feedback Journey

# Lab Overview
## Introduction
In this lab, you will continue Maya Novak’s ColorCloud experience after she has received her product and started using it in the ColorCloud mobile app. You will begin by signing in to Customer Voice to review the survey project and survey that were already prepared for you. You will then move to CI-D, where you will create a segment of customers whose first use in the app happened within the last 7 days. Finally, you will switch to CI-J, where you will add the survey to a text message and build a segment-based journey to send it.

This journey is designed to collect early feedback shortly after first product use, while the experience is still fresh in the customer’s mind. In the ColorCloud scenario, this is the moment when Maya is invited to share how easy it was to get started with her new ColorCloud Aura product.

## Objectives
By the end of this lab, you will be able to:
- Review a preconfigured Customer Voice survey project and survey
- Create a CI-D segment based on recent first app use behavior
- Add a Customer Voice survey to a text message in CI-J
- Build a segment-based journey to send the feedback request


# Exercise 1: Review the Customer Voice survey
In this exercise, you will sign in to Customer Voice and review the survey project and survey that were already prepared for the workshop.

**Step 1. Open Customer Voice**
- In your browser, open the Customer Voice environment associated with your workshop tenant
- Sign in with the same workshop credentials you used for Customer Insights - Journeys

**Step 2. Review the survey project**
- In Customer Voice, locate the project that was prepared for the workshop
- Open the project and review its name and structure
- Confirm that the project contains a survey for collecting first-use feedback related to ColorCloud Aura

**Step 3. Open the survey**
- Open the survey inside the project
- Review the survey title, welcome text, and questions
- Confirm that the survey is intended to capture a short first-use experience rating and feedback from customers

**Step 4. Confirm the survey is ready to be used**
- Verify that the survey is available to be added into CI-J content
- Do not make changes unless instructed during the workshop

**Expected outcome**

You have successfully signed in to Customer Voice and reviewed the preconfigured survey project and survey that will be used for the first-use feedback journey.


# Exercise 2: Build the CI-D segment for recent first app use
In this exercise, you will work in CI-D to create a segment of customers whose first use in the app happened within the last 7 days.

**Step 1. Open Customer Insights - Data**
- Open the CI-D environment you verified in Lab 1
- In the left navigation, go to Insights > **Segments**

**Step 2. Create a new segment**
- At the top command bar, click on **+ New** > Build your own
- Click on Edit details next to Untitled segment
- Name the segment **FirstUseLast7Days**
- Enter a description that clearly explains the purpose of the segment, for example: Customers whose first use in the ColorCloud app was within the last 7 days
- Add tags that help identify the purpose of the segment, for example:
  - App
  - Feedback
  - First Use
- Click on Done in the right bottom corner

**Step 3. Define the segment logic**
- In the right navigation, use the Attributes tab to locate the table and attribute that stores first app use information
- Add the attribute representing the first use date to the segment logic canvas
- Configure the condition so that the first use date is **within the last 7 days**
- If needed, set the appropriate relationship path so the segment evaluates at the unified customer profile level

**Step 4. Save and run the segment**
- At the bottom right corner click on Save
- At the bottom left corner click on Run
- Wait until the segment starts processing

**Step 5. Verify the segment status**
- Back in the Segments overview, verify that the **FirstUseLast7Days** segment has Status Queued, Refreshing, or Successful
- If successful, confirm that you can see Members for the segment
- Optionally open the segment and review the Segment members preview at the bottom

**Step 6. Check the segment availability in CI-J**
- Open the CI-J environment you verified in Lab 1 and used in Labs 2 and 3
- In the CI-J app, under the Real-time journeys area, go to Audience > Segments
- Confirm that you can see **FirstUseLast7Days** under the All Segments view where the Source is Customer Insights - Data

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/segment-builder-aspects) to learn more about Segments in CI-D

**Expected outcome**

You have created a CI-D segment named **FirstUseLast7Days** that identifies customers whose first use in the app was within the last 7 days, and you have verified that the segment is available in CI-J.


# Exercise 3: Add the survey to the text message
In this exercise, you will work in CI-J to update the text message that will be used to send the feedback survey.

**Step 1. Go to Text messages**
- In CI-J, make sure you are in the Real-time journeys area
- In the left navigation, go to **Channels > Text messages**

**Step 2. Open the draft text message**
- Locate and open **ColorCloud Aura CES** text message
- Confirm that the message is in Draft state so that you can update it

**Step 3. Add the Customer Voice survey**
- In the message editor, place your cursor where the survey link should appear
- Use the Customer Voice survey option to insert the survey from the Customer Voice project you reviewed in Exercise 1
- Select the correct first-use feedback survey
- Confirm that the survey link is added to the text message content

**Step 4. Review the rest of the message settings**
- Confirm that the correct text message sender is selected
- Confirm that the correct Compliance profile and Purpose are selected
- Review the message text to make sure it clearly asks the customer to provide feedback after first use

**Step 5. Save and publish the text message**
- In the right top corner click on Save
- Once saved, click on Ready to send
- Wait until the text message moves to Live state

**Expected outcome**

You have updated **ColorCloud Aura CES** text message by adding the Customer Voice survey and made it ready to send.


# Exercise 4: Build the segment-based first use feedback journey
In this exercise, you will create a segment-based journey that sends the feedback request text message to customers whose first app use happened within the last 7 days.

**Step 1. Go to Journeys**
- In CI-J, stay in the Real-time journeys area
- In the left navigation, go to **Journeys**

**Step 2. Create a new segment-based journey**
- In the top command bar select **+ New journey**
- In the pop up window click on Skip and create from blank in the right bottom corner
- Name the journey **ColorCloud Aura First Use Feedback**
- Choose **Segment-based**
- Under Select segments, choose **FirstUseLast7Days**
- Choose **A one-time journey where newly added audience members can start any time** under Select the frequency
- Set the right Time zone and Start
- Click on Create in the right bottom corner

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-segment-based-journey?source=recommendations) to learn more about Segment-based journeys

**Step 3. Add the text message**
- In the journey canvas, click on the plus sign Add an action
- Under Messages, choose Text message (Send a text message (SMS))
- In the right side panel, select **ColorCloud Aura CES** text message

**Step 4. Review journey settings**
- In the icon menu on the right side, review Entry settings
- Confirm that the journey is set up to allow audience members from the segment to enter when they qualify
- Save the journey

**Step 5. Publish the journey**
- In the right top corner click on Publish
- Wait until the journey is Live

**Expected outcome**

You have created and published **ColorCloud Aura First Use Feedback**. The journey starts from the **FirstUseLast7Days** CI-D segment and sends the **ColorCloud Aura CES** text message with the embedded Customer Voice survey.


# Lab Summary
In this lab, you extended Maya Novak’s ColorCloud journey into the feedback stage. You reviewed the preconfigured Customer Voice survey, created a CI-D segment for customers whose first app use happened within the last 7 days, updated the feedback text message with the survey link, and built a segment-based journey in CI-J to send it.

Consider where this journey fits in Maya Novak’s experience:
- Maya has already received her ColorCloud Aura product
- She has used the product in the app for the first time
- She enters the feedback journey through the **FirstUseLast7Days** segment
- She receives the **ColorCloud Aura CES** text message with a Customer Voice survey
- Her feedback can now be used to measure early onboarding success and customer experience

You are now ready to continue with the next step of Maya’s experience in **Lab 5: Measure Customer Adoption and Engagement**.
