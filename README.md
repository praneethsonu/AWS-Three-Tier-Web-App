# AWS Three-Tier Web Architecture
# Description:
This project is a hands-on walkthrough of a three-tier web architecture in AWS. We will be manually creating the necessary network, security, app, and database components and configurations in order to run this architecture in an available and scalable manner.

# Tier Architecture explanation:
- **Web Server**: This is the front part of a web application that displays the website to users. It handles how the site looks and interacts with users, like showing product pages or allowing people to sign up.

- **Application Server**: This middle part manages the business logic and processes user actions. For example, it checks the inventory to see if a product is in stock or updates a user's account details.

- **Database Server**: This is the back-end part that stores all the data for the application. It uses databases like MySQL or PostgreSQL to keep track of information.
# Architecture Overview:

<img width="4176" alt="3TierArch" src="https://github.com/user-attachments/assets/8ea462dc-281a-4bfe-a092-52695ec5fec0">

In this architecture, a public-facing Application Load Balancer forwards client traffic to our web-tier EC2 instances. The web tier is running Nginx webservers that are configured to serve a React.js website and redirect our API calls to the application tier’s internal facing load balancer. The internal facing load balancer then forwards that traffic to the application tier, which is written in Node.js. The application tier manipulates data in an Aurora MySQL multi-AZ database and returns it to our web tier. Load balancing, health checks, and autoscaling groups are created at each layer to maintain the availability of this architecture.

### Additional Components
#### Load Balancing, Health Checks, Auto Scaling Groups, AWS Certificate Manager (ACM), Amazon Route 53.

### Summary
This architecture ensures high availability, scalability, and reliability by distributing the load, monitoring instance health, and scaling resources dynamically. The web tier serves the front end and routes API calls, the application tier handles business logic and interacts with the database, and the database tier provides robust data storage and retrieval.
