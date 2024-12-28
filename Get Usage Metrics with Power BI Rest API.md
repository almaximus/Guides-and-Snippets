# Introduction

Power BI provides an opportunity to monitor usage metrics of dashboards and reports to track how they're used in your organization. 
However, the native usage metrics datasets provide limited functionality, e.g. there's no way to get usage metrics across all workspaces in one page.
To make usage metrics reports more flexible it's better to extract this data using a Power BI Rest API solution which is not straightforward and involves a lot of moving parts to make it work properly.
In this guide I'll be showing how to create a stable usage metric solution and how to make it work.
The whole process will be broken into the following sections:

1. Overwiew and how it works
2. Giving permissions to a user and setting up a Service Principal
3. Giving permissions to the Service Principal on Power BI side
4. Setting up a token
5. Getting data from edpoints
6. Extracting the data
7. Final thoughts
8. Common problems

#  Overwiew and how it works

The first thing we need to do to get the usage metrics is to create a custom application that will be requesting the data on our behalf. It's called a "Service Principal" (https://learn.microsoft.com/en-us/power-bi/developer/embedded/embed-service-principal?tabs=azure-portal). In order to create and use the service principal we will need enough permissions. If we don't have such kind of permissions you can ask your global admin to add them. After the service principal is created it should be added given access to Microsoft Fabric portal as well as to the workspaces which usage metrics we're interested in. If everything is set up properly the service principal will be able to generate a token which will be passed into a url of an endpoint which we will be extracting the data from. In case if there's a lack of permissions on any step the access to data will be denied. To test how the endpoints work use this endpoint https://learn.microsoft.com/en-us/rest/api/power-bi/apps/get-app#code-try-0. Pay attention to "Required Scope" section because if you don't have those permissions the solution won't work. After the access to the data granted you will need to use a workspace id, the id of usage metrics reports in that workspace and the name of the table. Basically, it's 3 levels of data to query from: (pics).
