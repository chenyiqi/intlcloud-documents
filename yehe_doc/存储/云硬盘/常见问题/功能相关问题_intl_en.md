### What is Tencent Cloud Block Storage?
Tencent Cloud Block Storage (CBS) is a highly available and highly reliable block storage device for CVM instances. It provides a wide variety of disks to meet diversified read/write requirements. For more information on CBS, see [Overview](https://intl.cloud.tencent.com/document/product/362/2345).
We recommend CBS when the data frequently changes and you want to persistently store them at a faster read/write speed. CBS can be mounted to any running instance in the same availability zone, enabling you to use an instance’s file system and database storage without following the instance lifecycle. For more information on the CBS operations, see [Operation Overview](https://intl.cloud.tencent.com/document/product/362/33140).

### What are the features of Tencent Cloud CBS?
Tencent Cloud CBS comes with three disk types: Premium Cloud Storage, SSD and Enhanced SSD, all three types offer the following features:
- Elastic mounting and unmounting: elastic cloud disks can be mounted and unmounted. Up to 20 elastic cloud disks can be mounted to each CVM to be used as data disks. 
- Elastic expansion: a single disk supports a maximum capacity of 32 TB. You can scale up the disk at any time.
- Snapshot backup: you can create a snapshot to back up data. This improves data reliability and allows rapid data restoration when necessary. You can also create a cloud disk from the snapshot to accelerate your business deployment.

### What is the difference between COS and CBS?
[Cloud Object Storage (COS)](https://intl.cloud.tencent.com/document/product/436) is available via Web APIs, and is not restricted by file systems, directory structure, number of files, or storage capacity. The service offers various SDKs and tools for business integration, which can also be used independently from CVM. COS is great when you need to access massive amounts of data but is not ideal for millisecond-level response or random read/write scenarios.
[CBS](https://intl.cloud.tencent.com/document/product/362) needs to be used together with CVM and can only be mounted and used after the file system is partitioned or formatted. COS and CBS both have distinct performance metrics for different use cases.

### What limits do cloud disks have?
- A single elastic cloud disk can be scaled up to 32 TB, and cannot be scaled down.
- Elastic cloud disks can only be mounted to CVMs within the same availability zone.
- Up to 20 elastic cloud disks can be mounted to a single CVM as data disks. You can directly mount elastic cloud disks to a CVM you are purchasing or [do so later](https://intl.cloud.tencent.com/document/product/362/32401).
- You can purchase up to 50 elastic cloud disks at one time on the [CBS console](https://console.cloud.tencent.com/cvm/cbs).



### What are the differences between different types of cloud disks?
CBS comes with three types:
- Premium Cloud Storage: suitable for most I/O applications including Web/APP services, logical processing, as well as small and medium-sized sites.
- SSD Cloud Storage: suitable for applications including transactional workloads, as well as small and medium-sized databases.
- Enhanced SSD: suitable for latency-sensitive or high-performance applications including medium and large-sized databases, NoSQL, and log analysis.

Each Cloud Storage service offers unique performance and features at different prices. You can select the cloud disk that best suits your application requirements and budget. For more information on disk types and performance, see [Cloud Disk Types](https://intl.cloud.tencent.com/document/product/362/31636).

### What advantages do cloud disks have?
Cloud disks offer high reliability, elasticity and performance. They are easy to use and support snapshot backup. For more information, see [Product Strengths](https://intl.cloud.tencent.com/document/product/362/3039).

### Can elastic cloud disks be used as system disks?
No. System disks cannot be unmounted or mounted.

[](id:Q1)
### Can cloud disks be used as data disks?
Yes. All types of local disks and cloud disks can be used as data disks.

### Can cloud disks be mounted and unmounted?
- Elastic cloud disks can be mounted and unmounted.
- System disks cannot be mounted or unmounted.

### Can elastic cloud disks be mounted and unmounted in batches?
- Elastic cloud disks can be mounted and unmounted in batches.
- System disks cannot be mounted or unmounted.
