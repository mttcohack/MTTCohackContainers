

# MTT CoHack Challenge : Containers


## Introduction

This challenge will cover the basics of containers and container runtimes, and get you familiar with the components of the application we will use throughout this hack.

## Requirements

### To be done before the CoHack (individual)

1. You will need Owner or Contributor permissions for an Azure subscription to use in the lab.
2. PC with local Docker Desktop installation 
    - Install Docker Desktop on Pc  <https://www.docker.com/products/docker-desktop/> (needs some reboots)
    - or use pre-build Azure vm with docker desktop and vs code <https://github.com/koenraadhaedens/win10devpcdocker> (will take about 40 minutes to install)

### At least 1 Team Member need to do this    

1. Prepare Azure Resources. (Azure Container Registry, Azure Virtual Network, Application Gateway, Azure Sql database).

    (some of this resources are optional if you want to have you container instances intagraded in a virtual network or if you want to use appication gateway to publish you web)
    
Use this template to deploy to your subscprition (about 15 min deployment time)
    

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkoenraadhaedens%2FMTTCohackContainers%2Fmain%2Fbeforecohack.json)


## Description

Build the API and Web images in this repository and store them in your ACR, test application first on local machine and then in Azure.

The application we will use in this hack has three components, as the following picture describes: a [web](./Resources/web) tier offers an HTML portal that shows the information produced by the [api](./Resources/api), that in its turn access a **database** with a simple query that shows the database version. You will find the source code for each application in the files supplied for this hack:

![app architecture](./images/app_arch.png)

You can fulfill the challenge with the following steps:


  - Build the **API** image in your local machine .
  - Build the **WEB** image in your local machine .
  - push your images to your ACR (Azure Container Registry) you deployed (see beforecohack)
  - Deploy the **API** image as Azure Container Instance in Azure, make sure that the **API** can connect to the database
  - Deploy the **WEB** frontend  as Azure Container Instance that will connect to the API

You should get in the web frontend something like the following. If the frontend is able to get the database version through the API it means that the whole chain is working (web -> api -> database)

## Success Criteria

- You can access the web component
- The web container can access the API container
- The api can access the database, and the database version is correctly displayed in the frontend

Here a sample screenshot of what it should look like:

![sample output](./images/aci_web.png)

Note the two links at the bottom of the page in the picture above will not work.


## Learning Resources

These docs might help you achieving these objectives:

- [API image documentation and source code](./Resources/api/README.md)
- [Web image documentation and source code](./Resources/web/README.md)
- [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/container-registry-intro)
- [Azure Container Instances](https://docs.microsoft.com/azure/container-instances/)

Based on the microsoft/WhatTheHack github repo
