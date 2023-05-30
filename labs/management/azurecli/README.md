<h1> Azure Management using PowerShell and Azure CLI</h1>
 
<h3>Task 1: Use the PowerShell CLI</h3>
Launch the cloud shell from the Azure Portal
<img width="1303" alt="image" src="https://user-images.githubusercontent.com/11691661/179504416-f2175247-d747-491c-88e2-2723ede65d35.png">

Half the screen will be in PowerShell command line interface (CLI) mode. If you’re familiar with PowerShell, you can manage your Azure environment using PowerShell commands.

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/11691661/179504508-50d24e73-d824-48d6-957d-e740dfce3eb5.png">

```
**Tip**
You can tell you're in PowerShell mode by the PS before your directory on the command line.
```

Use the PowerShell Get-date command to get the current date and time.

```
Get-date
```

Most Azure specific commands will start with the letters az. The Get-date command you just ran is a PowerShell specific command. Let's try an Azure command to check what version of the CLI you're using right now.

```
az version
```

<h3>Task 2: Use the BASH CLI</h3>
If you’re more familiar with BASH, you can use BASH command instead by shifting to the BASH CLI.

Enter bash to switch to the BASH CLI.

```
bash
```

```
**Tip**
You can tell you're in BASH mode by the username displayed on the command line. It will be your username@azure.
```

Again, use the Get-date command to get the current date and time.

```
Get-date
```

You received an error because Get-date is a PowerShell specific command.

Screenshot of BASH error message get-date command not found.
<img width="1440" alt="image" src="https://user-images.githubusercontent.com/11691661/179505428-d8c0d1f1-f818-4db4-b25a-3fd3e4f9b0f8.png">Use the date command to get the current date and time.

```
date
```

The Azure CLI is available to install in Windows, macOS and Linux environments. It can also be run in a Docker container and Azure Cloud Shell.

<h3> Task 3: Install Tools</h3
The current version of the Azure CLI is 2.38.0. For information about the latest release, see the release notes. To find your installed version and see if you need to update, run az version.

Install Azure CLI: 
[Install on Windows](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows)
 
[Install on macOS](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos)

Download and install VS Code
[VS Code](https://code.visualstudio.com/download)
 
Open Terminal
 ```
CTRL+SHIFT+`
 ```
 
Run the login command.
 
```
az login
```

If the CLI can open your default browser, it will initiate authorization code flow and open the default browser to load an Azure sign-in page.
Sign in with your account credentials in the browser.

<h3>Task 4: Finding commands</h3>

Azure CLI commands are organized as commands of groups. Each group represents an Azure service, and commands operate on that service.
To search for commands, use az find. For example, to search for command names containing secret, use the following command:

```
az find secret
```
 
Use the --help argument to get a complete list of commands and subgroups of a group. For example, to find the CLI commands for working with Network Security Groups (NSGs):

```
az network nsg --help
```

Interactive mode

The CLI offers an interactive mode that automatically displays help information and makes it easier to select subcommands. You enter interactive mode with the az interactive command.

```
az interactive
```
 
<h3>Task 5: Managing subscriptions using Azure CLI</h3 
Change the active tenant
To switch tenants, you need to sign in as a user within the desired tenant. Use az login to change the active tenant and update the subscription list to which you belong.

```
# sign in with a different tenant
 
az login --tenant <myTenantID>
```
 
Change the active subscription
 ```
 # change the active subscription using the subscription name
az account set --subscription "<name>"

# change the active subscription using the subscription ID
az account set --subscription "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"

# change the active subscription using a variable
subscriptionId="$(az account list --query "[?isDefault].id" -o tsv)"
az account set --subscription $subscriptionId
 ```
 
 Create Management Groups
 You can create a management group for several of your subscriptions by using the az account management-group create command:

```
az account management-group create --name <mg-yourname>
 ```
 
To see all your management groups, use the az account management-group list command:

```
az account management-group list
 ```
 
Add subscriptions to your new group by using the az account management-group subscription add command:

```
az account management-group subscription add --name <mg-yourname> --subscription "<subscription-name>"
 ```
 
To remove a subscription, use the az account management-group subscription remove command:

```
az account management-group subscription remove --name <mg-yourname> --subscription "My Demos"
 ```
 
To remove a management group, run the az account management-group delete command:

```
az account management-group delete --name mg-yourname
 ```
 
Removing a subscription or deleting a management group doesn't delete or deactivate a subscription.
 
 
<h3>Task 6: Managing resource Groups using Azure CLI</h3 
 
Create a resource group
To create a resource group, use the az group create command:

```
az group create --name <RG-your-name> --location eastus
```
 
A resource group belongs to a single location. To see all the locations supported in your current subscription, run the az account list-locations command:

```
az account list-locations
```
 
To see all the resource groups for your current subscription, use the az group list command:

```
az group list --output table
 ```
 
 ```
**Tip**
The --output parameter is a global parameter, available for all commands. The table value presents output in a friendly format.
 ```

When you create a resource, you create it in a resource group. The following example shows a storage account created by using the az storage account create command:

```
az storage account create --resource-group <RG-your-name> --name <strg-your-name> --location eastus --sku Standard_LRS
 ```
 
To remove a resource group, run the az group delete command:

```
az group delete --name <>RG-your-name>
 ```
 
When you remove a resource group, you delete all the resources that belong to it. There's no option to undelete resources. If you try any of the commands in this article, deleting the resource groups you create cleans up your account.
 
<h3>Common Azure CLI commands</h3
 
This below list shows some common commands used in the CLI and links to their reference documentation.


Resource group	
 ```
 az group
 ```
 
Virtual machines	
 ```
 az vm
 ```
Storage accounts	
 ```
 az storage account
 ```
 
Key Vault	
 ```
 az keyvault
 ```
 
Web applications	
 ```
 az webapp
 ```
 
SQL databases	
 ```
 az sql server
 ```
 
CosmosDB	
 ```
 az cosmosdb
 ```
