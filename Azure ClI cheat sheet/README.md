# Azure CLI Cheat Sheet

To improve your Azure CLI experience, you could use the VS Code extension to run Azure CLI files with a .azcli extension. This allows you to write and save Azure CLI commands in a file, and then execute them in the integrated terminal within VS Code. This can save you time and effort by automating common tasks or complex scripts, and also helps to minimize typing errors.

https://marketplace.visualstudio.com/items?itemName=ms-vscode.azurecli
# Personal for me

```commands
#Ctr+ä => To run command on Terminal
az version 
#Ctr+Shift+ä => To run command on Terminal
az login

az account list
az account list --output table
cls


az group create --name exampleRG --location eastus
az deployment group create --resource-group exampleRG --template-file samples\create-storage-account\main.bicep --parameters storagePrefix=uniquename
az resource list --resource-group exampleRG --output table
az resource list --resource-group exampleRG --resource-type "Microsoft.Storage/storageAccounts" --output table
az resource list --resource-group exampleRG --resource-type "Microsoft.Compute/virtualMachines"

az group delete --name exampleRG

```

# Global
## Azure Account
- `az login`: Log in to your Azure account
- `az account show`: Show the current subscription and tenant details
- `az account set --subscription <subscription ID or name>`: Set the current subscription for the CLI session
- `az logout`: Log out of the Azure account

## Resource Groups
- `az group create --name <resource group name> --location <location>`: Create a new resource group. For example: `az group create --name myResourceGroup --location eastus`
- `az group list`: List all resource groups in the current subscription
- `az group show --name <resource group name>`: Show details of a specific resource group. For example: `az group show --name myResourceGroup`
- `az group delete --name <resource group name>`: Delete a resource group and all its resources. For example: `az group delete --name myResourceGroup`

## Virtual Machines
- `az vm create --resource-group <resource group name> --name <VM name> --image <image> --admin-username <username> --admin-password <password>`: Create a new virtual machine. For example: `az vm create --resource-group myResourceGroup --name myVM --image UbuntuLTS --admin-username azureuser --admin-password MyPa$$w0rd`
- `az vm list`: List all virtual machines in the specified resource group or subscription
- `az vm show --resource-group <resource group name> --name <VM name>`: Show details of a specific virtual machine. For example: `az vm show --resource-group myResourceGroup --name myVM`
- `az vm start --resource-group <resource group name> --name <VM name>`: Start a stopped virtual machine. For example: `az vm start --resource-group myResourceGroup --name myVM`
- `az vm stop --resource-group <resource group name> --name <VM name>`: Stop a running virtual machine. For example: `az vm stop --resource-group myResourceGroup --name myVM`

## Storage Accounts
- `az storage account create --name <account name> --resource-group <resource group name> --sku <sku>`: Create a new storage account. For example: `az storage account create --name mystorageaccount --resource-group myResourceGroup --sku Standard_LRS`
- `az storage account list`: List all storage accounts in the specified resource group or subscription
- `az storage account show --name <account name> --resource-group <resource group name>`: Show details of a specific storage account. For example: `az storage account show --name mystorageaccount --resource-group myResourceGroup`
- `az storage account delete --name <account name> --resource-group <resource group name>`: Delete a storage account and all its contents. For example: `az storage account delete --name mystorageaccount --resource-group myResourceGroup`

## Networking
- `az network vnet create --name <VNet name> --resource-group <resource group name> --address-prefixes <address prefix> --subnet-name <subnet name> --subnet-prefix <subnet prefix>`: Create a new virtual network and subnet
- `az network vnet list`: List all virtual networks in the specified resource group or subscription
- `az network vnet show --name <VNet name> --resource-group <resource group name>`: Show details of a specific virtual network
- `az network vnet delete --name <VNet name> --resource-group <resource group name>`: Delete a virtual network and all its resources

## App Service
- `az webapp create --resource-group <resource group name> --plan <app service plan name> --name <app name> --runtime <runtime>`: Create a new web app
- `az webapp list`: List all web apps in the specified resource group or subscription
- `az webapp show --resource-group <resource group name> --name <app name>`: Show details of a specific web app
- `az webapp delete --resource-group <resource group name> --name <app name>`: Delete a web app and all its resources