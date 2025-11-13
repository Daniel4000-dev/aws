# Signing in and testing user permissions
here I test the permissions inherited by IAM users in the console.

## 3.1: Get the console sign-in URL
- In the navigation pane on the left, choose Dashboard.
  - Notice the Sign-in URL for IAM users in this account section at the top of the page. The sign-in URL looks similar to the following: **https://123456789012.signin.aws.amazon.com/console**.
  - This link can be used to sign in to the AWS account that I am currently using.
- Copied the sign-in link to a text editor.

## 3.2: Test user-1 permissions
- Opened a private or incognito window in my browser.
- Pasted the sign-in link into the private browser, and pressed ENTER.
  - I will now sign-in as user-1, who was hired as my Amazon S3 storage support staff.
- Signed in with the following credentials:
  - **IAM user name**: ```user-1```.
  - **Password**: ```Lab-Password1```
- Choose the **Services menu**, and choose **S3**. Or use the search bar to find and choose **S3**.
- Choose the name of one of my buckets, and browse the contents.
  - Because this user is part of the S3-Support group in IAM, they have permissions to view a list of Amazon S3 buckets and their contents. Now, to test whether the user has access to Amazon EC2.
- Choose the **Services menu**, and choose **EC2**. I can also use the search bar to find and choose **EC2**.
- In the left navigation pane, choose **Instances**.
  - I cannot see any instances. Instead, an error message says I are not authorized to perform this operation. This user has not been assigned any permissions to use Amazon EC2.
  - I will now sign in as user-2, who was hired as your Amazon EC2 support person.
- First, sign out user-1 from the console.
  - In the upper-right corner of the page, choose **user-1**.
  - Choose **Sign Out**.

## 3.3: Test user-2 permissions
- Pasted the sign-in link into the private browser again, and press ENTER.
- Signed in with the following credentials:
  - **IAM user name**: ```user-2```.
  - **Password**: ```Lab-Password1```.
- Choose the **Services menu**, and choose **EC2**. Or use the search bar to find and choose **EC2**.
- In the navigation pane on the left, choose **Instances**.
  - I now able to see an EC2 instance. However, I cannot make any changes to Amazon EC2 resources because I have read-only permissions.
  - If you cannot see an EC2 instance, then your Region might be incorrect. In the upper-right corner of the page, choose the Region name, and then choose the Region that you were in at the beginning of the lab (for example, N. Virginia).
- Select the EC2 instance.
- Choose the **Instance state** menu, and then choose **Stop instance**.
- To confirm that you want to stop the instance, choose **Stop**.
  - An error message appears and says that You are not authorized to perform this operation. This demonstrates that the policy only allows you to view information without making changes.
  - Next, check whether user-2 can access Amazon S3.
- Choose the **Services menu**, and choose **S3**. Or use the search bar to find and choose **S3**.
  - An error message says You don't have permissions to list buckets because user-2 does not have permissions to use Amazon S3.
  - You will now sign-in as user-3, who was hired as your Amazon EC2 administrator.
- First, sign out user-2 from the console:
  - In the upper-right corner of the page, choose **user-2**.
  - Choose **Sign Out**.

## 3.4: Test user-3 permissions
- Pasted the sign-in link into the private browser again, and press ENTER.
- Sign in with the following credentials:
  - **IAM user name**: ```user-3```.
  - **Password**: ```Lab-Password3```.
- Choose the **Services menu**, and choose **EC2**.
- In the navigation pane on the left, choose **Instances**.
  - An EC2 instance is listed. As an Amazon EC2 Administrator, this user should have permissions to Stop the EC2 instance.
  - If you cannot see an EC2 instance, then your Region might be incorrect. In the upper-right corner of the page, choose the Region name, and then choose the Region that you were in at the beginning of the lab (for example,** N. Virginia**).
- Select the EC2 instance.
- Choose the **Instance state** menu, and then choose **Stop instance**.
- To confirm that I want to stop the instance, choose **Stop**.
  - This time, the action is successful because user-3 has permissions to stop EC2 instances. The Instance state changes to Stopping and starts to shut down.
- Close the private browser window.

### Conclusion
Congratulations! You now have successfully done the following:
- Explored pre-created IAM users and groups
- Inspected IAM policies as applied to the pre-created groups
- Followed a real-world scenario, while adding users to groups with specific capabilities enabled
- Located and used the IAM sign-in URL
- Tested the effects of policies on service access