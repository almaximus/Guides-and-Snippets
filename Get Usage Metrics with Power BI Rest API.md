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

#  Overwiew and how it works
