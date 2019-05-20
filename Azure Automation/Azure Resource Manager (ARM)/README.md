# Azure Resource Manager (ARM)

## What Is It

Azure Resource Manager lets you deploy, update or delete resources for your cloud solution in a single, coordinated operation. Resources can include virtual machines, storage accounts, virtual networks, services, or any component that you are managing.

## Why Use It

- You can deploy, manage, and monitor all of the resources for your solution as a group, known as a resource group, rather than handling these resources individually.
- You can repeatedly deploy your solution throughout the development life-cycle and have confidence your resources are deployed in a consistent state.
- You can use declarative templates to define your deployment.
- You can define the dependencies between resources so they are deployed in the correct order.
- You can apply access control to all services in your resource group because Role-Based Access Control (RBAC) is natively integrated into the management platform.
- You can apply tags to resources to logically organize all of the resources in your subscription.
- You can clarify billing for your organization by viewing the rolled-up costs for the entire group or for a group of resources sharing the same tag.

For more information , you can see:
[Resource Manager](https://aka.ms/edx-azure210x-az3):
[Virtual Machines](https://aka.ms/edx-azure210x-az03):
[Storage](https://aka.ms/edx-azure210x-az5):
[Virtual Networks](https://aka.ms/edx-azure210x-az6):

1. Automation Account

    Azure Automation is an Azure service that provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment. It saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals. You can automate processes using runbooks or automate configuration management using Desired State Configuration.

    Here some common automation tasks.

    - Disaster recovery. Deploy quickly, new instances of Azure resources within an alternative Azure datacenter after a disaster occurs. Resources might include Azure VMs, virtual networks, or cloud services, along with database servers.
    - Provisioning. Perform initial and subsequent provisioning of a complete deployment, for example, a virtual network, where you assign VMs to it, create cloud services, and join the services to the same virtual network.
    - Managing Virtual Machines. Azure Automation can help manage the life cycle of your VMs. For instance, you might want to provision VMs, or shut down VMs at a specific time each day.
    - Running backups. Azure Automation is great for running regular backups of non-database systems, such as backing up Blob storage at certain intervals.
    - Deploying patches. Azure Automation allows you to develop a runbook to manage the updates at scheduled times to manage patch remediation. Ensure machines continually align with configured security policy.

    The first thing to do when you start using Azure Automation is create an Automation account. Automation accounts are like Azure Storage accounts in that they serve as a container. In Automation they are a container for all your runbook, runbook executions (jobs), and the assets that your runbooks depend on.

    It is easy to create an automation account, but you must be a subscription Owner to create the Run As accounts that are created by the service. If you do not have the proper subscription privileges, you will see a warning. 

    You must create at least one Automation account. You can create multiple automation accounts to segregate your automation assets. For example, you might use one account for development, another for production, and another for your on-premises environment. You can have up to 30 automation accounts.

    You can use role assignments to manage access to your Azure subscription resources. With Role-based access control (RBAC) you can limit both the scope (resources) and the permissions (roles) that users are given. For controlling access to automation resources you will use these roles.

    - Owner
    - Contributor
    - Reader
    - Automation Operator
    - Automation Job Operator
    - Automation Runbook Operator
    - Log Analytics Contributor
    - Log Analytics Reader
    - Monitoring Contributor
    - Monitoring Reader
    - Resource Policy Contributor
    - User Access Administrator

    Azure automation assets are resources (settings) that are globally available to be used in or associated with a runbook. There are currently six asset categories: 
    - Schedules: used to schedule runbooks to run automatically. This could be either a single date and time for the runbook to run once, or it could be a recurring schedule to start the runbook multiple times. A runbook can be linked to multiple schedules, and a schedule can have multiple runbooks linked to it.
    - Modules: A PowerShell module is a set of related Windows PowerShell functionalities, grouped together as a convenient unit. PowerShell modules can be imported as needed, and are often installed with a particular feature. For example, if you add the Active Directory role to your server, the Active Directory PowerShell module with all the associated cmdlets will also be installed. An Azure module asset isn't very different from a PowerShell module. It's simply a PowerShell module that optionally contains one additional file - a metadata file specifying an Azure Automation connection type to be used with the module. For example, email modules typically include a connection type. Azure module assets can be imported to make their cmdlets available for use within runbooks and DSC configurations. Certain module assets are shipped as “global module assets” in the Automation service. These global modules are available to you when you create an automation account. Notice in the graphic Azure.Storage, AzureRM.Automation, and AzureRM.Compute. You can add additional modules by browsing the gallery.
    - Certificates: can be stored securely in Azure Automation so they can be accessed by runbooks or DSC configurations using the Get-AutomationCertificate activity. This allows you to create runbooks and DSC configurations that use certificates for authentication or adds them to Azure or third party resources.
    - Connections: define the information required to connect to a service or application. The different types of connections you can create are defined by the modules imported into Automation. After you select the connection type a template that defines the properties needed by the connection will display. For example, the Azure module which comes pre-installed in Azure Automation contains a connection with fields for subscription id and certificate, which is the information needed to manage your Azure resources programmatically. For example the SMTPServerConnection type shows properties associated with email server connections. The properties for a connection are stored securely in the Automation, and can be accessed in the runbook with the Get-AutomationConnection activity.
    - Variables: are persistent values that are available to all runbooks and DSC configurations in your automation account. Variables can be String, Boolean, DateTime, Integer, or Not Specified. Variable assets can be encrypted along with credentials, certificates, and connections assets. These assets are encrypted and stored in the Azure Automation using a unique key that is generated for each automation account. To retrieve an unencrypted variable use the Get-AzureAutomationVariable command. To retrieve any encryption assets use a Get-AutomationVariable activity in a runbook or DSC configuration.
    - Credentials: holds a PSCredential object which contains security credentials. For example, your Azure login username and password. Runbooks and DSC configurations can use the Get-AzureAutomationCredential cmdlet to authenticate applications and services.

    For more information , you can see: [Azure Automation](https://aka.ms/edx-azure210x-az4)

2. Runbook

    Runbooks deliver the core functionality of Azure Automation by serving as containers for your custom scripts and workflows. In addition, runbooks typically reference Automation assets, such as credentials, variables, connections, and certificates. They also can contain other runbooks, thereby allowing you to build more complex workflows. You can invoke and run runbooks either on demand or according to your chosen schedule by leveraging Automation Schedule assets.

    You can create your own runbooks from scratch or modify runbooks from the Runbook Gallery for your own requirements. There are three different runbook types that you can choose from based on your requirements and PowerShell experience. If you prefer to work directly with the PowerShell code, then you can use a PowerShell runbook or a PowerShell Workflow runbook that you can edit offline or with the textual editor in the Azure portal. If you prefer to edit a runbook without being exposed to the underlying code, then you can create a Graphical runbook using the graphical editor in the Azure portal.

    Graphical Runbook:

    Graphical runbooks allow you to create runbooks for Azure Automation without the complexities of the underlying Windows PowerShell or PowerShell Workflow code. You create your workflow by adding activities from the library, linking them together, and then configuring the components.

    Graphical and Graphical PowerShell Workflow runbooks are created and edited with the graphical editor in the Azure portal. You can export them to a file and then import them into another automation account, but you cannot create or edit them with another tool. Graphical runbooks generate PowerShell code, but you can't directly view or modify the code. Graphical runbooks cannot be converted to one of the text formats nor can a text runbook be converted to graphical format. Graphical runbooks can be converted to Graphical PowerShell Workflow runbooks during import and vice-versa.

    PowerShell Runbook:

    The textual editor in Azure Automation can be used to edit PowerShell runbooks and PowerShell Workflow runbooks. The code editor has intellisense and color coding with additional special features to assist you in accessing resources common to runbooks.

    You can insert code for activities, assets, and child runbooks into a runbook. Rather than typing in the code yourself, you can select from a list of available resources and have the appropriate code inserted into the runbook.

    Each runbook in Azure Automation has two versions, Draft and Published. You edit the Draft version of the runbook and then Publish it so it can be executed. The Published version cannot be edited.

    Webhooks:

    There are two basic ways to start a runbook. The first, is by putting the runbook on a schedule. The second, is by using a webhook.

    A webhook allows you to start a particular runbook in Azure Automation through a single HTTP request. This allows external services such as Visual Studio Team Services, GitHub, or custom applications to start runbooks without implementing a full solution using the Azure Automation API.

    For security reasons, you can only view the URL in the Azure portal at the time the webhook is created. You should note the URL in a secure location for future use.

    Name: You can provide any name you want for a webhook since this is not exposed to the client. It is only used for you to identify the runbook in Azure Automation.

    URL: The URL of the webhook is the unique address that a client calls with an HTTP POST to start the runbook linked to the webhook. It is automatically generated when you create the webhook. You cannot specify a custom URL. The URL contains a security token that allows the runbook to be invoked by a third party system with no further authentication. For this reason, it should be treated like a password.

    Enabled: A webhook is enabled by default when it is created.

    Expires: Like a certificate, each webhook has an expiration date at which time it can no longer be used. This expiration date cannot be changed after the webhook is created, and the webhook also cannot be enabled again after the expiration date is reached.

    A webhook can define values for runbook parameters that are used when the runbook is started by that webhook. The webhook must include values for any mandatory parameters of the runbook and may include values for optional parameters.

    PowerShell Workflow:

    A Windows PowerShell workflow is a sequence of programmed, connected steps that perform long-running tasks or require the coordination of multiple steps across multiple devices or managed nodes. Workflows lets IT pros and developers author sequences of multi-device management activities, or single tasks within a workflow, as workflows. By design, workflows can be long-running, repeatable, frequent, parallelizable, interruptible, stoppable, and restartable. They can be suspended and resumed; they can also continue after an unexpected interruption, such as a network outage or computer restart. There are many benefits to using workflows.

    - Windows PowerShell scripting syntax. Workflows extend PowerShell which makes it is easy for IT Pros who are already familiar with scripting.
    - Multi-device management. You can simultaneously apply workflow tasks to hundreds of managed nodes. Workflows automatically add common parameters to enable multi-device management scenarios.
    - Running a single task to manage complex, end-to-end processes. You can combine related scripts or commands that act on an entire scenario into a single workflow. Status and progress of activities within the workflow are visible at any time.
    - Automated failure recovery. Workflows survive both planned and unplanned interruptions, such as computer restarts. You can suspend workflow operation, then restart or resume the workflow from the point at which it was suspended. You can author checkpoints as part of your workflow, so that you can resume the workflow from the last persisted task (or checkpoint), instead of restarting the workflow from the beginning.
    - Connection and activity retries. By using workflow common parameters, workflow users can retry connections to managed nodes if network connection failures occur. Workflow authors can also specify activities that must run again if the activity cannot be completed on one or more managed nodes (for example, if a target computer was offline while the activity was running).
    - Connect and disconnect. Users can connect and disconnect from the computer that is running the workflow, but the workflow remains running. For example, if you are running the workflow and managing the workflow on two different computers, you can log off of or restart the computer from which you are managing the workflow, and monitor workflow operations from another computer (such as a home computer) without interrupting the workflow.
    - Task Scheduling. Workflow tasks can be scheduled, and started when specific conditions are met, as with any other Windows PowerShell cmdlet or script.

    Workflow Syntax:

    To write the workflow, use a script editor, such as the Windows PowerShell Integrated Scripting Environment (ISE), that enforces workflow syntax and highlights syntax errors. The syntactic differences between scripts and workflows are significant, so a tool that knows workflows, as well as scripts, will save you significant coding and testing time.

Begin with the workflow keyword, which identifies a workflow command to Windows PowerShell. The workflow keyword is required in a script workflow. The name of the workflow follows the workflow keyword. The body of the workflow is enclosed in braces. A workflow is a Windows PowerShell command type. Select a name with a verb-noun format.

```json
		workflow Test-Workflow
		
		{
		    ...
		}
```

To add parameters to a workflow, use the Param keyword. These are the same techniques that you use to add parameters to a function. Lastly, simply add your standard PowerShell commands.

```json
		workflow MyFirstRunbook-Workflow

		{
		   Param(
		    [string]$VMName,
		    [string]$ResourceGroupName
		   )  
		....
		 Start-AzureRmVM -Name $VMName -ResourceGroupName $ResourceGroupName
		}
```

3. ARM Template

    An ARM template consists of JSON and expressions which you can use to construct values for your deployment. You must limit the size your template to 1 MB, and each parameter file to 64 KB. The 1 MB limit applies to the final state of the template after it has been expanded with iterative resource definitions, and values for variables and parameters.

```json
    {
       "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
       "contentVersion": "",
       "parameters": {  },
       "variables": {  },
       "resources": [  ],
       "outputs": {  }
    }
```

    - $Schema: Location of the JSON schema file that describes the version of the template language.
    - contentVersion: Version of the template (such as 1.0.0.0).
    - parameters: Optional values that are provided when deployment is executed to customize resource deployment.
    - resources: A manageable item that is available through Azure. Some common resources are a virtual machine, storage account, web app, database, and virtual network, but there are many more.
    - outputs: Values that are returned after deployment

    You can deploy your templates directly from the Portal using the new Templates hub. 

    You can also deploy your templates with PowerShell. To deploy a local template, you can use the TemplateFile parameter:

```Powershell
    New-AzureRmResourceGroupDeployment -Name ExampleDeployment -ResourceGroupName ExampleResourceGroup -TemplateFile <PathToTemplate>

    New-AzureRmResourceGroupDeployment -Name ExampleDeployment -ResourceGroupName ExampleResourceGroup -myParameterName "parameterValue"
```

    - [GitHub Resource Manager QuickStart Templates](https://github.com/Azure/azure-quickstart-templates)



    