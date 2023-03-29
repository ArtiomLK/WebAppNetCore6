# Windows Azure App for a .Net 6 Solution

## Create Azure Infrastructure from Code

### DEV

```bash
sub_id="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx";          echo $sub_id
rg_n="rg-WebAppNetCore6-dev-eastus";                    echo $rg_n
l="eastus";                                             echo $l
tags="project=gh architecture=net6 env=dev";            echo $tags
deployment_n="WebAppNetCore6-dev-eastus";               echo $deployment_n

# Create an Azure Resource Group
az group create \
--subscription $sub_id \
--name $rg_n \
--location $l \
--tags $tags

# Deploy Environment
az deployment sub create \
  --location $l \
  --name $deployment_n \
  --subscription $sub_id \
  --template-file .azure/iac/web_app.bicep \
  --parameters @.azure/iac/dev_parameters.json
```

### QA

```bash
sub_id="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx";          echo $sub_id
rg_n="rg-WebAppNetCore6-qa-eastus";                     echo $rg_n
l="eastus";                                             echo $l
tags="project=gh architecture=net6 env=qa";             echo $tags
deployment_n="WebAppNetCore6-qa-eastus";                echo $deployment_n

# Create an Azure Resource Group
az group create \
--subscription $sub_id \
--name $rg_n \
--location $l \
--tags $tags

# Deploy Environment
az deployment sub create \
  --location $l \
  --name $deployment_n \
  --subscription $sub_id \
  --template-file .azure/iac/web_app.bicep \
  --parameters @.azure/iac/qa_parameters.json
```

### STG

```bash
sub_id="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx";          echo $sub_id
rg_n="rg-WebAppNetCore6-stg-eastus";                    echo $rg_n
l="eastus";                                             echo $l
tags="project=gh architecture=net6 env=stg";            echo $tags
deployment_n="WebAppNetCore6-stg-eastus";               echo $deployment_n

# Create an Azure Resource Group
az group create \
--subscription $sub_id \
--name $rg_n \
--location $l \
--tags $tags

# Deploy Environment
az deployment sub create \
  --location $l \
  --name $deployment_n \
  --subscription $sub_id \
  --template-file .azure/iac/web_app.bicep \
  --parameters @.azure/iac/stg_parameters.json
```

### PROD

```bash
# PROD EAST US
sub_id="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx";          echo $sub_id
rg_n="rg-WebAppNetCore6-prod-eastus";                   echo $rg_n
l="eastus";                                             echo $l
tags="project=gh architecture=net6 env=prod";           echo $tags
deployment_n="WebAppNetCore6-prod-eastus";              echo $deployment_n
# PROD WEST US 3
rg_n_r2="rg-WebAppNetCore6-prod-westus3";               echo $rg_n_r2
l_r2="westus3";                                         echo $l_r2

# Create Region_1 Azure Resource Group
az group create \
--subscription $sub_id \
--name $rg_n \
--location $l \
--tags $tags

# Create Region_2 Azure Resource Group
az group create \
--subscription $sub_id \
--name $rg_n_r2 \
--location $l_r2 \
--tags $tags

# Deploy Environment
az deployment sub create \
  --location $l \
  --name $deployment_n \
  --subscription $sub_id \
  --template-file .azure/iac/web_app.bicep \
  --parameters @.azure/iac/prod_parameters.json
```

## Additional Resources

- GH
- [MS | Learn | Deploying .NET to Azure App Service][2]
- [MS | Learn | Building and testing .NET][3]
- VS
- [MS | Learn | Tutorial: Get started with C# and ASP.NET Core in Visual Studio][1]

[1]: https://learn.microsoft.com/en-us/visualstudio/get-started/csharp/tutorial-aspnet-core?view=vs-2022
[2]: https://docs.github.com/en/actions/deployment/deploying-to-your-cloud-provider/deploying-to-azure/deploying-net-to-azure-app-service
[3]: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-net
