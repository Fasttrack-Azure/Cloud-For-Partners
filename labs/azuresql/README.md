# Working with Azure SQL

This demo explains how you can use [SQL Database Projects](https://learn.microsoft.com/en-us/sql/azure-data-studio/extensions/sql-database-project-extension-getting-started?view=sql-server-ver16) extention in VS Code to build and publish Azure SQL projects.

## Step 1
```
# Create a single database and configure a firewall rule
# Variable block
let "randomIdentifier=$RANDOM*$RANDOM"
location="East US"
resourceGroup="<Your-RG-Name>"
tag="create-and-configure-database"
server="sb-azuresql-server-$randomIdentifier"
database="sbazuresqldb$randomIdentifier"
login="azureuser"
password="Admin@1234567"
# Specify appropriate IP address values for your environment
# to limit access to the SQL Database server
startIp=0.0.0.0
endIp=255.255.255.255

echo "Using resource group $resourceGroup with login: $login, password: $password..."
echo "Creating $resourceGroup in $location..."
az group create --name $resourceGroup --location "$location" --tags $tag
echo "Creating $server in $location..."
az sql server create --name $server --resource-group $resourceGroup --location "$location" --admin-user $login --admin-password $password
echo "Configuring firewall..."
az sql server firewall-rule create --resource-group $resourceGroup --server $server -n AllowYourIp --start-ip-address $startIp --end-ip-address $endIp
echo "Creating $database on $server..."
az sql db create --resource-group $resourceGroup --server $server --name $database --sample-name AdventureWorksLT --edition Basic --capacity 5
```

## Step 2
Install the [SQL Database Projects](https://learn.microsoft.com/en-us/sql/azure-data-studio/extensions/sql-database-project-extension-getting-started?view=sql-server-ver16) extention in VS Code

## Step 3
Navigate to the existing SQL project by clicking on the extention icon in the left pane of VS Code
Right click and publish the database project to your Azure SQL instance