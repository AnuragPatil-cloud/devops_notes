## Introduction to S3 Lifecycle Rule

Amazon S3 Lifecycle Rule is a cost-optimization and data-management feature that automatically manages objects stored in an S3 bucket throughout their lifetime. Lifecycle rules allow you to define actions such as transitioning objects to cheaper storage classes, archiving data, and deleting objects after a specific time period.

By using lifecycle rules, organizations can reduce storage costs, improve data governance, and eliminate manual cleanup tasks. Lifecycle configurations run automatically once per day and apply to either the entire bucket or selected objects based on prefixes and tags.

Lifecycle rules are commonly used for managing application logs, database backups, temporary uploads, compliance records, and archival data. They help ensure that data is stored in the most cost-effective storage class based on its access pattern and retention requirement.



# Steps to Configure S3 Lifecycle Rule

### Step 1: Open Amazon S3
Log in to AWS Management Console and open the **Amazon S3** service.
<img width="1470" height="589" alt="Screenshot 2025-12-29 at 4 30 47 PM" src="https://github.com/user-attachments/assets/2520a6f8-4e8d-4d01-a92c-fb116aceb950" />

### Step 2: Select Bucket
Click on the S3 bucket where you want to apply lifecycle rules.

### Step 3: Open Management Tab
Navigate to the **Management** tab of the selected bucket.
<img width="1466" height="633" alt="Screenshot 2025-12-29 at 4 30 58 PM" src="https://github.com/user-attachments/assets/fa976579-5c60-46d1-a1a6-6b5c13945860" />



### Step 4: Open Lifecycle Rules
Scroll to the **Lifecycle rules** section and click **Create lifecycle rule**.
<img width="1469" height="481" alt="Screenshot 2025-12-29 at 4 32 09 PM" src="https://github.com/user-attachments/assets/b0dd432d-ab18-4ac1-920a-319569c43405" />



### Step 5: Enter Rule Details
- Enter a **Lifecycle rule name**
- Select **Apply to all objects in the bucket**
<img width="1444" height="549" alt="Screenshot 2025-12-29 at 4 34 49 PM" src="https://github.com/user-attachments/assets/0312faca-a606-4ebf-beef-23619c1ab8ec" />



### Step 6: Configure Transition Rules

| Days After Upload | Storage Class |
|------------------|---------------|
| 30 Days | Standard-IA |
| 90 Days | Glacier |
| 180 Days | Deep Archive |

Enable:
- Apply to **current versions**
- Apply to **non-current versions**
<img width="1276" height="618" alt="Screenshot 2025-12-29 at 4 35 04 PM" src="https://github.com/user-attachments/assets/eba66cf5-a0ab-45d0-9f6a-6c413888bd30" />


### Step 7: Configure Expiration
<img width="1228" height="651" alt="Screenshot 2025-12-29 at 4 58 07 PM" src="https://github.com/user-attachments/assets/0d89b121-e6e4-465c-9433-daf3366106b8" />


### Step 8: Review and Create Rule
Review all settings and click **Create rule**.


### Step 9: Verify Rule
Confirm the rule status is **Enabled** under Lifecycle rules.
<img width="1455" height="411" alt="Screenshot 2025-12-29 at 4 35 26 PM" src="https://github.com/user-attachments/assets/fbe71ccc-f9b7-42a4-82a6-79ea8eddb9e2" />

