---
title: Query by history  
titleSuffix: Azure Boards
description: Learn how to query comments and history to work items to support audit requirements when working in Azure Boards
ms.technology: devops-agile
ms.assetid: A5AC271A-8DF0-40AD-9867-1B1E9E5B1FE9
ms.author: kaelli
author: KathrynEE
ms.topic: example-scenario
monikerRange: '>= tfs-2013'
ms.date: 08/27/2020
---

# Query history and discussion fields   

[!INCLUDE [temp](../includes/version-all.md)]

The history of a work item tells you who opened the item, what changed, and why. This information helps you track how an item changes over time. When you enter information in the history field, provide as much information as possible to help the next work item owner understand what has happened and what they have to do.  

> [!NOTE]  
> There is no Discussion work item field. To query work items with comments entered in the Discussion area, you filter on the History field. The full content of the text entered into the Discussion text box is added to the History field. 

## Supported operators and macros 

Query clauses that specify the **History** field can use the **Contains Words** and **Does Not Contain Words** operators. Search against an exact phrase or to use the wildcard character, *. You can only use the wildcard character at the end of a partial word or phrase.

The **History** field is automatically indexed for full-text search when full-text search is available. See Full-Text and partial word searches 

<a id="query-history" />

## Query the History of a work item 

You can use either the web portal or Team Explorer to view the history of a work item or find work items based on the contents of the **History** field. When you perform a search on the contents of the **History**  field, it returns only work items that have changes recorded in that field. That is, it doesn't register changes that were made to text in other fields.  

#### [Browser](#tab/browser/)
<a id="team-services" /> 

::: moniker range=">= tfs-2017"
![Screenshot of Query Editor to Search for items based on words contained in the History field.](media/hist-audit-query-ts-bt.png)
::: moniker-end

::: moniker range=">= tfs-2013 <= tfs-2015"
![Screenshot of Query Editor to Search for items based on words contained in the History field, earlier versions.](media/ALM_HA_HistoryQuery.png) 
::: moniker-end


#### [Visual Studio 2015](#tab/visual-studio/)
<a id="tee-query-history" />
<a id="team-explorer" />


The **Query Editor** isn't available when you are connected to a GitHub or third-party Git repository. Also, it isn't available from Visual Studio 2019 under the following conditions:   
* If you are set to use the default Landing page experience as described in [Set the Work Items experience in Visual Studio 2019](../work-items/set-work-item-experience-vs.md).  
* If you are set to use the new Git Tool as described in [Git experience in Visual Studio](/visualstudio/ide/git-with-visual-studio).  
 

**Visual Studio/Team Explorer and Team Explorer Everywhere**

![Screenshot of Query Editor to Search for items based on words contained in the History field in Team Explorer.](media/hist-audit-query-team-explorer.png) 

* * *
## List items based on the contents of the History field  

::: moniker range=">= tfs-2017"
You use the query editor to add the **History** field to a [query clause](using-queries.md). Comments entered into the **Discussion** area are queryable. Change history entries, such as which fields were changed, aren't queryable. To quickly find items based on words entered into the Discussion area, or **Description** or other rich-text fields, consider using [work item search](../../project/search/functional-work-item-search.md).
::: moniker-end

::: moniker range=">= tfs-2013 <= tfs-2015"
You use the query editor to add the **History** field to a [query clause](using-queries.md). Comments entered into the **History** field are queryable. Change history entries, such as which fields were changed, aren't queryable.
::: moniker-end

You can filter for work items by the date on which they were changed or for a specific time period. If you limit the scope of your query, it can help with performance by only returning those results that fit the date range that you want to include. 

:::row:::
   :::column span="1":::
   **Filter for**
   :::column-end:::
   :::column span="1":::
   **Include these query clauses**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   Items whose History field contains the word &quot;reproducible&quot;  
   :::column-end:::
   :::column span="1":::
   
   `History Contains Words reproducible`  
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   Items whose History field doesn&#39;t contain the word &quot;beta&quot;
   :::column-end:::
   :::column span="1":::
   
   `History Does Not Contain Words beta`
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Items that contain the phrase &quot;stack traces&quot; and were closed but reactivated
   :::column-end:::
   :::column span="1":::
   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`History Contains Words stack traces`  `And State Was Ever Closed`  
`And State <>  Closed`  
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Items closed within a specified time period
   :::column-end:::
   :::column span="1":::
   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`State = Done`  
`And Closed Date > 7/1/2015`  
`And Closed Date <= 7/21/2015`  
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Items I&#39;ve been associated with 
   :::column-end:::
   :::column span="1":::
   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`History Contains Words MyName`  
`Or Assigned To Was Ever _ @Me`  
   :::column-end:::
:::row-end:::
  

### Tips for using the query editor

- Type the complete word or phrase that is specified in the **History** field of those work items that you want to find.
- Enter the full text for the word that you want to search. The **History** field is indexed for full-text search. If you enter only a partial word, the query will not return work items that contain the full word. For example, if the **History** field contains the phrase *reproducible behavior* and you search for *repro*, the work item will not be found. However, if you search for the complete word *reproducible*, the work item will be found. You can also search for the string with a wild card, such as `repro*`. 
- The query editor ignores common words or stop words as defined in  [Configure and Manage Stopwords and Stoplists for Full-Text Search](/sql/relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search).
- On the query editor toolbar, choose ![Run query](../media/icons/run_query.png) or ![Run query, earlier version](../media/icons/run_query_te.png) icon and confirm that your query returns expected results. 
- If you don&#39;t receive the results you expect, adjust the word or phrase that you entered, and run the query again. 
 


<a id="view-history" />

## View the history of work items  

An entry is made to the **History** field each time a work item is saved. To view the history of changes, open an existing work item, and then choose the ![history tab icon](../media/icons/icon-history-tab-wi.png) or **History** tab, or for some work item types, choose the **Details** tab. 

<a id="web-portal-explorer-tab" /> 
The history details shown depend on the platform, version, and client you user. 

#### [Browser](#tab/browser/)
<a id="team-services-tab" /> 
<a id="team-services-view" /> 

::: moniker range=">= tfs-2017"

![Screenshot of Work item form, Web portal, Choose History tab.](media/hist-audit-wi-form-vsts-tab.png)  

The state change history diagram appears first. To see the entire history of state changes, choose **Show all**.

![Screenshot of Work item form, Web portal, State change history diagram (web portal only).](media/state-change-history-diagram.png)

Choose an entry in the left pane to view the details of changes made.

![Screenshot of Work item form, History tab, Web portal, Details.](media/hist-audit-wi-form.png)  

::: moniker-end

::: moniker range="tfs-2017"
> [!NOTE]  
> With TFS 2017 and later versions, the **History** field is no longer a rich-text field. To annotate the work item history, add to the **Description** or **Discussion** fields. 
::: moniker-end


::: moniker range=">= tfs-2013 <= tfs-2015"

To view only the comments that were added to the log, choose the **Discussion Only** tab. To view all changes made to the item, choose the **All Changes** tab, and then choose the **show all changes** link for a specific date and time.  

![Screenshot of Work item form, History tab, Web portal, earlier versions](media/hist-audit-choose-history-tab-tfs.png) 

::: moniker-end


#### [Visual Studio](#tab/visual-studio/)

To view only the comments that were added to the log, choose the **Discussion Only** tab. To view all changes made to the item, choose the **All Changes** tab, and then choose the **show all changes** link for a specific date and time.  

![Screenshot of Work item form, Team Explorer, History tab.](media/ALM_HA_AllChanges.png) 

* * *
## Fields that support history, auditing, and revision tracking 

You can use the following fields to filter queries and create reports. Several of these fields are populated with information as a work item progresses from one state to another. Other fields update when the work item is modified. Some fields don't appear on the work item form, but they are tracked for the WITs listed.  


:::row:::
   :::column span="1":::
   **Field name**
   :::column-end:::
   :::column span="2":::
   **Description**
   :::column-end:::
   :::column span="1":::
   **Work item type**
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::
   
   Changed By

   :::column-end:::
   :::column span="2":::
   
   The name of the team member who modified the work item most recently.

   Reference name=System.ChangedBy, Data type=String

   :::column-end:::
   :::column span="1":::
   All
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Change Date

  
   :::column-end:::
   :::column span="2":::
   
   The date and time when a work item was modified.

   Reference name=System.ChangedDate, Data type=DateTime

  
   :::column-end:::
   :::column span="1":::
   All
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Closed Date <sup>1</sup> 

  
   :::column-end:::
   :::column span="2":::
   
   The date and time when a work item was closed.

   Reference name=Microsoft.VSTS.Common.ClosedDate, Data type=DateTime

  
   :::column-end:::
   :::column span="1":::
   All
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Created Date

  
   :::column-end:::
   :::column span="2":::
   
   The date and time when a work item was created.
 
   Reference name=System.CreatedDate, Data type=DateTime

  
   :::column-end:::
   :::column span="1":::
   All
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   History
   :::column-end:::
   :::column span="2":::
   
   The record of changes that were made to the work item after it was created. Every time that the work item is updated, information is appended to the history, which specifies the date of the change, who made the changes, and which fields were changed. 
   
   > History field queries return work items whose Discussion comments or Description fields contain words that match the keywords entered. You can't use the History field to query on changes made to other fields. 
 
   You can't add formatted text to the history field. Once you&#39;ve saved the work item, you can't alter the history. 

   The `History` field, along with the `Description`, `Steps to Repro` and `Title` fields are automatically indexed for full-text search as described in [Query fields, operators, and macros](query-operators-variables.md). 

   Reference name=System.History, Data type=History

   :::column-end:::
   :::column span="1":::
   
   All
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   Resolved Date <sup>1</sup> 

  
   :::column-end:::
   :::column span="2":::
   
   The date and time when the work item was moved into a Resolved state. 

   Reference name=Microsoft.VSTS.Common.ResolvedDate, Data type=DateTime

  
   :::column-end:::
   :::column span="1":::
   Bug (Agile, CMMI) 
  
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::
   
   Rev

   :::column-end:::
   :::column span="2":::
   
   A number that is assigned to the historical revision of a work item. 

   Reference name=System.Rev, Data type=Integer

   :::column-end:::
   :::column span="1":::
   All
   :::column-end:::
:::row-end:::


:::row:::
   :::column span="1":::
   
   State Change Date

  
   :::column-end:::
   :::column span="2":::
   
   The date and time when the value of the State field changed.

   Reference name=Microsoft.VSTS.Common.StateChangeDate, Data type=DateTime

  
   :::column-end:::
   :::column span="1":::
   All
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::
   
   <a id="test-suite-audit"/>Test Suite Audit
  
   :::column-end:::
   :::column span="2":::
   
   Tracks additional operations performed when modifying a test suite, for example: adding tests to a test suite or changing configurations. This field can be viewed through the History tab or through a separate query. There will be a consolidated history view, including changes performed to work items field and changes resulting from related artifacts such as test points and configurations.

   Reference name=Microsoft.VSTS.TCM.TestSuiteAudit, Data type=PlainText


  
   :::column-end:::
   :::column span="1":::
   
   Test Suite
  
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::
   
   <a id="watermark"/>Watermark
  
   :::column-end:::
   :::column span="2":::
   
   A system managed field (not editable) that increments with changes made to a work item.

   Reference name=System.Watermark, Data type=Integer


  
   :::column-end:::
   :::column span="1":::
   
   All
  
   :::column-end:::
:::row-end:::



> [!NOTE]  
> 1. For these fields to be defined for a WIT, they must be included in the `WORKFLOW` section of the WIT definition. For example, this syntax is included within the `FIELDS` definition when transitioning to a Resolved state:
> 
>    ```xml
>    <FIELD refname="Microsoft.VSTS.Common.ResolvedDate">  
>       <SERVERDEFAULT from="clock" />  
>    </FIELD>  
>     ```

## Related articles


- [Query editor](using-queries.md)
- [Query fields, operators, and macros](query-operators-variables.md)   
- [Query by date or current iteration](query-by-date-or-current-iteration.md)
 

[!INCLUDE [temp](../includes/rest-apis-queries.md)]



