Provision Azure Environment Resources from Gallery
==================================================

            

**Description**


This runbook creates a number of Azure Environment Resources (in sequence): Azure Affinity Group, Azure Cloud Service, Azure Storage Account, and Azure VM all from an existing VM Image (specified as a Variable in the Assets).


**Requirements**


The creation of the Azure Environment Resources are based on the following input parameters: 'Project Name', 'VM Name', 'VM Instance Size' (and optionally 'Storage Account Name').


Before executing this runbook, make sure the following components are available:


  *  This runbook sample leverages organization id credential based authentication (Azure AD; instead of the Connect-Azure Runbook). Before using this runbook, you must create an Azure Active Directory user and allow that user to manage the Azure subscription
 you want to work against. You must also place this user's username / password in an Azure Automation credential asset.

You can find more information on configuring Azure so that Azure Automation can manage your Azure subscription(s) here: http://aka.ms/Sspv1l 

It does leverage an Automation Asset for the required Azure AD Credential. This example uses the following call to get this credential from the Asset store: 

     $Cred = Get-AutomationPSCredential -Name 'Azure AD Automation Account'
     $AzureSubscriptionName = Get-AutomationVariable -Name 'Primary Azure Subscription'


  *  Five more (5) Automation Assets (to be configured in the Assets tab). These are suggested, but not necessarily required. Replacing the 'Get-AutomationVariable' calls within this runbook with static or parameter variables is an alternative method. For this
 example though, the following dependencies exist:

  *  VARIABLES SET WITH AUTOMATION ASSETS:
        $AGLocation = Get-AutomationVariable -Name 'AGLocation'
        $VMImage = Get-AutomationVariable -Name 'VMImage'
            Example Image: a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd
        $VMImageOS = Get-AutomationVariable -Name 'VMImageOS'
        $AdminUsername = Get-AutomationVariable -Name 'AdminUsername'
        $Password = Get-AutomationVariable -Name 'Password'


***Note     **The entire runbook is heavily checkpointed and can be run multiple times without resource recreation.*



**Runbook Contents**


The runbook's contents are displayed below:

 

        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
