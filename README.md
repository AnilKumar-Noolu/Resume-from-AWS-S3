# Resume from AWS S3 and CloudFront :

Here is the Link of my Resume from S3 Endpoint: http://anil-kumar.com.s3-website-us-east-1.amazonaws.com/

In this Repo, i will explain how to host your resume on AWS S3 and use CloudFront to distribute it globally.

Prerequisites:

-> An AWS account with S3 and CloudFront access
-> A domain name (optional)

Step 1: Create a resume with HTML and CSS

-> Firstly, create a resume with all your experiences and educational background. Then with the help of Opensource and youtube, try to create HTML and CSS file for that resume.

-> Once Your HTML and CSS file is ready, we are good to proceed further with AWS Services like S3 and CloudFront.

Step 2: Create an S3 Bucket

1. Open the S3 Console and click on "Create bucket"

2. Enter a unique name for your bucket like <your-name.com> so that the static website link will be close the outer website's link and select the region closest to your target audience.

![Screenshot (5)](https://user-images.githubusercontent.com/98457309/228787587-17409118-bfe2-4b38-bbdb-bd0adf0d7ad3.png)

3. Also make sure to uncheck the 'Block All Public Access' and acknowledge that. Leave other default settings for the next pages and click "Create bucket" at the end.

![Screenshot (6)](https://user-images.githubusercontent.com/98457309/228787909-bf49e841-0f29-4b58-b2c5-78451848f8a1.png)

Step 2: Upload your Resume

1. Inside your bucket, click on "Upload"

2. Select your resume files i.e index.html and style.css and click "Next" (here I have uploaded headshot.png as I have added photo to my resume). if you want to add your photocopy to your resume, you can add that too.

3. Leave the default settings for the next pages and click "Upload" at the end
 
![Screenshot-7](https://user-images.githubusercontent.com/98457309/228789539-150faaa1-9b00-458c-98f0-2651e8056440.png)

Step 3: Configure Bucket Permissions

1.bSelect your bucket and click on the "Properties" tab.

2. Click on Static website Hosting at the end and enable that.

![Screenshot-8](https://user-images.githubusercontent.com/98457309/228790326-94355dbe-5f9b-4f07-ba9d-f3e4a3555f3a.png)

3. Make sure that you added index.html and error.html there, generally it redirects your website endpoint to index.html and incase of any error, it redirects it to the content specified in the error.html.

![Screenshot-9](https://user-images.githubusercontent.com/98457309/228790717-7cf13eba-59a8-4f23-b239-555b9fb7ae51.png)

4. Again, Select your bucket and click on the "Permissions" tab. Click on "Bucket Policy" and enter the following JSON policy, replacing "your-bucket-name" with your actual bucket name: Here, we are giving access for the Public to only read.

![Screenshot-10](https://user-images.githubusercontent.com/98457309/228791172-5be3dab6-3da1-463c-8ec1-bf32256727bb.png)

5. once it is done, click on Save

Step 4: Check in the Browser.

1. Once all the above steps are configured, You can go to 'Properties' Tab of your S3 Bucket and at the end, you will find static website hosting Where you can find the link of your S3 Bucket.

![Screenshot-11](https://user-images.githubusercontent.com/98457309/228792363-c00b0839-9302-4d76-8ee9-7d705ba8971e.png)

2. Try Pasting that link to your browser and check whether you can view your resume or not. In the below pic You can see my resume which is hosted on S3 Bucket.

![Screenshot (7)](https://user-images.githubusercontent.com/98457309/228792841-b4aa4567-d934-445d-a993-0cd9d0da99cc.png)

Till Now, You have been successfull in Hosting your website on S3 Bucket endpoint, You will not be charged a single penny from AWS for utilising this S3 Service.
But this is not secure and encrypted as we are using http and https. 

So, To make this more secure and Stable, we will be using cloudFront Distribution which is used for content delivery Network and Host this website using https.

Step 5: Create a CloudFront Distribution

1. Open the CloudFront Console

2. Click on "Create Distribution"

![Screenshot-12](https://user-images.githubusercontent.com/98457309/228795151-5e124766-d39c-412b-8513-e3f52a2f2000.png)

3.Select "Web" as the delivery method and click "Get Started"

4. Configure the following settings:
 
 Origin Domain Name: Select your S3 bucket from the dropdown list

 Origin Path: Leave it empty
 
 Origin ID: Auto-populated with the S3 bucket name
 
 Viewer Protocol Policy: Redirect HTTP to HTTPS
 
 Compress Objects Automatically: Yes
 
 Price Class: Select the region closest to your target audience
 
 Alternate Domain Names (CNAMEs): Enter your domain name (optional)

 Leave the default settings for the next pages and click "Create Distribution" at the end

![Screenshot-13](https://user-images.githubusercontent.com/98457309/228795264-0f7798ba-c768-476c-8064-2398dc01d585.png)

Step 5: Test your Distribution

1. Go to your CloudFront Distribution page and wait for the status to change to "Deployed"

![Screenshot-14](https://user-images.githubusercontent.com/98457309/228796895-ee4149b9-7881-42c3-81f5-4d245efc1ae8.png)

2. Click on the Domain Name to open your resume in a new tab

![Screenshot-15](https://user-images.githubusercontent.com/98457309/228796982-4d149f7e-8a51-41d1-8b8f-707451af3286.png)

3. Verify that your resume is displayed correctly. In the below picture, you can see that you are viewind resume from the CloudFront Distribution Domain Name.

![Screenshot (8)](https://user-images.githubusercontent.com/98457309/228802375-7f5d884c-3cd2-40f6-b7c2-f165e4e7990e.png)

(Optional)

-> If you already had a domain name, you can select that domain name while configuring CloudFront distribution, Also you need to update your DNS records to point to  your CloudFront Distribution.

-> Create a CNAME record for your domain name, pointing to the CloudFront Domain Name

Congratulations, If you have followed all the steps till now, you have successfully hosted your resume on AWS S3 using CloudFront!
