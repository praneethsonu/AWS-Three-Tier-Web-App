<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# P4 - Build a Three-Tier Web App

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-threetier)

**Author:** Praneeth Bhandwalkar  
**Email:** praneeth2003bhandwalkar2.0@gmail.com

---

## Build a Three-Tier Web App

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_2b3c4d5e)

---

## Introducing Today's Project!

In this project, I will demonstrate the three-tier web application. I'm doing this project to learn about the three tier and how they manage and scale the application.

### Tools and concepts

Services I used were Amazon S3, Amazon CloudFront, AWS Lambda, Amazon API Gateway, and Amazon DynamoDB. Key concepts I learnt include Lambda functions, which are a core part of allowing code to run in response to events without the need for a server.

### Project reflection

This project took me approximately 160 minutes to complete the project.

Through this project, I gained practical insights into the challenges of maintaining separation of concerns and ensuring smooth integration between the three layers and build a three-tier architecture.

---

## Presentation tier

For the presentation tier, I will set up an S3 bucket to store website files and upload a simple "index.html" file into the S3 bucket then set up CloudFront because it is used to deliver the website's content globally.

After uploading website files into the S3 bucket, I accessed my delivered website using the CloudFront distribution domain name.

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_3a4b5c6d)

---

## Logic tier

For the logic tier, I will set up the Lambda function and API Gateway because the Lambda function retrieves user data from the DynamoDB table and to access it I use an API Gateway to handle requests and route them to the right place.

The Lambda function retrieves data by executing code in response to events and integrating with various data sources, such as databases and APIs.

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_6a7b8c9d)

---

## Data tier

For the data tier, I will set up to create a DynamoDB table and add user data into the table because I need DynamoDB to store some user data.

The partition key for my DynamoDB table is essential for organizing data efficiently, which means it helps in distributing data across multiple servers for quick access and efficient querying.

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_u1v2w3x4)

---

## Logic and Data tier

Once all three layers of the three-tier architecture are set up, the next step is to update the "script.js" file with the API request and verify the data to display the returned data.

To test my API, I checked the Invoke URL of my prod stage API. This allowed me to determine whether I could use the API to retrieve user data. The results were shown as user data with the logic and data tier's integration

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_a112c3d5)

---

## Console Errors

The error in my distributed site was referencing a URL [YOUR-PROD-API-URL]/users?userId=1 because this URL is in line 9 of our script.js file.

To resolve the error, I updated script.js by replacing [YOUR-PROD-API-URL] in the script. I then reuploaded it into S3 because it will act as an integration for the logic tier and presentation tier.

I ran into a second error after updating script.js. This was an error with CORS (Cross-Origin Resource Sharing) is like a security bouncer for your browser. . because the API Gateway is not configured to allow requests from your CloudFront URL.

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_a1b2c3d5)

---

## Resolving CORS Errors

To resolve the CORS error, I first went to API Gateway navigated to the Resources tab selected users, and then Enabled the CORS with configuration GET and OPTIONS.

I also updated my Lambda function because of the CORS headers addition. The changes I made were to replace * with your CloudFront domain name. Keeping Access-Control-Allow-Origin means you're allowing everyone to use your API.

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_1qthryj2)

---

## Fixed Solution

I verified the fixed connection between API Gateway and CloudFront by Deploying the API by enabling CORS

![Image](http://learn.nextwork.org/thankful_azure_innocent_oriental_melon/uploads/aws-compute-threetier_2b3c4d5e)

---

---
