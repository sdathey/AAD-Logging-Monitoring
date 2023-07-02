# AAD-Logging-Monitoring

![Cloud Honeynet / Azure AD Logging and Monitoring](https://i.imgur.com/AYBRGCy.jpg)

## Introduction

In the previous project, Rayda Estate, a fictional company, deployed an Azure-based honeynet open to the Internet to attract  hackers. Log sources from various instances are collected in a Log Analytics workspace, enabling Microsoft Sentinel to generate attack maps, alerts, and incidents. Initial security metrics were measured over 24 hours in the insecure environment. Subsequently, security controls were implemented to fortify the environment, and metrics were measured for another 24 hours. One of those logs was Azure Active Directory Logs.
Azure Active Directory Logs capture the complete sign-in activity history and maintain an audit trail of all activities and changes within Azure AD for a specific tenant. These logs encompass sign-in and audit logs, detailing the activities and modifications that occur within the Active Directory. To seamlessly transmit these sign-in and audit logs to the Log Analytics workspace, I will configure the AAD diagnostic setting accordingly.

## Step-By-Step Configuration Of Azure AD Logging

![Architecture Diagram](https://i.imgur.com/46gTdRp.jpg)

1. From the Azure home page, search for Azure Active Directory in the search bar

2. Click to open the  Azure Active Directory from the drop-down menu.

![Architecture Diagram](https://i.imgur.com/EyoWCbk.jpg)

3. From the Azure Active Directory page

4. Click Diagnostic setting and then

5. Click Add diagnostic setting to configure the Diagnostic setting

![Architecture Diagram](https://i.imgur.com/B8fuY7a.jpg)

6. Give the Diagnostic setting a name by entering a name. In this case, the name is "AAD-Logs"

7. Select from the Logs categories which Logs you want to collect
  i.e.: AuditLogs, Signinlogs, ManagedIdentitySigninLogs, RiskyUsers, etc...
  
8. Select the destination for the selected logs. In this case, they are sent to the
  Log Analytics workspace
  
9. Select the appropriate Subscription. In this case "RaydaEstateProject"

10. Select the appropriate Logs Analytics workspace. In this case, "LogAnalyticsREP" 
  which resides in the east US 2
  
11. Click Save to create the Diagnostic setting for Azure Active Directory Tenant

## Test To Ensure The Logs Have Been Ingested Into The Logs Analytics Workspace

![Architecture Diagram](https://i.imgur.com/DpfQEML.jpg)

1. From the Azure home page, search for Log Analytics workspace in the search bar

2. Click to open the Log Analytics workspace from the drop-down menu

![Architecture Diagram](https://i.imgur.com/sm0qinX.jpg)

3. From the Log Analytics workspace page

4. Click Logs to access the query page 

5. Type AuditLogs ( AuditLogs is one of the Logs categories selected to be sent to the 
  Log Analytics workspace)

6. Click Run to run the AudiLogs query 

7. The results of the query are populated in the Log Analytics workspace 

![Architecture Diagram](https://i.imgur.com/xTOccA0.jpg)

8. Press Enter twice then type SigninLogs (SigninLogs is one of the Logs 
  categories selected to be sent to the Log Analytics workspace)

9. Click Run to run the SigninLogs query

10. The results of the query are populated in the Log Analytics workspace

## Conclusion
The configuration of the Azure Active Directory logs ingestion into the Log Analytics workspace was successful. Now, these logs are being efficiently collected and stored for analysis. This configuration enables the monitoring of Azure tenant-level logs through both the Log Analytics workspace and Microsoft Sentinel. By centralizing the logs in the Log Analytics workspace, organizations gain a comprehensive view of their Azure Active Directory activities and can leverage the powerful capabilities of Microsoft Sentinel for advanced threat detection and response. This integrated setup enhances the security and visibility of the Azure environment, enabling proactive monitoring and efficient incident management.
