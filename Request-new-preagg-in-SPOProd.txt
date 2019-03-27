# How to request a new preagg in SPOProd (SharePoint)

Q: How to request a new preagg in SPOProd for SharePoint?

## Step 1: Prepare information for SPARC OI validation

|Item |Description  |Comment  |
|---------|---------|---------|
|1     |  Account  |  See graphic below |
|2     |  Namespace  | See graphic below |
|3     | Metric (Preagg name)  | See graphic below |
|4     | List of dimensions and the possible unique values of each |         |
|5     | Business justification | Business justification becomes more important as an aggregate becomes large |
|6     | Will the preaggregate be used for a sev1 monitors? | Response should be (yes/No) |
|7     | Filters that may be applied to reduce the cost of the preaggregate | For example of MachineName and MachineRole dimensions and are only interested in the SharePoint Domain, this would lower the query cost significantly |
|8     | Environments you would like the preaggregate graduated to |         |
|9     | Provide link to the metric | [Example of link to metric](https://nam06.safelinks.protection.outlook.com/?url=https://jarvis-west.dc.ad.msft.net/?page%3Dsettings%26mode%3Dmdm%26tab%3Dmetrics%26account%3DSPOTest%26namespace%3DQosIncoming%26metric%3DTotalCount&data=04%7c01%7crafost%40microsoft.com%7ca8d12ea3ce9248c5a6b408d691eca461%7c72f988bf86f141af91ab2d7cd011db47%7c1%7c0%7c636856842900477078%7cUnknown%7cTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7c-1&sdata=d3enonlv/lKTfps%2B/68Qz%2Bze/8VJY8LqE85F36ShNVY%3D&reserved=0) |
|10     | Provide link to chart where preagg is used | [Example of preagg chart](https://nam06.safelinks.protection.outlook.com/?url=https://jarvis-west.dc.ad.msft.net/dashboard/share/6CD3DA5E&data=04%7c01%7crafost%40microsoft.com%7ca8d12ea3ce9248c5a6b408d691eca461%7c72f988bf86f141af91ab2d7cd011db47%7c1%7c0%7c636856842900477078%7cUnknown%7cTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7c-1&sdata=M9fy9fUK/SrQrCOqwzkKpzrnNX0Xdb3mn8pCCUhAN94%3D&reserved=0) |


### Cardinality calculation

In the example below, we have a cardinality of 12:

- 2 unique values for cluster
- 3 for environment
- 2 for Machine

![Cardinality](../.attachments/1066-cardinality.jpg)

## Step 2: Create a preaggregate in SPOTest

To create a preaggregate, follow the Geneva guidance found [here](https://genevamondocs.azurewebsites.net/metrics/management/metricjarvis.html):

## Step 3: Create a Azure DevOps work ticket with SPARC OI

Create a work ticket found [here](https://onedrive.visualstudio.com/SPARC/_workitems/create/Task?templateId=7d17d17b-febe-481d-9bf6-af974c701f27)

## Step 4: Send an email to SPARC OI

Send an email with the ticket number and any other details you would like to share to sparcoihelp@microsoft.com

## Other details to note

1) Number of tickets to create: If a single user is requesting multiple preaggs be migrated from SPOTest, a single ticket can be created

2) Preaggregates must be tested in the following environments in the following sequence:

    1. Dogfood
    2. SPOMSIT
    3. SPOPROD

3) Some commonly requested fields cause issues so are discouraged and others cannot be supported due to cardinality issues.  For example:

|Dimension  |Comment  |
|---------|---------|
|TenantID | Not supported currently - future support planned for S400/CWL100 |
|CallerID| Not supported|
|MachineName| Discouraged|
|DatabaseName| Discouraged|
