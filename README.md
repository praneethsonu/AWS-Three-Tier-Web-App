# AWS Three-Tier Web Architecture
# Description:
This project is a hands-on walkthrough of a three-tier web architecture in AWS. We will be manually creating the necessary network, security, app, and database components and configurations in order to run this architecture in an available and scalable manner.

# Tier Architecture explanation:
- **Web Server**: This is the front part of a web application that displays the website to users. It handles how the site looks and interacts with users, like showing product pages or allowing people to sign up.

- **Application Server**: This middle part manages the business logic and processes user actions. For example, it checks the inventory to see if a product is in stock or updates a user's account details.

- **Database Server**: This is the back-end part that stores all the data for the application. It uses databases like MySQL or PostgreSQL to keep track of information.
# Architecture Overview:

<img width="4176" alt="3TierArch" src="https://github.com/user-attachments/assets/8ea462dc-281a-4bfe-a092-52695ec5fec0">

In this architecture, we have three main layers:

**Web Tier**: Handles client requests and serves the front-end website.
**Application Tier**: Processes API requests and handles the business logic.
**Database Tier**: Manages data storage and retrieval.

# Components explanation:
**1. External Load Balancer (Public-Facing Application Load Balancer)**
- **Role**: This acts as the entry point for all client traffic.
- **Functionality**:
- Distributes incoming client requests to the web tier EC2 instances.
- Ensures even distribution of traffic for better performance and reliability.
- Performs health checks to ensure only healthy instances receive traffic.
2. Web Tier
Role: Serves the front-end of the application and redirects API calls.
Components:
Nginx Webservers: Running on EC2 instances.
React.js Website: The front-end application served by Nginx.
Functionality:
Serving the Website: Nginx serves the static files for the React.js application to the clients.
Redirecting API Calls: Nginx is configured to route API requests to the internal-facing load balancer of the application tier.
3. Internal Load Balancer (Application Tier Load Balancer)
Role: Manages traffic between the web tier and the application tier.
Functionality:
Receives API requests from the web tier.
Distributes these requests to the appropriate EC2 instances in the application tier.
Ensures high availability and load balancing within the application tier.
4. Application Tier
Role: Handles the application logic and processes API requests.
Components:
Node.js Application: Running on EC2 instances.
Functionality:
Processing Requests: The Node.js application receives API requests, performs necessary computations or data manipulations.
Database Interaction: Interacts with the Aurora MySQL database to fetch or update data.
Returning Responses: Sends the processed data back to the web tier via the internal load balancer.
5. Database Tier (Aurora MySQL Multi-AZ Database)
Role: Provides reliable and scalable data storage.
Functionality:
Data Storage: Stores all the application data in a structured format.
Multi-AZ Setup: Ensures high availability and fault tolerance by replicating data across multiple availability zones.
Data Retrieval and Manipulation: Handles queries and transactions from the application tier to manage the data.


