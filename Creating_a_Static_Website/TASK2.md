# Protecting website data
- In this task, I will enable versioning on my S3 bucket and confirm that it works.

## Enabling versioning on the S3 bucket
- In the Amazon S3 console, I enabled versioning on my S3 bucket.

![Enabled versioning](./public/assets/enabled_versioning.png)

- Opened the index.html file, in a text editor.
- Modified the file according to the following this:
  - Locate the first line that has the embedded CSS code bgcolor="aquamarine" in the HTML, and change it to bgcolor="gainsboro".
  - Locate the line that has the embedded CSS code bgcolor="orange" in the HTML, and change it to bgcolor="cornsilk".
  - Locate the second line that has the embedded CSS code bgcolor="aquamarine" in the HTML, and change it to bgcolor="gainsboro".
  - Save the changes.
- Uploaded the updated file to my S3 bucket.
- Reloaded the web browser tab with the website and noticed the changes.

![File Change](./public/assets/file_change.png)

- To see the latest version of the index.html file, go to the bucket.
- Go into the index.html file and toggle the **show versions**. Both versions of this file will then be listed.

![Versioning](./public/assets/versioning_check.png)