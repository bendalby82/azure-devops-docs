---
title: Deploy to IIS on a Windows VM (Classic)
description: Deploy an ASP.NET or Node.js web deployment package to an IIS web server on a Windows virtual machine using Deployment Groups
ms.assetid: 979E4504-C88A-4D0A-A912-6E5998D87445
ms.topic: quickstart
ms.custom: seodec18
ms.author: ronai
author: RoopeshNair
ms.date: 09/07/2021
monikerRange: '>= tfs-2018'
---

# Deploy to a Windows Virtual Machine

[!INCLUDE [version-tfs-2018](../../includes/version-tfs-2018.md)]

Learn how to set up continuous deployment of your ASP.NET or Node.js app to an IIS web server running on Windows using
Azure Pipelines. You can use the steps in this quickstart as long as your continuous integration pipeline publishes a web deployment package.

After you commit and push a code change, it is automatically built and then deployed. The results will automatically show up on your site.

## Define your CI build pipeline

You'll need a continuous integration (CI) build pipeline that publishes your web deployment package. To set up a CI build pipeline, see:

* [Build ASP.NET 4 apps](../aspnet/build-aspnet-4.md)

* [Build ASP.NET Core apps](../../ecosystems/dotnet-core.md)

* [Build JavaScript and Node.js apps](../../ecosystems/javascript.md)

## Prerequisites

### IIS configuration

The configuration varies depending on the type of app you are deploying.

#### ASP.NET app

[!INCLUDE [prepare-aspnet-windows-vm](../includes/prepare-aspnet-windows-vm.md)]

#### ASP.NET Core app

[!INCLUDE [prepare-aspnetcore-windows-vm](../includes/prepare-aspnetcore-windows-vm.md)]

#### Node.js app

Follow the instructions in [this topic](https://github.com/Azure/iisnode) to install and configure IISnode on IIS servers.

[!INCLUDE [create-deployment-group](../includes/create-deployment-group.md)]

## Define your CD release pipeline

Your CD release pipeline picks up the artifacts published by your CI build and then deploys them to your IIS servers.

1. If you haven't already done so, install the [IIS Web App Deployment Using WinRM](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.iiswebapp)
   extension from Marketplace. This extension contains the tasks required for this example.

1. Do one of the following:

   * If you've just completed a CI build then, in the build's **Summary** tab choose **Release**.
     This creates a new release pipeline that's automatically linked to the build pipeline.

   * Open the **Releases** tab of **Azure Pipelines**, open the **+** drop-down
     in the list of release pipelines, and choose **Create release pipeline**.

1. Select the **IIS Website Deployment** template and choose **Apply**.

1. If you created your new release pipeline from a build summary, check that the build pipeline
   and artifact is shown in the **Artifacts** section on the **Pipeline** tab. If you created a new
   release pipeline from the **Releases** tab, choose the **+ Add** link and select your build artifact.

1. Choose the **Continuous deployment** icon in the **Artifacts** section, check that the continuous deployment trigger is enabled,
   and add a filter to include the **main** branch.

1. Open the **Tasks** tab and select the **IIS Deployment** job. For the **Deployment Group**, select the deployment group you created earlier (such as *myIIS*).

1. Save the release pipeline.

## Create a release to deploy your app

You're now ready to create a release, which means to run the release pipeline with the artifacts produced by a specific build. This will result in deploying the build:

[!INCLUDE [simple-create-release](../includes/simple-create-release.md)]

## Next steps

* [Dynamically create and remove a deployment group](howto-webdeploy-iis-deploygroups.md#depgroup)
* [Apply stage-specific configurations](howto-webdeploy-iis-deploygroups.md#envirconfig)
* [Perform a safe rolling deployment](howto-webdeploy-iis-deploygroups.md#rolling)
* [Deploy a database with your app](howto-webdeploy-iis-deploygroups.md#database)
