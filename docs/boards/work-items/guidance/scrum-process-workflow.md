---
title: Scrum process work items types & workflow
titleSuffix: Azure Boards
description: How to guide for using the Scrum process  work item types and workflow to track work in Azure Boards, Azure DevOps, & Team Foundation Server 
ms.custom: work-items
ms.technology: devops-agile
ms.assetid: 34c866ea-a130-4371-bfc4-a3d9f87dccca
ms.topic: conceptual
ms.author: kaelli
author: KathrynEE
monikerRange: '>= tfs-2013'
ms.date: 11/19/2018
---

# Scrum process work item types and workflow  

[!INCLUDE [temp](../../includes/version-all.md)]

To plan a software project and track software defects using Scrum, teams use the product backlog item (PBI) and bug work item types (WITs). To gain insight into a portfolio of features, scenarios, or user experiences, product owners and program managers can map PBIs and bugs to features. When teams work in sprints, they define tasks which automatically link to PBIs and bugs.

![Scrum process, WITs used to plan and track](media/scrum-process-plan-wits.png) 

> [!NOTE]  
> If you are new to the Scrum process, review [About Sprints, Scrum and project management](../../sprints/scrum-overview.md) to get started. 

Using the web portal or Microsoft Test Manager, testers can create and run test cases and create bugs to track code defects. Impediments track blocking issues. 


[!INCLUDE [temp](../../includes/note-work-item-form-differences.md)]   

## Define PBIs and bugs  

When you define a product backlog item, you want to focus on the value that your customers will receive and avoid descriptions of how your team will develop the feature. The product owner can prioritize your product backlog based on each item's business value, effort, and relative dependency on other backlog items. As your business requirements evolve, so does your product backlog. Typically, teams specify details only for the highest priority items, or those items assigned to the current and next sprint.

You can create PBIs and bugs from the [quick add panel on the product backlog page](../../backlogs/create-your-backlog.md).  

<img src="media/IC675707.png" alt="Web portal, Agile process, Quick add panel " /> 

Later, you can open each PBI or bug to provide more details and estimate the effort. Also, by prioritizing the PBIs and bugs on the backlog page (which is captured in the Backlog Priority field), product owners can indicate which items should be given higher priority.  

![Product backlog item work item form](media/new-form-product-backlog-item.png)  


By defining the **Effort** for PBIs and bugs, teams can use the forecast feature and velocity charts to estimate future sprints or work efforts. By defining the **Business Value**, product owners can specify priorities separate from the changeable backlog stack ranking.

Use the following guidance and that provided for [fields used in common across work item types](#definitions-in-common) when filling out the form. For details about creating bugs, see [Manage bugs](../../backlogs/manage-bugs.md). 

:::row:::
   :::column span="1":::
   **Field/tab**
   :::column-end:::
   :::column span="3":::
   **Usage**
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::
   [Effort](../../queries/query-numeric.md)

   :::column-end:::
   :::column span="3":::
   Estimate the amount of work required to complete a PBI using any unit of measurement your team prefers, such as story points or time. A numeric value is required.  

   Agile [velocity charts](../../../report/dashboards/team-velocity.md) and [forecast](../../sprints/forecast.md) tools reference the values in this field. For additional guidance, see the [Estimating](/previous-versions/visualstudio/visual-studio-2013/hh765979(v=vs.120)) white paper.

   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   [Business Value](../../queries/query-numeric.md)

   :::column-end:::
   :::column span="3":::
   Specify a number that captures the relative value of a PBI compared to other PBIs. The higher the number, the greater the business value.

   :::column-end:::

:::row-end:::
:::row:::
   :::column span="1":::
   [Description](../../queries/titles-ids-descriptions.md)  

   :::column-end:::
   :::column span="3":::
   Provide enough detail for estimating how much work will be required to implement the item. Focus on who the feature is for, what users want to accomplish, and why. Don&#39;t describe how the feature should be developed. Do provide sufficient details so that your team can write tasks and test cases to implement the item. 

   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   [Acceptance Criteria](../../queries/titles-ids-descriptions.md) 

   :::column-end:::
   :::column span="3":::
   Define what &quot;Done&quot; means by describing the criteria that the team should use to verify whether the PBI or the bug fix has been fully implemented.<br /><br />Before work begins on a PBI or bug, describe the criteria for customer acceptance as clearly as possible. Conversations between the team and customers to determine the acceptance criteria helps ensure a common understanding within the team to meet customers&#39;  expectations. The acceptance criteria can be used as the basis for acceptance tests so that the team can more effectively evaluate whether an item has been satisfactorily completed.


   :::column-end:::
:::row-end:::


[!INCLUDE [temp](../../includes/discussion-tip.md)] 

## Track progress


As work progresses, you change the State field to update the status. Optionally, you can specify a reason. The state and reason fields appear on the work item form in the header area. 

<img src="media/scrum-bug-workflow-header-form.png" alt="Bug work item form, header area" /> 


### Scrum workflow states 

By updating the State, teams know which items are new, in progress, or completed. Most WITs support transition both forward and backward from each workflow state. These diagrams show the main progression and regression states of the PBI, bug, and task WITs. 

> [!div class="mx-tdBreakAll"]  
> |Product Backlog Item |Bug |Task |  
> |-------------|----------|---------| 
> |<img src="media/ALM_PT_Scrum_WF_PBI.png" title="Product Backlog Item workflow states, Scrum process " alt="Product Backlog Item workflow states, Scrum process" /> |<img src="media/ALM_PT_Scrum_WF_Bug.png" title="Bug workflow states, Scrum process"  alt="Bug workflow states, Scrum process" /> |<img src="media/ALM_PT_Scrum_WF_Task.png" title="Task workflow states, Scrum process"  alt="Task workflow states, Scrum process" /> |

PBIs and bugs follow this typical workflow progression:

-   The product owner creates a PBI or a tester creates a bug in the **New** state with the default reason, **New backlog item**  
-   The product owner moves the item to **Approved** after it is sufficiently described and ready for the team to estimate the level of effort. Most of the time, items near the top of the Product Backlog are in the Approved state, while items toward the middle and bottom are in a New state  
-   The team updates the status to **Committed** when they decide to commit to working on it during the sprint  
-   The item is moved to the **Done** state when the team has completed all its associated tasks and the product owner agrees that it has been implemented according to the Acceptance Criteria.  


### Update status with Kanban or taskboards

Teams can use the [Kanban board](../../boards/kanban-basics.md) to update the status of PBIs, and the [sprint taskboard](../../sprints/task-board.md) to update the status of tasks. Dragging items to a new state column updates both the State and Reason fields.

![Track progress on the Kanban board](../../boards/media/ALM_CC_MoveCard.png)

You can customize the Kanban board to support additional [swim lanes](../../boards/expedite-work.md) or [columns](../../boards/add-columns.md). For additional customization options, see [Customize your work tracking experience](#customize-work-tracking).


## Map PBIs to features

When you manage a suite of products or user experiences, you might want to view the scope and progress of work across the product portfolio. You can do this by [defining features](../../backlogs/define-features-epics.md) and [mapping PBIs to features](../../backlogs/organize-backlog.md).

Using portfolio backlogs, you can [drill down from one backlog to another](../../plans/portfolio-management.md) to view the level of detail you want. Also, you can use portfolio backlogs to view a rollup of work in progress across several teams when you [setup a hierarchy of teams](../../../organizations/settings/add-teams.md).

## Define tasks  

When your team manages their work in sprints, they can use the sprint backlog page to break down the work to be accomplished into distinct tasks.

![Add a task to an item in the sprint backlog](media/IC795962.png)  

Name the task and estimate the work it will take.

<img src="media/scrum-task-form.png" alt="Scrum process, Task work item form" />  

Using Scrum, teams forecast work and define tasks at the start of each sprint, and each team member performs a subset of those tasks. Tasks can include development, testing, and other kinds of work. For example, a developer can define tasks to implement PBIs, and a tester can define tasks to write and run test cases.

When teams estimate work using hours or days, they define tasks and the **Remaining Work** and **Activity** (optional) fields.

:::row:::
   :::column span="1":::
   **Field/tab**
   :::column-end:::
   :::column span="3":::
   **Usage**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   [Remaining Work](../../queries/query-numeric.md) 

   :::column-end:::
   :::column span="3":::
   Indicate how many hours or days of work remain to complete a task. As work progresses, update this field. It&#39;s used to calculate capacity charts, the sprint burndown chart, and the [Sprint Burndown (Scrum)](../../../report/sql-reports/sprint-burndown-scrum.md) report.<br />If you divide a task into subtasks, specify Remaining Work for the subtasks only. You can specify work in any unit of measurement your team chooses.

   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   [Activity](../../queries/query-numeric.md) 

   :::column-end:::
   :::column span="3":::
   Select the type of activity this task represents when your team estimates sprint capacity by activity.

   :::column-end:::
:::row-end:::


## Track test progress

### Test PBIs  

From the web portal or Test Manager, you can [create test cases that automatically link to a PBI or bug](../../../test/create-test-cases.md). Or, you can link a PBI or bug to a test case from the :::image type="icon" source="../../backlogs/media/icon-links-tab-wi.png" border="false"::: (links tab).  


<img src="media/IC793453.png" alt="Web portal, Select the test suite and add a test case" /> 


The test case contains a number of fields, many of which are automated and integrated with Test Manager and the build process. For a description of each field, see [Query based on build and test integration fields](../../queries/build-test-integration.md).

![Scrum Test case work item form](media/scrum-test-case-form.png)  

The :::image type="icon" source="../../backlogs/media/icon-links-tab-wi.png" border="false"::: (links tab) captures the links to all the PBIs and bugs in a test case. By linking PBIs and bugs to test cases, the team can track the progress made in testing each item.  

### Track code defects

You can [create bugs from the web portal web portal, Visual Studio, or when testing with Test Manager](../../backlogs/manage-bugs.md). 

[!INCLUDE [temp](../../includes/common-work-item-fields.md)]   

## Customize work item types
[!INCLUDE [temp](../../includes/customize-work-tracking.md)] 

## Related articles

[!INCLUDE [temp](../../includes/create-team-project-links.md)]  



### Track impediments

Use the impediment WIT to track events that may block progress or ship a PBI. Use the Bug WIT exclusively to track code defects.  

You can add an impediment from the [New work item widget](../../../report/dashboards/widget-catalog.md#new-work-item-widget) added to a [team dashboard](../../../report/dashboards/dashboards.md), or from the **New** menu on the Queries page. 

![Add work item from a New work item widget](media/scrum-new-work-item-widget.png)  

Work items you add from the widget are automatically scoped to your team's default area and iteration paths. To change the team context, see [Switch team context](../../../project/navigation/go-to-project-repo.md?toc=/azure/devops/boards/plans/toc.json&bc=/azure/devops/boards/plans/breadcrumb/toc.json).  


### Backlog list order

The [Backlog Priority](../../queries/planning-ranking-priorities.md) field is used to track the relative ranking of PBIs, bugs, features, or epics. However, by default it doesn't appear on the work item form. The sequence of items on the backlog page is determined according to where you have [added the items or moved the items on the page](../../backlogs/create-your-backlog.md#move-items-priority-order). As you drag items, a background process updates this field.  





### Links control, client work item form 

Work item forms displayed in a client and the web portal for TFS 2015 and earlier versions display link tabs and link control restrictions as described in the following table. 

:::row:::
   :::column span="1":::
   **Tab name**
   :::column-end:::
   :::column span="3":::
   **Work item type**
   :::column-end:::
   :::column span="3":::
   **Link restrictions**
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::
   **All Links**

   :::column-end:::
   :::column span="3":::
   Feedback Request

   Feedback Response

   :::column-end:::
   :::column span="3":::
   
   - No restrictions.

   
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Links**

   :::column-end:::
   :::column span="3":::
   Product Backlog Item

   Bug

   Impediment

   Shared steps

   Task

   Test Case

   

   :::column-end:::
   :::column span="3":::
   
   - No restrictions.

   
   

   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Links**

   :::column-end:::
   :::column span="3":::
   Code Review Request

   :::column-end:::
   :::column span="3":::
   
   - Allows only **Parent** and **Child** links to Code Review Response work items.

   - Excludes links to work items in other projects.

   
   

   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Stories**

   :::column-end:::
   :::column span="3":::
   Feedback Response

   :::column-end:::
   :::column span="3":::
   
   - Allows only **Related** links.

   - Allows links to Bug and Product Backlog Items.

   - Excludes links to work items in other projects.

   
   

   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Storyboards**

   :::column-end:::
   :::column span="3":::
   Product Backlog Item

   :::column-end:::
   :::column span="3":::
   
   - Allows only **Storyboard** links.

   
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Tasks**

   :::column-end:::
   :::column span="3":::
   Product Backlog Item

   :::column-end:::
   :::column span="3":::
   
   - Allows only **Child** links to Tasks.

   - Excludes links to work items in other projects.

   
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Test Cases**

   :::column-end:::
   :::column span="3":::
   Product Backlog Item

   Bug

   :::column-end:::
   :::column span="3":::
   
   - Allows only **Tested By** links.

   - Allows links only to test cases.

   - Excludes links to work items in other projects.

   
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   **Tested Backlog Items**

   :::column-end:::
   :::column span="3":::
   Test case

   :::column-end:::
   :::column span="3":::
   
   - Allows only **Tests** links.

   - Allows links to Bug and Product Backlog Items.

   - Excludes links to work items in other projects.

   
   :::column-end:::
:::row-end:::