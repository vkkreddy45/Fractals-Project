## Steps to Deploy

- Create a project on Google Cloud Platform Console associated with the correct billing account.
- Search and enable the following APIs:
    - Cloud Build
    - Cloud Shell
    - Cloud Functions
- Create a Cloud Storage Bucket to upload the screenshots of the fractals <!-- Add screenshots and highlight access selection-->

- Enter the name of your bucket:

![img.png](docs/img.png)

- Choose the region where you would like to store your data:

![img_1.png](docs/img_1.png)

- Choose default storage class for your data:

![img_2.png](docs/img_2.png)

- Choose how to control access to objects:

![img_3.png](docs/img_3.png)

- Type of data protection within secured Google Cloud Platform:

![img_4.png](docs/img_4.png)

- Sample fractal images added to the cloud bucket

![img_5.png](docs/img_5.png)

- Type of access initial given to image object:

![img_6.png](docs/img_6.png)

- Later, it can be changed to project requirements:

![img_7.png](docs/img_7.png)

- Once the access is changed according to requirements, you can view the public URL to access the image:

![img_9.png](docs/img_9.png)

- Enabled public access to remaining images:

![img_11.png](docs/img_11.png)

- Clone the forked git repo (git link)

- Install Google Cloud SDK Shell on local machine

- Login to your account and select the newly created project

- Change the current working directory to cloud/python

- Make the required changes on main.py and index.html

- Create the Cloud Function using the below command:

`Command: gcloud functions deploy fractals --runtime python39 --trigger-http --allow-unauthenticated`

## Code Changes 

- Modify the function name translate to fractals in main.py

- Clear the body of the html page

- Create labels for fractals with corresponding public URLs in index.html
