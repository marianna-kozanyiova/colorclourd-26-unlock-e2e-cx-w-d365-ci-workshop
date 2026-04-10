# Lab 6 - Optional: Explore AI-Powered Customer Insights

[Reading time: X min]

[Lab time: XX min]

- [Lab Overview](#lab-overview)
- [Exercise 1: Ask Copilot questions about your customer data in CI-D](#exercise-1-ask-copilot-questions-about-your-customer-data-in-ci-d)
- [Exercise 2: Use Copilot to improve a ColorCloud email in CI-J](#exercise-2-use-copilot-to-improve-a-colorcloud-email-in-ci-j)
- [Exercise 3: Use Copilot to draft a follow-up journey in CI-J](#exercise-3-use-copilot-to-draft-a-follow-up-journey-in-ci-j)
- [Lab Summary](#lab-summary)

# Lab Overview
## Introduction
In this optional lab, you will explore how AI can help ColorCloud move faster from customer insight to customer action. In Lab 5, you created measures and a segment that identify customers showing strong commercial value and product adoption. In this lab, you will build on that work by using Copilot in both `CI-D` and `CI-J`.

You will begin in `CI-D`, where you will use Copilot to explore the unified Customer table and uncover customer profile patterns that can inform how ColorCloud communicates with valuable customers. You will then move to `CI-J`, where you will use Copilot to refine an existing ColorCloud email based on those insights. Finally, you will use Journey Copilot to draft a simple follow-up journey for the existing `HighValueAdopters` audience using the updated message.

This lab is designed to show how AI can support both sides of the customer experience process:
- understanding customers and finding opportunities in `CI-D`
- accelerating content and journey design in `CI-J`

## Objectives
By the end of this lab, you will be able to:
- check Data prep report in `CI-D`
- use Copilot in `CI-D` to ask questions about unified customer data
- use Copilot in `CI-J` to improve existing email content and draft a simple follow-up journey


# Exercise 1: Ask Copilot questions about your customer data in CI-D
In this exercise, you will check AI-generated data prep report and use Copilot in `CI-D` to explore profile patterns in the unified Customer table. The goal is not to analyze the {{Your user ID}}HighValueAdopters segment directly, but to identify broader customer characteristics that can help ColorCloud decide how to position the next accessories message for valuable customers.

**Step 1. Check Data prep report**
- Open the `CI-D` environment you used in previous labs
- In the left navigation, go to Home
- Click on View data prep report in the right top corner of the second Data prep report section of the Home screen
- Review `Overall data quality grade`, `Insights readiness`, `Critical issues` and `Warnings`

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/data-prep-overview) to learn more about data prep report

**Step 2. Have Dialog with data**
- In the left navigation, go to Insights > **Discovery**
- Use Copilot to ask `What are the most common values in the countryofresidence column in the Customer table?` Based on the values provided you should see that DE is the predominant market for ColorCloud.
- Use Copilot to ask `How many customers with countryofresidence in DE have a gold value in the loyalty_tier column?` The answer should be 53.
- Use Copilot to ask `How many customers customers with countryofresidence in DE with gold value in loyalty_tier column have a value in the rewardpoints column?` The answer should be 10.

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/dialog-with-data) to learn more about dialog with data

**Expected outcome**

You learned that `Germany (DE)` is ColorCloud’s  `predominant market`. Gold loyalty tier and reward points are present only for a smaller subset of customers, so market relevance is the stronger insight to carry into CI-J.


# Exercise 2: Use Copilot to improve a ColorCloud email in CI-J
In this exercise, you will use the insight from Exercise 1 to improve an existing ColorCloud email with Copilot in `CI-J`.

**Step 1. Update existing ColorCloud email using content ideas**
- Open the `CI-J` environment you used in previous labs
- Make sure you are in the Real-time journeys area, in the left navigation go to Channels > **Emails**
- Open `{{Your user ID}} ColorCloud Aura Accessories` email then click on Edit in the right top corner
- In the email body canvas, click on `Hi {{firstname}}, ...` Text element, once selected, click on Rewrite button right above the Text > Tone > Formal
- Copilot has generated some option for you, choose one by clicking on Insert text button in the left bottom corner of the pop up window
- Optional: Since the text will be inserted without styling, you can highlight it and update the Font (Montserrat-Regular), Size (14px) and Text color (white) via the command bar right underneath the email header
- In the right top corner click on Save, once saved, click on Ready to send

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/content-ideas) to learn more about content ideas

**Expected outcome**

You used Copilot in `CI-J` to improve an existing ColorCloud email so it better matches your customer profile patterns identified in Exercise 1.


# Exercise 3: Use Copilot to draft a follow-up journey in CI-J
In this exercise, you will use your **`{{Your user ID}}HighValueAdopters`** segment as audience and the updated email to draft a simple follow-up journey with Copilot in `CI-J`.

**Step 1. Draft new ColorCloud journey with Copilot**
- Still in the Real-time journeys area, in the left navigation go to Engagement > **Journeys**
- In top command bar click on **+ New journey**
- Update the following prompt with your user ID `Create a journey for customers in the {{Your user ID}}HighValueAdopters segment. Send the {{Your user ID}} ColorCloud Aura Accessories email. Wait 3 days and send the {{Your user ID}} ColorCloud Aura Accessories email again to customers who didn't open it.` and then insert it in the Create journey with Copilot pop up window and click on Send (the paper-plane icon) in right bottom corner
- After Copilot is done generating, click on create journey
- Once the journey is created, check if the structure of the journey works for the prompt above and click on Save in the right top corner

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-use-copilot-create-journey) to learn more about creating journey using AI assistance

**Expected outcome**

You used Copilot in `CI-J` to draft a simple follow-up journey that connects the **`{{Your user ID}}HighValueAdopters`** segment with your updated accessories email.


# Lab Summary
In this lab, you explored how AI can help ColorCloud move from insight to action. You first used Copilot in `CI-D` to ask natural-language questions about unified customer data and identify patterns. You then used Copilot in `CI-J` to improve an existing ColorCloud email taking into consideration patterns you discovered. Finally, you used Copilot to draft a simple follow-up journey that connects the **`{{Your user ID}}HighValueAdopters`** segment from Lab 5 with the updated email.

Consider where this lab fits in the ColorCloud scenario:
- `CI-D` helped you explore unified customer profile data and assess data readiness for AI-powered insights
- the customer profile patterns you identified helped inform how ColorCloud should position its accessories communication
- `CI-J` helped you use Copilot to accelerate both content improvement and journey design
- together, `CI-D` and `CI-J` showed how AI can support the path from insight to activation using assets and audiences already created in earlier labs
