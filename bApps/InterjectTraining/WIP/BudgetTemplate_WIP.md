---
title: Budget Template
layout: custom
keywords: [Training, Budget, Budget Template]
description: 
---

## Overview

**Purpose**: This is the primary tool used for managing Budgets. This tool can be downloaded and customized in your local environment.

**Filter Options**:

* **District** - *Required*. Individual district. Cannot use district ranges or groupings
* **YYYY-MM** - *Required*. Needs to be in YYYY-MM format
* **Currency** - *Optional*. Blank defaults to your home district currency. Other options are USD and CAD.
* [ **Base Year** ](#base-year-option-and-fincube) - *Required*. Used in the pull. Drop-down filter ranges from *Aug Proj -> Dec Act*<br><br>
[ *Retain Rows - Related Parameters (used in the pull)* ](#retain-rows-and-how-it-works)
* **Retain Rows** - *Required*. Drop-down filter includes *Yes*, *No-Show Last Saved*, *No-Show Prior Bud*. If *Yes*, the Input columns will not wipe out on the pull.
* **Retain Comments** - *Required*. Drop-down filter includes *Yes* and *No*. If *Yes*, pulling in on the report will not wipe out comments not yet saved to the database.
* **Insert at End** - *Required*. Drop-down filter includes *Yes* and *No*. If *Yes* and **Retain Rows** is also *Yes*, then new accounts get added at the bottom of their grouping.<br><br>
[ *Summary and Detail Accounts - Related Parameters* ](#summary-and-detail-level-accounts)
* **Insert By Full Acct** - *Required*. Used in the pull. Drop-down filter includes *Yes* and *No*. For *Yes*, Accounts not yet in the template get pulled in on the detail level. For *No*, they are summarized in at the summary level and dropped in.
* **Zero Out Missing Accts** - *Required*. Used in the save. Drop-down filter includes *Yes* and *No*. For *Yes*, if an account has an amount in the database but is not in the template, the account in the database will be zeroed out. For *No*, the amount in the database will remain unaffected, and any Summary level accounts are offsetted to include the missing accounts automatically.

![](/images/WCNTraining/Budget/BudgetTemplate_FullView.png)

## Base Year option and Fincube

The **Base Year** drop-down filter changes how Actuals and Projections for the current year are pulled in from Fincube. For example, the screenshot below shows the *Aug Proj* option, which pulled in Actuals from January -> July, and Projections from August -> December.

![](/images/WCNTraining/Budget/BudgetTemplate_BaseYear01.png)

If we change the **Base Year** to *Aug Act*, August will pull in as Actual instead.

![](/images/WCNTraining/Budget/BudgetTemplate_BaseYear02.png)

## Retain Rows and how it works

With **Retain Rows** on *Yes*, any inputs in the Input columns will remain when the template is refreshed, or even if the report is cleared.

For example, the screenshot below shows a formula used on the *50020-600-00* account.

![](/images/WCNTraining/Budget/BudgetTemplate_RetainRowsBeforeClear.png)

We clear the report, and afterwards we see that not only have all of the rows remain, but the formula is still there.

![](/images/WCNTraining/Budget/BudgetTemplate_RetainRowsAfterClear.png)

The **Retain Comments** on *Yes* will keep any comments saved in the template, even if there are different comments saved in the database.

If a new account is added to the Template with **Retain Rows** set to *Yes*, the setting for **Insert at End** dictates if the new account is added where it would normally go or get inserted at the end.

For example, if *50045-600-00* is added to the Template while **Insert at End** is set to *No*, it is nestled between the 50035 and 50050 accounts.

![](/images/WCNTraining/Budget/BudgetTemplate_InsertAtEndNo.png)

Otherwise if **Insert at End** is set to *Yes*, the added account is added at the bottom. Use this if you use formulas, so that newly added accounts do not mess them up.

![](/images/WCNTraining/Budget/BudgetTemplate_InsertAtEndYes.png)

## Summary and Detail level accounts

A new feature to the Budget Template is the ability to pull/save to Detail and Summary level accounts at the same time.

### Pulling Summary and Detail levels together
On the pull, the **Insert By Full Acct** drop-down option dictates if the missing accounts are added on the Summary or Detail level. When **Retain Rows** is set to *Yes*, this permits you to pull in accounts on a different level than the ones you already have in your template.

Let's go through the following example. In the screenshot below, we see four account combinations for the 36009 account.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetailPullStart.png)

With **Retain Rows** set to *Yes* and **Insert By Full Acct** set to *No*, we delete the 36009-000-00 and 36009-600-00 rows.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetailPullStart.png)

When we pull on the tool now, the two detail rows 36009-000-00 and 36009-600-00 are summarized into one row, with the account header of 36009 alone. 36009-000-00 had $1,000 amounts for all months, and 36009-600-00 had $2,000 for all months. Together they have $3,000 for all months.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetailPullStart.png)

>**Things to Remember**<br>
>For this to work, **Retain Rows** MUST be set to *Yes*. Otherwise, if **Retain Rows** is set to *No* and you pull, it will wipe out all rows and pull in all accounts either on the Summary or Detail level (depending on how you set **Insert By Full Acct**).

### Saving Summary and Detail levels together

Here Paul is going to write Save notes.

## Do I have security rights to Save from the Budget Template?

Only people in the District Position Assignment (DPA) for the District in Toolbox can save to this file. Your Division Controller can add you if you are not already in the DPA.

![](/images/WCNTraining/Capital/CapitalInput_DPANavigation.png)

![](/images/WCNTraining/Capital/CapitalInput_DPAWindow.png)

## Budget Template and the Control Center

Based on your position in the DPA for the district, you will have a certain level of access to this report. The types of levels you may be on are: **A/C**, **Dist**, **Div**, **Reg**, or **Corp**.

Budget is locked at these levels in the **Control Center**, in the N column. In the example below, District 2050 is locked at the Reg Level.

![](/images/WCNTraining/Budget/BudgetUpload_ControlCenter1District.png)

If an A/C level user tried saving to 2050 Budget, they would be stopped with the following message.

![](/images/WCNTraining/Budget/BudgetUpload_LockLevel1District.png)

You are able to save Budget as long as the Budget lock level is your level or below. Otherwise you will not be able to save Budget.

## After Corp Cutoff and after BOD

If you save to Budget **After Corp Cutoff**, the numbers will still be updated in Target Center 2.0. However, they will not be synced through to Interject.

In this example, the *Corp Cutoff* date in Control Center is set to 11/3/2018.

![](/images/WCNTraining/Budget/BudgetUpload_CCAfterCorpCutoff.png)

We then try and upload a change to Budget using the **Budget Upload** tool (after this date), and get the following popup and in-row messages.

<!--
![](/images/WCNTraining/Budget/BudgetUpload_AfterCorpCutoffMessage.png)
![](/images/WCNTraining/Budget/BudgetUpload_AfterCorpCutoffRowMessage.png)
-->

So our changes here have been saved to Target Center 2.0, but they are not yet synced to Interject. Once the *Corp Cutoff* date is set to a Date/Time after our change or BOD, this change will then be synced to Interject.

We can use the [ Budget Change Query Tool ](/bApps/InterjectTraining/Budget/BudgetChangeQueryToolSummary.html) to confirm that our save has been registered in Target Center 2.0. the new tab [ UnsyncedChanges ](/bApps/InterjectTraining/Budget/BudgetChangeQuery_UnsyncedChanges.html) is designed to pull in all amounts not yet synced to Interject, which neatly matches our inquiry. The screenshot below shows that our Budget save did indeed succeed and is in the database.

<!-- ![](/images/WCNTraining/Budget/BudgetUpload_UnsyncedChangesBCQuery.png) -->

Once **BOD** for a Budget Year has been created, then any save from the **Budget Upload Tool** will not automatically sync to Interject again. This is just like with *After Corp Cutoff*, and while it is not in Interject it is in Target Center 2.0 and be checked using the [ UnsyncedChanges ](/bApps/InterjectTraining/Budget/BudgetChangeQuery_UnsyncedChanges.html) tab in the [ Budget Change Query Tool ](/bApps/InterjectTraining/Budget/BudgetChangeQueryToolSummary.html). Once Corporate has versioned your change, the Budget amount will be sycned through to Interject.

## Common Save Errors

![](/images/WCNTraining/Budget/BudgetUpload_LockLevelError.png)

*Budget is locked above your level in the Control Center. If you need to make changes, work with your supervisor to unlock Budget back to your level.*

___
![](/images/WCNTraining/Budget/BudgetUpload_DPAError.png)

*You need to be in the District Position Assignment at an approved position to use this tool for any saves. Your Division Controllers can add you to the DPA in Toolbox.*

___
<button class="collapsible">Other Possible Save Errors</button>
<div markdown="1" class="panel">
![](/images/WCNTraining/Budget/BudgetUpload_NotinDPAforDistrict.png)

*You need to be in the DPA for the district you are trying to save to. Your Division Controller can add you to the District Position Assignment in Toolbox.*

___
![](/images/WCNTraining/Budget/BudgetUpload_CannotUpdateAutocalcs.png)

*You cannot update Autocalc with this tool. Please remove the Account from your save.*
        
___
![](/images/WCNTraining/Budget/BudgetUpload_AfterCorpCutoffMessage.png)
![](/images/WCNTraining/Budget/BudgetUpload_AfterCorpCutoffRowMessageSingle.png)

*The save succeeded, but it is After Corp Cutoff for this District. The number will not be updated in Interject until Corp Cutoff is updated or BOD.*
</div>