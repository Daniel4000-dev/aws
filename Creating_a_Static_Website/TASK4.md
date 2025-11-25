# Enhancing durability and planning for DR

- Here I'll enable cross-Region replication on my source S3 bucket.

## Enabling cross-Region replication

- In a different Region than the Region for my source bucket, created a second bucket and enabled versioning on it. The second bucket is my destination bucket.
![Cross region bucket](./public/assets/cross_region_bucket.png)
- On my source S3 bucket, enabled cross-Region replication. When I created the replication rule, I made sure that I did the following:
  - Replicate the entire source bucket.
  - Use **CafeRole** for the AWS Identity and Access Management (IAM) role. This IAM role gives Amazon S3 the permissions to read objects from the source bucket and replicate them to the destination bucket.