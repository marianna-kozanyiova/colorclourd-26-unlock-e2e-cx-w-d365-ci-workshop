# Lab 1: Access Environment & Finalize Configuration
Contents

[Lab Overview](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/edit/main/lab01.md#lab-overview)

[Exercise 1](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/edit/main/lab01.md#exercise-1-access-environment)

[Exercise 2](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/edit/main/lab01.md#exercise-2-verify-preconfigured-ci-d-components)

[Exercise 3](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/edit/main/lab01.md#exercise-3-verify-preconfigured-ci-j-components)

[Exercise 4](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/blob/main/lab01.md#exercise-4-finalize-ci-j-template-configuration)

# Lab Overview
## Introduction
In this lab, you will get access to the Dynamics 365 Customer Insights environments and review the setup prepared for the workshop. You will validate key configurations across CI-D and CI-J to ensure everything is ready for building end-to-end customer experience for Maya.

## Objectives
By the end of this lab, you will be able to:
- Access the CI-D and CI-J environments
- Familiarize yourself with & verify the preconfigured components
- Ensure your environment is ready for the upcoming labs

# Exercise 1: Sign in to Customer Insights - Journeys
In this exercise, you will sign in to your assigned Dynamics 365 Customer Insights - Journeys environment by using the details provided on your access card. It is recommended that you use a separate browser profile for the workshop.

**Step 1. Locate your access card**
- Find the access card assigned to you for the workshop. Confirm that it includes the following details:
    - Customer Insights - Journeys environment URL
    - Username
    - Password

**Step 2. Create a new browser profile**
- Open Microsoft Edge or Google Chrome and create a new browser profile dedicated to the workshop. This helps prevent sign-in issues caused by existing work or personal Microsoft accounts already active in your browser
    - In Microsoft Edge, select your profile icon in the top-right corner and choose Set up new personal profile or Add profile
    - In Google Chrome, select your profile icon in the top-right corner and choose Add

**Step 3. Open a new browser window in the workshop profile**
- After creating the new profile, open a new browser window in that profile and keep all workshop activity in this window

**Step 4. Go to the assigned environment URL**
- In the address bar, enter the Customer Insights - Journeys environment URL from your access card, then press Enter

**Step 5. Enter your username**
- On the Microsoft sign-in page, enter the username from your access card, then select Next

**Step 6. Enter your password**
- Type the password from your access card, then select Sign in

**Step 7. Wait for the environment to load and choose Customer Insights - Journeys app**
- After sign-in is complete, wait for the Dynamics 365 environment homepage to open and use the app list to select Customer Insights - Journeys

**Step 8. Confirm successful access**
- Verify that you can see the Customer Insights - Journeys app and that the environment opens without errors

**Expected outcome**

You are signed in to your assigned Customer Insights - Journeys environment and ready to continue with the next exercise.

**Tips**
- Use only the browser profile created for the workshop.
- Do not sign in with your personal or corporate Microsoft account unless instructed to do so.
- If the page does not load or you see an access error, ask the instructor for assistance before proceeding.

# Exercise 2: Verify Preconfigured CI-D Components
In this exercise, you will access the Customer Insights - Data environment connected to your Customer Insights - Journeys app and verify that the required data and configuration are available for the workshop.

**Step 1. Open Settings in Customer Insights - Journeys**
- In the Customer Insights - Journeys app, navigate to the left bottom corner and click on Real-time journeys
- Choose Settings area

**Step 2. Locate the Customer Insights connector**
- In the Settings area, scroll down within the menu on the left side to the Data management section
- Select Customer Insights connector

**Step 3. Copy the Customer Insights - Data URL**
- In the connector details, locate the Customer Insights - Data environment URL
- Copy the URL to your clipboard

**Step 4. Open Customer Insights - Data in a new tab**
- Open a new browser tab (in the same workshop browser profile)
- Paste the copied URL into the address bar
- Press Enter

**Step 5. Verify the environment loads successfully**
- Wait for the Customer Insights - Data home (welcome) page to load

**Step 6. Confirm the number of customers**
- In the top-right corner of the page, verify that you see 500 customers

**Step 7. Verify data sources**
- Navigate to Data > Data sources
- Confirm that the following data sources are available:
    - Dataverse
    - ECommerce
    - ERP
    - IotHub
    - Warranty
 
**Step 8. Verify tables**
- Navigate to Data > Tables
- Open the following tables one by one and inspect Rows and Columns (what data do you have available):
    - contact
    - ProductRegistrations
    - Products
    - TelemetrySummary
    - Transactions
 
**Step 9. Verify unified customer profiles**
- Navigate to Customers
- Confirm that you can see unified customer profile records (cards)

**Expected outcome**

You have successfully accessed Customer Insights - Data and verified that:
- The environment contains approximately 500 customers
- All required data sources and tables are available
- Unified customer profiles have been created
You are now ready to use this data in the upcoming labs.

# Exercise 3: Verify Preconfigured CI-J Components
In this exercise, you will return to the Customer Insights - Journeys app and verify that key components required for the workshop are already configured.

**Step 1. Go back to Customer Insights - Journeys**
- Go back to the browser tab where you have Customer Insights - Journeys app open in the Settings area

**Step 2. Verify Feature switches**
- In the left side menu navigate to Overview section and click on Featurew switches
- Verify that Copilot Global Opt-in consent and Global data sharing consent are Enabled, these enable the AI-powered functionalities
- Verify that Integrations Customer Voice integration is Enabled, this enables use of Customer Voice surveys (usually for feedback collection purposes) in emails and text messages

**Step 3. Verify Email marketing domain**
- In the left side menu navigate to Email marketing section and click on Domains
- Verify that you have one out of the box domain available, this is the domain from which your emails would be sent

**Step 4. Verify Brand profile**
- In the left side menu navigate to Customer engagement section and click on Brand profiles
- Open the ColorCloud record and verify
    - Sender (using the out of the box Email marketing domain from Step 3.),
    - Social links (can be dynamically pulled into your content blocks),
    - Theme (will be used for your emails with this Brand profile)

**Step 5. Verify Form settings**
- Staying in Customer engagement section and click on Form settings
- Open the Marketing form defaults record
- Verify that reCAPTCHA is set to Active including Site and Secret keys being populated, this enables you to use reCAPTCHA on forms as a security measure

**Step 6. Verify SMS provider**
- Staying in Customer engagement section and click on SMS providers
- Verify that ColorCloud record with Display Name Twilio is available, this is the phone number from which your text messages would be sent

**Step 7. Verify Compliance profiles**
- Staying in Customer engagement section and click on Compliance profiles
- Open ColorCloud Commercial DOI record
- Verify Address (is dynamically pulled into your content blocks)
- Open Preference center (is dynamically pulled into your content blocks to allow recipients to unsubscribe from Commercial Purpose communication)
- Go back to ColorCloud Commercial DOI record and check Consent purposes (these define how consent will be respected for the emails and text messages with the speicfic Customer profile and Purpose)
- Still under the ColorCloud Commercial DOI record check Double opt-in (used for forms with Consent purpose checkboxes, where, if enabled, Double opt-in is sent right after form submission to verify email address of the person submitting the form prior to Contact and/or Lead + Consent record creation)
- Go back to Compliance profiles and open ColorCloud Legitimate Interest
- Open Preference center (allows recipients to unsubscribe from Legitimate interest Purpose communication, that is the only difference opposed to ColorCloud Commercial DOI)

[Consent management overview](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-compliance-settings)

**Step 8. Verify Audience data**
- Navigate to Real-time journeys area, Audience section in the left side menu and click on Contacts
- Change the My Active Contacts view to All Contacts
- Verify that Contact records are available, these are also the records ingested into yoru CI-D environment via Dataverse connection
- In the Audience section in the left side menu click on Consent center
- Verify that Contact Point Consent records are available with different channels (Text Message and Email), Purposes (Commercial and Legitimate interest) and Consent statuses (Opted In and Opted out), these records are checked by the system prior to send out communication (Email or Text message) with specific Purpose to the recipients

**Step 9. Verify Assets**
- Still in the Real-time journeys area, go to Assets section in the left side menu and click on Library
- Verify that there is 1 font and 2 logo files available
- Still in the Assets section, click on Content blocks
- Verify that there are 3 Content block records, Header, Commercial Footer and Transactional Footer

**Expected outcome**

You have successfully verified that all required Customer Insights - Journeys components are preconfigured, including:
- Feature switches (Copilot, Customer Voice integration)
- Email domain configuration
- Brand profile
- Form settings
- SMS provider
- Compliance profiles
- Audience data and consent records
- Marketing assets (files and content blocks)

You are now almost ready to start building segments and journeys in the next labs.

# Exercise 4: Finalize CI-J Template Configuration
