# Azure Data Platform/Analytics Platform
This project is here to... {to do}

## Pre-requisites:
- An Azure Resource Group with Contributor Access

# How to set up the project

## Step 1: Click Deploy To Azure below to get started

[![Deploy To Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fsalmanmkc%2Ftemplatedeployment%2Fmain%2Ftemplate.json)

Fill in the corresponding fields:
![Deploy a custom ARM Template on Azure](https://user-images.githubusercontent.com/32169182/110212845-42bf6b00-7e95-11eb-9fc3-55247d4302ec.png)

Click deploy and you should have this showing:


![Deployment is in progress](https://user-images.githubusercontent.com/32169182/110212922-95008c00-7e95-11eb-8e3e-887ce5e1f011.png)




This should take approximately 5 minutes, however that's solely due to there being a whole Virtual Machine deployment (IaaS), and you can continue to do the next steps as the Virtual Machine continues to deploy.

If you navigate to your newly created resource group or if you click *Go To Deployment* you should have all of these resources (the names may differ based on your input parameters unpon deploying the template:



![All the resources deployed](https://user-images.githubusercontent.com/32169182/110212984-f163ab80-7e95-11eb-89c1-0c1f12b2bbca.png)


## Step 2: Configure the Azure Data Factory to use a Private Endpoint
- Navigate to your Azure Data Factory that has been created in your resourece group
- Go to the networking tab on the left
- Change the Networking Access from Public Endpoint to Private Endpoint

![Private Endpoint Set Up for Azure Data Factory](https://user-images.githubusercontent.com/32169182/110213255-245a6f00-7e97-11eb-8e95-336beeaecc95.png)

- Select Private endpoint connections at the top
- Add a Private Endpoint by clicking *+Private Endpoint*

![image](https://user-images.githubusercontent.com/32169182/110213333-7c917100-7e97-11eb-9933-1954045994c4.png)

Add an endpoint:

Tab 1:
![image](https://user-images.githubusercontent.com/32169182/110741470-97177180-822c-11eb-9238-f14e1dd2cd86.png)

Target your own resource in tab 2
![image](https://user-images.githubusercontent.com/32169182/110741578-d47bff00-822c-11eb-9e98-c71b5d6ce10e.png)

Naviate to your Azure Data Factory and lunch it
![image](https://user-images.githubusercontent.com/32169182/110761884-241bf400-8248-11eb-97fa-7d50dbc29956.png)

1. Click the Manage option on the left menu
2. Click Integration Runtimes
3. Click New 
![image](https://user-images.githubusercontent.com/32169182/112648343-57ae6f00-8e41-11eb-85d4-18a2d4fffd81.png)

Choose Azure, Self-Hosted
![image](https://user-images.githubusercontent.com/32169182/112648784-c4c20480-8e41-11eb-9b4f-8b16e0f58782.png)
