# AAW Frequently Asked Questions

Welcome to the AAW F.A.Q. If your question does not appear in this document, please reach out to us on our [Slack Support Channel](https://statcan-aaw.slack.com/).

### What data formats are supported in the AAW?

The AAW includes tools that allow data science users to open many file formats. There's quite a push in StatCan to standardize on SDMX, with little to no added context. I don't really know what that means, so I wouldn't expect our users to either. So maybe they hear "SDMX standard" and think that means for everything all the time. Not sure.

The AAW supports many commonly used file formats, including (but not limited to):

- csv
- xlsx
- json
- xml
- sas7bdat
- sqlite
- many others... just ask

### What do we say to people about costs? What's a good ballpark example figure for usage and costing?



### What are the steps for getting Protected B data into MinIO? I want to show that. I know we can't make a Protected B notebook with MinIO but that's how we are supposed to do things, right?
### What does integration with Power BI look like? What can be shared between AAW and Power BI? Is it just data?


In addition to what @Yann Coderre wrote: I just added aaw-cost-use-cases.ods to our shared GDrive, which covers three example use cases and gives ballpark figures. I haven't looked at it in months, so some of the unit costs probably need adjusting – particularly MinIO, which switched to gateway mode since that doc was created.
We get ProB data into MinIO via FDI. The do an Azure Data Factory pipeline to move data, typically from on prem, to an Azure Storage Account. MinIO is an S3 gateway to that storage account, and that MinIO is only accessible from workloads Kubernetes-labeled something to the effect of .statcan.gc.ca/classification: protected-b.
At the moment, I think it's nothing. An easy thing to do would be to use a storage account bridge like you suggested: do whatever processing you want in AAW, persist to MinIO, then load it into PowerBI from there.
