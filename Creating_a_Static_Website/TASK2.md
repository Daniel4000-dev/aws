# Creating a bucket policy to grant public read access

- Under Bukets, choose the name of the bucket, **cafe-s3-demo-bucket** in my case.
- Choose **Permissions** 
- Under **Bucket Policy** choose **Edit**
- To grant public read access for the website, copy the following bucket policy, and paste it in the Bucket policy editor.

```json
{
    "version": "2012-10-17",
    "statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3": "GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::cafe-s3-demo-bucket/*"
            ]
        }
    ]
}
```