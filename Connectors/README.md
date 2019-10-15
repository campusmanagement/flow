# What are Custom Connectors?
Connectors in Power Apps or Logic apps are gateways, built into the platform (Power apps / Logic apps), which can integrate with the application/ perform action on process from applications outside the boundary of the platform. Below link can be referred for more detailed information on Custom Connectors: https://docs.microsoft.com/en-us/connectors/custom-connectors/
As the name suggests, Custom Connectors obviously do not come with the platform. A user must configure it to an endpoint. The endpoint can be any application/interface outside the boundary of the platform. These endpoints can be an on-premise application or a server less code hosted in cloud like Azure. The concept of custom connectors is to provide actions, in flow or logic apps, that can be performed with the data from CDS or CDS supported Dynamics applications. 
	
## Creation and Configuration of custom connector:
Once we have the pre-requisites setup. We can create custom connectors with the help of following URL:  https://docs.microsoft.com/en-us/connectors/custom-connectors/define-openapi-definition. In the document Open-API-Definition should be referred to as Swagger document which will be defined for all the APIs and integration APIs created under campus nexus student. Configuration of custom connectors depends on Student deployments. 
		
1.	Assuming the swagger definition is generated for any desired API, used for integration. We need to save the swagger document of the selected API/API’s to a 	Json file in the file system.
2.	During the process of creating a Custom connector, we need to select Import an Open API File.
3.	Import the saved swagger Json document.
4.	In the next screen Upload a logo ( Campus Nexus student logo Preferably),
5.	Change the description if needed
6.	Add the appropriate Student API server Host name
7.	Under the Base Url, leave the forward slash alone. Our API definitions starts with CMC.Nexus.web. The base URL should read “/”.
8.	Under the security tab, select the appropriate Authentication methodology for API Authentication.
	a.	If API Key is selected:
		i.	Add “ApiKey” as parameter and label.
		ii.	Parameter Location should be Header.
		iii. If Oauth 2.0 is selected as Authentication method, Create an app registration under the Azure Active Directory where houses Campus Nexus Student API     and Power Platform.
		iv.	Once you have the App registration completed, retrieve the Application ID and App Secret, 
		v.	Add Permissions to Student API in the App. 
		vi.	Add the Redirect URL in the Security Tab to the Redirect URL for the App registered in the above steps.
		vii. Finally, Grant permission to the APP to access resources under the tenant.   

### Redistribution/Reusing the Custom Connectors for different environments:  
For all the commands to use Custom connectors the following URL helps us
https://docs.microsoft.com/en-us/connectors/custom-connectors/paconn-cli
	
How Command Line Interface (CLI) can be used for redistributing the Custom connectors for multiple environments will be explained with the help of following images and commands. From the above link and from the Pre-Requisites, one must install Python, which will be used with CLI to create or update Custom Connectors. Assuming we have the Python installed, following commands will help in logging in to the tenant and subsequently the desired environment. 
Paconn is the package where all the commands to create/update connectors are defined. We will be using Paconn for all our Custom connector Deployment process. Instructions on Installation of the package is given in the above link.  

### Login:

1.	When you want to login to a given tenant, we will have to run a command
Paconn login
In the Command line, result of the command will be link “https”//microsoft.com/devicelogin” which needs to be copied to a browser and there will be a code given in the CLI, that code needs to be entered in the browser.
2.	You will be asked to enter a suitable login credentials or select from your existing Microsoft/Organization account. 
3.	Next command can be used to download the connector: 
paconn download 
This will enable us to select the organization which will be used to download the 	   connector.
4.	Select the connector which you want to download. And the downloaded connector will be saved under the folder in command line. 
5.	The connector will have 4 files.
	a.	apiDefinition.swagger.json – The Api Open Definition.
	b.	apiProperties.json – Custom connector security configuration.
	c.	icon.png – Icon of the connector.
	d.	settings.json – Environment configurations.


### Deploying customer connectors in another environment:
In the apiProperties.json we would have all the tenant and authentication information. We can choose to change the same depending on the tenant we use to create/update the custom connector. 

#### paconn create --api-prop [Path to apiProperties.json] --api-def [Path to apiDefinition.swagger.json] --icon [Path to icon.png] --secret [The OAuth2 client secret for the connector]

The command is self-explanatory. If we are using AAD as our authentication model we may need to provide the app registration client secret.
If we are using the api key we need to change the apiproperties.json and the new apikey if needed.
The same process to select the Environment and organization has to be followed like download command.

### Updating custom connectors in different environments:
If we are updated the API definition. 
1.	 We need to down load the custom connector from a QA environment in test tenant. Using the paconn download command.
2.	Replace the apiDefinition.swagger.json  from the deployable folder with the new file in the downloaded folder.
3.	Use the following command to update the swagger definition for a given customer connector.
	 paconn update --api-prop [Path to apiProperties.json] --api-def [Path to apiDefinition.swagger.json] --icon [Path to icon.png] --secret 
		--secret aregument is optional depending on the authentication model being used.
		During the update process as well, we can choose the environment in a given tenant and choose the organization in a given environment. As we saw in the download section.
