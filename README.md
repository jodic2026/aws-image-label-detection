# AWS Image Label Detection System

## 📌 Project Overview
This project is a cloud-based image labeling system built using Amazon Rekognition. It analyzes images stored in Amazon S3 and automatically generates descriptive labels with confidence scores.

---

## Tech and Enviroments Used
- AWS Rekognition
- Amazon S3
- IAM
- Python
- Boto3
- Matplotlib

---

## Terminologies

☁️ S3 (Simple Storage Service) - A cloud storage service from Amazon Web Services used to store and retrieve files like images, videos, and documents.

💻 AWS Command Line Interface (CLI) - A tool that lets you interact with AWS services (like S3 or EC2) using commands in your terminal instead of the web console.

🐍 boto3 - The official Python SDK for AWS that allows Python code to communicate with AWS services like Amazon S3 and Amazon Rekognition.

📊 matplotlib - A Python library used for creating graphs and visualizations. In the project, it’s used to display images and draw bounding boxes.

🖼️ PIL (Python Imaging Library) - A Python library (via Pillow) used to open, manipulate, and process images.

🔄 BytesIO - A class from Python’s built-in io module that allows you to handle binary data (like images) in memory as if it were a file.

🔐 IAM (Identity and Access Management) - A service in Amazon Web Services that controls who can access AWS resources and what actions they are allowed to perform.

🪣 Amazon S3 Bucket - A container in Amazon S3 where files (e.g. images) are stored in the cloud.

📦 Importing Libraries - The process of loading external Python modules (like boto3 or matplotlib) into the script so their functions can be used. 

---
## Architecture Diagram
<img width="1038" height="630" alt="Architecture" src="https://github.com/user-attachments/assets/d0f04642-8c4a-4065-9d71-bec4ed2fb48d" />

---

## Workflow
1. Upload image to Amazon S3  
2. Python script sends request to AWS Rekognition  
3. Rekognition analyzes the image  
4. Labels + confidence scores are returned  
5. Results are displayed and visualized  


---
## How To Build

1) Create an Amazon S3 Bucket, assign a bucket name, and upload the photo to be analyzed. 
<img width="816" height="481" alt="image" src="https://github.com/user-attachments/assets/39cf01e0-353a-4c7b-9644-ebfdab3cb8ec" />

In this project, I will be using a sample from Makati City. 

![Makati City 2](https://github.com/user-attachments/assets/5cbb64e7-818d-4599-9373-182632a438be)

<img width="1647" height="611" alt="image" src="https://github.com/user-attachments/assets/f2e03c87-16e1-44ca-a1a9-6b69f902424c" />

2) We need to install the AWS Command Line Interface so that we can interact with AWS Services using commands from our terminal. 

<img width="1109" height="615" alt="image" src="https://github.com/user-attachments/assets/78831159-a777-44de-99cf-8bf9c2963202" />


3) After installation, we will configure the AWS CLI by entering the command, 
- aws configure

Running this command will ask for both the access key and the secret access key. 
We need these credentials to access and authenticate our AWS account from the AWS CLI.

In order get these access keys, we need to go back to AWS Management Console and search for IAM in the search bar -> Go to Users -> Create User. Since I am using an AWS Sandbox and user is already automatically created for me, I will proceed to the next step. 

(For those who needs to create user, just assign a user name -> click Next -> For the Permission options, choose the option ‘Attach policies directly’ and attach the ‘AdministratorAccess’ policy.)

<img width="1069" height="282" alt="image" src="https://github.com/user-attachments/assets/92bcc795-f58c-4fd3-aa45-7848d523c49d" />

<img width="1700" height="463" alt="image" src="https://github.com/user-attachments/assets/158bec99-c65c-484a-8486-6b72f35282e9" />

4) Since account is already made for me, I went to Security Credentials -> Create access key -> Use Case -> Command Line Interface (CLI) -> assign a description tag value -> get your access keys. 

<img width="1360" height="374" alt="image" src="https://github.com/user-attachments/assets/6833d109-4e4f-4d0c-a772-2d3f5f4e438a" />



## Sample Output




## Conclusion





---
## Roadblocks/Challenges: 
- The experience of doing this project would have been elevated I understood Python script. 
- I was encountering errors because I was not saving the script in IDE.

---

## 💡 What I Learned

- How to store and retrieve data from Amazon S3
- How to configure AWS CLI for secure access
- How to integrate AWS Rekognition with Python
- How cloud-based image recognition works in real-world scenarios

---

## 🌍 Use Cases
- Automated image tagging for content platforms (eg. automatically tag product images, categorize items (shoes, bags, electronics), improve search results for users)
- Smart search systems (eg. search by image content instead of text)
- Content moderation and filtering (eg. detect unsafe or inappropriate content, flag or block harmful images)

---
## 👤 Author
JoDic2026



