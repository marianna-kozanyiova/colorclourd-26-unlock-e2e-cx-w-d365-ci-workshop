# Lab 2: Build Trigger-based Subscription Incentive Journey

# Lab Overview
## Introduction
In this lab, you will work in Dynamics 365 Customer Insights - Journeys (CI-J) to build the first step in Maya Novak’s experience with ColorCloud. You will create a marketing form from the preconfigured ColorCloud Form Template, build a confirmation email from the ColorCloud Email Template, and then orchestrate a trigger-based journey that starts when the marketing form is submitted.

This journey represents the moment when a prospective customer subscribes to the ColorCloud newsletter to receive a discount code for their first purchase. The goal of the journey is to onboard new customers and measure early engagement with the subscription confirmation email.

## Objectives
By the end of this lab, you will be able to:
- Create a marketing form from an existing custom form template
- Create a subscription confirmation email from an existing custom email template
- Build a trigger-based journey using the Marketing form submitted trigger
- Configure a journey condition based on a specific form
- Set a journey goal to onboard new customers
- Define success as 1000 recipients opening the email


# Exercise 1: Build the subscription form
In this exercise, you will create a new marketing form based on the preconfigured ColorCloud Form Template. This form will be used to capture newsletter subscription requests from prospective customers who want to receive a discount code.

**Step 1. Go to Forms**
- In Customer Insights - Journeys, make sure you are in the Real-time journeys area
- In the left navigation, go to Assets > Forms

**Step 2. Create a new form from template**
- Select **+ New**
- Choose to create the form from an existing template
- Select **ColorCloud Form Template**

**Step 3. Enter form details**
- Name the form **ColorCloud Newsletter Subscription Form**
- Review the initial structure that was inherited from the template

**Step 4. Review and update the form fields**
- Confirm that the form is intended to capture at minimum the subscriber’s email address
- Review whether the template already contains the required consent-related elements
- If needed, update labels or helper text so the form clearly communicates that the subscriber will receive a newsletter subscription confirmation and a discount code

**Step 5. Review form settings**
- Open the form settings and verify the correct configuration inherited from the template
- Confirm that the form uses the preconfigured compliance setup appropriate for commercial communication
- Confirm that reCAPTCHA is enabled through the default form settings prepared in Lab 1

**Step 6. Save and publish the form**
- Select **Save**
- Then select **Publish**
- Wait until the form is published successfully

**Expected outcome**

You have created and published a form named **ColorCloud Newsletter Subscription Form** based on the ColorCloud Form Template. The form is ready to be used in a trigger-based journey.


# Exercise 2: Build the subscription confirmation email
In this exercise, you will create the first marketing email in the ColorCloud scenario. This email confirms the newsletter subscription and delivers the promised discount code.

**Step 1. Go to Emails**
- In Customer Insights - Journeys, stay in the Real-time journeys area
- In the left navigation, go to Assets > Emails

**Step 2. Create a new email from template**
- Select **+ New**
- Choose to create the email from an existing template
- Select **ColorCloud Email Template**

**Step 3. Enter email details**
- Name the email **ColorCloud Newsletter Subscription Confirmation with Discount Code**
- Select the appropriate Brand profile for ColorCloud if it is not already prepopulated

**Step 4. Update the subject line**
- Enter a subject line that reflects the purpose of the message, for example:
  - **Welcome to ColorCloud - here is your discount code**

**Step 5. Build the email content**
- Update the body of the email so it thanks the recipient for subscribing to the ColorCloud newsletter
- Add copy that introduces ColorCloud as a connected lifestyle brand
- Clearly present the discount code for the subscriber’s first purchase
- Include a short call to action that encourages the recipient to browse ColorCloud products
- Keep the branded header and footer content inherited from the template

**Step 6. Review compliance and sender settings**
- Verify that the correct compliance profile is selected for commercial communication
- Verify the sender details inherited from the Brand profile

**Step 7. Run required checks**
- Select **Check content**
- Resolve any issues or warnings that prevent the email from being made ready to send

**Step 8. Make the email ready to send**
- Once validation passes, select **Ready to send**
- Wait until the email status updates successfully

**Expected outcome**

You have created an email named **ColorCloud Newsletter Subscription Confirmation with Discount Code** and made it ready to send. The email is ready to be used in a real-time journey.


# Exercise 3: Build the trigger-based subscription incentive journey
In this exercise, you will create a trigger-based journey that starts when the newsletter subscription form is submitted. You will configure the form as the trigger condition, send the confirmation email, and set a goal to onboard new customers. Success for the journey will be reached when 1000 recipients open the email.

**Step 1. Go to Journeys**
- In Customer Insights - Journeys, stay in the Real-time journeys area
- In the left navigation, go to Journeys

**Step 2. Create a new trigger-based journey**
- Select **+ New journey**
- Choose **Trigger-based journey**

**Step 3. Enter journey details**
- Name the journey **ColorCloud Subscription Incentive Journey**
- Confirm that the journey type is trigger-based

**Step 4. Select the trigger**
- For the journey trigger, select **Marketing form submitted**
- Continue to the journey designer

**Step 5. Add the form condition**
- In the trigger configuration, specify that the journey should only start when the submitted form is the **ColorCloud Newsletter Subscription Form**
- This ensures the journey reacts only to the subscription form created in Exercise 1

**Step 6. Add the email**
- In the journey canvas, add an **Email** tile after the trigger
- Select **ColorCloud Newsletter Subscription Confirmation with Discount Code** as the email to send

**Step 7. Configure the journey goal**
- Open the goal settings for the journey
- Set the business goal to **Onboard new customers**
- Configure the goal success condition so that the goal is reached when **1000 recipients open the email**

**Step 8. Review the journey**
- Confirm the journey includes:
  - A **Marketing form submitted** trigger
  - A condition limited to **ColorCloud Newsletter Subscription Form**
  - The email **ColorCloud Newsletter Subscription Confirmation with Discount Code**
  - A goal for onboarding new customers
  - A goal success condition based on **1000 email opens**

**Step 9. Publish the journey**
- Select **Go live**
- Wait until the journey is published successfully

**Expected outcome**

You have created and published a trigger-based journey named **ColorCloud Subscription Incentive Journey**. The journey starts when someone submits the ColorCloud newsletter subscription form, sends a confirmation email with a discount code, and tracks progress toward the onboarding goal. The goal is considered achieved when 1000 recipients open the email.


# Exercise 4: Test and validate the end-to-end setup
In this exercise, you will validate that all assets are connected correctly and that the journey is ready for use.

**Step 1. Review published assets**
- Confirm that the following assets are published or ready to send:
  - **ColorCloud Newsletter Subscription Form**
  - **ColorCloud Newsletter Subscription Confirmation with Discount Code**
  - **ColorCloud Subscription Incentive Journey**

**Step 2. Verify journey logic**
- Open the live journey and review the trigger and email steps
- Confirm that the journey starts only from the intended form submission event

**Step 3. Discuss the scenario**
- Consider where this journey fits in Maya Novak’s experience:
  - Maya discovers ColorCloud online
  - She subscribes to receive a discount code
  - She receives the confirmation email and discount code
  - This becomes the starting point for her first purchase journey

**Expected outcome**

You have validated the complete subscription incentive setup in CI-J. ColorCloud now has a working trigger-based entry journey for prospective customers who subscribe through the marketing form.


# Lab Summary
In this lab, you created the first live interaction in Maya’s ColorCloud journey. You built a subscription form, created a confirmation email with a discount code, and connected both assets through a trigger-based real-time journey in Customer Insights - Journeys.

You are now ready to continue with the next step of Maya’s experience in [Lab 3: Build Segment-based Post-Purchase Onboarding & Upsell Journey](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/blob/main/lab03.md).
