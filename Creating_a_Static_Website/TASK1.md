# Launching a static website

Note: the file uploaded to my S3 bucket can be found in the /static-website directory

## Creating an S3 bucket to host my static website
Here i will create an S3 bucket and configure it to host my static website.

- Opened the Amazon S3 console.
- Created a bucket in my choice AWS Region. (I used ```US East (N. Virginia) us-east-1```)
Note: I cleared the ```Block all public access``` and enable ```ACLs```.
![Bucket Created](public/assets/created_bucket)
- Enabled static Website hosting on my bucket in the properties tab after uploading my document.
- Used the index.html file for my index document.
![Enabled static hosting](public/assets/enabled_static_hosting)