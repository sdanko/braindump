# Data Services

With data services, there is some kind of source that need to get to some sink(data warehouse, another database etc.).

This process involves multiple steps:
- Extract data
- Transform data
- Load data

Azure Data Factory is in charge of orchestrating all of these steps.

For transformation there are multiple services:
- HdInsight(large number of open source solutions as a data source)
- Data Bricks(it uses Apache Spark)

## Azure Synapse Analytics

It supports orchestration, it has a data warehouse capability, and it has its own Apache Spark 
transformation service. It brings everything together in one workspace.