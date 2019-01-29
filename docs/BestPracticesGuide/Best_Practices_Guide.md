---
title: "Best Practices Guide"
date: 2018-11-14T11:59:23+05:30
draft: false
weight: 4
---
# Best Practices Guide

Given below are the best practices to follow for different file types
when updating your products. Following these best practices ensures a
seamless update process and a lower number of merge conflicts.

<table>
<thead>
<tr class="header">
<th>File Type</th>
<th>Best Practices</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>.jar files</td>
<td><p>Do not modify the original .jar files.</p>
<p>When updating your product, the WSO2 in-place tool replaces the existing .jar files with updated ones. If you modify the original .jar files, your customization will be lost. To avoid this, use an extension point as explained in Using Extension Points in Carbon and https://github.com/wso2-extensions. See https://store.wso2.com/store/pages/top-assets for a list of released connectors and extensions.</p></td>
</tr>
<tr class="even">
<td>.war files</td>
<td><p>Do not modify .war files.</p>
<p>It is not recommended to modify .war files. In case you have modified .war files in your distribution, after updating your product distribution, reapply your modifications in the updated .war files.</p></td>
</tr>
<tr class="odd">
<td>.car files</td>
<td><p>Do not modify the original .car files. In case your original product distribution contains .car files, do not modify them as they can be changed by continuous updates.</p></td>
</tr>
<tr class="even">
<td>.jag/.js files</td>
<td>Maintain the same code indentation of the original .js files in the updated .js files.</td>
</tr>
<tr class="odd">
<td>.jks files</td>
<td>The in-place update tool doesn't update .jks files.</td>
</tr>
<tr class="even">
<td>.json files</td>
<td><div class="content-wrapper">
<p>Maintain the same code indentation of the original .json files in the updated .json files. Else, there will be merge conflicts.</p>
??? note "Click to see example"
<p>Shown below is the difference between a .json file before and after a modification. As shown, the indentation has changed in the updated file and this might result in a merge conflict in the WSO2 in-place update tool.</p>

<p>Maintain the order of the .json file as much as possible. For example, when you add a new key-value pair, add it to the end of the file.</p>
??? note "Click to see example"
<p>Shown below is the difference between a .json file before and after a modification. As shown, the new key-value pair is not added to the end of the file. As a result, line number 2 in the original file is not the same as the updated file, which will cause a merge conflict in the WSO2 in-place update tool.</p>

There will not be merge conflicts when the new line is added to the end of the file, preserving the original order:


</div>
</div>
</div>
</div></td>
</tr>
</tbody>
</table>
