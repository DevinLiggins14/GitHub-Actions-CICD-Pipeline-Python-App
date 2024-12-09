# CI/CD Pipeline Workflow for Python Application

---

## Description:
This GitHub Actions workflow automates the **building**, **testing**, and **deploying** of a Python application as a Docker image to DockerHub. It enhances development efficiency and ensures code quality through automation.

## **✨ Key Features**

### **Trigger**  
- Initiates automatically when code is pushed to the `main` branch.

### **Pipeline Jobs**
1. **🛠️ Build Job:**  
   - Builds and pushes a Docker image to DockerHub.  
2. **🧪 Test Job:**  
   - Runs unit tests to validate the Python application.

---

## **📋 Visual Workflow**

| **Stage**           | **Purpose**                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Code Commit**      | Triggered by a push to the `main` branch.                                   |
| **Build**            | Creates and publishes a Docker image to DockerHub.                         |
| **Test**             | Validates application reliability through automated unit tests.            |

---

## **🔑 Secrets Configuration**

Add these secrets to your GitHub repository:
| **Secret Name**      | **Purpose**                                   |
|-----------------------|-----------------------------------------------|
| `DOCKERHUB_USERNAME` | DockerHub username for authentication.        |
| `DOCKERHUB_TOKEN`    | DockerHub personal access token for login.    |

---

## **📖 Step-by-Step Guide**

### **Step 1: Set Up GitHub Actions Workflow**
1. Navigate to your repository's **Actions** tab.
2. Click **New Workflow** and choose **Set Up a Workflow Yourself**.
3. Save the following workflow file as `.github/workflows/main.yml`.


<img src="https://github.com/user-attachments/assets/72a5aa44-67ea-435d-b430-532221420689"/>
<br/> The pipline will begin but we will see it has failed since the DockerHub account and password has not been defined <br/> 
<img src="https://github.com/user-attachments/assets/7a81903d-4c0b-413d-87ac-b8e57b152494"/>



## Step 2: Define the DockerHub account user name and password 

<br/> Go to Secrets and Variables within GitHub  to configure the DockerHub user name and password <br/> 

<img src="https://github.com/user-attachments/assets/158d4434-ed7c-4eec-a5aa-953b600a2f95"/>
<br/> Enter the correct information <br/>

<br/> That worked but we have another error: <br/>
<img src="https://github.com/user-attachments/assets/0ceabded-9bab-4bd8-baf1-529b5f5b2538"/>
<br/> This error is because the Dockerfile is in the incorrect path within GitHub, it should be in GitHub-Actions-CICD-Pipeline-Python-App/Dockerfile (Double check the other file paths as well),
 <br/> 

 <img src="https://github.com/user-attachments/assets/3f756870-d064-4010-ac38-e22f4f686fa2"/>
<br/> Fixed, now lets check the actions tab since it will be automatically updated once new code has been added automatically. <br/>
 <img src="https://github.com/user-attachments/assets/36c0d73f-d58c-4d95-9501-fededefc2ffe"/>
<br/> It appears the test was successful but the test was not <br/>

<br/> The Docker image is even visible now on my DockerHub profile <br/> 
<img src="https://github.com/user-attachments/assets/4d621790-191a-4fd6-876b-1752686a9f7b"/>
<br/> Now to investigate why the test was unsuccessful <br/>
<img src="https://github.com/user-attachments/assets/7ae5bbb1-5d19-4c09-ae7b-ac084f920216"/>
<img src="https://github.com/user-attachments/assets/9dee360a-77f5-4eb7-bab2-169cbc54673f"/>
<br/> This issue appears to be from the Flask application trying to import url_quote from werkzeug.urls, but that function no longer exists in recent versions of Werkzeug. This is due to breaking changes introduced in Werkzeug 2.0 and later.<br/> 

<br/> To fix this make an edit to requirements.txt to add Werkzeug==2.2.3 in addition to Flask==2.2.3. This ensures that no incompatible version will be installed. <br/>

<br/> Let's view the testing and possible deployment now <br/>
<img src="https://github.com/user-attachments/assets/eb5a11e3-34c5-497a-a761-15713c9f175a"/>
<br/> The build and testing worked! Now got to DockerHub to confirm <br/>
<img src="https://github.com/user-attachments/assets/355b0c57-1d73-4715-8882-2b0bcee4c3a0"/>
<img src="https://github.com/user-attachments/assets/ee33853d-0a0a-4c82-a1d5-c97644db0bf9"/>
<br/> Since the application is supposed to be fully functional I will pull the image from DockerHub onto a local linux machine and attempt to access from a browser. I will copy the command listed within the DockerHub repository to pull the image <br/>

```Bash
docker pull dlliggins/my-image:latest
```

<img src="https://github.com/user-attachments/assets/28c2a313-4e08-4bf2-9f53-608c1acc74e9"/>
<br/> Now that I have pulled the docker image locally onto the linux server I will run it as a container and expose port 8080 to access it in a browser <br/> 

```Bash
docker run -d -p 8080:8080 dlliggins/my-image:latest
```

<img src="https://github.com/user-attachments/assets/b6b68861-4973-49b3-939a-0b2840b15a61"/>
<img src="https://github.com/user-attachments/assets/68dd43c5-16c8-4efa-8fc0-6b965289d641"/>

<br/> Success! By automating the build, test, and deployment processes with GitHub Actions, the development cycle has been streamlined and ensures that only stable, tested code reaches production. The pipeline ensures continuous delivery 
 <br/>
