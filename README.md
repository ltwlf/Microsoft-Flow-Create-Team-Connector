# Custom Flow Connector to create a Microsoft Team

The connector does not need any code. It just leverages the Microsoft Graph API with the help of an Open API 2.0 specification (swagger file).

## Install

### 1. Register App in Azure Portal
  * Regiser an new Azure AD App in you Azure AD
  * Add the Microsoft Graph permission for delegated "Read and write all groups" (Group.ReadWrite.All)
  * Copy the application id / client id
  * Generate and copy a key / app secret
### 2. Install Custom Connector
  * Sign in to PowerApps Portal https://web.powerapps.com 
  * Navigate to custom connectors -> create custom connector -> import an OpenAPI file 
  * Enter a title for the connector e.g. "Microsoft Teams - Create Team Connector" and choose the teams.swagger.json file from this Git repo -> next
  * Verfiy the following settings: Scheme: (x) HTTPS; Host: "graph.microsoft.com"; Base URL "/" and continue
  * As authentication type choose "OAuth 2.0" 
  * Select "Generic Oauth 2" as Identity provider
    * Client Id -> paste from step 1
    * Client secrret -> paste from step 1
    * Authorization URL: "https://login.microsoftonline.com/_yourtenant_.onmicrosoft.com/oauth2/v2.0/authorize"
    * Token URL: "https://login.microsoftonline.com/_yourtenant_.onmicrosoft.com/oauth2/v2.0/token"
    * Refresh URL: ""https://login.microsoftonline.com/_yourtenant_.onmicrosoft.com/oauth2/v2.0/refresh"
    * Scope: "Group.ReadWrite.All"
    * Create the connector 
    * Navigate to the secuirty tab again and copy the "Redirect URL" and register URL as Reply URL in your Azure AD App within the Azure Portal 
### 3. Create a connection and try the action in flow. You have first to create an Unified Group before you can create a Team. Use the Azure AD - Create Group action to create Unfified Group and use the ID of this group to create Team.


  

