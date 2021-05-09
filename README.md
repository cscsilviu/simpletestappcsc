# Deploy infrastructure and web application with SQL

Scope of documentation is to enable yourself to deploy an Azure App Service infrastrcuture with Application plan, SQL database and also upload the code of your simple application from a .Zip file:

# Parameters from the **appservicetemplate.parameters.json**:
# Params that need an explicit value
- applicationName = YOUR_APPLICATION_NAME
- svcPlanName = APPLICATION_PLAN_NAME
- sqlServerName = SQL_SERVER_NAME
- sqldbName = SQL_DBNAME
# Params that have a default value but you can change it for you own project if you have a scalling plan
- sku
- sqldbCollection
- sqldbEdition
- sqldbRequestedObjectiveName
- svcPlanSize
- minimumCapacity
- maximumCapacity
- defaultCapacity
- metricName
- metricThresholdToScaleOut
- metricThresholdToScaleIn
- changePercentScaleOut
- changePercentScaleIn
- autoscaleEnabled

# Parameters from the GitHub infrastructuredeploy.yml action file. This file will trigger the action which will in the end trigger the creation
- AZURE_WEBAPP_NAME:
- resourceGroupName:
- creds:

# Prerequisites 
- Azure subscription
- Resource group created in Azure portal
- Azure KeyVault where you will store your SQL credentials
- GitHub Secret to be stored with the credentials used for the ResourceGroup you will use for deployment

# How to get the permissions for Git actions to be able to deploy your infrastructure:
- Azure CLI: use **az group** list to get you resource group where you want your deployment to be done. 
- AZURE CLI: **az ad sp create-for-rbac --name "deploysimpletestapp" --role contributor --scope "<YOUSCOPE>" --sdk-auth**
- copy the Credential code to your secret vault in GitHub and give it a name
- Change the **creds:** parameter with you secret tag. Ex: ${{ secrets.<YOUT_CRED_TAG_HERE> }}
  
