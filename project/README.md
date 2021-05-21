# Project

### CBI v3

* Streamline \(decrease\) amendment process
* Introduce structured / template of conditions for automation. In the past, the conditions are freehand text of conditions
* No authority / guiding principle to guide how the conditions are written
* Change of activity A =&gt; B where the business activity no longer relevant does not need to "formal amendment process
* G's idea is to split condition into 2 part: fixed and free-hand text
* I's idea is similar to v2, but more of identification which is important and which is not
* Goal of ZeroOps:
* a\) We focus on conditions and OIC focus more on project and company assessment. 
* b\) Focus on automation of SI and more human touch on Non-SI 

### CBI

* Minimize room for errors and downstream issues, e.g. unnecessary amendments.
* Fixing the text saves you time from having to check for formatting issues in the Preview mode or Letter of Award.
* Translate project interests into fixed, clear language
* Ensure conditions are verifiable, and ultimately serves the scheme objectives.
* Standard Incentive \(SI\) is fixed regardless of the achievement
* Regular Incentive \(Non-SI\) is tiered according to the achievement

### What is Condition

EDB sets out project milestone conditions in the Letter of Award for companies to meet, in order to achieve incentive outcomes. \(i.e To quality for tranche 1 of the incentive, the Company shall fulfill all of the following conditions at the specified "Due Date" and maintain them until the specified "Maintain Till Date" at least specified Quantum\)

Flow - CB =&gt; LOA =&gt; APU =&gt; Amendment



Why there are two network call – projectMilestoneCondition \(PMC\) and condition-template \(CT\)?

**Creating a new application**

When creating a new application, Element BE call CB API \(tranche-template\) to retrieve the Preamble as well as Default Conditions and save this information into their database. In this process, we have the application Id and the scheme name.

**What extra information that we are retrieving when we are calling the PMC API?**

Background: Technically the PMC API call should give information on condition text that matches with whatever was displayed on the screen.

**First usage:** There are some inline parameter / highlighting in the actual condition. We do not want to reverse engineer, like where is this inline parameter going to be filled in. So, we make use the PMC API call to retrieve information and combine it with CT API call to retrieve the condition template. We make use of the information from PMC and fill in the \[ inlineparameter \] in the condition template.

When OIC update the value, the condition text get updated in the condition and there is no need to make additional API call to retrieve the information and reload the conditions text. That is why we need additional API call to CT and cannot rely everything on the PMC.

**Second usage** of CT is when we want to add condition. Because not all conditions needed in the scheme are supported in the PMC API call. Like Other conditions, Project Specific conditions, etc. So, when you click on the Add Condition button, there is no more network call as we already have all the information in CT API call.

**Third usage** We also make use of CT API to send all the version of the condition to frontend so that the PMC API call can tell us what version we are using for that particular condition \(stored in the metadata\). If no version provided, it is defaulted to version 1.

**In summary:** PMC is to show what the application is and CT is to display what we need to.

So, extra info that we got from CT are parameters \(input type, input width, input label, group condition, default date strategy, has Minimum Criteria\) and these info are not in PMC. We can put the information in the metadata but we choose not to, to keep metadata lean.

**Where are you pulling the condition wording from? \(Not from Element database\)**

It is from CT API call because we need to do the inline parameter and the job of displaying. But technically, the CT API can PMC API should match in term of the condition text.

PMC we retrieve the scheme name, application number and the previously saved user inputs.

CT network call is proxy to CB API which in turn return info what the inline parameter to show, what text to show \(like activity tag\) and preload all the conditions bank \(in add condition when needed\).

Example: help text is in the condition template and not in the project milestone condition.

If we make changes \(HelpText\) in the condition, it will be reflected in right away in the condition bank. But condition bank metadata always take precedence when we retrieve the information. If there is info in the metadata, we will not check the condition template.

**Linked Incentive**

When use add a linked incentive, Element will call the tranche- template API to save the new preamble and default condition. And force the reload on the widget and when reload, it will call the PMC network call and CT network call using the new application, then we will load the new information.

Elements create for us two additional columns: condition bank id and condition bank metadata

Why do we not keep everything in Element database? Because we cannot keep telling Element what to store, the work cycle is longer and take longer to apply to production.

We do not care how Element use Condition Bank during creating or loading, but what CB care \(or CB is dumb component\) is whenever we are called with showConditionBankWidget, we will display.

Element will call window.showConditionBankWidget with the application Number, version, config and we will make projectmilestonecondition api call using the application Number , version.

**Saving and updating**

When saving, the api call is api/v1/conditions/{conditionId} , this is element API to do the update in their database.

In this API call, we are also updating condition text that got updated in the inline parameter in the request payload and we save it on element, because elements will use the information to display in Letter of Acceptance.

**Edit / Preview mode**

Element has Edit and Preview Mode. When they load existing application, default is the preview mode, condition bank widget does not show. It will show Condition Section 2 \(NOT WIDGET\). They do not call showConditionWidget. Our widget only shows up in Edit mode.

**Tranche-template API**

-        Used when creating new tranche

-        Used when creating new application

We are not sure what they do with the data \(assume it is saved in the database\)

We act as API Proxy to bypass the authentication and authorization.

