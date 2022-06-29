# Cloud Run deployment - [Project - Python with GCP]

---

# 1. Cloud Run

## Steps for Deployment

- Create a New Project in GCP Console associated with the correct billing account.
- Create a Empty git repository
- Initially we should enable Google cloud build API and Container Registry.
- The created repositiry mainly follows the flask file structure. Its looks like below figure.
<img width="372" alt="Screen Shot 2022-04-30 at 11 58 12 AM" src="https://user-images.githubusercontent.com/98420519/166115323-d03519ba-9278-4056-814d-8a309b0be542.png">

- From the above structure Dockerfile and cloudbuild.yaml are the mandatory files for automating the complete process.
---
- To create docker image and push to your GCP project we follow the below commands:
    - docker build .
    - docker images
- Initially, when we run the docker images command we will have the repository as <None>, tag as latest, image id as some value, created as hrs/days/months, size as amount of size used.
- Copy the latest image id and paste it in the command below:
[docker tag <latest-image-id> gcr.io/[project id]/[project name]]
- Now when we give the above command repository name and docker image will be allocated. 
---
- To configure docker authentication after logging into gcloud, we run the below command:
[gcloud auth configure-docker]
- First, we need to enable the conatiner registry and cloud build.
-  Then use the command below to push the docker image to container
``` docker push <REPOSITORY-NAME>```
- The above command will create the docker image in the cloud registry
- The as above cloud build api is enabled.
- Now create a cloud Run serverless function with the latest docker image created.
- Deploy it with the initial revision.
- Then edit the revision by changing port number to PORT-80
- This gives the initial app for the website and it is the default process , this entire process and workflow can be defined
    below image
    
![Web 1920 – 1](https://user-images.githubusercontent.com/52027911/166115561-9ab403b8-62be-46cd-9034-07f81d57bc63.png)
    
* Now we must automate this process because everytime we make changes to project the entire process should be automated.
    Here is the workflow that depicts the automation process
    
    
![Web 1920 – 2](https://user-images.githubusercontent.com/52027911/166115588-7f67abc3-4948-4efc-8943-2e19f2e33aed.png)

- First, we create a git repository and add all the required files to the repository.
- We must configure the cloudbild.yaml accordingly to your projectid.
<img width="819" alt="Screen Shot 2022-04-30 at 12 27 20 PM" src="https://user-images.githubusercontent.com/98420519/166116020-4a16844c-1fca-48f3-8cbb-f85ad80ee58e.png">
    
Cloud Docs - https://cloud.google.com/build/docs/deploying-builds/deploy-cloud-run

- Now we must create a trigger using cloud build api. The trigger fires when a change is made to the git repository. we must add repository in order to trigger the event.
    
<img width="1433" alt="Screen Shot 2022-04-30 at 12 31 41 PM" src="https://user-images.githubusercontent.com/98420519/166116150-72554604-6744-482b-b6a9-3a61844f9cc9.png">

- Now every time we create changes and push to a commit it'll trigger event creates a docker image (latest)
    
![image](https://user-images.githubusercontent.com/52027911/166116361-a151ec3c-78d6-4ad8-ba0b-6042adea8d18.png)
    
- A new revision will be added on the cloud run after creation of latest images.
    
![image](https://user-images.githubusercontent.com/52027911/166116426-6678d834-1e46-4c8d-9b4a-89b1029aff85.png)
And Updates are made and changes can be viewed in the latest revision.
    
Here is the actual GitHUB-https://github.com/bhargavvummadi/demo-fractals  repo used for automation.
    
    
    


