# Lab 2: Build Trigger-based Subscription Incentive Journey

# Lab Overview
## Introduction
In this lab, you will work in Dynamics 365 Customer Insights - Journeys (CI-J) to build the first step in Maya Novak’s experience with ColorCloud. You will create a marketing form from the preconfigured ColorCloud Form Template, build a confirmation email from the ColorCloud Email Template, and then orchestrate a trigger-based journey that starts when the marketing form is submitted.

This journey represents the moment when a prospective customer subscribes to the ColorCloud newsletter to receive a discount code for their first purchase. The goal of the journey is to onboard new customers and measure early engagement with the subscription confirmation email.

## Objectives
By the end of this lab, you will be able to:
- Create a marketing form from an existing custom form template
- Create an email from an existing custom email template
- Build a trigger-based journey using the Marketing form submitted trigger
- Set a journey goal

# Exercise 1: Build the subscription form
In this exercise, you will create a new marketing form based on the preconfigured ColorCloud Form Template. This form will be used to capture newsletter subscription requests from prospective customers who want to receive a discount code.

**Step 1. Go to Forms**
- In Customer Insights - Journeys, make sure you are in the Real-time journeys area
- In the left navigation, go to Channels > Forms

**Step 2. Create a new form from template**
- In the top command bar, select **+ New**
- In the Form Templates pop up window, under Custom templates, click on **ColorCloud Form Template** and click on Select in the right bottom corner

**Step 3. Enter form details**
- Name the form **ColorCloud Newsletter Subscription**
- Review the initial structure that was inherited from the template

**Step 4. Review the form fields and elements**
- Confirm that the form is intended to capture at minimum the subscriber’s email address, click on the Email field and review the Edit field section on the right side making sure the Required flag is On and under Advanced section, Validation is set to Email
- Review whether the template already contains the required consent-related elements, click on the consent checkbox field and review the Edit purpose section on the right side, where Compliance profile should be set to ColorCloud Commercial DOI, Purpose set to Commercial, Required flag is On and under Properties section, Update user's consent for both Email and Text is checked
- Confirm that reCAPTCHA is placed on the form

**Step 5. Review form settings**
- Check that the Audience is set to Contact in the right top corner
- In the icon menu on the right side from Edit purpose section, click on Form settings (4th icon from the top)
- Expand the Audience section and check that Choose how to handle duplicate contacts is set to Use a rule to match an existing contact and Select contact matching rule is set to Update contact using email
- Exapnd the Submission section and check that the Thank you notification refers to Double opt-in email
- Expand the Consent setion and check that the Double opt-in is Enabled (it should be since the Compliance profile ColorCloud Commercial DOI has been selected for the consent checkbox of the form)

**Step 6. Save and publish the form**
- In the right top corner click on **Save**
- Then click on **Publish**
- Wait until the form is published successfully
- Click on Publish options and create new standalone page (you have the possibility to copy script with which you can embed on your own website, or use standalone page created by Microsoft where the form is hoted, if you finish this lab earlier, you can utilize the standalone page to test the form submission)

**Expected outcome**

You have created and published a form named **ColorCloud Newsletter Subscription** based on the ColorCloud Form Template. The form is ready to be used in a trigger-based journey.


# Exercise 2: Build the subscription confirmation email
In this exercise, you will create the first marketing email in the ColorCloud scenario. This email confirms the newsletter subscription and delivers the promised discount code.

**Step 1. Go to Emails**
- In Customer Insights - Journeys, stay in the Real-time journeys area
- In the left navigation, go to Channels > Emails

**Step 2. Create a new email from template**
- In the top command bar, select **+ New**
- In the Email Templates pop up window, under Custom templates, click on **ColorCloud Email Template** and click on Select in the right bottom corner

**Step 3. Enter email details**
- Name the email **ColorCloud Newsletter Subscription Confirmation with Discount Code**

**Step 4. Verify the email details**
- Confirm that the Brand profile in the right top corner is set to ColorCloud
- Expand the email header and confirm that the Sender is ColorCloud and that the Subject is Welcome to ColorCloud – here’s your exclusive offer 🎁
- In the icon menu on the right side, click on Personalize (person with lightning bolt icon) and check that under Dynamic text FirstName is set to Contact > First Name (defines the attribute from which the value will be pulled from Contact record for each recipient, represented in the email body as {{FirstName}})
- In the icon menu on the right side, click on Settings (mailbox with cog wheel icon), check that Company address is the same as the one you saw in Compliance profile in Lab 1, then expand Compliance section and check that Compliance profile is set to ColorCloud Commercial DOI and that the Purpose is set to Transactional (since the discount code was promised after subscription to newsletter, this email needs to be sent independently of consent given for the specific email address)
- In the body of the email check the footer content block and confirm that there is no Unsubscribe link (since the email is classified as Transactional and the enforcement model for this Purpose is Disabled, it means that we always send these kinds of emails to deliver information to the customer that is necessary for ColorCloud products and services, therefore, don't really offer a way to unsubscribe from transactional communication)

**Step 5. Save and publish the email**
- Once verified, click on Save in the right top corner and then click on **Ready to send**
- Wait until the email is published successfully

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

You have created and published a trigger-based journey named **ColorCloud Subscription Incentive**. The journey starts when someone submits the ColorCloud newsletter subscription form, sends a confirmation email with a discount code, and tracks progress toward the onboarding goal. The goal is considered achieved when 1000 recipients open the email.


# Lab Summary
In this lab, you created the first live interaction in Maya’s ColorCloud journey. You built a subscription form, created a confirmation email with a discount code, and connected both assets through a trigger-based real-time journey in Customer Insights - Journeys.

Consider where this journey fits in Maya Novak’s experience:
  - Maya discovers ColorCloud online
  - She subscribes to receive a discount code via **ColorCloud Newsletter Subscription** Form
  - She receives the **ColorCloud Newsletter Subscription Confirmation with Discount Code** confirmation email and discount code via **ColorCloud Subscription Incentive** Journey
  - This becomes the starting point for her first purchase journey

You are now ready to continue with the next step of Maya’s experience in [Lab 3: Build Segment-based Post-Purchase Onboarding & Upsell Journey](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/blob/main/lab03.md).
