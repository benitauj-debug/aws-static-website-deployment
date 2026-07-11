# aws-static-website-deployment
Deployed a static e-commerce website on AWS EC2 using Ubuntu, Nginx, a custom domain, and HTTPS with  SSL.

Project Documentation
Project Title
Deploying and Hosting a Secure Static Website on AWS EC2 with Nginx and HTTPS

Project Overview
This project demonstrates how I deployed and hosted a static e-commerce website on Amazon Web Services (AWS) using an Ubuntu EC2 instance. The website was configured with Nginx as the web server, connected to a custom domain purchased through Dynadot, and secured with a free SSL certificate from Let's Encrypt using Certbot.
The goal was to gain hands-on experience with cloud infrastructure, Linux administration, web servers, networking, DNS configuration, and HTTPS implementation.

Project Architecture
User
   │
   ▼
Custom Domain (Dynadot)
   │
DNS Records
   │
   ▼
AWS EC2 Instance
(Ubuntu)
   │
Nginx Web Server
   │
Static Website Files
(HTML, CSS, JavaScript, Images)


Technologies Used
Cloud Platform
• Amazon EC2 (AWS Free Tier)
Operating System
• Ubuntu Server
Web Server
• Nginx
Security
• Let's Encrypt
• Certbot SSL
Networking
• VPC
• Public Subnet
• Internet Gateway
• Route Table
• Security Groups
Domain Registrar
• Dynadot
Connection Tool
• MobaXterm (SSH)

Objectives
The objectives of this project were:
• Launch an Ubuntu EC2 instance
• Configure AWS networking
• Connect remotely using SSH
• Install and configure Nginx
• Register a custom domain
• Configure DNS records
• Enable HTTPS using SSL
• Deploy a static website

Implementation Steps
Step 1
Created an AWS Free Tier account.

Step 2
Created an EC2 Ubuntu instance.
Selected:
• Ubuntu Server
• Free Tier eligible
• Generated a PEM key pair

Step 3
Configured networking.
Configured:
• VPC
• Public Subnet
• Internet Gateway
• Route Table
• Security Group
Opened the following ports:
SSH (22)
HTTP (80)
HTTPS (443)

Step 4
Connected to the server using MobaXterm.
Used:
ssh -i key.pem ubuntu@Public-IP

Successfully accessed the Linux server.

Step 5
Updated Ubuntu.
sudo apt update
sudo apt upgrade -y


Step 6
Installed Nginx.
sudo apt install nginx -y

Verified installation.
sudo systemctl status nginx

Visited the server's public IP and confirmed the default Nginx page was displayed.

Step 7
Purchased a custom domain from Dynadot.
Configured DNS.
Created:
A Record
Pointed the domain to the EC2 public IP address.
Waited for DNS propagation.

Step 8
Verified domain mapping.
Visited:
http://roserencollections.xyz

Confirmed the domain was pointing to the server.

Step 9
Installed Certbot.
Installed Snap.
Installed Certbot.
Installed the Nginx plugin.
Verified installation.

Step 10
Generated SSL Certificate.
Executed:
sudo certbot --nginx -d roserencollections.xyz

Accepted the terms.
Registered an email.
Certificate was successfully issued.
HTTPS was automatically configured.

Step 11
Verified SSL.
Visited:
https://roserencollections.xyz

Confirmed HTTPS was enabled.

Step 12
Located the website root directory.
Verified Nginx root.
sudo nginx -T | grep root

Found:
/var/www/html


Step 13
Removed the default Nginx page.
Deleted:
index.nginx-debian.html


Step 14
Uploaded the website files.
Used the MobaXterm SFTP browser.
Transferred:
• HTML
• CSS
• Images
• JavaScript
• Other website assets

Challenges Encountered
 Could not locate the website directory
Issue
Attempted:
cd/var/www/html

Result
No such file or directory

Cause
Forgot to leave a space after the cd command.
Solution
Used:
cd /var/www/html


 Certbot installation errors
Issue
Initially received:
unrecognized arguments

Cause
Incorrect command syntax.
Solution
Corrected the command and successfully generated the SSL certificate.

 Default Nginx page still displayed
Issue
After SSL setup, the website still showed:
"Welcome to nginx"
Cause
The default index page had not been removed.
Solution
Deleted:
index.nginx-debian.html


 Permission denied in MobaXterm
Issue
Received:
SFTP Permission Denied

Cause
The directory belonged to the root user.
Solution
Changed ownership:
sudo chown -R ubuntu:ubuntu /var/www/html

Updated permissions:
sudo chmod -R 755 /var/www/html

Successfully uploaded the files afterwards.

5. Images and CSS not displaying
Issue
The website loaded as plain text without styling or images.
Cause
The upload process had not fully completed, and the folder structure needed to be preserved.
Resolution
Continued uploading all files and folders while verifying the web root and asset locations.

Skills Demonstrated
Linux Administration
AWS EC2
SSH Remote Access
DNS Configuration
SSL Certificate Installation
Nginx Configuration
Cloud Networking
Web Server Management
Domain Management
Troubleshooting
Problem Solving

Lessons Learned
I learned how cloud infrastructure components work together to deliver a live website over the internet. I gained practical experience configuring AWS networking, deploying applications on Linux servers, managing web servers, securing websites with HTTPS, troubleshooting deployment issues, and resolving file permission and directory structure problems.
I also learned the importance of understanding how static websites reference CSS, JavaScript, and image assets, as incorrect file placement can prevent a website from rendering properly.

Outcome
Successfully:
• Launched an Ubuntu EC2 instance
• Configured networking
• Connected through SSH
• Installed Nginx
• Connected a custom domain
• Enabled HTTPS with Let's Encrypt
• Deployed a static website to the cloud
• Diagnosed and resolved deployment issues related to permissions, directory structure, and web server configuration
