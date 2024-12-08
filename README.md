# CI/CD Pipeline Workflow for Python Application

---

## **🚀 Description**
This GitHub Actions workflow automates the **building**, **testing**, and **deploying** of a Python application as a Docker image to DockerHub. It enhances development efficiency and ensures code quality through automation.

<p align="center">
  <img src="" alt="CI/CD Workflow Animation" width="600"/>
</p>

---

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



