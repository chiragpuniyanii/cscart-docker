# CS-Cart Multi-Vendor Setup on Docker (EC2 Instance)

This repository contains the detailed steps and configuration required to install CS-Cart Multi-Vendor in a Docker container running on an EC2 instance with Ubuntu. The setup includes creating Docker containers for Apache, PHP, MySQL, and all necessary dependencies

## Prerequisites
Before starting, ensure you have the following:
- A **CS-Cart Multi-Vendor Zip** file (e.g., `multivendor_v4.18.2.SP1.zip`)
- **Amazon EC2** instance with **Ubuntu** installed
- **Docker and Docker Compose installed on the EC2 instance**
- **SSH key** to access the EC2 instance
- **Domain** or public IP address for your EC2 instance

## Steps for Setup

### Step 1: Download CS-Cart Multi-Vendor Zip
1. Go to [CS-Cart's website](https://www.cs-cart.com/) and download the **CS-Cart Multi-Vendor version**.
2. Save the file (e.g., `multivendor_v4.18.2.SP1.zip`) to your local machine.

### Step 2: Transfer Zip File from Local Machine to EC2 Instance
1. Open **PowerShell** or **Git Bash** on your Windows machine.
2. Use the following command to transfer the zip file to your EC2 instance:
   ```bash
   scp -i "C:\path\to\your\secret_key.pem" "C:\path\to\your\multivendor_v4.18.2.SP1.zip" ubuntu@<your-ec2-public-ip>:/home/ubuntu/

### Step 3: Install Dependencies
  *Ensure that Docker and Docker Compose are installed on your EC2 instance:*


    sudo apt-get update
    sudo apt-get install docker.io docker-compose -y

### Step 4: Setup Docker Environment
  **Create the Dockerfile**
  
  *Dockerfile*
  
  ***The Dockerfile for this setup is already present in the repository. This file configures PHP 8.1 with Apache and installs the necessary PHP extensions for running CS-Cart. You don't need to create it from scratch; just ensure that the Dockerfile is in the root 
  directory of your project.***


  **Create the docker-compose.yml**
  
  *docker-compose.yml*
  
***The docker-compose.yml file is also present in the repository. It manages the containers for your CS-Cart web server and MySQL database. Similarly, ensure this file is in the root directory.***

### Step 5: Build and Run Containers
**Now that all the necessary files are set up, build and run the Docker containers:**

**Build the Docker containers:**

    docker-compose up --build

Access your CS-Cart Multi-Vendor setup by visiting your EC2 instance's public IP (or localhost if running locally) in the browser.

## Step 6: Stopping and Restarting Containers
  **To stop the containers:**


    docker-compose down
  **To restart the containers:**


    docker-compose up

## Step 7: Database Setup
  **The docker-compose.yml file includes MySQL as a service. It is automatically configured with the following credentials:**

      MySQL Database Name: cscart_db
      MySQL User: cscart_user
      MySQL Password: chirag
      MySQL Root Password: chirag
      
Ensure that the database is running when you access the CS-Cart web application.

## Step 8: Additional Configuration
  **Make sure to configure your config.local.php file and other CS-Cart configuration settings after installation.**
