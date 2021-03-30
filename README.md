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


# Managed VNET
By creating a managed VNET it allows us to access our PaaS resources on a private endpoint.

1. Click the Manage option on the left menu
2. Click Integration Runtimes
3. Click New 
![image](https://user-images.githubusercontent.com/32169182/112648343-57ae6f00-8e41-11eb-85d4-18a2d4fffd81.png)

Choose Azure, Self-Hosted, then continue

![image](https://user-images.githubusercontent.com/32169182/112648784-c4c20480-8e41-11eb-9b4f-8b16e0f58782.png)

Then click Azure and continue again

![image](https://user-images.githubusercontent.com/32169182/112648937-e6bb8700-8e41-11eb-9901-14cd99603603.png)

1. Give it a good name, in this case I've named it managed-vnet
2. Enable Vritual network configuration
Then click create

![image](https://user-images.githubusercontent.com/32169182/112649193-1c607000-8e42-11eb-95ea-50202c2f9daf.png)


1. Click Manage Private Endpoints
2. New

![image](https://user-images.githubusercontent.com/32169182/112649804-aa3c5b00-8e42-11eb-9e42-93b858179546.png)


Choose Azure Data Lake Gen 2 (ADLS2)
![image](https://user-images.githubusercontent.com/32169182/112958691-a35f6200-913a-11eb-8e6e-3e3f6efeebe3.png)


Give it a name, choose your Azure Subscription and your Storage Account that you made during the initial deployment stage


![image](https://user-images.githubusercontent.com/32169182/112960444-541a3100-913c-11eb-86e6-97521d3d632e.png)


Go to your storage account and approve the private endpoint

![image](https://user-images.githubusercontent.com/32169182/112960855-bd01a900-913c-11eb-839a-b4eb1aa5f727.png)


Go back to Linked Services, and click new

![image](https://user-images.githubusercontent.com/32169182/112961071-ee7a7480-913c-11eb-83d1-d379eea1fdad.png)


Choose Azure Data Lake Storage Gen2
![image](https://user-images.githubusercontent.com/32169182/112961136-ff2aea80-913c-11eb-8aa7-aa8f278731c0.png)


For *Connect via integration runtime* select from the dropdown your managed vnet that you just created in the previous step
![image](https://user-images.githubusercontent.com/32169182/112961505-592bb000-913d-11eb-825d-6be05b84eacb.png)


If successful this should show up and your private endpoint should be approved
![image](https://user-images.githubusercontent.com/32169182/112961652-79f40580-913d-11eb-9409-f9f157f9615c.png)


Test the connection

![image](https://user-images.githubusercontent.com/32169182/112961913-ba538380-913d-11eb-93e0-c82429e53dd2.png)


Now this approach is by using a key, if you have owner access to your subscription then you will be able to grant access via managed identity by configuring Access Control (IAM) and you can select Managed Identity in the steps above.
