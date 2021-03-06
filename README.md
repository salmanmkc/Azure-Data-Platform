# Azure Data Factory Project
This project is here to... {to do}

## Pre-requisites:
- An Azure Subscription with Contributor Access

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

