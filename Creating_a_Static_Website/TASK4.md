# Enhancing durability and planning for DR

- Here I'll enable cross-Region replication on my source S3 bucket.

## Enabling cross-Region replication

- In a different Region than the Region for my source bucket, created a second bucket and enabled versioning on it. The second bucket is my destination bucket.

![Cross region bucket](./public/assets/cross_region_bucket.png)

- On my source S3 bucket, enabled cross-Region replication. When I created the replication rule, I made sure that I did the following:
  - Replicate the entire source bucket.
  - Use **CafeRole** for the AWS Identity and Access Management (IAM) role. This IAM role gives Amazon S3 the permissions to read objects from the source bucket and replicate them to the destination bucket.
  - If encountered the warning The replication rule is saved, but it might not work, you can ignore it and proceed to the next step.
  - Chose No, On the prompt about Replicate existing objects.

**CafeRole** has the following permissions:
  ```json
Version: 2012-10-17
Statement:
  - Action:
  - s3:ListBucket
  - s3:ReplicateObject
  - s3:ReplicateDelete
  - s3:ReplicateTags
  - s3:Get*
    Resource:
  - '*'
    Effect: Allow
  ```
  This access policy allows the role to perform the replication tasks on all S3 buckets. In a real production environment, you should restrict the policy to apply to only your source and destination S3 buckets.

  - Made a minor change to the index.html file, and uploaded the new version to my source bucket.
  - Verified that the source bucket now has three versions of the index.html file.
  ![Three version bucket](./public/assets/three_bucket.png)
  - Confirmed that the new object was replicated to my destination bucket. You might need to reload the browser tab.

