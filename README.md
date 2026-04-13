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
- Smart search systems (eg. search by image content)
- Content moderation and filtering (eg. detect unsafe or inappropriate content, flag or block harmful images)

---
## 👤 Author
JoDic2026



