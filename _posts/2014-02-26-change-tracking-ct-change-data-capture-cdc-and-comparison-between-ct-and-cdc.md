---
title: Change Tracking (CT),  Change Data Capture (CDC) and Comparison between CT and CDC
date: 2014-02-26 22:06
category: 
author: 
tags: [programming, sql]
summary: 
---

This week I had to learn more about the&nbsp;Change Tracking (CT)&nbsp;and&nbsp;Change Data Capture (CDC) that was introduced in SQL Server 2008.

To learn more about the subject I read the 3 articles written by&nbsp;<a title="Chandra Sekhar" href="http://www.codeproject.com/Members/SQLVERSITY" target="_blank">Chandra Sekhar</a>.

<strong>1)&nbsp;<a href="http://www.codeproject.com/Articles/537649/SQL-Server-Change-Tracking-CT" target="_blank">Change Tracking (CT)</a></strong>

<strong>2)&nbsp;</strong><a href="http://sqlversity.wordpress.com/2013/01/29/change-data-capture/" target="_blank"><strong>Change data Capture (CDC)</strong><strong>&nbsp;</strong></a>

<strong>3)</strong>&nbsp;<strong><a href="http://sqlversity.wordpress.com/2013/01/29/comparison-between-change-tracking-ct-and-change-data-capture-cdc/" target="_blank">Comparison between CT and&nbsp;CDC</a></strong>
<blockquote><strong>Background:</strong>

Prior to SQL Server 2008, developers had to create some custom tracking solutions using DML Trigger and additional tables to track the data which we have modified.
<ul>
 	<li>DML Triggers: These are the part of our transaction which contains the DML by which it is triggered. As we all know that, triggers are very expensive and we are using them in our transaction, the execution time will increase so that the performance of our project will be affected<strong>.&nbsp;</strong></li>
 	<li>Additional tables: By running the above DML triggers, we are able to track the data. But there is nothing to store these changes. To store this changed data, we need to create these additional tables. These tables will have similar columns as the tables which we need to track.</li>
</ul>
<h4>Drawbacks</h4>
<ul>
 	<li>Takes much time to develop/create DML triggers and additional tables</li>
 	<li>Performance hit</li>
 	<li>Very complex process</li>
</ul>
<h4>SQL Server 2008</h4>
To overcome the above drawbacks, SQL Server 2008 introduced powerful and efficient tracking mechanisms called<strong>&nbsp;Change Tracking (CT)&nbsp;</strong>and<strong>&nbsp;</strong><strong>Change data Capture (CDC)</strong><strong>&nbsp;</strong>
<h4><strong>Similarities:</strong></h4>
<ul>
 	<li>Both Track DML changes</li>
 	<li>Both Track whether column data has changes or not</li>
 	<li>Required to enable them on table as well as on database</li>
</ul>
<strong>Differences:</strong>
<table border="1">
<tbody>
<tr>
<td>
<h6><strong>S.No.</strong></h6>
</td>
<td>
<h6><strong>Change Tracking</strong></h6>
</td>
<td>
<h6><strong>Change Data Capture</strong></h6>
</td>
</tr>
<tr>
<td>1</td>
<td>It tracks only whether the data has been changed or not. But never captures the modified values</td>
<td>It captures values also</td>
</tr>
<tr>
<td>2</td>
<td>It follows synchronous tracking mechanism to track the data</td>
<td>It follows asynchronous tracking mechanism which reads data changes from ldf file</td>
</tr>
<tr>
<td>3</td>
<td>It works in all the editions of SQL Server like Express, Workgroup, Web, Standard, Enterprise, DataCenter</td>
<td>It works only in Enterprise and DataCenter editions</td>
</tr>
<tr>
<td>4</td>
<td>Does not hold historical data</td>
<td>Holds historical data</td>
</tr>
<tr>
<td>5</td>
<td>No need to access ldf file of that particular database</td>
<td>Needs to access ldf file of that particular database</td>
</tr>
<tr>
<td>6</td>
<td>Uses temp db</td>
<td>Uses Transaction log (ldf file)</td>
</tr>
<tr>
<td>7</td>
<td>Returns less information regarding the changes in the data</td>
<td>Returns more information compared to CT</td>
</tr>
<tr>
<td>8</td>
<td>Little bit difficult to get the full data of the table for which we have to join CHANGETABLE with the table based on primary key</td>
<td>We can query directly from tables</td>
</tr>
<tr>
<td>9</td>
<td>SQL Server agent is not required to track the data</td>
<td>SQL Server Agent should be enabled to capture the data</td>
</tr>
<tr>
<td>10</td>
<td>We can enable it on a table when the table has primary key on it</td>
<td>No restriction as it is in the CT</td>
</tr>
<tr>
<td>11</td>
<td>User can truncate the table when it is enabled on the table</td>
<td>User can not truncate when it is enabled on the table</td>
</tr>
<tr>
<td>12</td>
<td>We can turn off auto clean up</td>
<td>We can’t turn off</td>
</tr>
<tr>
<td>13</td>
<td>Only SYSADMIN can enable CT</td>
<td>Only DBOwner can enable CDC</td>
</tr>
</tbody>
</table>
</blockquote>