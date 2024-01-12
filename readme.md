

# MTT CoHack Challenge : Containers


## Introduction

This challenge will cover the basics of containers and container runtimes, and get you familiar with the components of the application we will use throughout this hack.

## Requirements

Your CoHack Host will provide you with the credentials to login to azure for this Cohack session.

## Description

Build the API and Web images in this repository and store them in your ACR, test application first on local machine and then in Azure.

The application we will use in this hack has three components, as the following picture describes: a [web](./Resources/web) tier offers an HTML portal that shows the information produced by the [api](./Resources/api), that in its turn access a **database** with a simple query that shows the database version. You will find the source code for each application in the files supplied for this hack:

![app architecture](./images/app_arch.png)

You can fulfill the challenge with the following steps:

  - Build the **API** image in your local machine .
  - Build the **WEB** image in your local machine .
  - Run containers on local machine and make sure that you can browse to the webcontainer and see the api info.
  - push your images to your ACR (Azure Container Registry) alreday deployed 
  - Deploy the **API** image as Azure Container Instance in Azure, make sure that the **API** is not exposed to the public internet and that the **API** can connect to the public endpoint from the database over the internal network.
  - Deploy the **WEB** frontend as an APP Service, the webservice needs to be accessible from the internet and must be able to connect to **API** over internal network.
  - (optional challenge) deploy solution to **AKS**.
  - (optional Challenge) Make sure **secure info** is not as clear text in deployment file

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
- [Use CLI to push docker image to ACR](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-get-started-docker-cli?tabs=azure-cli)
- [docker CLI Cheat Sheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- [Tutorial: Create an Azure container registry and push a container image](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-tutorial-prepare-acr)

Based on the microsoft/WhatTheHack github repo
