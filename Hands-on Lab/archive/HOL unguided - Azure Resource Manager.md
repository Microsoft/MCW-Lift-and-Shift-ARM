![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Azure Resource Manager
</div>

<div class="MCWHeader2">
Hands-on lab unguided
</div>

<div class="MCWHeader3">
August 2018
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.
© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Azure Resource Manager hands-on lab unguided](#azure-resource-manager-hands-on-lab-unguided)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Overview](#overview)
    - [Solution architecture](#solution-architecture)
    - [Requirements](#requirements)
    - [Help references](#help-references)
    - [Exercise 1: Configure Automation account](#exercise-1-configure-automation-account)
        - [Task 1: Create Azure Automation account](#task-1-create-azure-automation-account)
    - [Exercise 2: Define the network foundation](#exercise-2-define-the-network-foundation)
        - [Task 1: Define the network foundation](#task-1-define-the-network-foundation)
    - [Exercise 3: Extend with Compute](#exercise-3-extend-with-compute)
        - [Task 1: Add storage and set to use Premium](#task-1-add-storage-and-set-to-use-premium)
        - [Task 2: Add a virtual machine for the web server](#task-2-add-a-virtual-machine-for-the-web-server)
        - [Task 3: Add a virtual machine for the SQL Server](#task-3-add-a-virtual-machine-for-the-sql-server)
        - [Task 4: Deploy completed solution to Azure](#task-4-deploy-completed-solution-to-azure)
    - [Exercise 4: Lock down the environment](#exercise-4-lock-down-the-environment)
        - [Task 1: Restrict traffic to the web server](#task-1-restrict-traffic-to-the-web-server)
        - [Task 2: Update the network security group to allow Windows Remote Desktop](#task-2-update-the-network-security-group-to-allow-windows-remote-desktop)
    - [Exercise 5: Scale out the deployment](#exercise-5-scale-out-the-deployment)
        - [Task 1: Parameterize the size of the environment and add load balancing](#task-1-parameterize-the-size-of-the-environment-and-add-load-balancing)
    - [After the hands-on lab](#after-the-hands-on-lab)
        - [Task 1: Delete the resource groups created](#task-1-delete-the-resource-groups-created)

<!-- /TOC -->

# Azure Resource Manager hands-on lab unguided

## Abstract and learning objectives 

In this hands-on lab, you will learn how to author an Azure Resource Manager (ARM) template that can be used to deploy infrastructure such as virtual machine, storage, and networking. This lab will also teach the you how to deploy virtual machines that are automatically configured by the Azure Automation Desired State Configuration (DSC) service.

By the end of this lab, you will be better able to migrate and enable easy deployment for lift-and-shift capabilities. In addition, you will learn to build and deploy complex infrastructure solutions with Azure Resource Manager templates, work with Azure Automation Desired State Configuration (DSC) for deploying server configurations, as well as scale existing templatized deployments leveraging VM Scale Sets.

## Overview

Lucerne Publishing is one of the largest English-language publishers in the world. With nearly 200 years of history, Lucerne has published some of the world's foremost authors, including Nobel Prize, Pulitzer Prize, National Book Award, Newbery Medal and Caldecott Medal winners. Lucerne is consistently at the forefront of innovation, using digital technology to create unique reading and viewing experiences and expand the reach of its authors and documentary producers.

Lucerne is starting a three-year project to move most of its data center footprint to the cloud. "We are convinced that cloud implementations will give us cost savings and more importantly, deliver operational flexibility," says Greg Vernon, head of infrastructure and enterprise operations at Lucerne. "Like every other business, we are under constant pressure to do more with less. We believe that cloud computing will be substantially cheaper over time than in-house data centers."

The company has asked you to define an Azure Resource Manager (ARM) template that can deploy their application CloudShop and its associated database using Azure Virtual Machines.

## Solution architecture

![This image is a representation of the Solution Architecture.](images/Hands-onlabstep-by-step-AzureResourceManagerimages/media/image2.png "Solution Architecture")

## Requirements

- Azure Subscription
- Understanding of Azure Infrastructure as a Service components
- Familiarity with JavaScript Object Notation (JSON)
- Familiarity with PowerShell

## Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| Creating and deploying Azure resource groups through Visual Studio | https://docs.microsoft.com/en-us/azure/azure-resource-manager/vs-azure-tools-resource-groups-deployment-projects-create-deploy | 
| Azure Quick Start Templates | <https://azure.microsoft.com/en-us/resources/templates/> |
| Using Managed Disks with Templates | <https://docs.microsoft.com/en-us/azure/virtual-machines/windows/using-managed-disks-template-deployments> |
| Azure VM Scale Sets Templates | <https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-mvss-start> |
| Azure DSC Extension for Virtual Machines | <https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/dsc-template> |
| Azure Virtual Machine Scale Sets | <https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/> |
| Azure Virtual Machine Scale Sets and Azure Automation DSC| <https://github.com/Azure/azure-quickstart-templates/tree/master/201-vmss-automation-dsc> |
| App Service for Linux | <https://docs.microsoft.com/en-us/azure/app-service/containers/app-service-linux-intro/> |
| Azure CLI | <https://docs.microsoft.com/en-us/cli/azure/install-azure-cli/> |



## Exercise 1: Configure Automation account

Duration: 15 minutes

Contoso has asked you to create an ARM template that will configure the
network for a proof of concept deployment of their new application
CloudShop. Before creating the ARM Template, you must first create and
configure an Azure Automation account using the Azure portal.

### Task 1: Create Azure Automation account

**Tasks to complete**

-   Create Automation account in Azure portal.

-   Upload the Web and SQL .ps1 files found in the C:\\Hackathon
    directory (downloaded student files from Exercise 0 -- Task 2).

-   Compile the files so they are available to virtual machines that.
    check-in

**Exit criteria**

-   You log into the portal and verify creation of the Azure Automation
    account, taking note of the Registration URL, Registration Keys, and
    the names of the nodes you compiled.

## Exercise 2: Define the network foundation

Duration: 15 minutes

Contoso has asked you to create an ARM template that will configure the
network for a proof of concept deployment of their new application
CloudShop.

### Task 1: Define the network foundation

**Tasks to complete**

-   Create a new ARM template solution using Visual Studio and name the
    Project **ARMHackathon** in the **C:\\Hackathon** directory.

-   Using Visual Studio, create a Virtual Network in the template named
    **hackathonVnet**.

-   Rename **Subnet1** to **FrontEndNet**.

-   Rename **Subnet2** to **DatabaseNet**.

-   Using Visual Studio, deploy the Virtual Network to Azure in a
    Resource Group called **ARMHackathon**.

**Exit criteria**

-   A Virtual Network deployed to your Azure subscription containing the
    following virtual network characteristics:

    -   Resource Group: **ARMHackathon**

    -   Name: **hackathonVNET**

    -   Address space: **10.0.0.0/16**

    -   Subnet: FrontEndNet -- **10.0.0.0/24**

    -   Subnet: DatabaseNet -- **10.0.1.0/24**

## Exercise 3: Extend with Compute

Duration: 60 minutes

The next task is to update the template by adding a storage account, a
Public IP, and virtual machines for the web server(s) and a SQL server.
The servers will be automatically configured using a PowerShell DSC
script supplied to you by the infrastructure team.

### Task 1: Add storage and set to use Premium

**Tasks to complete**

-   Add a new storage account to the template named **hackstorage**. All
    virtual machines in the template will use this storage account.

-   Change the default storage account type to use Premium Storage.

**Exit criteria**

-   A new storage account in the template.

-   The new storage account should default to using Premium Storage in
    the template.

### Task 2: Add a virtual machine for the web server

**Tasks to complete**

-   Add the following resources to the template:

    -   A Windows VM for the web front-end named **hackathonVM**.

    -   Change the default Windows OS Version to be **2016-Datacenter**,
        and make sure that is the only OS Version that can be selected.

    -   Update the size of the VM to be a Standard DS1 version 2 so that
        it can use Premium Storage.

    -   Add a Public IP named **hackathonPublicIP** linked to the NIC of
        the web VM.

    -   Azure DSC Extension:

        -   This DSC Extension is named **hackathonDSC** for the web
            servers that use the CloudShopWeb.WebServer configuration
            node of your Automation account.

**Exit criteria**

-   Windows VM that will be running Windows Server Datacenter 2016 with
    a Public IP was added to the template. This VM will check-in with
    Azure Automation DSC to receive its configuration upon provisioning
    and continue to check in to ensure its configuration is correct.

-   The template should accept parameters for the Registration URL,
    Registration Key, and Configuration Node name(s) of the Automation
    account.

### Task 3: Add a virtual machine for the SQL Server

**Tasks to complete**

-   Add the following resources to the template:

    -   A Windows VM for the databased backend named **hackathonSqlVM**.

    -   Update the Image Publisher to allow for SQL Server Images, and
        insure that the SQL Server version deployed will be 2016.

    -   Replace the new SQL VM's WindowsOSVersion parameter with a new
        parameter that allows the administrators to choose from the
        different versions of SQL available for 2016: Web, Standard,
        Enterprise.

    -   Add a new parameter to allow the Administrator to choose which
        size of SQL Server they want from Standard DS1 -- Standard DS5
        version 2.

    -   Change the OS Disk to use managed disks and add two empty 1 TB Data Disks to the SQL Server (also managed).

    -   Azure DSC Extension:

        -   This DSC Extension is named **hackathonDSCSql** for the SQL
            database that configures the SQL Server and restores the
            AdventureWorks database.

        -   The scripts for the DSC Configurations are in C:\\Hackathon.

        -   Add a dependency on the DSC extension for the web tier to
            the DSC extension for the SQL server. This allows for the
            virtual machines to be provisioned in parallel but the
            customizations to be orchestrated.
            
**Exit criteria**

-   SQL Server virtual machine named **hackathonSqlVM**.

    -   The variables named **hackathonSQLVMImagePublisher** and
        **hackathonSqlVMImageOffer** that contain the image
        configuration should use the following:

        -   Image Publisher: **MicrosoftSQLServer**

        -   Image Offer: **SQL2016-WS2016**

    -   The parameter **hackathonSQLVMWindowsOSVersion** should be
        deleted.

    -   The VM should accept a parameter named **hackathonSqlVMSKU**
        that allows the user to specify the SQL Server SKU using one of
        the following values. The **default** value should be **Web**.

        -   **Web, Standard, Enterprise**

    -   Should have a parameter that specifies the size of the virtual
        machine. The default value should be Standard\_DS2.

        -   Standard\_DS1\_v2, Standard\_DS2\_v2, Standard\_DS3\_v2,
            Standard\_DS4\_v2, Standard\_DS5\_v2

    -   The virtual machine should have 2 x 1 TB Data Disks attached.

    -   The PowerShell DSC Script will perform the following based on
        this configuration:

        -   Data Disks combined into a 2TB volume using Windows Storage
            Spaces.

        -   The SQL Server should have the default path for data, logs,
            and backup referring to the F: drive and the database should
            be restored to the F: drive.

        -   SQL Server should be in mixed authentication mode.

### Task 4: Deploy completed solution to Azure

**Tasks to complete**

-   Save all changes to the Visual Studio Solution named ARMHackathon.

-   Copy the contents of azuredeploy.json into
    [www.jsonlint.com](http://www.jsonlint.com), and determine if the
    json is clean.

-   Using Visual Studio perform a new deployment.

-   After the deployment is complete, check the status of the Servers in
    Azure Automation DSC. Once they show compliant, move on to the next
    task.

-   Locate the DNS name used for the web front-end VM. Paste this name
    into a new browser window.

**Exit criteria**

-   All the resources you added are now found in the **ARMHackathon**
    resource group.

-   The website loads, and the CloudShop application is now useable.

    ![The Cloud Shop webpage displays, with a list of products from
    which to
    choose.](images/Hands-onlabunguided-AzureResourceManagerimages/media/image18.png "Cloud Shop webpage")

## Exercise 4: Lock down the environment 

Duration: 15 minutes

In this portion of the hackathon, you will deploy a network security
group to restrict the network attack surface for the deployment.

### Task 1: Restrict traffic to the web server

**Tasks to complete**

-   Create and deploy a network security group (NSG), named
    **hackathonNetworkSecurityGroup** that allows the following traffic
    on the **FrontEndNet** subnet:

    -   Source: INTERNET, Destination port: 80

-   Update the **hackathonVnet** to show it depends on the newly created
    **hackathonNetworkSecurityGroup**.

**Exit criteria**

-   The NSG is now deployed to the **ARMHackathon** resource group.

-   Validate restrictions by connecting to the web server using a web
    browser. Traffic should be allowed in, and the site should load.

-   Attempt to connect using remote desktop and click **Connect** in the
    portal. This connection should fail.

-   The **hackathonVnet** **dependsOn** array should be updated to
    reference **hackathonNetworkSecurityGroup**.

### Task 2: Update the network security group to allow Windows Remote Desktop 

**Tasks to complete**

-   Update the network security group on the deployed resources to allow
    the remote desktop protocol (port 3389).

**Exit criteria**

-   Access to the web front-end should be successful by clicking
    **Connect** in the Azure Preview Portal.

-   The website should still load when directing a web browser to the
    web frond end VM's Public IP Address.

-   In the Azure portal, there should now be 2 Inbound Security Rules:
    webrule for HTTP/80, and rdprule for TCP/3389.

## Exercise 5: Scale out the deployment

Duration: 60 minutes

In this portion of the exercise, you will use the Azure Virtual Machine
Scale Sets feature to scale out the web front-end and the storage sub
system.

> Note: This is an *advanced* configuration based on the feature Azure
Scale Sets. It is recommended that unless you have configured scale sets
before that you use the Leader's guide with the hackathon answers to
complete this exercise.

### Task 1: Parameterize the size of the environment and add load balancing

**Tasks to complete**

-   Delete the **ARMHackathon** resource group using the Azure portal.

-   Using Visual Studio update your solution:

    -   Remove the existing virtual machine and network adapter because
        the scale set replaces them.

    -   Add a new parameter called **instanceCount** to the template.
        This variable should define how many web servers should be
        created.

    -   Add a new parameter called **newStorageAccountSuffix** with type
        string. This will be used to build the names of the storage
        accounts for the scale set VMs.

    -   In Resources add a storage accounts section that will
        concatenate the names using the **newStorageAccountSuffix**
        parameter and use the copyIndex to build 5 storage accounts in a
        loop.

    -   Add a Load Balancer that will use the Public IP address as the
        FrontEnd Pool and the VM Scale Set as the Backend Pool. It will
        also need a TCP probe on port 80 with the floating IP option set
        to False. Also, add an HTTP probe on port 80 with a request path
        of "/".

    -   Add the virtual machine scale set configuration that will use
        the storage accounts and creates several virtual machines based
        on the **instanceCount** parameter.

-   Deploy this solution to a new resource group named
    **ARMHackathonScaleSets**.

**Exit criteria**

-   The ARMHackathon RG and its contents have been deleted.

-   A new RG named **ARMHackathonScaleSets** has been created with all
    the correct resources from your ARM template.

-   The scale set should provision the number of virtual machines based
    on the instanceCount parameter.

-   The virtual machines provisioned by the scale set should execute the
    same DSC script used in the initial web server configuration.

-   The SQL Server has executed the SQL DSC script used in the initial
    SQL server configuration.

-   Once the machines show as "Compliant" in the DSC nodes blade of the
    Azure portal, the website loads by pointing a web browser to the
    Public IP DNS name which is now associated with the Load Balancer.

## After the hands-on lab 

Duration: 10 minutes

### Task 1: Delete the resource groups created

1.  Within the Azure portal, click Resource Groups on the left
    navigation.

2.  Delete each of the resource groups created in this lab by clicking
    them followed by clicking the Delete Resource Group button. You will
    need to confirm the name of the resource group to delete.

You should follow all steps provided *after* attending the hands-on lab.

