## Technical Lab Report: Launching a Static Website on Amazon S3

### 1. Objective

The objective of this task was to create and configure an **Amazon S3 bucket** to host a static website, adhering to AWS best practices for deployment and access control. The static website content was sourced from the `/static-website` directory.

---

### 2. Procedure: S3 Bucket Creation and Configuration

#### 2.1 Bucket Creation and Initial Setup

1.  The Amazon S3 console was accessed to initiate the process.
2.  A new bucket was created using the **Create bucket** button in the chosen AWS Region: **US East (N. Virginia) (us-east-1)**.
3.  **Critical Configuration:** During creation, the default **Block all public access** setting was **cleared** and **ACLs** (Access Control Lists) were **enabled** to prepare the bucket for public web access.
    ![Bucket Created](./public/assets/created_bucket.png)

#### 2.2 Static Website Hosting Enablement

1.  The website content, including the `index.html` file, CSS folder, and images folder, was uploaded to the S3 bucket (`cafe-s3-demo-bucket`).
2.  Under the **Properties** tab of the bucket, **Static website hosting** was enabled.
3.  The **Index document** was specified as `index.html`.
    ![Enabled static hosting](public/assets/enabled_static_hosting.png)

---

### 3. Access Control and Troubleshooting

#### 3.1 Initial Access Attempt and Denial

1.  The endpoint link for the static website was opened in a separate browser tab.
2.  The initial access attempt resulted in an **Access Denied** error.
    ![Access denied](public/assets/access_denied.png)
3.  **Rationale:** AWS security follows the principle of "If not implicitly allowed, default to explicit deny." Although public access was unblocked during creation, an explicit **Bucket Policy** was still required to grant public read permission.

#### 3.2 Creating a Bucket Policy for Public Read Access

1.  The **Permissions** tab for the bucket (`cafe-s3-demo-bucket`) was accessed.
2.  Under the **Bucket Policy** section, the following JSON policy was added to grant public `s3:GetObject` permission:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::cafe-s3-demo-bucket/*"
            ]
        }
    ]
}
```
![Bucket policy added](public/assets/bucket_policy_added.png)