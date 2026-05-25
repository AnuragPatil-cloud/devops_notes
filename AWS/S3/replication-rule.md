## Introduction to S3 Replication Rule

Amazon S3 Replication Rule is a data replication feature that automatically copies objects from one S3 bucket to another bucket, either in the same AWS Region (SRR – Same-Region Replication) or in a different AWS Region (CRR – Cross-Region Replication).

Replication rules help in maintaining data durability, disaster recovery, compliance requirements, and low-latency access for users located in different geographic locations. Once replication is enabled, all new objects uploaded to the source bucket are automatically replicated to the destination bucket without manual intervention.

S3 Replication supports filtering objects using prefixes and tags, replicating existing objects, and maintaining object metadata, permissions, and encryption settings. This ensures that replicated data remains consistent, secure, and available across multiple locations.

Replication rules are widely used for backup storage, business continuity planning, regulatory compliance, and global content distribution.


# Steps to Configure S3 Replication Rule

### Step 1: Enable Versioning on Both Buckets
Open **Amazon S3** and enable **Versioning** on:
- Source bucket
- Destination bucket

### Step 2: Open Source Bucket
Go to the **source bucket** from which objects will be replicated.




### Step 3: Open Management Tab
Navigate to the **Management** tab of the source bucket.
<img width="1457" height="333" alt="Screenshot 2025-12-29 at 4 38 31 PM" src="https://github.com/user-attachments/assets/89a93ae3-4fdb-474f-a72f-65049d3b8da9" />


### Step 4: Open Replication Rules
Scroll to **Replication rules** and click **Create replication rule**.
<img width="1470" height="557" alt="Screenshot 2025-12-29 at 4 39 43 PM" src="https://github.com/user-attachments/assets/84290554-14e4-452c-b90d-c27d22e4b6a2" />

### Step 5: Enter Rule Name
Provide a name for the replication rule.



### Step 6: Choose Rule Scope
Select:<img width="1469" height="278" alt="Screenshot 2025-12-29 at 4 39 55 PM" src="https://github.com/user-attachments/assets/a53649ec-c30b-4569-a2f2-bab4560e2443" />

### step 7: chose destination bucket 
<img width="1464" height="369" alt="Screenshot 2025-12-29 at 4 40 12 PM" src="https://github.com/user-attachments/assets/340e47d6-08c2-4ea8-9c91-53f382c9bdc2" />
<img width="1364" height="393" alt="Screenshot 2025-12-29 at 4 41 36 PM" src="https://github.com/user-attachments/assets/40676828-41ee-4b1a-b20f-b385c3eba904" />
<img width="1454" height="440" alt="Screenshot 2025-12-29 at 4 41 53 PM" src="https://github.com/user-attachments/assets/27696270-6292-449c-a91c-dfe1a36b9ee7" />

### step 8: create job to replication 
<img width="634" height="305" alt="Screenshot 2025-12-29 at 4 42 15 PM" src="https://github.com/user-attachments/assets/ac4149ec-f5f8-4209-b6fd-1ecf4f0c9dea" />

### chose destination bucket to store report in buccket 
<img width="1460" height="531" alt="Screenshot 2025-12-29 at 4 42 45 PM" src="https://github.com/user-attachments/assets/6f720c09-4480-4dfd-a401-85a6c287f2b1" />

<img width="1438" height="298" alt="Screenshot 2025-12-29 at 4 43 02 PM" src="https://github.com/user-attachments/assets/0f2de54d-8c0b-40f7-85f9-d2fa7f0ac072" />

### create replication role 


