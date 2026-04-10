# Lab 6: Optional - Explore AI-Powered Customer Insights

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

You will begin in `CI-D`, where you will use Copilot to ask natural-language questions about your unified customer data and identify an audience that ColorCloud could act on next. You will then move to `CI-J`, where you will use Copilot to improve an existing ColorCloud email for that audience. Finally, you will use Journey Copilot to draft a simple follow-up journey based on the same audience and message.

This lab is designed to show how AI can support both sides of the customer experience process:
- understanding customers and finding opportunities in `CI-D`
- accelerating content and journey design in `CI-J`

## Objectives
By the end of this lab, you will be able to:
- use Copilot in `CI-D` to ask questions about unified customer data
- use Copilot in `CI-J` to improve existing email content and draft a simple follow-up journey


# Exercise 1: Ask Copilot questions about your customer data in CI-D
In this exercise, you will use Copilot in `CI-D` to ask questions about the customer data and measures you created in earlier labs. The goal is to uncover one insight that could justify a follow-up marketing action for ColorCloud.

**Step 1. Open the Discovery experience**
- Open the `CI-D` environment you used in previous labs
- In the left navigation, go to Insights > **Discovery**

**Step 2. Ask one or more business questions**
Use Copilot to ask 2–3 questions about your ColorCloud customer data.

Suggested questions:
- **Which customers in the `{{Your user ID}}HighValueAdopters` segment are the best candidates for an accessories offer?**
- **What behaviors or attributes make customers in the `{{Your user ID}}HighValueAdopters` segment good candidates for a follow-up accessories message?**
- **What action should ColorCloud take next for customers in the `{{Your user ID}}HighValueAdopters` segment to deepen adoption and increase value?**

These questions tie directly to the measures and segment logic from Lab 5, including revenue, orders, registrations, registration rate, and the **`{{Your user ID}}HighValueAdopters`** segment. They also help justify a next step that can be reflected in the email and journey updates later in this lab.

**Step 3. Review the Copilot responses**
- Review the answer Copilot returns for each question
- Identify one insight that supports a follow-up accessories or engagement action for ColorCloud

For example, you may find that:
- high-value adopters are good candidates for accessories because they already show strong purchase and activation behavior
- some customers are engaged enough to benefit from a more premium or tailored accessories message
- ColorCloud should use a follow-up journey to increase accessory adoption and deepen product usage

**Step 4. Capture one recommended action**
Based on the insight you found, write down one action ColorCloud could take next.

Example:
- Update the **ColorCloud Aura Accessories** email so it better fits high-value adopters
- Create a simple follow-up journey for the **`{{Your user ID}}HighValueAdopters`** segment using that updated email

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/dialog-with-data) to learn more about dialog with data

**Expected outcome**

You used Copilot in `CI-D` to ask questions about unified customer data and identified one insight and next best action for the **`{{Your user ID}}HighValueAdopters`** audience.


# Exercise 2: Use Copilot to improve a ColorCloud email in CI-J
In this exercise, you will use the insight from Exercise 1 to improve an existing ColorCloud email with Copilot in `CI-J`.

Microsoft documents **Content ideas** in Customer Insights - Journeys as a Copilot capability that helps generate email content from key points and a selected tone of voice. Microsoft also notes that the generated content should still be reviewed and refined by the user. ([learn.microsoft.com](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/content-ideas))

**Step 1. Open an existing ColorCloud email**
- Open the `CI-J` environment you used in previous labs
- Go to the email you want to improve

You can use:
- **ColorCloud Aura Accessories** email, or
- any other email created in earlier labs, such as onboarding or feedback email

**Step 2. Decide how the email should change**
Use the insight from Exercise 1 to decide what should be improved.

Recommended approach:
- update the email so it better fits customers in the **`{{Your user ID}}HighValueAdopters`** segment
- make the message feel more relevant for customers who already show strong adoption and value
- strengthen the value of the accessories offer and the call to action

**Step 3. Open Content ideas**
- In the email editor, open Copilot **Content ideas**

**Step 4. Generate improved content**
Enter a few key points for the email.

Example key points for **ColorCloud Aura Accessories**:
- Thank the customer for choosing ColorCloud Aura
- Highlight accessories that enhance the product experience
- Position the accessories offer for customers who are already engaged with the product
- Keep the tone premium, helpful, and concise
- Encourage customers to continue getting more value from their ColorCloud experience

**Step 5. Review and apply the output**
- Generate content ideas
- Review the suggestions
- Insert or adapt one of the generated sections into your email
- Make small edits so the email fits the ColorCloud brand and the audience you identified in Exercise 1

**Expected outcome**

You used Copilot in `CI-J` to improve an existing ColorCloud email so it better matches the **`{{Your user ID}}HighValueAdopters`** audience and the action identified in Exercise 1.

**Microsoft documentation**
- [Copilot - Use AI to kickstart email creation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/content-ideas)

# Exercise 3: Use Copilot to draft a follow-up journey in CI-J
In this exercise, you will use the same audience and updated email to draft a simple follow-up journey with Copilot in `CI-J`.

Microsoft documents **Journey Copilot** as a preview feature that lets users describe a journey in conversational language and generate a journey draft. Microsoft also notes that the prompt must start from an existing segment or trigger, and that the feature is currently limited to the United States and English. ([learn.microsoft.com](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-use-copilot-create-journey))

**Step 1. Identify the audience**
Use the existing **`{{Your user ID}}HighValueAdopters`** segment that you created in Lab 5.

This keeps the exercise simple and ties it directly to the audience you analyzed in Exercise 1 and the email you updated in Exercise 2.

**Step 2. Decide on the journey**
Use Copilot to draft a simple follow-up journey for that audience.

Recommended journey:
- Start from the existing **`{{Your user ID}}HighValueAdopters`** segment
- Send the updated **ColorCloud Aura Accessories** email
- Wait 3 days
- Send a follow-up email encouraging customers to enhance their ColorCloud experience with accessories

Suggested prompt:
**Create a journey for customers in the `{{Your user ID}}HighValueAdopters` segment. Send the updated ColorCloud Aura Accessories email, wait 3 days, and then send a follow-up email encouraging customers to enhance their ColorCloud experience with accessories.**

**Step 3. Review the generated journey**
- Review the journey Copilot creates
- Check whether the steps match your intended audience and message
- Make any small adjustments needed

**Step 4. Save your observation**
Write down:
- the prompt you used
- whether Copilot created the journey successfully
- one thing you would refine before publishing

**Expected outcome**

You used Copilot in `CI-J` to draft a simple follow-up journey that connects the **`{{Your user ID}}HighValueAdopters`** segment with your updated accessories email.

**Microsoft documentation**
- [Copilot - Create journeys using AI assistance (preview)](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-use-copilot-create-journey)

# Lab Summary
In this lab, you explored how AI can help ColorCloud move from insight to action more quickly. You first used Copilot in `CI-D` to ask natural-language questions about unified customer data and identify a next best action for the **`{{Your user ID}}HighValueAdopters`** segment. You then used Copilot in `CI-J` to improve an existing ColorCloud email for that audience. Finally, you optionally used Copilot to draft a simple follow-up journey that connects the same audience with the updated message.

Consider where this lab fits in the ColorCloud scenario:
- Lab 5 helped ColorCloud measure customer value and product adoption
- this lab showed how AI can help interpret those insights and suggest a useful next step
- the improved email and follow-up journey demonstrate how ColorCloud can quickly turn insight into action for high-value adopters
- together, `CI-D` and `CI-J` show how AI can support both customer understanding and customer engagement

This optional lab is a natural continuation of Lab 5 because it builds directly on the measures and audience logic already created there, especially the **`{{Your user ID}}HighValueAdopters`** segment.
