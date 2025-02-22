---
# Metadata required by https://docs.microsoft.com/samples/browse/
# Metadata properties: https://review.docs.microsoft.com/help/contribute/samples/process/onboarding?branch=main#add-metadata-to-readme
languages:
- csharp
page_type: sample
name: "ASP.NET Core 6.0 Web App Sign-in user"
description: "This is a ASP.NET Core 6.0 Web App that sign-in users. The code in this sample is used by one or more articles on docs.microsoft.com."
products:
- azure
- azure-active-directory
- ms-graph
- microsoft-identity-platform
urlFragment: ms-identity-docs-code-csharp-sign-in
---

# ASP.NET Core 6.0 Web App - Sign-in user | Microsoft identity platform

The web app in this scenario has been created using the ASP.NET Core 6.0 Razor template, and slightly modified to add authentication enabling the users sign-in that follows the [Open Id Connect](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-protocols-oidc) standard protocol. To lite up Open Id, it is using [ASP.NET Core Identity](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/identity?view=aspnetcore-6.0) middlewares.  In other words, a simple web app is secured by adding an authentication layer allowing users to sign-in with their Work and school (Azure AD) accounts, and as a result it can make web API calls to protected resources on behalf of the signed-in user.

![A screenshot of an ASP.NET Core 6.0 Web App displaying a response from Microsoft Graph.](./app-signedin.png)

> :page_with_curl: This sample application backs one or more technical articles on docs.microsoft.com. <!-- TODO: Link to first tutorial in series when published. -->

## Prerequisites

- An Azure Active Directory (Azure AD) tenant. You can [open an Azure account for free](https://azure.microsoft.com/free) to get an Azure AD instance.
- [.NET 6.0 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)

## Setup

### 1. Register the web API application in your Azure Active Directory

First, complete the steps in [Register an application with the Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app) to register the sample app.

Use the following settings for your app registration:

| App registration <br/> setting | Value for this sample app                          | Notes                                                                                                       |
|:------------------------------:|:---------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| **Name**                       | `active-directory-dotnet-webapp-aspnetcore`        | Suggested value for this sample. <br/> You can change the app name at any time.                             |
| **Supported account types**    | **My organization only**                           | Required for this sample. <br/> Support for the Single tenant.                                              |
| **Platform type**              | `Web`                                              | Required value for this sample. <br/> Enables the required and optional settings for the app type.          |
| **Redirect URIs**              | `https://localhost:5001/signin-oidc`               | Required value for this sample. <br/> You can change that later in your own implementation.                 |
| **Front-channel logout URL**   | `https://localhost:5001/signout-oidc`              | Required value for this sample. <br/> You can change that later in your own implementation.                 |
| **Client secret**              | _Value shown in Azure portal_                      | :warning: Record this value immediately! <br/> It's shown only _once_ (when you create it).                 |

> :information_source: **Bold text** in the table matches (or is similar to) a UI element in the Azure portal, while `code formatting` indicates a value you enter into a text box or select in the Azure portal.

### 2. Configure the web app

1. Open the _~/sign-in-webapp/WebApp.csrpoj_ in your code editor.
1. Open the _appsettings.json_ file and modify the following code:

    ```json
    "TenantId": "[Enter 'common', or 'organizations' or the Tenant ID (Obtained from the Azure portal. Select 'Endpoints' from the 'App registrations' blade and use the GUID in any of the URLs), e.g. da41245a5-11b3-996c-00a8-4d99re19f292]",
    "ClientId": "[Enter the Client Id (Application ID obtained from the Azure portal), e.g. ba74781c2-53c2-442a-97c2-3d60re42f403]",
    "ClientSecret": "[Copy the client secret added to the app from the Azure portal]",
    ```

## Run the application

### 1. Run the webapp

1. Execute the following command to get the app up and running:

   ```bash
   dotnet run
   ```

### 2. Signin into the web app

1. Once the web app is listening, navigate to https://localhost:5001
1. Sign-in with your user credentials.

### 3. Signout

1. Click Sign out

![A screenshot of an ASP.NET Core 6.0 Web App indicating the user signed-out and allowing click "Sign in" to signin again.](./app-signedout.png)

## About the code

The ASP.NET Core 6.0 Web App will allow users to sign-in, so it can retrieve a Security Token scoped specifically for the Microsoft Graph API, and will use that token to access the user's information. For more information about the proposed scenario, please take a look at the following diagram:

:link: For more information about how to proctect your projects, please let's take a look at https://docs.microsoft.com/en-us/azure/active-directory/develop/sample-v2-code. To know more about how this sample has been generated, please visit https://docs.microsoft.com/en-us/aspnet/core/tutorials/razor-pages/?view=aspnetcore-6.0

## Reporting problems

### Sample app not working?

If you can't get the sample working, you've checked [Stack Overflow](http://stackoverflow.com/questions/tagged/msal), and you've already searched the issues in this sample's repository, open an issue report the problem.

1. Search the [GitHub issues](../../issues) in the repository - your problem might already have been reported or have an answer.
1. Nothing similar? [Open an issue](../../issues/new) that clearly explains the problem you're having running the sample app.

### All other issues

> :warning: WARNING: Any issue _not_ limited to running this or another sample app will be closed without being addressed.

For all other requests, see [Support and help options for developers | Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/developer-support-help-options).

## Contributing

If you'd like to contribute to this sample, see [CONTRIBUTING.MD](/CONTRIBUTING.md).

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
