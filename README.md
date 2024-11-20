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

**1. Web Tier**: Handles client requests and serves the front-end website.

**2. Application Tier**: Processes API requests and handles the business logic.

**3. Database Tier**: Manages data storage and retrieval.

### Components explanation

#### 1. Web Tier
- **Role**: Serves the front-end of the application and redirects API calls.
- **Components**:
  - **Nginx Webservers**: Running on EC2 instances.
  - **React.js Website**: The front-end application served by Nginx.
- **Functionality**:
  - **Serving the Website**: Nginx serves the static files for the React.js application to the clients.
  - **Redirecting API Calls**: Nginx is configured to route API requests to the internal-facing load balancer of the application tier.

#### 2. Application Tier
- **Role**: Handles the application logic and processes API requests.
- **Components**:
  - **Node.js Application**: Running on EC2 instances.
- **Functionality**:
  - **Processing Requests**: The Node.js application receives API requests, performs necessary computations or data manipulations.
  - **Database Interaction**: Interacts with the Aurora MySQL database to fetch or update data.
  - **Returning Responses**: Sends the processed data back to the web tier via the internal load balancer.

#### 2. Database Tier (MySQL Database)
- **Role**: Provides reliable and scalable data storage.
- **Functionality**:
  - **Data Storage**: Stores all the application data in a structured format.
  - **Multi-AZ Setup**: Ensures high availability and fault tolerance by replicating data across multiple availability zones.
  - **Data Retrieval and Manipulation**: Handles queries and transactions from the application tier to manage the data.

### Additional Components
#### Load Balancing, Health Checks, Auto Scaling Groups, AWS Certificate Manager (ACM), Amazon Route 53.

### Summary
This architecture ensures high availability, scalability, and reliability by distributing the load, monitoring instance health, and scaling resources dynamically. The web tier serves the front-end and routes API calls, the application tier handles business logic and interacts with the database, and the database tier provides robust data storage and retrieval.
