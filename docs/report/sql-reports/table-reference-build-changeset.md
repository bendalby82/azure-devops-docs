---
title: Build Changeset tables 
titleSuffix: Azure DevOps Server
description: Learn how to use FactBuildChangeset to query for data about the changesets.
ms.technology: devops-analytics
ms.topic: reference
ms.assetid: 66ab6ac3-ff81-4ed7-9535-dd7ce9ebbb37
ms.author: kaelli
author: KathrynEE
monikerRange: '< azure-devops'
ms.date: 10/19/2021
---

# Build Changeset tables

[!INCLUDE [temp](../includes/tfs-report-platform-version.md)]

Use FactBuildChangeset and the associated dimension tables to query for data. Find out about the changesets that were incorporated in each build.
  
> [!IMPORTANT]  
> Build tables are only applicable for XAML builds, which are deprecated for TFS 2018 and later versions. If your build process isn't based on XAML builds, these tables and the TFS Warehouse for builds won't yield any meaningful data.  

For information about the measures and dimensions that are associated with these tables in the SQL Server Analysis Services cube, see [Builds](perspective-build-analyze-report-build-details-coverage.md).  
  
![Tables for Changesets in a Build](media/teamproj_factbuildchangeset.png "TeamProj_FactBuildChangeset")  
  
 FactBuildChangeset is associated with the following dimension tables:  
  
- DimBuild   
- DimChangeset    
- DimPerson   
- DimTeamProject  
  
For more information, see these articles:
- [Builds](perspective-build-analyze-report-build-details-coverage.md)   
- [Find and view changesets](../../repos/tfvc/find-view-changesets.md)   
- [Table reference for the relational warehouse database](table-reference-relational-warehouse-database.md) 
- [Continuous integration on any platform](../../pipelines/get-started/what-is-azure-pipelines.md)