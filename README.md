# Static Website Hosting on AWS with CI/CD 🚀

### If you found this repo useful, give it a STAR 🌠

This blog post will guide you through creating a simple CI/CD pipeline to host a static website on AWS using S3, CloudFront, and GitHub for continuous integration and deployment. We'll also ensure our website is secure and highly available.

# Introduction
In this tutorial, we will set up a CI/CD pipeline for a static website hosted on AWS.

We will use the following AWS services:
<div style="padding-left: 20px;">
  • Amazon S3: To store our static website files.<br>
  • Amazon CloudFront: To distribute content globally with low latency.<br>
  • Namecheap (DNS): To manage our domain name.<br>
  • AWS Certificate Manager: To provide SSL/TLS certificates for secure HTTPS access.<br>
  • GitHub: To host our website source code.<br>
  • AWS Code Pipeline: To automate the deployment process.<br>
</div>

# Architecture Diagram for AWS
![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/4c1a501b-cf9c-48ae-b08b-54619f860937)

## Prerequisites
Before we begin, ensure you have the following:
> `An AWS account`

> `A GitHub account`

> `A domain name registered via Namecheap or any other registrar`

##  Step-by-Step Instructions
Setting Up the S3 Bucket

### A. Create an S3 Bucket:
Go to the AWS Management Console and navigate to S3.

![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/bd0114b0-5822-40b8-97fb-48dd9fa5fb11)
<div style="padding-left: 20px;">
  
   - Click "Create bucket"
   - Enter a unique bucket name (e.g., www.staticwebsitedemo.xyz).
   - Block all public access.

![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/5a382d80-5ecb-46d7-936c-2a9ea07af4d7)

 - Select the region and click "Create bucket".
</div>

### Configure Bucket for Static Website Hosting:
<div style="padding-left: 20px;">
  
  - Click on the bucket name.
  - Go to the "Properties" tab.
  - Scroll down to "Static website hosting" and enable it.
  - Specify the index document (e.g., index.html).
  - Upload the index.html and style.css files to the bucket.
![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/15616394-6bcc-47fa-be5c-6e1f1db0bd2b)

  -  Access Your Website:
  -  Now you'll see the endpoint or URL to access your website.
  -  You can manually upload your website files to Amazon S3, but it will show a 403 forbidden error due to disabled public access.
    </div>
![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/21cf213f-de49-4080-88e1-e4379235f592)

### B. Configuring CloudFront
<div style="padding-left: 20px;">
  
1.	Create a CloudFront Distribution:
  - Go to the CloudFront console and click "Create Distribution".
  - Select the endpoint URL from the dropdown.
  - Add your custom domain (e.g., www.staticwebsitedemo.xyz).
  - Request a Certificate.
  - Configure SSL/TLS.
  - Create Distribution.
</div>

### C. Setting Up DNS via Name Cheap provider
<div style="padding-left: 20px;">
  
1.	Configure DNS with Name Cheap:
  - In NameCheap, go to Advanced DNS and add a new CName record.
  - Select CName from the dropdown menu and paste the CloudFront distribution URL as the value.
    </div>

### D. Creating an SSL Certificate
<div style="padding-left: 20px;">
  
1.	Request a Certificate in ACM:
  - Go to the ACM console and request a public certificate.
  - Enter your domain name and follow the validation steps.
</div>

### E. Integrating GitHub with Code Pipeline:
<div style="padding-left: 20px;">
  
1.	Add Source Stage in Code Pipeline
  - Use GitHub repository and authorize access.
![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/f28f91e9-2e70-4e0a-b39f-3431dc8d6bc0)

  - Click GitHub webhook.
  - Configure deployment provider as S3 and extract files before deployment.
![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/223e7261-aad6-498b-962d-60024311b2db)

  - Create the pipeline.
</div>

### F. Deploying the Website
<div style="padding-left: 20px;">
  
1.	Commit and Push Code to GitHub:
  - Code Pipeline will automatically build and deploy your site to S3.
2.	Test the Deployment:
  - Open your browser and navigate to your domain (e.g., www.staticwebsitedemo.xyz).
  - Verify that your website is live and served via CloudFront with HTTPS.
  - Make changes in index.html file on GitHub and see if changes are reflected on the website.

![image](https://github.com/hazelevans1624/Static-website-on-cloud/assets/173595802/402a2c35-9916-4354-8ae0-61e959bf19f9)

</div>

# 5. Conclusion
By following these steps, you have successfully set up a CI/CD pipeline for a static website on AWS using S3, CloudFront, and Code Pipeline. This ensures that your site is always up-to-date and securely delivered to users worldwide.
Feel free to reach out if you have any questions or run into any issues. Happy coding! 🚀


