

# MTT CoHack Challenge : Containers Setup


#### To be done before the CoHack (For each Team)

1. You will need Owner or Contributor permissions for an Azure subscription to use in the lab.
2. PC with local Docker Desktop installation 
    - Install Docker Desktop on Pc  <https://www.docker.com/products/docker-desktop/> (needs some reboots)
    - or use pre-build Azure vm with docker desktop and vs code <https://github.com/koenraadhaedens/win10devpcdocker> (will take about 40 minutes to install)

#### Can be done at the beginning of the Hack    

1. Prepare Azure Resources. (Azure Container Registry, Azure Virtual Network, Application Gateway, Azure Sql database).

    (some of this resources are optional if you want to have you container instances intagraded in a virtual network or if you want to use appication gateway to publish you web)
    
Use this template to deploy to your subscprition (about 15 min deployment time)
     

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkoenraadhaedens%2FMTTCohackContainers%2Fmain%2F%setup%2Fbeforecohack.json)
