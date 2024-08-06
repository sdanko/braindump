# Azure Monitor and Service Health

Data like logs from Entra ID, activity logs and metrics get stored to Azure Monitor automatically.

Every type of resource has diagnostic settings.

Log Analytics Workspace is useful if you want to analyze certain log data. You can store data up to 2 years.
You pay for the amount of data ingested.

You can also write log data to a storage account.

You can also connect logs to Event Hub.

You can create alert rules based on some criteria. You can have different action rules for the alert. 
These rules call an action group.

## Service Health

In service health you can historically see what has happened to your environment. You can also see planned maintenance.