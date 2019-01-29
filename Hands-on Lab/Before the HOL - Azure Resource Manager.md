
![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Azure Resource Manager
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
December 2018
</div>


Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Azure Resource Manager before the hands-on lab setup guide](#azure-resource-manager-before-the-hands-on-lab-setup-guide)
  - [Requirements](#requirements)
  - [Before the hands-on lab](#before-the-hands-on-lab)
    - [Task 1: Create a virtual machine for your lab environment](#task-1-create-a-virtual-machine-for-your-lab-environment)
    - [Task 2: Connect to the VM and download the student files](#task-2-connect-to-the-vm-and-download-the-student-files)
    - [Task 3: Validate connectivity to Azure](#task-3-validate-connectivity-to-azure)

<!-- /TOC -->

# Azure Resource Manager before the hands-on lab setup guide

## Requirements

- Azure Subscription
- Understanding of Azure Infrastructure as a Service components
- Familiarity with JavaScript Object Notation (JSON)
- Familiarity with PowerShell

## Before the hands-on lab

Duration: 15 minutes

Prior to attending the lab, follow the instructions below to create a
lab environment using an Azure Virtual Machine and download the needed
files for the lab exercise.

### Task 1: Create a virtual machine for your lab environment 

1.  Launch a browser using incognito or in-private mode, and navigate to
    <https://portal.azure.com>. Once prompted, login with your Microsoft
    Azure credentials. If prompted, choose whether your account is an
    organization account or just a Microsoft Account.

2.  Click on +NEW, and in the search box, type in Visual Studio
    Community 2017, and press enter. Click
    the Visual Studio Community 2017 image running on Windows Server
    2016 and with the latest update.

3.  In the returned search results, click the image name.

    ![In the Everything blade, Visual Studio Community 2017 is typed in the Search field. Under Name, Visual Studio Community on Windows Server 2016 is circled.](images/Setup/2018-08-15-10-04-24.png "Everything blade")

4.  In the Marketplace solution blade, click **Create**.

5.  Set the following configuration on the Basics tab, and select **OK**:

    -   Name: **LABVM**

    -   VM disk type: **Premium SSD**

    -   User name: **demouser**

    -   Password: **demo\@pass123**

    -   Subscription: **If you have multiple subscriptions choose the subscription to execute your labs in**.

    -   Resource Group: **OPSLABRG**

    -   Location: **Choose the closest Azure region to you**.

6.  Choose the **DS1\_V2 Standard** instance size on the Size blade.


7.  On the Settings blade, choose **RDP (3389)** on the Select public inbound ports dropdown.

    ![In the Select public inbound ports dropdown, RDP is selected.](images/Setup/2018-08-15-10-09-55.png "Select public inbound ports")

8.  Accept the remaining default values on the Settings blade, and click **OK**. On the Summary page, click **Create**. The deployment should  begin provisioning. It may take more than 10 minutes for the virtual machine to complete provisioning.

    ![Screenshot of the Deploying Visual Studio Community 2017 icon.](images/Setup/image4.png "Deploying Visual Studio Community 2017 icon")

### Task 2: Connect to the VM and download the student files

1.  Move back to the Portal page on your local machine, and wait for **LABVM** to show the Status of **Running**. Click **Connect** to establish a new Remote Desktop Session.

    ![The Connect button is circled on the Portal page.](images/Setup/image5.png "Connect button")

2.  Depending on your remote desktop protocol client and browser
    configuration, you will either be prompted to open an RDP file, or
    you will need to download it and then open it separately to connect.
    You may also be required to click, **Use a different account**.

    ![In the Windows Security dialog box, demouser is typed in the credentials field, and the password is hidden. At the bottom, the link to Use a different account is circled.](images/Setup/image6.png "Windows Security dialog box")

3.  Login with the credentials specified during creation:

    a.  User: **demouser**

    b.  Password: **demo\@pass123**

4.  You will be presented with a Remote Desktop Connection warning because of a certificate trust issue. Click, **Don't ask me again for connections to this computer** followed by clicking **Yes** to continue with the connection.

    ![The Remote Desktop Connection warning page explains that the identity of the remote computer cannot be identified, and asks if you still want to connect. The checkbox is selected and circled to not ask again for connections to this computer. At the bottom, the Yes button is circled.](images/Setup/image7.png "Remote Desktop Connection warning page")

5.  When logging on for the first time, you will see a prompt on the right asking about network discovery. Select **No**.

    ![The Networks prompt asking if you want your PC to be discoverable, and the No button is circled.](images/Setup/image8.png "Networks prompt")

6.  Notice the Server Manager opens by default. On the left, click **Local Server**.

    ![Local Server is circled in the left Server Manager menu.](images/Setup/image9.png "Local Server")

7.  On the right side of the pane, click **On** by **IE Enhanced Security Configuration**.

    ![In Local Server information, IE Enhanced Security Configuration is circled, and is set to On.](images/Setup/image10.png "Local Server information")

8.  Change to **Off** for Administrators, and click **OK**.

    ![On the Internet Explorer Enhanced Security Configuration page, under Administrators, the radio button is selected for Off. At the bottom, the OK button is circled.](images/Setup/image11.png "Internet Explorer Enhanced Security Configuration page")

9.  In the lower left corner, click Internet Explorer to open it. On first use, you will be prompted about security settings. Accept the
    defaults by clicking **OK**.

    ![In the Internet Explorer 11 Setup window, the checkbox is selected for \"Use recommended security, privacy, and compatibility settings. At the bottom, the OK button is circled.](images/Setup/image12.png "Internet Explorer 11 Setup window")

10. If prompted, click **Don't show this again** regarding protected mode.

11. Open Internet options by clicking the **Tools** icon in the upper right corner, then selecting **Internet options**.

    ![In Internet Explorer, the tools icon is highlighted and Internet options is highlighted in the dropdown.](images/Setup/2018-08-15-11-46-27.png "Internet Explorer tools menu")

12. Switch to the **Security** tab, verify that **Internet** is selected, then click the **Custom level...** button.

    ![In Internet options, the security tab is selected, the Internet zone is highlighted, and the custom level button is highlighted.](images/Setup/2018-08-15-11-57-11.png "Internet Options Security tab")

13. In the Settings pane, set the **File download** setting to **Enable** and click **OK**.
    
    ![In the Security Settings window, File download is highlighted and enable is selected.](images/Setup/2018-08-15-11-52-57.png "Internet Explorer security settings")

14. To download the exercise files for the lab, paste this URL into the browser:

    <https://cloudworkshop.blob.core.windows.net/arm-hackathon/ARM_Hackathon_Guide_Student_Files.zip>

15. You will be prompted about what you want to do with the file. Select **Save**.

    ![In the Internet Explorer Save, window, a prompt asks what you want to do with the file, and the Save button is circled.](images/Setup/image13.png "Internet Explorer Save window")

16. Download progress is shown at the bottom of the browser window. When the download is complete, click **Open folder**.

    ![The Open Folder button is circled on the Download progress bar.](images/Setup/image14.png "Download progress bar")

17. The **Downloads** folder will open. ***Right-click*** the zip file, and click **Extract All**. In the **Extract Compressed (Zipped) Folders** window, enter **C:\\Hackathon** in the **Files will be extracted to this folder** dialog. Click the **Extract** button.

### Task 3: Validate connectivity to Azure

1.  Within the virtual machine, launch **Visual Studio 2017**, and validate you can login with your Microsoft Account when prompted.

    ![The Visual Studio sign-in page displays.](images/Setup/image15.png "Visual Studio sign-in page")

2.  Validate connectivity to your Azure subscription. Launch **Visual Studio**, open **Server Explorer** from the View menu, and ensure you can connect to your Azure subscription.

    ![In the Visual Studio Server Explorer window, the sub-menu displays for the Azure subscription, confirming that a connection to the Azure subscription can be made.](images/Setup/image16.png "Visual Studio Server Explorer")

You should follow all steps provided *before* attending the hands-on lab.
