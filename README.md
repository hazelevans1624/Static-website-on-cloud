# Static Website Hosting on AWS with CI/CD 🚀

### If you found this repo useful, give it a STAR 🌠

This blog post will guide you through creating a simple CI/CD pipeline to host a static website on AWS using S3, CloudFront, and GitHub for continuous integration and deployment. We'll also ensure our website is secure and highly available.

# Introduction
In this tutorial, we will set up a CI/CD pipeline for a static website hosted on AWS.

We will use the following AWS services:

• Amazon S3: To store our static website files.

• Amazon CloudFront: To distribute content globally with low latency.

• Namecheap (DNS): To manage our domain name.

• AWS Certificate Manager: To provide SSL/TLS certificates for secure HTTPS access.

• GitHub: To host our website source code.

• AWS Code Pipeline: To automate the deployment process.

# Architecture Diagram for AWS
Image

## Prerequisites
Before we begin, ensure you have the following:

> `An AWS account`

>`A GitHub account`

>`A domain name registered via Namecheap or any other registrar`

##  Step-by-Step Instructions
Setting Up the S3 Bucket

### Create an S3 Bucket:
Go to the AWS Management Console and navigate to S3.

Image

> - Click "Create bucket"

> - Enter a unique bucket name (e.g., www.staticwebsitedemo.xyz).

>- Block all public access.

Image

>- Select the region and click "Create bucket".

### Configure Bucket for Static Website Hosting:
>- Click on the bucket name.

>-  Go to the "Properties" tab.

>-  Scroll down to "Static website hosting" and enable it.

>-  Specify the index document (e.g., index.html).

>-  Upload the index.html and style.css files to the bucket.
Image

3.	Access Your Website:
>-  Now you'll see the endpoint or URL to access your website.
>- You can manually upload your website files to Amazon S3, but it will show a 403 forbidden error due to disabled public access.

### B. Configuring CloudFront
1.	Create a CloudFront Distribution:
>- Go to the CloudFront console and click "Create Distribution".
>- Select the endpoint URL from the dropdown.
>- Add your custom domain (e.g., www.staticwebsitedemo.xyz).
>- Request a Certificate.
>- Configure SSL/TLS.
>- Create Distribution.

### C. Setting Up DNS via Name Cheap provider
1.	Configure DNS with Name Cheap:
>- 	In NameCheap, go to Advanced DNS and add a new CName record.
>- 	Select CName from the dropdown menu and paste the CloudFront distribution URL as the value.

### D. Creating an SSL Certificate
1.	Request a Certificate in ACM:
>- 	Go to the ACM console and request a public certificate.
>- 	Enter your domain name and follow the validation steps.

### E. Integrating GitHub with Code Pipeline:
1.	Add Source Stage in Code Pipeline
>- 	Use GitHub repository and authorize access.

Image
>- 	Click GitHub webhook.
>- 	Configure deployment provider as S3 and extract files before deployment.

Image
>- 	Create the pipeline.

### F. Deploying the Website
1.	Commit and Push Code to GitHub:
>- 	Code Pipeline will automatically build and deploy your site to S3.
2.	Test the Deployment:
>- 	Open your browser and navigate to your domain (e.g., www.staticwebsitedemo.xyz).
>- 	Verify that your website is live and served via CloudFront with HTTPS.
>- 	Make changes in index.html file on GitHub and see if changes are reflected on the website.

Image 

# 5. Conclusion
By following these steps, you have successfully set up a CI/CD pipeline for a static website on AWS using S3, CloudFront, and Code Pipeline. This ensures that your site is always up-to-date and securely delivered to users worldwide.
Feel free to reach out if you have any questions or run into any issues. Happy coding! 🚀


