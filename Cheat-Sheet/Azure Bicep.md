# Azure Bicep

```commands
#Ctr+ä => To run command on Terminal
az version 
#Ctr+Shift+ä => To run command on Terminal
az login

az account list
az account list --output table
cls

#--------------BICEP Example
az group create --name exampleRG --location eastus
az deployment group create --resource-group exampleRG --template-file samples\create-storage-account\main.bicep --parameters storagePrefix=uniquename
az resource list --resource-group exampleRG --output table
az resource list --resource-group exampleRG --resource-type "Microsoft.Storage/storageAccounts" --output table
az resource list --resource-group exampleRG --resource-type "Microsoft.Compute/virtualMachines"

az group delete --name exampleRG --yes

#---------------Generate the BECIP Code from resource
## 3 ways
# First
az group export --resource-group exampleRG  >  Generated\exampleRG_template.json
az bicep decompile --file Generated\exampleRG_template.json

# Second
using the VS code extention CTR+Shift+P the BECIP:INSERT resource => then give it the resource ID EX: "/subscriptions/39aac29d-2d84-4f93-a60b-601c6dec6a53/resourceGroups/exampleRG"
then the BECIP code will be generated 
you can use the Azure Resource Explorer at https://resources.azure.com/ to extract the resource-ID .

# third 
throw the Portal .

```

#Scoap RG or Sub
#Parameter.json must be generated !!! how . code be file.local.json file.prod.json
# Validation named what-IF 
# az deployment sub  what-if --location westeurope  --parameters .\main.parameters.json  --template-file .\main.bicep
#to generate Bicep code for a resource 
# 1- Generate the ARM Template online on the portal 
# 2- az bicep decompile --file .\template.json
# 3- az bicep upgrade