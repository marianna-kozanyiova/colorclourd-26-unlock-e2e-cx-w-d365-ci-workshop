# Lab 3a: Build Segment-based Post-Purchase Onboarding & Upsell Journey

[Reading time: 5 min]

[Lab time: XX min]

- [Lab Overview](#lab-overview)
- [Exercise 1: Build the CI-D segments](#exercise-1-build-the-ci-d-segments)
- [Exercise 2: Finalize the CI-J Email and Text messages](#exercise-2-finalize-the-ci-j-email-and-text-messages)

# Lab Overview
## Introduction
In this lab, you will continue Maya Novak's ColorCloud experience after her first purchase. You will begin in `CI-D`, where you will create two segments: customers whose ColorCloud Aura product has been shipped and customers who already use the ColorCloud mobile app. You will then switch to `CI-J`, where you will prepare the required email and text message assets and build a segment-based journey for post-purchase onboarding and upsell.

This journey supports customers after purchase in a more personalized way. Customers whose product has been shipped will first receive an onboarding email. That email includes an inline condition so the Download app section is shown only if the customer is not already an app user. The journey then tests two subject line variants through an A/B test. Next, it branches based on whether the customer clicked the **Download the app** link. Customers who clicked the link continue into channel optimization for accessory upsell. Customers who did not click the link are further split based on app usage and then receive the relevant text message reminder.

## Objectives
By the end of this lab, you will be able to:
- Create `CI-D` segments for `CI-J` journeys
- Update an email with personalization and inline conditions
- Create a text message
- Build a segment-based cross-channel journey with an A/B test, branching logic, and channel optimization


# Exercise 1: Build the CI-D segments
In this exercise, you will work in `CI-D` to create the customer segments needed for the post-purchase onboarding and upsell journey.

**Step 1. Open Customer Insights - Data**
- Open the `CI-D` environment you verified in Lab 1
- In the left navigation, go to Insights > **Segments**

**Step 2. Create the AllAppUsers segment**
- At the top command bar, click **+ New** > Build your own
- Click Edit details next to Untitled segment
- Use your user ID as a prefix when naming the segment, **`{{Your user ID}}AllAppUsers`**. For example, if your user is colorcloud01@andrasfordos.onmicrosoft.com, name your segment **`01AllAppUsers`**.
- Enter a description that clearly explains the purpose of the segment, for example: Customers who use the ColorCloud app
- Add the following tag:
  - App
- Click Done in the bottom-right corner
- In the right navigation, on the Attributes tab, expand `Telemetry : IotHUB`, select `username` to add it to the segment logic builder canvas, change the `is` operator to `is not`, and change the `equal to` operator to `empty`
- At the top of the logic Rule 1 block, click Set relationship path and choose `IotHUB_Telemetry > ERP_Product > eCommerce_Transactions > eCommerce_Users > Customer`, then click Done
- In the bottom-right corner click Save, then in the bottom-left corner click Run. If you get a warning about Segment table being Inactive, click Continue running.

**Step 3. Create the ProductShippedAura segment**
- Back in the Segments overview, at the top command bar, click **+ New** > Build your own
- Click Edit details next to Untitled segment
- Use your user ID as a prefix when naming the segment, **`{{Your user ID}}ProductShippedAura`**. For example, if your user is colorcloud01@andrasfordos.onmicrosoft.com, name your segment **`01ProductShippedAura`**.
- Enter a description that clearly explains the purpose of the segment, for example: Customers whose ColorCloud Aura product has been shipped in the past 30 days
- Add the following tags:
  - Aura
  - Onboarding
- Click Done in the bottom-right corner
- In the right navigation, on the Attributes tab, expand `Product : ERP`, select `category` to add it to the segment logic builder canvas, enter `Device` after `equal to`, and check `Ignore case`. Hint: if you are unsure which attributes are available, check `Data > Tables`.
- In the right navigation, on the Attributes tab, expand `Product : ERP`, select `name` > Add item to > Existing rule > Rule 1, change the `is` operator to `contains`, enter `Aura` after `contains`, and check `Ignore case`
- In the right navigation, on the Attributes tab, expand `Transactions : eCommerce`, select `Status` > Add item to > Existing rule > Rule 1, enter `Shipped` after `equal to`, and check `Ignore case`
- In the right navigation, on the Attributes tab, expand `Transactions : eCommerce`, select `ShippedDate` > Add item to > Existing rule > Rule 1, change the specific date operator to `within last`, and enter `30`
- At the top of the logic Rule 1 block, click Set relationship path and choose `ERP_Product > eCommerce_Transactions > eCommerce_Users > Customer`, then click Done
- In the bottom-right corner click Save, then in the bottom-left corner click Run

**Step 4. Verify the Status of AllAppUsers and ProductShippedAura segments**
- Back in the Segments overview, make sure that both segments have status Queued, Refreshing, or Successful. If successful, verify that you can see the number of members for each segment. When you open a segment, you can preview the customer profiles included in it.

Optional: Check [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/customer-insights/data/segment-builder-aspects) to learn more about segments in `CI-D`

**Step 5. Check CI-D segments availability in CI-J**
- Open the `CI-J` environment you verified in Lab 1 and used in Lab 2
- In the `CI-J` app, under the Real-time journeys area, in the Audience section on the left-side navigation, click Segments and verify that you can see your segments under the All Segments view where the Source is `Customer Insights - Data`

**Expected outcome**

You have created `CI-D` segments named **`{{Your user ID}}ProductShippedAura`** for customers whose ColorCloud Aura product has been shipped and **`{{Your user ID}}AllAppUsers`** for customers who already use the ColorCloud app, and you have verified that the segments are available in `CI-J`.


# Exercise 2: Finalize the CI-J Email and Text messages
In this exercise, you will continue in `CI-J` to finalize the email and text messages for the onboarding and upsell journey.

**Step 1. Finalize ColorCloud Aura On Its Way Version A Email**
- In `CI-J`, make sure you are in the Real-time journeys area
- In the left navigation, go to **Channels > Emails**
- Open `ColorCloud Aura On Its Way Version A`, which is in Draft state, click the drop-down next to Save in the top-right corner, and select Save as
- In the Quick Create: Email drawer on the right side, add your user ID prefix to the Name and delete Copy from the end of the name. For example, if your user is colorcloud01@andrasfordos.onmicrosoft.com, name your email **`01 ColorCloud Aura On Its Way Version A`**, then click Save and Close in the bottom-right corner
- Go back to **Channels > Emails** and open the email **`{{Your user ID}} ColorCloud Aura On Its Way Version A`** you just created
- Click the drop-down arrows in the email header next to From: and Subject:, place your cursor in the Subject field right before the word your, and click Personalization on the right side of the Subject field > + New dynamic text > Choose an attribute > Audience > CustomerProfile > `firstname` > Save. `{{firstname}}` should be added right before the word your.
- In the body of the email, select the Get set up in minutes text, then in the icon menu on the right side click Personalize, expand Inline conditions > + Add condition, define Display name as `NotAppUser`, update the condition to Make condition on segment membership, change `Is in segment` to `Is not in segment`, look for your **`{{Your user ID}}AllAppUsers`** CI-D segment, then click Save & copy
- Optional: You can check the email elements as you did in Lab 2. Check the Brand profile, Personalize, Settings, and the footer content block.
- In the top-right corner click Save, and once saved, click Ready to send and make sure that your email moves to Live state

**Step 2. Verify rest of the Emails**
- Go back to **Channels > Emails**, open the `ColorCloud Aura On Its Way Version B` email, and check that the Subject is not personalized. This is Version B of the email you just created, but without personalization.
- Go back to **Channels > Emails**, open `ColorCloud Aura Accessories`. This email will be sent to customers who clicked the Download app link from **`{{Your user ID}} ColorCloud Aura On Its Way Version A`** if the system determines that email is the best channel in the journey.

**Step 3. Create ColorCloud Aura On Its Way Text message**
- In `CI-J`, make sure you are in the Real-time journeys area
- In the left navigation, go to **Channels > Text messages**
- In the top command bar click **+ New**
- Name the text message **`{{Your user ID}} ColorCloud Aura On Its Way`** using your user ID prefix, the same naming approach used for forms, emails, journeys, and segments in the previous labs
- Choose `+15074835080` as Text message sender
- Enter the following under Message:

```text
Hi {{firstname}}, your ColorCloud Aura 🌈 is on its way 🚚! 📲 Download the app to get started: https://colorcloud.rocks/ Unsubscribe: {{Preferencecenter}}
```

Then place your cursor right before the comma > Personalization icon > + New dynamic text > Choose an attribute > Audience > CustomerProfile > `firstname` > Save, so `{{firstname}}` is added before the comma. Then place your cursor after `Unsubscribe:` > Personalization icon > + New dynamic text > Choose an attribute > Compliance > Preference center > Save, so `{{Preferencecenter}}` is added after `Unsubscribe:`.
- Choose `ColorCloud Commercial DOI` as the Compliance profile and `Commercial` as the Purpose
- In the top-right corner click Save, and once saved, click Ready to send

**Step 4. Verify rest of the Text messages**
- Go back to **Channels > Text messages**, open `ColorCloud Aura On Its Way App Users`. This text message will be sent to customers who already use the app.
- Go back to **Channels > Text messages**, open `ColorCloud Aura Accessories`. This text message will be sent to customers who are not app users yet and clicked the Download the app link in **`{{Your user ID}} ColorCloud Aura On Its Way Version A`**.

**Expected outcome**

You have finalized **`{{Your user ID}} ColorCloud Aura On Its Way Version A`** email and verified the other emails used in the onboarding and upsell journey. You have created **`{{Your user ID}} ColorCloud Aura On Its Way`** text message and verified the other text messages used in the journey.


You are now ready to continue with building the journey in [Lab 3b: Build Segment-based Post-Purchase Onboarding & Upsell Journey](https://github.com/marianna-kozanyiova/colorclourd-26-unlock-e2e-cx-w-d365-ci-workshop/blob/main/lab03b.md).
