# Adding users to groups

## Scenario
I recently hired user-1 into a role where they will provide support for Amazon S3. In this task, I add them to the S3-Support group so that they inherit the necessary permissions through the attached AmazonS3ReadOnlyAccess policy.

### 2.1: Adding user-1 to the S3-support group
- In the left navigation pane, choose **User groups**.
- Choose the name of the **S3-Support** group.
- On the **Users** tab, choose **Add users**.
- Select **user-1**, and choose **Add users**.
  - On the Users tab, notice that user-1 was added to the group.

### 2.2: Adding user-2 to the EC2-Suppport group
I hired user-2 into a role where they will provide support for Amazon EC2. I will add them to the EC2-Support group so that they inherit the necessary permissions through the attached AmazonEC2ReadOnlyAccess policy.

- Following previous steps I added **user-2** to the **EC2-Support** group.

### 2.3: Adding user-3 to the EC2-Admin group
I hired user-3 as my Amazon EC2 administrator to manage my EC2 instances. I will add them to the EC2-Admin group so that they inherit the necessary permissions through the attached EC2-Admin-Policy.

- Followed the previous steps and added **user-3** to the **EC2-Admin** group.
- In the navigation pane on the left, choose **User groups**.
  - Each group had a 1 in the Users column. This indicates the number of users in each group.

