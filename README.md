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

1) Create an Amazon S3 Bucket and Upload an Image

I started by creating an Amazon S3 bucket, assigning it a unique name, and uploading the image that I want to analyze.

For this project, I used a sample image from Makati City.
<img width="816" height="481" alt="image" src="https://github.com/user-attachments/assets/39cf01e0-353a-4c7b-9644-ebfdab3cb8ec" />

<img width="1647" height="611" alt="image" src="https://github.com/user-attachments/assets/f2e03c87-16e1-44ca-a1a9-6b69f902424c" />





2) Install AWS Command Line Interface (CLI) 
Next, I installed the AWS Command Line Interface (CLI), which allows me to interact with AWS services directly from my terminal using commands.
<img width="1109" height="615" alt="image" src="https://github.com/user-attachments/assets/78831159-a777-44de-99cf-8bf9c2963202" />





3) Configure the AWS CLI
After installation, I configured the AWS CLI by running the following command:

aws configure

This command prompted me to enter my AWS Access Key ID and Secret Access Key. These credentials are required to authenticate and access my AWS account through the CLI.

To generate these access keys, I went to the AWS Management Console and searched for IAM → Users → Create User.

Since I am using an AWS Sandbox environment where a user is already pre-configured, I skipped the user creation step and proceeded to generating access keys.

(For those who need to create a user: assign a username → click Next → select “Attach policies directly” → attach the “AdministratorAccess” policy.)

<img width="1069" height="282" alt="image" src="https://github.com/user-attachments/assets/92bcc795-f58c-4fd3-aa45-7848d523c49d" />

<img width="1700" height="463" alt="image" src="https://github.com/user-attachments/assets/158bec99-c65c-484a-8486-6b72f35282e9" />

After that, I navigated to Security Credentials → Create Access Key → Command Line Interface (CLI), added a description tag, and generated my access keys.

<img width="1360" height="374" alt="image" src="https://github.com/user-attachments/assets/6833d109-4e4f-4d0c-a772-2d3f5f4e438a" />

I then returned to the CLI and entered my credentials. It looked like this:

<img width="485" height="107" alt="image" src="https://github.com/user-attachments/assets/714e7f14-3696-4f87-b509-9dbf83c24cea" />


At this point, I successfully configured the AWS CLI.





4) Set Up My Development Environment

I installed my preferred IDE (Virtual Studio Code) and created a .py file for this project.

Next, I opened a terminal and installed the required libraries:

pip install boto3
pip install matplotlib

5) Import Required Libraries
I then added the necessary libraries for this project:

import boto3
import matplotlib.pyplot as plt
import matplotlib.patches as patches
from PIL import Image
from io import BytesIO

boto3 to interact with AWS services
matplotlib for visualization
PIL (Python Imaging Library) to handle image data
BytesIO from the io module to process image data in memory


<img width="1477" height="788" alt="image" src="https://github.com/user-attachments/assets/1371b8a5-9994-46f3-baab-311fe5120a19" />

6) Define the detect_labels Function
Next, I defined a function called detect_labels. This function accepts a photo and a bucket name as input parameters.

Within the function, I perform the following steps:

I create an Amazon Rekognition client using boto3.
I call the detect_labels method to analyze the image stored in the S3 bucket.
I print the detected labels along with their confidence scores.
I retrieve the image from the S3 bucket using boto3 and process it using PIL.
I use matplotlib to display the image and draw bounding boxes around the detected objects.



def detect_labels(photo, bucket):
    # Create a Rekognition client
    client = boto3.client('rekognition')

    # Detect labels in the photo
    response = client.detect_labels(
        Image={'S3Object': {'Bucket': bucket, 'Name': photo}},
        MaxLabels=10)

    # Print detected labels
    print('Detected labels for ' + photo)
    print()
    for label in response['Labels']:
        print("Label:", label['Name'])
        print("Confidence:", label['Confidence'])
        print()

    # Load the image from S3
    s3 = boto3.resource('s3')
    obj = s3.Object(bucket, photo)
    img_data = obj.get()['Body'].read()
    img = Image.open(BytesIO(img_data))

    # Display the image with bounding boxes
    plt.imshow(img)
    ax = plt.gca()
    for label in response['Labels']:
        for instance in label.get('Instances', []):
            bbox = instance['BoundingBox']
            left = bbox['Left'] * img.width
            top = bbox['Top'] * img.height
            width = bbox['Width'] * img.width
            height = bbox['Height'] * img.height
            rect = patches.Rectangle((left, top), width, height, linewidth=1, edgecolor='r', facecolor='none')
            ax.add_patch(rect)
            label_text = label['Name'] + ' (' + str(round(label['Confidence'], 2)) + '%)'
            plt.text(left, top - 2, label_text, color='r', fontsize=8, bbox=dict(facecolor='white', alpha=0.7))
    plt.show()

    return len(response['Labels'])



7) Create the main Function

After defining the detect_labels function, I created a main function to test it.

In this step:

I specify the image file name and S3 bucket name.
I call the detect_labels function using these parameters.
I print the total number of detected labels.

(Note: I made sure to replace 'image_file_name' and 'bucket_name' with my actual values.)


def main():
    photo = 'image_file_name'
    bucket = 'bucket_name'
    label_count = detect_labels(photo, bucket)
    print("Labels detected:", label_count)
if __name__ == "__main__":
    main()


<img width="424" height="165" alt="image" src="https://github.com/user-attachments/assets/61bc256b-c21f-4ef5-ae54-4b56c18dd481" />






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



